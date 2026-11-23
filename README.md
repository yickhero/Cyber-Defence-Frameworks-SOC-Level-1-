# Cyber-Defence-Frameworks-SOC-Level-1-
Here is my note after finishing cyber defence framework module from tryhackme
# Pyramid of Pain

### Common Hashing Algorithms
A hash is not considered to be cryptographically secure if two files have the same hash value or digest.

1. **MD5 (Message Digest, defined by RFC 1321):** Designed by Ron Rivest in 1992, this is a widely used cryptographic hash function with a 128-bit hash value. MD5 hashes are **NOT** considered cryptographically secure. In 2011, the IETF published RFC 6151 ("Updated Security Considerations for the MD5 Message-Digest and the HMAC-MD5 Algorithms"), which mentioned a number of attacks against MD5 hashes, including hash collisions.
2. **SHA-1 (Secure Hash Algorithm 1, defined by RFC 3174):** Invented by the United States National Security Agency in 1995. When data is fed to the SHA-1 Hashing Algorithm, it takes an input and produces a 160-bit hash value string as a 40-digit hexadecimal number. NIST deprecated the use of SHA-1 in 2011 and banned its use for digital signatures at the end of 2013 based on it being susceptible to brute-force attacks. Instead, NIST recommends migrating from SHA-1 to stronger hash algorithms in the SHA-2 and SHA-3 families.
3. **SHA-2 (Secure Hash Algorithm 2):** Designed by the National Institute of Standards and Technology (NIST) and the National Security Agency (NSA) in 2001 to replace SHA-1. SHA-2 has many variants, and arguably the most common is **SHA-256**, which returns a hash value of 256-bits as a 64-digit hexadecimal number.

### Fast Flux
* Fast Flux is a DNS technique used by botnets to hide phishing, web proxying, malware delivery, and malware communication activities behind compromised hosts acting as proxies.
* The purpose of using a Fast Flux network is to make the communication between malware and its command and control server (C&C) challenging to be discovered by security professionals.
* The primary concept of a Fast Flux network is having multiple IP addresses associated with a domain name, which is constantly changing.

### Network Artifacts
* A network artifact can be a user-agent string, C2 information, or URI patterns followed by HTTP POST requests.
* An attacker might use a User-Agent string that hasn’t been observed in your environment before or seems out of the ordinary. The User-Agent is defined by RFC2616 as the request-header field that contains the information about the user agent originating the request.
* Network artifacts can be detected in PCAPs (files that contain network packet dumps) by using a tool such as Wireshark or TShark, or by exploring IDS (Intrusion Detection System) alerts from a tool such as Snort.

### TTPs
* **TTPs** stands for **Tactics, Techniques & Procedures**.
* This includes the whole MITRE ATT&CK Matrix, which means all the steps taken by an adversary to achieve their goal, starting from phishing attempts to persistence and data exfiltration.

---

# Cyber Kill Chain

### The 7 Attack Phases
1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control
7. Actions on Objectives

### 1. Reconnaissance
The research and planning phase of an attack against a system or victim.
* **OSINT (Open-Source Intelligence):** A valuable piece of recon where adversaries gather insights about their target through publicly available information. Public sources include:
  * Search engines
  * Print and online media
  * Social media accounts
  * Online forums and blogs
  * Online public record databases
  * WHOIS and technical data
* **Passive Recon:** Involves having no direct interaction with the target. This may include WHOIS lookups, social media scraping, or reviewing breach data.
* **Active Recon:** Involves direct contact with the target with activities such as social engineering, port scanning, banner grabbing, or probing for open services.
* **Recon Tools:**
  * **theHarvester:** Other than gathering emails, this tool is also capable of gathering names, subdomains, IPs, and URLs using multiple public data sources.
  * **Hunter.io:** An email hunting tool that will let you obtain contact information associated with the domain.
  * **OSINT Framework:** Provides a collection of OSINT tools based on various categories.

### 2. Weaponization
Turning raw information into actionable attack tools through crafting malware and exploits into a payload.
* **Malware:** A program or software that is designed to damage, disrupt, or gain unauthorized access to a computer.
* **Exploits:** Programs or code that take advantage of a vulnerability or flaw in an application or system.
* **Payload:** Malicious code that the attacker runs on the system.
* **Weaponization Phase Techniques:**
  * Create an infected Microsoft Office document containing malicious macros or VBA (Visual Basic for Applications) scripts.
  * Create a malicious payload or a very sophisticated worm, implant it on USB drives, and then distribute them in public.
  * Set up Command and Control (C2) infrastructure for executing commands on the victim's machine or delivering more payloads.
  * Infect the victim's host with a backdoor, which provides a way to access the computer system and bypass security mechanisms.
  * Tailoring phishing templates or OAuth-consent apps to look legitimate and dupe the victim.

### 3. Delivery
Choosing the method for transmitting the payload or malware onto the target environment.
* **Delivery Options:** Phishing emails, USB drives, redirecting websites (watering hole attacks).

### 4. Exploitation
The moment the attacker's code executes on the target, taking advantage of a known vulnerability.
* **Key Techniques:**
  * **Malicious Macro Execution:** May have been delivered through a phishing email, executing ransomware when the victim opens it.
  * **Zero-Day Exploits:** Leverages unknown and unpatched flaws in a system, leaving no opportunity for detection at the beginning.
  * **Known CVEs:** The attacker chooses to exploit unpatched public vulnerabilities found on the target environment.
* **Signs of Exploitation:**
  * Unexpected process spawns.
  * Registry changes or new services created.
  * Suspicious command-line arguments found in system logs.

### 5. Installation
Establishing persistence on the target system. A persistent backdoor can be achieved through:
* Installing a web shell on the webserver.
* Installing a backdoor on the victim's machine.
* Creating or modifying Windows services (known as **T1543.003** on MITRE ATT&CK).
* Adding an entry to the "run keys" for the malicious payload in the Registry or the Startup Folder.

### 6. Command & Control (C2)
Establishing a C2 channel through the malware to remotely control and manipulate the victim.

### 7. Actions on Objectives
Taking action on the original objectives of the attack.

---

# Unified Kill Chain

### Threat Modelling
In a cybersecurity context, threat modelling is a series of steps to ultimately improve the security of a system. It is about identifying risk and essentially boils down to:
1. Identifying what systems and applications need to be secured and what function they serve in the environment (e.g., is the system critical to normal operations, and is it holding sensitive information like payment info or addresses?).
2. Assessing what vulnerabilities and weaknesses these systems and applications may have and how they could potentially be exploited.
3. Creating a plan of action to secure these systems and applications from the vulnerabilities highlighted.
4. Putting in policies to prevent these vulnerabilities from occurring again where possible (e.g., implementing an SDLC for an application or training employees on phishing awareness).

### Unified Kill Chain Goals
* **The "Through" Goal:** Follows a successful foothold being established on the target network. It includes: pivoting, discovery, privilege escalation, execution, credential access, and lateral movement.
* **The "Out" Goal:** Wraps up the journey of an adversary’s attack on an environment, where they have critical asset access and can fulfil their attack goals. It includes: collection, exfiltration, impact, and objectives.

---

# MITRE

### MITRE ATT&CK Framework
The **MITRE ATT&CK** framework is a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations. In 2013, MITRE recognized the need to document and categorize the standard tactics, techniques, and procedures (TTPs) used by advanced persistent threat (APT) groups.

* **Tactic:** An adversary's goal or objective. The "why" of an attack.
* **Technique:** How an adversary achieves their goal or objective.
* **Procedure:** The implementation, or how the technique is executed.

| Who | Their Goal | How They Use ATT&CK |
| :--- | :--- | :--- |
| **Cyber Threat Intelligence (CTI) Teams** | Collect and analyze threat information to improve an organization's security posture. | Map observed threat actor behavior to ATT&CK TTPs to create profiles that are actionable across the industry. |
| **SOC Analysts** | Investigate and triage security alerts. | Link activity to tactics and techniques to provide detailed context for alerts and prioritize incidents. |
| **Detection Engineers** | Design and improve detection systems. | Map SIEM/EDR and other rules to ATT&CK to ensure better detection efforts. |
| **Incident Responders** | Respond to and investigate security incidents. | Map incident timelines to MITRE tactics and techniques to better visualize the attack. |
| **Red & Purple Teams** | Emulate adversary behavior to test and improve defenses. | Build emulation plans and exercises aligned with techniques and known group operations. |

### Cyber Analytics Repository (CAR)
* MITRE defines the **Cyber Analytics Repository (CAR)** as a knowledge base of analytics developed by MITRE based on the MITRE ATT&CK adversary model.
* CAR is a collection of ready-made detection analytics built around ATT&CK, defining a data model leveraged in pseudocode representations as well as implementations directly targeted at specific tools (e.g., Splunk, EQL, LogPoint).
* Each analytic describes how to detect an adversary's behavior, providing a description, references to associated ATT&CK tactics and techniques, and an **Implementations** section with pseudocode and example SIEM queries so defenders can translate ATT&CK TTPs into real detections.

### D3FEND
* **D3FEND (Detection, Denial, and Disruption Framework Empowering Network Defense)** is a structured framework that maps out defensive techniques and establishes a common language for describing how security controls work.
* D3FEND comes with its own matrix, broken down into seven tactics, each with its associated techniques and IDs.
* *Example:* **Credential Rotation (`D3-CRO`)** emphasizes the regular rotation of passwords to prevent attackers from reusing stolen credentials. D3FEND explains how this defense works, what to consider when implementing it, and how it relates to specific digital artifacts and ATT&CK techniques, helping you see both the attacker's move and the defender's countermeasure.

### Adversary Emulation Library & Caldera
* **MITRE's Adversary Emulation Library:** Primarily maintained and contributed to by The Center for Threat Informed Defense (CTID), this is a free resource of adversary emulation plans. It contains step-by-step guides on how to mimic real-world attacks by known threat groups.
* **Caldera:** An automated adversary emulation tool designed to help security teams test and enhance their defenses. It simulates real-world attacker behavior utilizing the ATT&CK framework, allowing defenders to evaluate detection methods and practice incident response in a controlled environment. Caldera supports both offensive and defensive operations for red and blue team exercises.

### Specialized MITRE Frameworks
* **AADAPT (Adversarial Actions in Digital Asset Payment Technologies):** A newly released knowledge base with its own matrix covering adversary tactics and techniques related to digital asset management systems. Following a similar structure to ATT&CK, it helps defenders understand and mitigate threats targeting blockchain networks, smart contracts, digital wallets, and other digital asset technologies.
* **ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems):** A knowledge base and framework with its own matrix focusing on threats targeting artificial intelligence and machine learning systems. It documents real-world attack techniques, vulnerabilities, and mitigations specific to AI technology.
