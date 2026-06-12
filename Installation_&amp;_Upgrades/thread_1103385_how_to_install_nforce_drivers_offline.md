---
title: "how to install nforce drivers offline?"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by barryvanveen on 2009-03-22
Dear all,

My Hardy installation crashes when I connect my computer to the internet. I guess new drivers for my ethernet can fix this (it worked for windows on the same pc)...

The problem is that I need to install the Nforce driver without using synaptic. I downloaded the driver on my laptop and executed it on my pc but I got an error: 

*"No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface".*

When I press OK I get another error:

*"You do not appear to have libc header files installed on your system. Please install your distribution's libc development package".*

So my question is: How can I install the libc development package without using synaptic?


Thanks in advance,

Barry

---

### Post by cariboo on 2009-03-22
You can not install windows drivers in Linux. Your network adapter should be using the forcedeth driver if it is an Nvidia nic. To check what driver you are using, open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

paste the output in your next post.

Jim

---

### Post by barryvanveen on 2009-03-22
Hey Jim,

Thanks for the quick reply. Offcourse I'm trying to install the linux 32bit driver, with which I got those errors...

lshw doesn't really give me any output. On the next line a couple of words come by: CPUID, PCI (sysfs) and some more that go away really quick. But these words disapear again and I get the next command line, no information on screen. 

sudo lspci gives me the following output:

> 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)


Hope you can make something of this. 


Thanks!

---

