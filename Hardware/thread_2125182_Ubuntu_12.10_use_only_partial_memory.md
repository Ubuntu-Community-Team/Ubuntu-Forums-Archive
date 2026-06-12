---
title: "Ubuntu 12.10 use only partial memory"
date: 2013-03-13
forum: Hardware
---

### Post by themind24 on 2013-03-13
Hi everyone,
I installed Ubuntu 12.10 Gnome Remix on my new laptop but I've a problem with memory.
My laptop has 4 GB memory but Ubuntu recognize only 2,4 GB.
Obviously both BIOS and Windows 8 recognize all 4GB.

My laptop configuration:
Lenovo B590
CPU: Intel Core i5-3210M
Ram: 4 GB DDR3-SDRAM
Chipset motherboard: Intel HM77 Express
Integrated graphics: HD Graphics 4000.
Operating System: Ubuntu 12.10 
Kernel: Linux 3.5.0-17-generic (x86_64)


Some useful command outputs:
```

dmidecode --type memory

	Array Handle: 0x000B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1600 MHz
	Manufacturer: Hynix/Hyundai
	Serial Number: 1A21B5B9
	Asset Tag: 9876543210
	Part Number: HMT351S6EFR8C-PB  
	Rank: Unknown
	Configured Clock Speed: 1600 MHz

```


```

free -m

                   total       used       free     shared    buffers     cached
Mem:          2483       1136       1346          0         56        515
-/+ buffers/cache:        563       1919
Swap:         4884          0       4884

```


```

cat /proc/meminfo | grep "Mem*"

MemTotal:        2542664 kB
MemFree:         1373552 kB


```

Also running live version of Ubuntu the memory is always only 2,4GB.

Can someone help me?
Thanks a lot.

---

### Post by themind24 on 2013-03-13
it may be possible that the lost memory is borrowed from Intel HD Graphics?
if it's true, it always borrows fixed maximum memory?!

---

### Post by foresthill on 2013-03-13
You're fine, stop worrying. I have 4 GB of RAM in my notebook, and have never once seen RAM usage go above 1 GB. I'm not sure if you have the System Monitor applet installed, but if you do, this command in the terminal will bring it up:

> gnome-system-monitor

Assuming you have the applet, you'll see that you RAM usage is probably ~ 500 MB or less. You simply don't need 4 GB of memory for any Ubuntu application I'm aware of. 

Regarding the missing 2 GB, I would guess that your Intel integrated graphics are using it, though I could be wrong. But it remains irrelevant, 2 GB of usable RAM is more than enough.

---

### Post by themind24 on 2013-03-14
Thanks for the answer.
I know that 2,4 gb for standard use is enought, but for example if I'd like virtualize another system I need more memory.
So the problem exist and I can't ignore it :S

---

### Post by foresthill on 2013-03-14
A little googling reveals to me that HD 4000 graphics can use a maximum of 1.7 GB of system RAM for onboard video. Have you tried going into your system bios and looking for a setting to change the amount of RAM your onboard video uses? Most decent bioses have that option.

I honestly don't see a problem here though. If you go into System Monitor and see that all 2.4 GB of RAM is being used, take a screenshot and show us. But until that happens, there is absolutely no problem here. Besides, if it bothers you that much, just add some RAM, but I can almost guarantee you will never use it except maybe in Windows.

---

### Post by themind24 on 2013-05-02
The problem disappeared with new kernel 3.8.0-19-generic.
The system recognize 3,7GB of Memory now.
Thanks to everyone.

---

