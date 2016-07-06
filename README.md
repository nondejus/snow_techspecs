
### What type of data does SNOW collect? (Technical details)

Host telemetry gathering is at the core of SNOW’s approach to defending infrastructure: SNOW has two reporting streams for each agent, and each poll at random intervals to reduce their predictability from an attacker’s perspective.

1. The base module, which handles loading and updating the sensor module, polls every 10 minutes on average; 
1. The sensor module, which reports the actualtelemetry, polls every 2 minutes on average.

The following data is automatically collected from SNOW. However, please note that any of these collections can be turned off without rebuilding the agent by using dynamic configurations.

* List of running process, along with path of program, list of included DLLs with paths, and SHA-1 hash of each executable module
* List of registered services (with metadata)
* List of loaded drivers (with metadata)
* List of auto-run programs (with metadata)
* List of installed programs
* Time when processes start and end
* Processes running "cloaked" (e.g. obtained through brute-force polling of all possible PIDs on a system that don't appear in a normal process listing)
* Metadata (path, size, access times) on files considered suspicious (such as a program that was running cloaked, but not exclusively)
* Domains to which DNS requests were issued
* Metadata (IP, port) of UDP and TCP network connections
* Metadata on files added, removed or modified in directories of interest (exactly which depend on OS and specific client sensitivity)
* For programs chosen at random, memory pages marked as executable are scanned for the presence of recognizable artifacts of executable code
  * Full memory pages of code are not transferred as regular telemetry, but may be requested for examination
* History of IP addresses used by the machine
* Performance metrics of the agent itself, as well as lists of agent execution checkpoints
* Remote logon attempts through RDP and SSH
* Password bruteforce attempts (the attempted passwords are ignored by the agent)
* Environment variables critical for runtime behaviour

