---
title: "ubuntu 16.04 on Dell Precision 7510"
date: 2016-08-19
forum: Hardware
---

### Post by aa-hcl on 2016-08-19
Hi,

I have a new dell precision 7510 in the following configuration:

Intel® Core™ i7-6820HQ CPU @ 2.70GHz × 8
Quadro M2000M/PCIe/SSE2
64 GB RAM

with Samsung Pro 850 1Tb SSD (M.2 slot is currently empty).

The system can be supplied by Dell with ubuntu, but I got it with Win7, took the HDD with Win7 out and put aside to keep and use if I have trouble with the hardware.
Ubuntu is freshly  installed on SATA Samsung SSD (no dual boot - no other OS).


In general, the laptop works. The main issue - touchpad and stick are recognised as ps/2 mouse (as clear from xinput --list). Although some features of the touchpad (i.e. scrolling) does work, but scrolling on the stick does not. Also no support for disable touchpad while typing, etc.

I tried all possible ways to resolve it and it looks like that the touchpad is not recognised by the kernel.

I have (output of uname -a):
Linux aa-7510 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Has anyone got this system (P7510) supplied with ubuntu 14.04? If yes, can you please post the output of xinput --list? 

What is the way forward with this problem?  I really would like to have the touchpad to be recognised.

P.S. I am trying to push dell Pro support to provide me with "linux recovery image" supplied for this system, but at the moment they seem trying to avoid answering... as my system is supplied with Win7

---

### Post by lars-albertsson on 2016-09-17
I tried 14.04 on a 7510, but it was nowhere near working, in spite of Dell claiming it to be supported.

I run 16.04 with some success, except that I cannot upgrade the kernel, since the upgrade process seems to break LTE support.

The touchpad works fine, however. Here is the output of xinput --list:

[FONT=monospace][COLOR=#000000]<removed incorrect information, see below>[/COLOR][/FONT]

---

### Post by aa-hcl on 2016-09-17
Dear lars-albertsson,

I am really grateful for your post. Can you please share some technical details:

with what kernel do you get the above output for xinput? (i.e. what is output of uname -a)

how did you install the system (i.e. 16.04 fresh install?)? what version (16.04.1 ?)? Is it on SATA or M.2 drive?

I still get the touchpad and stick not detected.

Other parts of the laptop are working mostly fine and all devices are detected OK (I did not check the finger print reader).

After BIOS upgrade USB 3.1 also works. I did not check that your can get through USB 3.1 various connection as I did not get the adaptor yet., but DP port work fine

With Advanced dock station I currently run 3x 4K monitors (the laptop 4K + 2x 4K connected through DP port of the dock) - all seems to be working.

Camera works without any tricks, wifi works. I did not check all possible combinations of the ports, but so far all seems to be working.

I am currently on ubuntu 16.04.1

I am really looking for your reply.

Many thanks!

I really looking for your information

---

### Post by lars-albertsson on 2016-09-18
Sorry, I was apparently confused, since I pasted information from another computer... Here is the output of "xinput --list" from the 7510:

[FONT=monospace][COLOR=#000000]&#9121; Virtual core pointer                          id=2    [master pointer  (3)]                                                                                                                    [/COLOR]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]                                                                                                                    
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint Stick             id=14   [slave  pointer  (2)]                                                                                                                    
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad          id=13   [slave  pointer  (2)]                                                                                                                    
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]                                                                                                                    
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]                                                                                                                    
    &#8627; Power Button                              id=6    [slave  keyboard (3)]                                                                                                                    
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]                                                                                                                    
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]                                                                                                                    
    &#8627; Power Button                              id=9    [slave  keyboard (3)]                                                                                                                    
    &#8627; Sleep Button                              id=10   [slave  keyboard (3)]                                                                                                                    
    &#8627; Integrated_Webcam_HD                      id=11   [slave  keyboard (3)]                                                                                                                    
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]                                                                                                                    
    &#8627; DELL Wireless hotkeys                     id=15   [slave  keyboard (3)]                                                                                                                    
    &#8627; Dell WMI hotkeys                          id=16   [slave  keyboard (3)]                                                                                                                    


I installed a fresh 16.04.1 and then put a hold on kernel upgrades, so I am still on 4.4.0-21. Output of uname -a:

[/FONT][FONT=monospace][COLOR=#000000]Linux glomund 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux[/COLOR][/FONT][FONT=monospace]

I use a SATA SSD as root disk and an M.2 NVRAM for /home.

The machine is overall working, albeit not great. I have occasional trouble with suspending and with graphics.
 



[/FONT]

---

### Post by 7-cornelius on 2016-10-04
Hi,

I had running the precision 7510 quite well until my palmrest including the touchpad was exchanged by dell support. The old touchpad was recognized fine by the kernel but it seems like they have a new series now that won't get recognized. Do you already filled a kernel bug?

---

### Post by philroche2 on 2016-11-29
This looks like the relevant bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1590590](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1590590)

---

### Post by dragon-788 on 2017-10-14
I believe one of the tricks with this laptop is to blacklist the module it is loading to let the xserver-xorg-input-synaptics or xserver-xorg-input-libinput take over. This enables things like using synclient to enable/disable features for testing from the terminal and then persisting those settings via a custom xorg.conf.d file.

---

