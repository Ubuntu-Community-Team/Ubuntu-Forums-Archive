---
title: "No proprietary drivers available"
date: 2013-12-24
forum: Hardware
---

### Post by josephellengar2 on 2013-12-24
Hi all! I have an HP Envy 17t with a Nvidia Geforce 740m and have been trying to get the proprietary driver to work. Unfortunately, no luck.

First, any time I use either the Linux Mint driver utility or the Jockey driver utility, it tells me that there are not proprietary drivers available, even if I have drivers installed.

Also, when I install nvidia-current or a different driver from the repos, I simply get the normal crash symptoms-- Cinnamon won't start, I get a bunch of Fallback modes, etc.

Normally I just install from the repos and then let it go at that-- I don't do any configuration. If I do configuration, I get some really low resolution problems.

Third, the same thing happens regardless of which driver I download and install directly from the Nvidia site.

Am I missing a step here?

Thanks!

---

### Post by Yellow Pasque on 2013-12-24
You have an Optimus GPU setup, so you can't just install the nvidia driver directly (or it will bork the intel driver and you get the crashes). [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by buzzingrobot on 2013-12-24
Your BIOS *may* provide three options:

1. Use only the integrated Intel card.
2. Use only the discrete Nvidia card.
3. Use Optimus, which enables software-driven switching between either card as demand ebbs and flows.

If you select to use only the Intel card, you will not see any proprietary drivers listed as the Intel driver is in the kernel.

---

### Post by josephellengar2 on 2013-12-24
> **buzzingrobot said:**
> Your BIOS *may* provide three options:

1. Use only the integrated Intel card.
2. Use only the discrete Nvidia card.
3. Use Optimus, which enables software-driven switching between either card as demand ebbs and flows.

If you select to use only the Intel card, you will not see any proprietary drivers listed as the Intel driver is in the kernel.

It doesn't. Is there any way to disable the intel graphics entirely through software? Bumblebee isn't all that stable for me.

---

### Post by markackerman8@gmail.com on 2014-02-03
Wow

I have the same problem.  Finally I thought I could get good graphics with my new Hp Envy 17 j078, because it has Nvidia - but wow - "No proprietary drivers found" and any atempt to manually install kills the system.

Any one with luck using the 740m proprietary driver in Linux (with intel I7 processor) !!

Mark
[email]markackerman8@gmail.com[/email]

---

### Post by buzzingrobot on 2014-02-04
If the BIOS offers no way to activate only the Nvidia, not Optimus, then I believe the choice is down to using Bumblebee, which is an open source effort to do what Nvidia's Optimus does.  I think 14.04 will offer "Nvidia Prime", which is supposed to be a better way to do these things than Bumblebee. 

Optimus is one of those things that exist, like a BIOS that won't let the machine's owner turn it off and use the Nvidia without it, because vendors assume only Windows will be running on the machines. Except for a few decimal points around the margins, they're right.

---

### Post by markackerman8@gmail.com on 2014-02-04
Here is some more thorough info - if anyone can help

  I have been trying to get proprietary graphics working with my brand new HP Envy 17 m7-j078 notebook.  I had been trying for 2 1/2 years with my previous HP Laptop with no success and TRIED EVERYTHING - Over and Over.  It had ATI Muxless Hybrid Graphics with its' Intel I7.  I thought this one with its Optimus NVIDIA GeForce GT 740M dedicated card would solve the problem because of all the blogs saying Bumblebee works like a charm.  It has now been 2 weeks and over 20 attempts and 5--10 re-installs of Ubuntu Linux Mint, and still no luck.
   Perhaps someone can help me troubleshoot this and stop spinning my wheels and get me out of this rabbit hole, while even learning something, so I can help all the others I have convinced to get into Linux.  Thanks in advance, thanks a lot.

  Here are some details that may be useful (in no specific order)
• HP Envy Touchsmart m7-j078ca notebook
• Intel® Core™ i7-4700MQ
• NVIDIA GeForce GT 740M (2 GB DDR3 dedicated)
• Linux Mint 16 Petra
• Bumblebee 3.2.1
• ack@Aarawn ~ $ lspci -vnn | grep '\''[030[02]\]'
			00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor 				
					Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
			01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)
&#8728; Note that here it doesn't say 01:00 is a "VGA" Controller but a "3D Controller"
• ack@Aarawn ~ $ sudo modprobe nvidia
				[sudo] password for ack: 
				FATAL: Module nvidia not found.
• installed
&#8728; bumblebee-nvidia    primus
&#8728; nvidia-304   nvidia-current (304)   nvidia-prime  nvidia settings  nvidia settings-304
• Xorg.conf with any mention of Nvidia results in TTY1 X crash and only deleting sometimes returns mdm to functioning order
• $ optirun firefox
&#8728; [ 1228.929955] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
&#8728; [ 1228.929986] [ERROR]Aborting because fallback start is disabled.
• ack@Aarawn ~ $ sudo gedit /etc/bumblebee/xorg.conf.nvidia
	Section "ServerLayout"
    		Identifier  "Layout0"
    		Option      "AutoAddDevices" "false"
    		Option      "AutoAddGPU" "false"
	EndSection

	Section "Device"
    		Identifier  "DiscreteNvidia"
    		Driver      "nvidia"
   		VendorName  "NVIDIA Corporation"
    		Option "ProbeAllGpus" "false"
    		Option "NoLogo" "true"
    		Option "UseEDID" "false"
    		Option "UseDisplayDevice" "none"
	EndSection

• ack@Aarawn ~ $ bumblebeed
&#8728; [ 3052.038351] [ERROR]Module 'nvidia' is not found.
• ack@Aarawn ~ $dmesg
	[ 2288.712311] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:1292)
	[ 2288.712311] NVRM: installed in this system is not supported by the 304.116
	[ 2288.712311] NVRM: NVIDIA Linux driver release.  Please see 'Appendix
	[ 2288.712311] NVRM: A - Supported NVIDIA GPU Products' in this release's
	[ 2288.712311] NVRM: README, available on the Linux driver download page
	[ 2288.712311] NVRM: at [www.nvidia.com](www.nvidia.com).
	[ 2288.712320] nvidia: probe of 0000:01:00.0 failed with error -1
	[ 2288.712331] NVRM: The NVIDIA probe routine failed for 1 device(s).
	[ 2288.712332] NVRM: None of the NVIDIA graphics adapters were initialized!
- 

I am going to try a number of other things, but am getting exhausted and would really appreciate a fresh perspective on this issue.
Thanks again.

Mark
[email]markackerman8@gmail.com[/email]

---

### Post by Yellow Pasque on 2014-02-05
```
[ 2288.712311] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:1292)
[ 2288.712311] NVRM: installed in this system is not supported by the 304.116
[ 2288.712311] NVRM: NVIDIA Linux driver release.
```

You need a newer version of the nvidia driver for a 740m. If you already tried that, be more specific about the error(s) you get.

---

### Post by markackerman8@gmail.com on 2014-02-05
Is my computer is 'actually' trying to load a proprietary Nvidia driver finally?, and the problem MAY be just a different version of the proprietary driver??? If so this is awesome news !!

if so, a newer one I suppose - or perhaps an older one??  I should presume anything at this moment.

And which way would you suggest installing it?  Please be specific as it is starting to appear that I am missing some key simple but important steps or things.

Which if any of these ways would you suggest.
 ** a/ **from Synaptic Package manager.  If so which version do you suggest?  nvidia-310/319/03 331, and if so what other packages (nvidia-###-updates, nvidia-###-dev, nvidia-###,nvidia-current ...nvidia-common, nvidia-prime, nvidia-settings-###, or just nvidia-settings no number, nvidia settingds-updaters??? .... ???, or .....

**  b/** Download from Nvidias websight and install the latest.  I have already downloaded NVIDIA-Linux-x86_64-331.38.run and think I tried that (not totally sure).
My guess is that installing from the .run file always hoses my system

**c/** or some other way??

	With respect to the errors you need SPECIFIED could you tell me how to troubleshoot these as I only know a few COMMANDS  which I will state below with the messages I had in the past and wrote down 
	(at this point all my nvidia has been purged until I get some idea of the best way to install it in my system:

# lspci
	$ lspci 
		showed
			00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor   
				Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
			**01:00.0 3D controller [0302]**: NVIDIA Corporation GK208M **[GeForce GT 740M]** [10de:1292] (rev a1)

		now shows
			00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
			01:00.0 3D controller: NVIDIA Corporation GK208M [**GeForce GT 740M] **(rev a1)
$ dmesg
		once showed
			[    9.903642] **nvidia: module license 'NVIDIA' taints kernel.**
			[    9.903646] Disabling lock debugging due to kernel taint
			[    9.906214] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
			[    9.906456] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
			[  593.587889] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
		and another time showed
			[  139.666069] bbswitch: enabling discrete graphics
			[  140.119854] **nvidia: module license 'NVIDIA' taints kernel.**
# modprobe nvidia
		now shows
			FATAL: Module nvidia not found.
	once showed
		$ sudo modprobe nvidia  
&#8227; **ERROR: could not insert 'nvidia_331':** Unknown symbol in module, or unknown parameter (see dmesg)
• and dmesg's relevant lines are
			[    9.903642] **nvidia: module license 'NVIDIA' taints kernel.**
			[    9.903646] Disabling lock debugging due to kernel taint
			[    9.906214] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
			[    9.906456] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
			[  593.587889] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
	
 $ sudo** lshw **-class display
	before said
  		*-display UNCLAIMED     
       			description: 3D controller
       			product: GK208M [GeForce GT 740M]
       			vendor: NVIDIA Corporation
       			physical id: 0
       			bus info: pci@0000:01:00.0
			version: a1
     			  width: 64 bits
     			  clock: 33MHz
    			  configuration: latency=0
   			    resources: memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) 					memory:b2000000-b207ffff
	now shows
 		... 
			clock: 33MHz
      			capabilities: pm msi pciexpress bus_master cap_list rom
       			configuration: **driver=nouveau** latency=0
       			resources: irq:46 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) memory:b2000000-b207ffff

			
# optirun firefox
and #bumblebeed (which I didn't even realize I had used - WOW, and is what found that error) 

Thanks Mate,
Mark

---

### Post by markackerman8@gmail.com on 2014-02-19
Bump

---

### Post by Yellow Pasque on 2014-02-20
> **markackerman8@gmail.com said:**
> IWhich if any of these ways would you suggest.

None of the above. Follow the Bumblebee wiki: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Any version >= 319.17 should work

> With respect to the errors you need SPECIFIED could you tell me how to troubleshoot these as I only know a few COMMANDS

First, you need to remove any prior nvidia drivers you installed and make sure intel driver is working normally. Then, if it's still not working after installing Bumblebee, see: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)
Oh, and go easy on the Caps Lock..

---

