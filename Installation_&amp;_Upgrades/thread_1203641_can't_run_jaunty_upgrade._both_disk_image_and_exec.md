---
title: "can't run jaunty upgrade. both disk image and executable"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by K_Boomer on 2009-07-03
I stopped using ubunty gutsy gibbon a while back due to the problems I was having. I want to fix them now so I can later give back to the community.

Oh... And I have forgotten most of the commands, so speak easy please.

Currently using gutsy gibbon 7.10 on a computer I built so long ago that  I forget many of the specs.

But here's the problems I am having:
I want to update to jaunty but my computer wont recognize the disc image. I have burned it multiple times from a reliable source (he has helped over 20 other computers without problems. It goes directly to the Ubuntu loading screen. 

I have checked my BIOs and made sure the boot order was correct (cd, then hd, then floppy).

I then tried running the disk directly from my desktop. Upon clicking wubi.exe, i get an error message saying that it cannot run executable. 

I tried forcing it to in the terminal:
________________________________________________________________________
kiefer@Kiefers-desktop:/media/cdrom$ ls
autorun.inf  dists    isolinux    pics  preseed             ubuntu
casper       install  md5sum.txt  pool  README.diskdefines  wubi.exe
kiefer@Kiefers-desktop:/media/cdrom$ ./ wubi.exe 
bash: ./: is a directory
kiefer@Kiefers-desktop:/media/cdrom$ sudo ./ wubi.exe 
[sudo] password for kiefer:
sudo: ./: command not found
kiefer@Kiefers-desktop:/media/cdrom$ ls -l
total 1528
-r--r--r-- 1 root root     143 2009-04-20 08:29 autorun.inf
dr-xr-xr-x 2 root root    2048 2009-04-20 08:29 casper
dr-xr-xr-x 3 root root    2048 2009-04-20 08:29 dists
dr-xr-xr-x 2 root root    2048 2009-04-20 08:29 install
dr-xr-xr-x 2 root root   12288 2009-04-20 08:29 isolinux
-r--r--r-- 1 root root    4794 2009-04-20 08:29 md5sum.txt
dr-xr-xr-x 2 root root    2048 2009-04-20 08:29 pics
dr-xr-xr-x 4 root root    2048 2009-04-20 08:29 pool
dr-xr-xr-x 2 root root    2048 2009-04-20 08:29 preseed
-r--r--r-- 1 root root     229 2009-04-20 08:29 README.diskdefines
lr-xr-xr-x 1 root root       1 2009-04-20 08:29 ubuntu -> .
-r--r--r-- 1 root root 1533687 2009-04-20 02:39 wubi.exe
kiefer@Kiefers-desktop:/media/cdrom$ winecnfg
bash: winecnfg: command not found
kiefer@Kiefers-desktop:/media/cdrom$ sudo !!
sudo winecnfg
sudo: winecnfg: command not found
kiefer@Kiefers-desktop:/media/cdrom$ sudo winecfg
wine: /home/kiefer/.wine is not owned by you
kiefer@Kiefers-desktop:/media/cdrom$ su
Password: 
su: Authentication failure
Sorry.
kiefer@Kiefers-desktop:/media/cdrom$ su
Password: 
su: Authentication failure
Sorry.
__________________________________________________________________________

help?
Don't know if my lspci will be of use, but here you are:

kiefer@Kiefers-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

---

### Post by K_Boomer on 2009-07-03
Also, the cd runs on another 32 bit computer. md5sums has been verified.

---

### Post by ronparent on 2009-07-03
At the first screen, prior to selecting run with no changes to your computer, try hitting F6 and X-ing the apic and lapic otions (noapic, nolapic). See if you can then continue on to boot from the live cd.

---

### Post by K_Boomer on 2009-07-03
> **ronparent said:**
> At the first screen, prior to selecting run with no changes to your computer, try hitting F6 and X-ing the apic and lapic otions (noapic, nolapic). See if you can then continue on to boot from the live cd.
First, thanks for your reply.

But I am confused what you mean by "prior to selecting run with no changes to your computer." I don't know what that option is. My computer boots up, I get an option to press tab or esc to access different menus and then it goes straight to the ubuntu loading screen (no login screen). 

What is this "first screen?"

---

### Post by ronparent on 2009-07-04
Write in a hurry, regret in liesure. Your first boot screen on the live cd is actually overlaid with a language selection screen which is cleared with an install language selection. The screen remaining, at that point, is to select 1)running without changes 2) Installing 3) ...etc. This is where you have the option of hitting F6 to modify your boot options. Hit F6 ab=nd hit the space bar on the apic and lapic option to x them. Then esc to the main boot menu and select the first choice to boot withou any changes to your computer. If everything works fine and you are satisfied with the result, you can the instaall from the live cd by just hitting the install icon on the desktop.

---

