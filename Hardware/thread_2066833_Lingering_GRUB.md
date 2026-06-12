---
title: "Lingering GRUB"
date: 2012-10-05
forum: Hardware
---

### Post by JFW20 on 2012-10-05
HI all, a few weeks ago I installed ubuntu 12.04 lts on my hand me down toshiba satellite. Long story short I had to download plpbts << I think thats what it was called>> to be able to boot from the live usb I created. Well I was going to try to recover my windows xp and reinstall ubuntu with a larger partition etc..

I deleted the partition and the grub remains. At first there were no issues using my boot loader (plpbt) it would run and I could still boot windows. Unfortunately I went to sleep thinking I would finish up today...bam my pc will no longer boot from the disc!!??!!??

I tried cleaning the lens, went through google nothing...

Any help would be greatly appreciated is there any way to get rid of grub from grub??

Please help!! currently I'm just leaving the computer hoping that the same way it stopped booting it will magically start recognizing my disc.

---

### Post by oldfred on 2012-10-05
What does boot? CD, Hard drive? 

Where is grub installed? And did you then leave grub in MBR but remove the rest of grub in an Ubuntu partition?

If you can boot a liveCD. then post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Was this what you used to boot USB?
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by JFW20 on 2012-10-05
Hi, the problem is that now nothing would boot. There was something strange about the MBR before, figured out after the fact that I could have downloaded a driver, but instead I made a cd of pbptl to boot cd's and live usb's etc.. 

Now nothing will boot, I deleted the ubuntu partition. I can press f2 and get to the setup area and tell it to boot from cd but nothing happens.. I'm not sure where grub is installed. I don't have a windows recovery disc either. ugh

That is what I used to make the booting cd. I'm going to look into the boot repair you gave the link to. Thanks for the assistance I'll update once I've looked into it.

Thanks again.

---

### Post by JFW20 on 2012-10-05
I looked at that program it would be great, but my issue is that my computer will not boot from cd. It won't boot from anything.. 

Is grub useless now that the ubuntu partition is gone? Is there any way for me to tell it to boot frrom the cd through grub? or do anything through grub for that matter..

sorry for being fragmented, it wont boot a cd period, so I don't think this can help me.. are you thinking there is chance it would boot this or did you not understand what I was saying? 

Ugh tell me I can get this fixed its seeming more and more like its destined for the landfill..
 thanks

---

### Post by oldfred on 2012-10-05
If you cannot get CD to boot and there is nothing to manually boot in the hard drive then you can remove drive & plug it into another system to make repairs or install a new system.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda2 ro
initrd (hd0,5)/initrd.img
boot

---

