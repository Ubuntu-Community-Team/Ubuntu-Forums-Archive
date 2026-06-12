---
title: "grub on removable"
date: 2009-09-30
forum: Hardware
---

### Post by kenlprotech on 2009-09-30
I've been running a dual boot system for 6-8 months (XP Pro + Unbuntu 8.04) No big problems, but I want to add Vista Ultimate to the mix to help me with software testing.

BEFORE adding Vista, I would like to boot from a removable drive instead of the hdd. I have 3 options:

IDE Super Drive (LS-120)
USB Super Drive (LS-120)
USB Flash Drive

This MB doesn't have a built in floppy controller. I have spent hours looking for the best approach, but I don't see a clear direction and I have not been able to format the super drive media.

Questions are three:

1) Is this a good approach for adding Vista, keeping XP and Hardy? (will use a separate partition from the XP boot part)

2) Which boot method of the 3 will be the best? My gut tells me IDE

3) If you suggest a Super Drive, should I use a floppy or a 120MB disk?

TIA and have a great Wednesday.

---

### Post by oldfred on 2009-09-30
Are not superdrives pretty old? You could use a floppy in the super drive but USB is much more current, if your system will boot from it.

Why do you want to boot from a removable device? If it is missing then you cannot boot. Or is it just a temporary boot?

You can create a USB from 9.04 but I do nto think you can from 8.04. You can use Supergrub or  unetbootin  to create bootable disk or just a grub entry to point to all the systems you want to boot.

---

### Post by kenlprotech on 2009-10-02
[COLOR="Sienna"]olfred - Thanks. I am using extra hardware around here. Yup, superdrives are old and an internal one can run on my IDE chain with a machine that has no floppy port.

I am not super comfortable with Vista altering my set up. That's why I want to boot from a removable drive _before_ adding Vista.

Maybe someone could point me to the perfect doc that helps me add Vista [the normal way] without blowing out XP & 8.04. Probably something I should know anyway.

NOTE 1: Due to a recent hardware upgrade from RAID controller to plain SATA mb, my XP system drive is H: not C: (doesn't bother me and maybe it will help in the long run) Yes, C: is big enough to add a bloated OS.

NOTE 2: My XP config is more critical than my 8.04 config.

...no wait... Maybe I should Add Vista the normal way and then upgrade 8.04 to 9.04 Would that make more sense? [/COLOR]

---

### Post by oldfred on 2009-10-02
I have installed grub enough times I look at it as only reinstalling grub - no big deal as long as you are prepared. I am a belt & suspenders guy when it comes to booting. I alway have supergrub, a live CD, gparted, partition magic, another livecd, and ubcd and an install on a USB and a floppy boot. I figure no matter what I can somehow get into my system.

I see some people have issues with raid, I do not understand it for desktops. I just backup somewhat regularly.

The bigger issue has been Win7 as it somehow moves any other windows boot to its partition which works, but if you uninstall the Win7 your other windows is hosed.

Some people to be super safe unplug a hard drive. But then you have to go back and manually add that to menu.lst to get that drieve to boot. And if you change boot order that can cause bigger issues.

I just have XP and always have intalled it first. These are some sites discussing dual boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by louieb on 2009-10-02
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product).  And the 2nd product can only be booted thru the boot loader in the 1st product. 

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it.   [Multibooters, Pictures here worth 1000+ words]("http://www.multibooters.co.uk/multiboot.html") 

Or do what I did when I installed Win 7. - unplugged the drive with XP during the install.  

If the PC will boot to a USB drive, then  a dedicated GRUB partition on the drive would  work for you. I use one on all 4 of my PCs.   [IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

---

