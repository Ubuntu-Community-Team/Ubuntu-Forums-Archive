---
title: "How to use NT Bootloader to dual boot WinXP and Ubuntu 9.04 (GRUB) ?!"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by dklord666 on 2009-05-15
Hi! I´m new at linux (when I mean new, it´s new at all), and I´ve been researching some installation options to be using in my new upcoming (first one) install of Ubuntu. 

It seens the best option (at least for me) is to **_NOT_** install GRUB at MBR of my Desktop PC.

Right now I´ve have the following partitions:

Windows XP (NTFS) -> 60GB
Windows DATA (NTFS) -> 130GB
Unnalocated -> 40GB

(by the way, the Unnalocated will be set to this when installing the UBUNTU:

Ubuntu -> 15GB
Ubuntu /home -> 15GB
SWAP -> 4GB
FAT32 -> 6GB

Any suggestion would be apprecited as well for this scheme)

Now, using google I´ve found some good references on how to install GRUB in a partition and not in the MBR, specially this one (it´s for Fedora, but it gave me a pretty good idea of how to do it): 

[http://www.johnspencer.org.uk/LinuxTutorials/DualBoot/dual_booting_windows_xp_and_fedora.htm](http://www.johnspencer.org.uk/LinuxTutorials/DualBoot/dual_booting_windows_xp_and_fedora.htm)

On this link, in a particular section, we have these steps described:


[LIST]
[*]
[LIST]
[*] [FONT=Arial]Select "Use GRUB as the boot loader" [/FONT]
[*] [FONT=Arial]Choose advanced boot loader options[/FONT]
[/LIST]

[LIST]
[*] [COLOR=Magenta][FONT=Arial]Choose to[/FONT][/COLOR][COLOR=Magenta][FONT=Arial] Install Boot Loader on  "First sector of boot partition".                 [/FONT][/COLOR]
[*]  [FONT=Arial]If prompted toward the end of the installation make a boot disk.[/FONT]
[/LIST]
 
[/LIST]

_**So... my question is: **_

In the _**Choose to Install Boot Loader on "First sector of boot partition"**_ option WHICH partition should I use to do that?! The Windows one ?! The Ubuntu one ?! Should I create a new partition just to install the GRUB ?! Any idea?!

Thanks!!!![B] :p
[/B]

---

### Post by whoop on 2009-05-15
I would advice to just pop in an ubuntu live-cd boot from it, and tell the installer to use the unallocated space. You can use grub to boot all your different os's and this will automatically be configured for you.

I wonder why it would be the best option for you not to install grub to it's default location.

---

### Post by dklord666 on 2009-05-15
Hi whoop! How are you?!

Thanks for your reply!

In fact my only reason for not installing GRUB in MBR was some findings when "googling" about windows reinstallations, hard disk resizing, etc!

I will do exactly what you said, just boot through the livecd, install Ubuntu using the unnalocated free space, I just wonder what to do after that... install GRUB in which partition (first boot sector): Windows ?! Ubuntu ?! In a dedicated boot partition ?!

From your personal experience, what is your advice, just forget about those issues I could have (if) I resintall Windows, or resize partitions using Acronis Disk Director ?!

Another question, IF I install GRUB in MBR, and resize partitions using Ubuntu, should I expect the same issues as if I did it with Windows ?!

By the way, I do not resize that much, just want to be prepared if I need to (in fact, in 2 years, this is the first time I resized my HD, just to install Ubuntu)... ;)

Wish to hear back from you soon!

Thanks alot! Have a nice day!

---

### Post by whoop on 2009-05-15
I would suggest just letting the installer decide on what to do (concerning grub). If you ever want to remove ubuntu and have a clean windows machine you can just remove every linux partition, resize windows partition and run a tool like fixmbr (which is on the windows cd) to recover your mbr.

---

### Post by gamblor01 on 2009-05-15
> 
I will do exactly what you said, just boot through the livecd, install Ubuntu using the unnalocated free space, I just wonder what to do after that... install GRUB in which partition (first boot sector): Windows ?! Ubuntu ?! In a dedicated boot partition ?!

Yes, using grub is the easiest thing to do.  Pop in the live cd, and go through the install process.  Make sure that on the third or fourth step you select to install Ubuntu to free space you currently have.

On the very last screen of the installation there will be an "Advanced" button.  You will want to click on that and ensure that grub is being installed to (hd0).  In Windows terminology (hd0) is the equivalent of the MBR.

Do ***NOT*** install grub to the first partition (/dev/sda1) as this will overwrite the Windows bootloader on that partition.  As long as you install to (hd0) you should be fine.  The Ubuntu installer will take care of setting up your /boot/grub/menu.lst file properly for you...this is the file that grub reads to determine what operating systems reside on which partitions, and how to load them.

> 
Another question, IF I install GRUB in MBR, and resize partitions using Ubuntu, should I expect the same issues as if I did it with Windows ?!

Yes, I would think it would cause the same issues no matter what was loaded into the MBR.  Luckily, it's easy to use the Windows CD (and the "fixmbr" command) or a Linux live CD to put either Windows or grub in the MBR.  It's very simple to recover one or the other.

I have used the NT bootloader to dual boot systems in the past and I can tell you it's a pain.  You have to go to each partition and use the dd command to copy the first 512 bytes of the partition and store that into a file (I always called mine bootsect.lnx).  Then copy that file over to your Windows partition and edit boot.ini accordingly.  If you resized/changed your partitions, I imagine you would have to recreate the bootsect.lnx file(s) all over again and copy them over to the Windows partition.

Just install grub in (hd0) and everything will be much simpler.  ;)

---

### Post by dklord666 on 2009-05-15
Friends! 

Thanks a lot for your explanations, and your time!

I´ll proceed exactly as both of you suggested, and just go ahead and let Ubuntu install GRUB in MBR...

gamblor01 you´re right, it seens too much trouble for just a small thing... You´re past experiences just tell us that! 

For sure it seens very easy to recover the MBR partition either way (reinstalling GRUB or using fixmbr)!

I´ll do it during the weekend, let you know as soon as it´s done!

Thanks once again!

Wish you a very nice weekend!

Cheers!

---

