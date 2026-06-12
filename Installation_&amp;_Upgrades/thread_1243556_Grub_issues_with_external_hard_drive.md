---
title: "Grub issues with external hard drive"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by jw8212 on 2009-08-18
I downloaded the ISO file ubuntu-9.04-desktop-i386, and installed it on an external hard drive. Now every time I start my computer without it, I get a grub error 21.

My goal was to install Ubuntu onto the external so I could boot from the external into Ubuntu, but when I didn't have the external in, it would automatically boot into Windows Vista, which is what my laptop came pre-installed with.

I partitioned the external within the Ubuntu installation screen, giving it 75.42 gigs of room, formatted as ext4, and a 4.77 swap space. It installed nicely, and upon reboot, the grub screen popped up, giving me my Ubuntu boot options, then my Vista options. Fine, no problem. I boot into Ubuntu and spend some time there.

I turn my laptop off, and unplug the external. Wanting to get back on Vista, I turned my computer back on, only to have grub pop back up and give me an error 21. I plugged the external in and restarted. The grub menu came up and I picked Vista.

The first Vista option (it gave two) instantly called for me to recover my system to factory defaults. I hit exit and tried the second. It booted fine, and that's what I'm on now.

What I want to know is if there's a way to rid myself of this grub screen, so that I don't need my external just to start my computer. I'd REALLY rather not have to recover my Vista, but worse case, I have a copy of my files on the internal hard drive, so recovery would be just a painful hassle I'd like to avoid if possible. I want to keep my Ubuntu, but my original goal was to make it bootable form the external alone, so I could carry it with me and boot Ubuntu from a different computer (without affecting that computer in any way). Is there any way to achieve this goal?

---

### Post by presence1960 on 2009-08-18
That's because you installed GRUB to MBR of the internal disk. Now when you boot it looks for menu.lst on your external disk to bring up the GRUB boot menu, which of course is not there because it is unplugged. What you need to do is this:

1. You have a recovery partition, that is why you are asked to recover to factory defaults when you choose that vista option in the menu. As such you don't have access to vista recovery console which you will need to restore Vista's bootloader to MBR of the internal disk. Go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to download the iso and burn it to CD/DVD as image. This will enable you to access Vista recovery console. Boot from that with external unplugged and follow the [instructions]("http://ubuntuforums.org/showthread.php?t=1014708") to put the Vista bootloader back to MBR of internal disk. When complete reboot without external plugged in and it should boot right into windows. Now the next step:

2 Plug in your external drive and boot the Ubuntu Live CD, choose "try Ubuntu without any changes", when the desktop loads open a terminal and do this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In # 6 use setup (hd1) to put GRUB onto MBR of external disk. 
Reboot and go into BIOS. Set the external drive to boot before your internal disk. This will give you what you want. if you boot with the external plugged in that will boot first and GRUB will take over and you can boot into Ubuntu. If you boot without the external plugged in Windows bootloader will take over  and will boot Vista.

FYI next time you install. You can choose where GRUB gets installed by clicking the advanced tab on the Ready to install window. See attached screen shot.

---

