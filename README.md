# Linux System Hardening and Lynis Assessment

## Overview
An academic system-hardening project using a Kali Linux virtual
machine, applicable CIS Debian Linux Benchmark recommendations,
and Lynis security audits.

The project established a baseline, implemented and verified ten
CIS-aligned configuration changes, and repeated the audit to
evaluate the resulting change in hardening posture.

## Academic Context
Completed for CYBR 510: Security Test Engineering at the
University of San Diego.

Assignment: System Hardening and Compliance

## Objective
Improve the security configuration of a Linux virtual machine
through controlled, documented changes while preserving evidence
for a reproducible before-and-after comparison.

This project demonstrates selected CIS-aligned hardening measures.
It does not claim full CIS Benchmark compliance or certification.

## Test Environment
- Operating system: Kali GNU/Linux Rolling 2026.1
- Virtualization platform: Oracle VirtualBox
- Architecture: x86-64
- Kernel: Linux 6.19.14+kali-amd64
- Audit tool: Lynis 3.1.6
- Hardening reference: applicable CIS Debian Linux Benchmark
  recommendations

Because Kali is Debian-derived but uses a rolling-release model,
individual recommendations were evaluated for applicability
before implementation.

## Methodology
1. Documented the virtual machine and audit-tool versions.
2. Performed a baseline Lynis system audit.
3. Preserved baseline audit output, logs, and report data.
4. Identified ten applicable configuration settings that were
   absent from the baseline.
5. Applied and verified each hardening change.
6. Recorded the final configurations in a change log.
7. Repeated the Lynis audit using the same VM and tool version.
8. Compared the results and documented assessment limitations.

## Hardening Changes

| # | Configuration | Implementation |
|---|---|---|
| 1 | Restrict cron access | Created an explicit allow-list with root:crontab ownership and mode 640. |
| 2 | Local login banner | Replaced OS-identifying content with an authorized-use notice. |
| 3 | Remote login banner | Updated /etc/issue.net with an authorized-use notice. |
| 4 | Core-dump restrictions | Configured hard core limits of zero and fs.suid_dumpable=0. |
| 5 | Restrictive default umask | Set umask 027 for new interactive login shells and verified the effective setting. |
| 6 | Post-login message | Replaced /etc/motd content with a neutral authorized-use notice. |
| 7 | DCCP module restriction | Added module-loading restrictions and verified the module remained unloaded. |
| 8 | SCTP module restriction | Added module-loading restrictions and verified the module remained unloaded. |
| 9 | RDS module restriction | Added module-loading restrictions and verified the module remained unloaded. |
| 10 | TIPC module restriction | Added module-loading restrictions and verified the module remained unloaded. |

Each change was checked, implemented, verified, and documented.

An initial "at" scheduler allow-list was excluded from the final
count because the package was not installed. A cron permission
refinement remained part of the original cron control rather
than being counted as an additional change.

## Results

| Measurement | Baseline | Post-hardening |
|---|---|---|
| Lynis Hardening Index | 60 | 62 |
| Selected lab changes implemented | 0 | 10 |
| Lynis version | 3.1.6 | 3.1.6 |
| Test system | Same Kali VM | Same Kali VM |

The Hardening Index increased by two points after the ten
configuration changes were implemented and verified.

The baseline audit performed 268 tests.

## Interpretation
The Lynis Hardening Index is a tool-specific indicator, not a
percentage of system security or CIS compliance.

Ten configuration changes do not necessarily produce ten points
of improvement. Some controls provide preventive or policy
benefits that may not materially affect the score.

For example, DCCP, SCTP, RDS, and TIPC were already unloaded.
The hardening changes restricted future loading rather than
removing functionality that was actively in use.

The evaluation therefore considers both the audit score and
the verified configuration changes.

## Evidence and Documentation
The accompanying report includes:
- Virtual-machine environment details
- Baseline audit results
- Configuration and verification screenshots
- A summary of the ten counted changes
- Post-hardening audit results
- Before-and-after analysis
- Limitations and proposed future improvements

## Assessment Limitations
- Selected Debian Benchmark recommendations were applied to
  a Kali Rolling VM; this was not a complete benchmark assessment.
- Lynis reported that the installed tool version was more than
  six months old.
- Kali Rolling was not included in the tool's end-of-life database.
- Using the same VM and Lynis version supports a controlled
  comparison, but does not eliminate tool-coverage limitations.
- The audit score does not establish total system security.

## Skills Demonstrated
- Linux security configuration
- CIS-aligned control selection
- Security auditing with Lynis
- File ownership and permission management
- Shell configuration and default access controls
- Kernel-module restrictions
- Configuration verification
- Evidence preservation and technical reporting

## Report
See the accompanying Assignment 5.1 report for implementation
details, screenshots, verification results, and analysis.

## Scope
All changes documented in this project were performed on the
designated educational virtual machine.

The configurations reflect that VM's requirements and should
not be treated as a universally applicable production baseline.
