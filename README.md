# Worst Fit RCE Nuclei Template

## Description
This Nuclei template identifies a **Remote Code Execution (RCE)** vulnerability that leverages Windows' "Best Fit" mapping of Unicode fullwidth characters. When certain UTF-16 characters are processed, they can be misinterpreted as ANSI equivalents, allowing attackers to bypass input validation and inject malicious commands. This vulnerability primarily affects systems that process user input without proper sanitization before passing it to shell commands.

## Exploit Details
- **Vulnerability Type**: Command Injection via Fullwidth Character Encoding
- **Platform**: Windows
- **Mechanism**: Exploitation of Windows' "Best Fit" mapping to inject arbitrary commands through the use of fullwidth characters.

### Example Payload
```http
POST /vulnerable-endpoint HTTP/1.1
Host: target-site.com
Content-Type: application/x-www-form-urlencoded

input=＂ --use-askpass=calc ＂


Explanation: The payload uses fullwidth quotation marks (＂) to bypass input sanitization. If executed, this command launches the Windows Calculator (calc.exe), demonstrating the RCE.


https://worst.fit/assets/EU-24-Tsai-WorstFit-Unveiling-Hidden-Transformers-in-Windows-ANSI.pdf
