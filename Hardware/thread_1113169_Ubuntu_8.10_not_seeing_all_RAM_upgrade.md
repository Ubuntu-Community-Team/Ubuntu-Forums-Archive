---
title: "Ubuntu 8.10 not seeing all RAM upgrade"
date: 2009-04-01
forum: Hardware
---

### Post by joberly on 2009-04-01
So, I have a PC that had 1gb of ram (2x512mb) and have added 2x1gb sticks for a total of 3gb. The BIOS sees all 3gb. 

DMIDECODE sees everything properly:

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0 5
	Current Speed: 160 ns
	Type: ECC DIMM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 0 5
	Current Speed: 162 ns
	Type: ECC DIMM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 0 5
	Current Speed: 164 ns
	Type: ECC DIMM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: 0 5
	Current Speed: 166 ns
	Type: ECC DIMM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK


But, 

free -m
             total       used       free     shared    buffers     cached
Mem:          2468       1725        742          0         49       1295
-/+ buffers/cache:        380       2088
Swap:         2768          4       2764

Sees only what is being reported, 2.5gb. What is the -/+ 380 buffers/cache?

---

