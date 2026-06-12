---
title: "no audio in ubuntu 11.04"
date: 2011-05-11
forum: Hardware
---

### Post by ameq8 on 2011-05-11
hi! i'm new to linux and had just installed ubuntu 11.04. my problem is that i have no sound. i followed the instruction on how to check for errors and here is what i got:
"   	 	 	 	 	ameq8@ameq8-Aspire-4520:~$ ubuntu-bug audio   1390  
 ERROR: symptom script /usr/share/apport/symptoms/audio.py crashed:  
 Traceback (most recent call last):  
   File "/usr/lib/python2.7/dist-packages/apport/ui.py", line 56, in thread_collect_info  
     package = symb['run'](report, ui)  
   File "/usr/share/apport/symptoms/audio.py", line 192, in run  
     (package, card, isOutput, jack) = ask_jack_and_card(report, ui)  
   File "/usr/share/apport/symptoms/audio.py", line 22, in ask_jack_and_card  
     cards = parse_cards()  
   File "/usr/share/apport/symptoms/_audio_data.py", line 301, in parse_cards  
     cards = add_pa_cards(cards, pactl_parsed)  
   File "/usr/share/apport/symptoms/_audio_data.py", line 188, in add_pa_cards  
     for pa_card in pactlvalues['Card'].itervalues():  
 KeyError: 'Card'  
 ameq8@ameq8-Aspire-4520


please help me know what is the meaning of these messages. thanks!

---

### Post by lidex on 2011-05-11
No idea. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by georgiebest7 on 2011-05-12
I had tried posting another thread but haven't received any response there yet, so hoping for better luck with this one.

Since updating Ubuntu to 11.04, it has stopped recognising my sound card. Here is the ALSA info:

[http://www.alsa-project.org/db/?f=60f06c55ea276e259f1cadb82e7af918ad68d89c](http://www.alsa-project.org/db/?f=60f06c55ea276e259f1cadb82e7af918ad68d89c)

I would highly appreciate all suggestions/fixes.

---

### Post by Yellow Pasque on 2011-05-12
Hmm, no kernel module and no dmesg warnings. Odd.. Well, reinstall kernel and try and load the module:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo depmod -a
sudo modprobe snd-hda-intel
```
Then, check the end of dmesg.

---

### Post by georgiebest7 on 2011-05-12
> **Temüjin said:**
> Hmm, no kernel module and no dmesg warnings. Odd.. Well, reinstall kernel and try and load the module:
```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo depmod -a
sudo modprobe snd-hda-intel
```
Then, check the end of dmesg.

Pardon my ignorance, but dmesg?

---

### Post by Yellow Pasque on 2011-05-12
Like:
```
dmesg | tail -n 30
```

---

### Post by georgiebest7 on 2011-05-12
Right I've tried and here's what I get

> 

[   18.127085] type=1400 audit(1305222458.209:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=714 comm="apparmor_parser"
[   18.138165] type=1400 audit(1305222458.219:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=713 comm="apparmor_parser"
[   18.139085] type=1400 audit(1305222458.219:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=714 comm="apparmor_parser"
[   18.140315] type=1400 audit(1305222458.229:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=714 comm="apparmor_parser"
[   18.165513] type=1400 audit(1305222458.249:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=722 comm="apparmor_parser"
[   18.174620] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   18.174841] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   18.175538] type=1400 audit(1305222458.259:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=722 comm="apparmor_parser"
[   18.175719] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.179629] type=1400 audit(1305222458.259:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=723 comm="apparmor_parser"
[   18.438573] input: HP WMI hotkeys as /devices/virtual/input/input6
[   19.430043] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   19.430076] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   19.430088] nvidia 0000:00:12.0: setting latency timer to 64
[   19.430095] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.441490] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   19.600240] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   19.607077] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90001000000, using 3072k, total 3072k
[   19.607083] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   19.607085] vesafb: scrolling: redraw
[   19.607089] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   19.607335] Console: switching to colour frame buffer device 128x48
[   19.607364] fb0: VESA VGA frame buffer device
[   19.655014] ppdev: user-space parallel port driver
[   19.679522] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   22.701467] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.635710] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.390030] eth1: no IPv6 routers present
[  157.268300] exe (1851): /proc/1851/oom_adj is deprecated, please use /proc/1851/oom_score_adj instead.
[  218.210044] CE: hpet increased min_delta_ns to 11520 nsec


Any ideas?

---

### Post by Yellow Pasque on 2011-05-12
Try disabling the codec in the BIOS. Boot that. Then reboot and enable it.

---

### Post by georgiebest7 on 2011-05-12
> **Temüjin said:**
> Try disabling the codec in the BIOS. Boot that. Then reboot and enable it.

I must apologise one more time and am sorry if this is beginning to get annoying, but I need a dummy guide to this.

Cheers for putting up with my low skillset.

---

### Post by Yellow Pasque on 2011-05-12
Do you know how to enter your BIOS/system settings? It's usually pressing 'Del' when the computer first starts.

---

### Post by retchid on 2011-05-12
If new install it is probably on MUTE.   Dont know why but installed Ubuntu a few times and had to unmute the sound.

Either that or you have two sound cards and you haven't told it which one to use.  Had that on open Suse

---

### Post by georgiebest7 on 2011-05-12
> **Temüjin said:**
> Do you know how to enter your BIOS/system settings? It's usually pressing 'Del' when the computer first starts.

Oh yeah managed that by clicking F10

But I cannot for the life of me figure out how to disable the codec.

I can see the PhoenuxBIOS Setup Utility but the only options it shows me are:
> 
Main - this has all system info and then gives me an option for a Diagnostic Log

Security - this gives me the option to change Administrator Password and Power-On Password

System Configuration - this gives me Language / Button Sound / Dedicated Video Memory up to / Virtualization Technology and also Boot Options

Diagnostics - Primary Hard Disk Self Test / Memory Test

Exit


Once again I do appreciate the advice.

---

### Post by Yellow Pasque on 2011-05-12
Maybe it's not possible with your BIOS? You could also try removing the battery and holding the power button for 10 seconds or so. That should reset the CMOS.
> If new install it is probably on MUTE.
The problem is deeper than that. What is the output of:
```
lspci
```

---

### Post by georgiebest7 on 2011-05-12
Here's what I got:

> 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)


---

### Post by Yellow Pasque on 2011-05-12
It;s not showing up there. Try the battery trick.

---

### Post by georgiebest7 on 2011-05-12
> **Temüjin said:**
> It;s not showing up there. Try the battery trick.

Tried that but it wont work and the lspci gives the same result. I think I'll try formatting and going back to Ubuntu 10.10 and see if that fixes things.

Thanks for the help and patience (I might be back).

---

### Post by lidex on 2011-05-12
Perhaps it's disabled already. Maybe boot options??
What does system info in the bios say about onboard sound?
Get the diagnostic log.
Was it working previously and in what OS?

What are these outputs:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

