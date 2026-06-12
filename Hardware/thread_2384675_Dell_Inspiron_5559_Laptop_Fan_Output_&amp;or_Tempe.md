---
title: "Dell Inspiron 5559 Laptop Fan Output &amp;/or Temperature Concern"
date: 2018-02-10
forum: Hardware
---

### Post by accounts0 on 2018-02-10
I have a Dell Inspiron 5559 Laptop running Ubuntu 16.04 with KDE. The CPU's a 2.5GHz Intel Core i7-6500U DC/QC(HT). There's a 2.5" SSD in the original HDDs spot, & an old 2.5" 1TB SATAIII HDD in an adapter which replaced the original Slimline DVD-RW.


I have it set on a shelf atop a wire rack that looks like it used to be the tray from inside a toaster oven. It's got 3/4" between 3mm bars, & is 1/2" high. I rigged up a couple pipe clamps that looks like an upside-down "U", so that when my cats sleep on the laptop the fan's blowholes aren't blocked. The cats stay on top of the clamp & there's like a space under it where the fan blows out unimpeded- high enough that the fur won't reach. I blow out the laptops' vents every month or 2- been in electronics repair forever & know how bad it can get.


The problem I face is that my KDE widget says my fan's at ~3400 rpm with the CPU at 70 degrees C. I don't have it set to report temps on each core, just as a whole. When I put my hand near the fan blower I feel some slow moving hot air, but not like I expect to feel- it would likely move a feather out of the way but not a potato chip, if you were to lean it up against the egress vent there.


Tonight I blew it out especially thoroughly, & it came to mind that I haven't disassembled its insides for over a year, maybe there's a clump in there. But even so I don't see the fan unable to resolve the high temps- just when its got a real workload it takes much longer.


As for power hogging software I regularly run current Bitcoin Core, & Litecoin Core, with the blocks split between the HDD & the SSD- newer on SSD & symlinks to old ones on the HDD. Also I run a Windows 7 VM headless in VirtualBox & rdp into it as needed. The guest has 2x vCPUs, 100% execution cap, & 2x .vdi images between the SSD & HDD. Windows stays on so it can run my backup software, SyncBackPro which interfaces between a read-only Samba share & AWS S3. Its settings say it uses at most 9 I/O threads to talk to S3. The executable takes up 1 (32-bit) process & is above 90% CPU in Task Manager whenever its working on a job. The backup jobs' priorities are set to run at lower, normal, & higher, depending on how often they run. eg. 'Daily' jobs run at 'higher', while 'Monthly' jobs at 'lower'. Regardless of which particular backup job is running, the VMs 2x vCPUs are pegged at 100% when that app's doing anything.


When I look at htop on the host, I see low percentages around 80% for 1 bar (of 4) & 90's & 100 on the rest. Usually there are 3 bars around 95 & 1 around 80, & it changes which core but not the levels, not for long enough to notice it though. It says its load average is 2.7 on the low end & 3.6 on the higher end. On s-tui 'Power', 'Temperature', & 'Frequency' are all maxxed out except for a single-pixel blip every few inches. Utilization around 60%.






TL;DR:
The VM's high CPU gives the host high temperatures that the fan barely keeps up on until the VM chills out.

---

### Post by Yellow Pasque on 2018-02-10
If you're mining and running a VM, the CPU is going to get hot. There's no way around it.
70C is warm, but it's not alarming for a laptop CPU.

---

