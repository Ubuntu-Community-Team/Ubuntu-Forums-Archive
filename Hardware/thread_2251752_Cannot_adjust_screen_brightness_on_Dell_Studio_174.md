---
title: "Cannot adjust screen brightness on Dell Studio 1749"
date: 2014-11-06
forum: Hardware
---

### Post by pfeiffep on 2014-11-06
Most everything on my Dell Studio 1749 works like a charm running Ubuntu 14.04.1. One exception that was really annoying me was the inability to adjust screen brightness. 
I spent a couple of days searching for solutions based on screen brightness and Dell and Ubuntu - I didn't find anything that remedied my situation.
 
I decided to attack the problem from a different perspective:p - starting with the graphics card / driver! 

Steps that solved this 'problem'[INDENT]* Determine graphics in system[/INDENT]
```
sudo lshw -C display
[sudo] password forpfeiffep: 
  *-display              
       description:VGA compatible controller 
       product: CoreProcessor Integrated Graphics Controller 
       vendor: IntelCorporation 
       physical id:2 
       bus info:pci@0000:00:02.0 
       version: 02 
       width: 64bits 
       clock: 33MHz 
       capabilities:msi pm vga_controller bus_master cap_list rom 
      configuration: driver=i915 latency=0 
       resources:irq:43 memory:f0000000-f03fffff memory:d0000000-dfffffffioport:1800(size=8)  
```[INDENT]
* [View Article and Download]("http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5")

* After downloadingsimply double clickintel-linux-graphics-installer_1.0.6-0intel1_amd64.deb[/INDENT]
and follow theprompts (requires reboot)

* After installation and reboot 
```
Processor   Intel®Core™ i3 CPU M 330 @ 2.13GHz × 4 \
Graphics   Intel®Ironlake Mobile
OS Type   64-bit
```

---

### Post by pfeiffep on 2014-11-06
It appears that reducing screen brightness to about 50% using this fix has extended operating time on battery by 30 - 45 minutes. ):P

---

### Post by pfeiffep on 2014-11-15
[COLOR=#000000]* After downloading simply double click intel-linux-graphics-installer_1.0.6-0intel1_amd64.deb[/COLOR]
[COLOR=#000000]and follow the prompts (requires reboot)

**[SIZE=4]11/15/2014 Update :[/SIZE]** Today's software update provided a warning about untrusted sources so I reviewed the site and discovered I forgot 2 steps.
The new download [link]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7")  .............. Instructions on the page
[/COLOR][INDENT]**[COLOR=#333333][FONT=Arial]Signatures - Ubuntu*[/FONT][/COLOR]**
[COLOR=#333333][FONT=Arial]In order to "trust" the Intel® Graphics Installer for Linux*, you will need to add keys to Ubuntu's software package manager ("apt"). Open a terminal, and execute these lines:[/FONT][/COLOR][/INDENT]
```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O - | sudo apt-key add -

wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O - | sudo apt-key add -
```[COLOR=#000000][FONT=Consolas]
[/FONT][/COLOR]
[COLOR=#000000]


[/COLOR]

---

### Post by Bastik on 2015-02-17
Sorry replied to wring post, please delete

---

