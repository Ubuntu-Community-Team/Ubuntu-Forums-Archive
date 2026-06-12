---
title: "How to install Ubuntu 6.10 &quot;Edgy Eft&quot; on a MacBook"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Stefan Daniel Schwarz on 2006-11-01
Hello world!

Here's my guide **[how to install Ubuntu 6.10 "Edgy Eft" on a MacBook]("https://wiki.ubuntu.com/MacBook")**.

Why another HOWTO? There are others available already. But this one is different:
[LIST]
[*]Using only GRUB instead of LILO bootloader
[*]For the latest Ubuntu release
[*]Made for the official wiki
[*]Designed for Copy and Paste
[*]**Installation completes successfully without error, yes, on a MacBook!**
[/LIST]
I'm posting here to let you know about it, and so it can be discussed in a forum, which is more appropriate for discussion than a wiki.

Have fun with Ubuntu on the MacBook!

See ya! :cool:
-- StefanDanielSchwarz

---

### Post by learning on 2006-11-01
Just what I have been waiting for, thank you!  I'm going to try this out on my macbook, as soon as I get the time.  Are there any issues I should be aware of?  Does sound work?  Anything else not working?

---

### Post by Stefan Daniel Schwarz on 2006-11-02
> **learning said:**
> Are there any issues I should be aware of?  Does sound work?  Anything else not working?

I can only test it on a Black MacBook, but on mine, sound worked flawlessly. Suspend to RAM is troublesome, on resume the screen backlight isn't turned back on, even the backlight controller program doesn't affect brightness anymore. The remote control doesn't work out of the box, the internal mike doesn't work with Ekiga (some say it works with Skype, but I don't use that, so couldn't test it). Didn't yet test an external monitor. Also not yet a native way to control fan speed and temperature. Bugs for all of these problems have been filed at Launchpad!

That said, it's quite usable already: Kernel panic workaround (lpj), sane keyboard layout (xkb), LAN and WLAN work out of the box, backlight controller and iSight patch available, easy to set up Beryl. We're getting there, considering how new the MacBooks are, support has improved very quickly!

See ya!
-- sds

---

### Post by anzevi on 2006-11-04
very nice work! :)

---

### Post by phersotty on 2006-11-05
Hello,  

First thanks for the HowTo :KS  I followed it exactly except I used diskutil to partition the drive instead of Boot Camp.   When I got to step 7 rEFIt didn't show Linux as an option.  Instead it showed the Apple icon and an icon for a hard drive.  I selected the hard drive and it said missing operating system.  I had a triple boot system with Dapper before I tried your HowTo.  

I will try again with Bootcamp. :mrgreen:

---

### Post by Stefan Daniel Schwarz on 2006-11-05
> **phersotty said:**
> When I got to step 7 rEFIt didn't show Linux as an option.  Instead it showed the Apple icon and an icon for a hard drive.  I selected the hard drive and it said missing operating system.

Did you select "Start Partitioning Tool" **before** selecting the hard drive? Before you can boot GRUB, you **have** to update the GPT/MBR partition tables! Then, **after** another reboot, rEFIt should offer the new option "Boot Linux from Partition 3". Only then will GRUB work...

Let me know if you made it work that way - good luck!

See ya
-- sds

---

### Post by n00bWillingToLearn on 2006-11-05
I am on a macbook pro and I just wanted to say that your isight intructions worked verbatom on it also, I assume that your grub instructions would work on my macbook pro also, but I have already installed Edgy using LILO, and couldn't successfully adapt your instructions to work when installing grub manually post install. If you could give instructions on how to do that I would really appreciate it.
Also, if macbook users are also not able to use their ttys ( they were unusably distorted for me ) I have a fix for that if anybody cares.

Thank you verry much, I have been trying to get GRUB to work on my macbook pro for a long time :)

---

### Post by phersotty on 2006-11-06
> **Stefan Daniel Schwarz said:**
> Did you select "Start Partitioning Tool" **before** selecting the hard drive? Before you can boot GRUB, you **have** to update the GPT/MBR partition tables! Then, **after** another reboot, rEFIt should offer the new option "Boot Linux from Partition 3". Only then will GRUB work...

Let me know if you made it work that way - good luck!

See ya
-- sds

Yep I did exactly that and the partition table were in sync.  When I rebooted I get the blue Apple and a hard drive.  When I select the hard drive icon it creates a blank screen with the message Missing Operating System.  :confused: 

When I had my MacBook setup as a triple boot there was an icon of Tux the Penguin, but all I get now is an icon with a plain old hard drive.

---

### Post by phersotty on 2006-11-06
Hi,

I'm still getting stuck at steps 6-8 

Is the code > sudo chroot /target update-grub -y an exact command or does target refer to the root partion?  In other words should I be typing something like > sudo chroot /mnt/ubuntu update-grub -y  I tried it that way after getting the Missing Operating System message at reboot, but it still doesn't like me.

Since I haven't had much luck with Grub so far I tried lilo based on the instructions from OnMac.net, but I wasn't able to set sda3 as the active partition.  Then I went back to grub and checked /boot/grub/menu.lst and compared it to /etc/fstab and noticed the UUID notation.  It seems to me that the partition naming conventions aren't matching each other.

Okay I've got one more question.  If you only use a dual boot osX/Ubuntu can you still share files between the systems?  On the triple boot config I shared files between systems by saving everything on the XP fat32 partition.

Many thanks -phersotty

---

### Post by phersotty on 2006-11-06
Its working!! but I cheated!  I put the Edgy Eft CD back in the Macbook and selected Erase entire disk.  That's right the only OS on my Macbook is Ubuntu Edgy.  Grub worked immediately on reboot without any configuring.  All the other steps worked with cut and paste.  I now have a lightning zippy fast Macbook complete with Beryl and Emerald effects!!   :D :cool:

---

### Post by n00bWillingToLearn on 2006-11-06
> **phersotty said:**
> Its working!! but I cheated!  I put the Edgy Eft CD back in the Macbook and selected Erase entire disk.  That's right the only OS on my Macbook is Ubuntu Edgy.  Grub worked immediately on reboot without any configuring.  All the other steps worked with cut and paste.  I now have a lightning zippy fast Macbook complete with Beryl and Emerald effects!!   :D :cool:


Be sure to keep at least your OS x install CD and an external hard drive so you can do any firmware upgrades down the road.

---

### Post by phersotty on 2006-11-06
> **n00bWillingToLearn said:**
> Be sure to keep at least your OS x install CD and an external hard drive so you can do any firmware upgrades down the road.

Well once I was convinced that Edgy will work good on the Macbook I decided to redo everything from scratch.  I pulled an "all-nighter" installed OS x Tiger, Windoz Vista, and Edgy Eft.  When I rebooted I got same story.  rEFIt shows the Blue Apple, a windows logo for Vista.  I start the partitioning tool in rEFIt and it syncs the partition tables.  Then I restart and still only get those two commercial os.

I am only using 4 partitions Mac has hold of the first two (sda1 & sda2), Edgy sda3 with 2G swapfile, and Vista on sda4.  Grub doesn't come up so I tried lilo and it parted doesn't recognize the partition type.  The only way I can get into Edgy is to chroot from the LiveCD.

I'm going in loops aren't I? ](*,)     For bootloader = grub next bootloader=lilo ...grub.... lilo....grub... :-k

---

### Post by phersotty on 2006-11-06
> **n00bWillingToLearn said:**
>  I assume that your grub instructions would work on my macbook pro also, but I have already installed Edgy using LILO, 

Hi,  How did you install Edgy using LILO?  I couldn't set the active partition for LILO to boot to.  parted replied that I had an unknown partition type.

---

### Post by phersotty on 2006-11-06
Hello Stefan Daniel Schwarz,

I don't mean to be taking over this thread, but I do have little thing to verify.  Your guide is for a Macbook not a Macbook Pro correct?  What I am working with is a "plain jane" white Intel Macbook.  -phersotty

---

### Post by Nutrabuntu on 2006-11-06
I get the same "operating system missing" message after I sync the mbr using rEFIt. One thing I noticed in your instructions - it says that the hard disk shows up **before** syncing the mbr. It doesn't- only the apple icon and the linux cd are displayed until you sync the mbr. I doubt this makes a difference but I thought I would mention it. 
Hmmm.... Do you have any ideas about what else I should try? Thanks!

---

### Post by n00bWillingToLearn on 2006-11-06
> **phersotty said:**
> Hi, How did you install Edgy using LILO? I couldn't set the active partition for LILO to boot to. parted replied that I had an unknown partition type.
 
I installed using the Alternate install CD which gives you the option to install LILO instead of GRUB.

---

### Post by Stefan Daniel Schwarz on 2006-11-06
> **n00bWillingToLearn said:**
> I assume that your grub instructions would work on my macbook pro also, but I have already installed Edgy using LILO, and couldn't successfully adapt your instructions to work when installing grub manually post install. If you could give instructions on how to do that I would really appreciate it.

Boot into your Edgy installation using LILO as you used to, then remove LILO and install GRUB. "sudo update-grub -y" will ensure you have a menu.lst. Enter the GRUB shell with "sudo grub" and enter the following commands: "root (hd0,2)" followed by "setup (hd0,2)" - this enables GRUB booting from /dev/sda3.

If it failed and you can't boot anymore, use a live CD, then chroot into your system and reinstall LILO or try GRUB again with a different configuration.

It's a little bit risky, but the commands I provided do work with a default setup (/dev/sda3 for root, bootable, and /dev/sda4 as swap partition).

> **n00bWillingToLearn said:**
> Also, if macbook users are also not able to use their ttys ( they were unusably distorted for me ) I have a fix for that if anybody cares.

As of Edgy, the problem seems to have been fixed, my ttys work.

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-06
phersotty: You already got it working, but I'll still answer your questions...

> **phersotty said:**
> Is the code  an exact command or does target refer to the root partion?

All the code is written for verbatim copying and pasting.

> **phersotty said:**
> Then I went back to grub and checked /boot/grub/menu.lst and compared it to /etc/fstab and noticed the UUID notation.  It seems to me that the partition naming conventions aren't matching each other.

Don't worry about that, it's not a problem. The difference is between GPT and MBR partition schemes. The booted system works with GPT (so you can use more than four partitions and address them with UUID labels), but GRUB only understands MBR (so you can only boot from the first four partitions and must refer to them as sdaX or hd(0,X)).

> **phersotty said:**
> Okay I've got one more question.  If you only use a dual boot osX/Ubuntu can you still share files between the systems?  On the triple boot config I shared files between systems by saving everything on the XP fat32 partition.

You can mount the OS X filesystem from Ubuntu. Might work the other way around, too, but I haven't tried that. To mount the Mac OS X partition at /mnt, use a command like this:

```
sudo mount -t hfsplus /dev/sda2 /mnt
```

Of course you can also put it in your /etc/fstab to have it automounted when your system boots up. IMPORTANT - Check out this link for more information if you want read+write-access: [http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

See ya
-- sds

---

### Post by phersotty on 2006-11-06
> **Stefan Daniel Schwarz said:**
> phersotty: You already got it working, but I'll still answer your questions...

Thanks sds for answering my endless questions.  Your right I did have it working and working good too!  Your How To Guide was very helpful.  I might post my own how to for cramming osX, Vista beta, and Edgy or (Edgy Knot)into a Macbook as soon as I get it all working smoothly.  -phersotty

---

### Post by Stefan Daniel Schwarz on 2006-11-06
phersotty, n00bWillingToLearn, utrabuntu - I'm sorry to hear that fixing GRUB didn't go so easily for you. Because of your troubles, I've updated the HOWTO with a work-around how to fix GRUB by chroot'ing into the installed system from the live CD.

It's a little more elaborate than using one or two GRUB commands directly, but since GRUB doesn't boot at all for you, this should fix the problem!

Take a look and check out the new instructions at Step 8 (marked with red)... [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Hope it works!

See ya
-- sds

---

### Post by phersotty on 2006-11-06
> **Stefan Daniel Schwarz said:**
> 

Take a look and check out the new instructions at Step 8 (marked with red)... [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Hope it works!

See ya
-- sds

Thanks !  It looks like a logical fix.  I will try it out as soon as I get home.

---

### Post by muckster on 2006-11-07
Hi,

first I'd like to thank all of you for the guide, I've waited for this guide to come. But I still have problems trying to set up a triple boot (OS X, Ubuntu Edgy, WinXP) system on my MacBook.

In my first attempts I had OS X and Windows XP installed (both working fine). After installing Ubuntu, fixing the MBR via the rEFIt partitioning tool and restarting, Linux doesn't show up as an option in the boot menu at all. Trying to fix it with your proposed solution didn't work either:
After entering the grub console via 
sudo chroot /mnt grub
and changing the partition type, the next command
root (hd0,2)
encountered with an "Error 24: Attempt to access block outside partition".
Quitting the grub console, rebooting and fixing the MBR showed no change at all, regard the fact that my Windows XP installation didn't boot.

So I repartioned the whole system via Mac OS X install disk, installed OS X and tried to install Ubuntu before WinXP -- with nearly the same results:
After step 6 of your guide and and fixing the MBR I had a "legacy OS" icon. Selecting this icon resulted in "Boot disc error. Non system disk" (the same error message occurs when you start your Windows system with a floppy disc inserted -- if you have it as first item in your boot sequence).
So again I booted off the LiveCD and tried to fix it, but the same error 24 occured in the grub console.

Any help would be appreciated...](*,)

Regards,

muckster

---

### Post by phersotty on 2006-11-07
> **muckster said:**
> Hi,

first I'd like to thank all of you for the guide, I've waited for this guide to come. But I still have problems trying to set up a triple boot (OS X, Ubuntu Edgy, WinXP) system on my MacBook.



I think it should be noted that SDS's guide [https://wiki.ubuntu.com/MacBook]("https://wiki.ubuntu.com/MacBook")
is not intended for Triple booting.  Its intended for a dual boot of osX/Edgy.  For dual boot I think the guide is perfect! =D>  

That said, I am also trying to triple boot osX/Vista/Edgy and my partition table keeps getting screwed up.  I've successfully done it with osX/XP/Dapper according to [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu") 

Now I want to try something new.

Pre Mac Intel it was always a common practice to install windows first then Linux because Windows knocks out the Linux boot loader.  With that in mind, I am going to try from scratch again following these steps and see what happens.

1. Fresh install OS X 
2. Install Windows with Bootcamp. 
3. Install Edgy by resizing newly installed Windows partition.

I will post back my results.

---

### Post by Nutrabuntu on 2006-11-07
I got the same "Error 24: Attempt to access block outside partition" message when I tried. I am dual booting not triple booting. Back to square one but, with progress!

---

### Post by n00bWillingToLearn on 2006-11-07
> **Stefan Daniel Schwarz said:**
> phersotty: You already got it working, but I'll still answer your questions...



All the code is written for verbatim copying and pasting.



Don't worry about that, it's not a problem. The difference is between GPT and MBR partition schemes. The booted system works with GPT (so you can use more than four partitions and address them with UUID labels), but GRUB only understands MBR (so you can only boot from the first four partitions and must refer to them as sdaX or hd(0,X)).



You can mount the OS X filesystem from Ubuntu. Might work the other way around, too, but I haven't tried that. To mount the Mac OS X partition at /mnt, use a command like this:

```
sudo mount -t hfsplus /dev/sda2 /mnt
```Of course you can also put it in your /etc/fstab to have it automounted when your system boots up. IMPORTANT - Check out this link for more information if you want read+write-access: [http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

See ya
-- sds

AFIK there is no way currently to read ext3 partitions from within Tiger, there were drivers that worked with previous versions of OSx, but unfortunately that is not an option on intel macs :(

Also, I have had two HFS+ partitions corrupted by writing to them under Dapper ( I did follow the instructions and disabled journaling ) and neither disk utility nor disk warrior could fix the filesystem ( luckily I had nothing important on them ) so, unless things have changed, or my experiences are isolated, I would not recommend mounting HFS+ volumes read write in Edgy :( :(

I have looked, and I havn't been able to find any other filesystem supported by both OSx and linux that will support Unix permissions :( :( :(

---

### Post by n00bWillingToLearn on 2006-11-07
> **Stefan Daniel Schwarz said:**
> phersotty, n00bWillingToLearn, utrabuntu - I'm sorry to hear that fixing GRUB didn't go so easily for you. Because of your troubles, I've updated the HOWTO with a work-around how to fix GRUB by chroot'ing into the installed system from the live CD.

It's a little more elaborate than using one or two GRUB commands directly, but since GRUB doesn't boot at all for you, this should fix the problem!

Take a look and check out the new instructions at Step 8 (marked with red)... [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Hope it works!

See ya
-- sds

I followed the instructions for step 8 ( minus the chroot as I can still boot using LILO ) there were no errors, but grub still doesn't seem to be installed, when I boot I now have two options for booting linux rEFIt, "boot linux from hard drive" ( which I already had before ) and "boot linux from partition 3" ( which is new ) and both of those options lead me to boot using LILO. Do I need to do more than "apt-get remove lilo", or is does it really only work in a chroot? And I wonder if the tty's are only fixed in Edgy for macbooks, or if it has something to do with the fact that I am using lilo, but I still can only use my tty's if I don't use a bootsplash.

Thank you again for this guide, now that there is a known fix we may have a patch for ubiquity so that intel mac installs will "just work" with Feisty ( as they don't plan on adding support for LILO in ubiquity getting GRUB to work seems like the only solution ).

---

### Post by Stefan Daniel Schwarz on 2006-11-08
> **n00bWillingToLearn said:**
> I followed the instructions for step 8 ( minus the chroot as I can still boot using LILO ) there were no errors, but grub still doesn't seem to be installed, when I boot I now have two options for booting linux rEFIt, "boot linux from hard drive" ( which I already had before ) and "boot linux from partition 3" ( which is new ) and both of those options lead me to boot using LILO. Do I need to do more than "apt-get remove lilo", or is does it really only work in a chroot? 

To uninstall the LILO boot loader, you could use "sudo lilo -U", but you'd have to reinstall it before doing so. If that fails as well, try the chroot, it's not much effort and won't harm your current install.

> **n00bWillingToLearn said:**
> And I wonder if the tty's are only fixed in Edgy for macbooks, or if it has something to do with the fact that I am using lilo, but I still can only use my tty's if I don't use a bootsplash.

I am using the "splash" kernel option and tty's do work for me, on a Black MacBook.

See ya
-- sds

---

### Post by michaels on 2006-11-08
Does this how-to work totally and equally on 15' macbook pro?

---

### Post by n00bWillingToLearn on 2006-11-10
> **Stefan Daniel Schwarz said:**
> To uninstall the LILO boot loader, you could use "sudo lilo -U", but you'd have to reinstall it before doing so. 

That did it, I now have grub! And no more kernel panics to boot! Thanks

---

### Post by phersotty on 2006-11-10
> **n00bWillingToLearn said:**
> That did it, I now have grub! And no more kernel panics to boot! Thanks

Congratulations!

I didn't have as much luck.

I completely erased my Macbook and started over beginning with installing osX and followed the guide again step by step and created the following notes.

Step 3:  I noticed that Boot Camp creates a 128 mb unallocated gap between the osX partition and the "windows" partition.

Step 7: reboot resulted in missing operating system

Step 8: no grub shell at boot and  had to use live cd to fix grub
> grub> root(hd0,2) replied with Error: 24 Attempt to access block outside partition
> parted> print replied with Unable to open /dev/hda - unrecognised disk label

At this point I tried lilo iinstead of grub and but it wasn't able to install either because of the above issue with the partition table.

I know the rest of the guide works because earlier I was to complete it without installing osX on the Macbook.

The conclusion that I have come to is that somewhere in the process I have repeatly had issues with the partition table.  I am not sure if they were caused by Boot Camp or the partitioner in Edgy.  

-phersotty
  


Below: I am posting back some of my results from an earlier post.

> Now I want to try something new.

Pre Mac Intel it was always a common practice to install windows first then Linux because Windows knocks out the Linux boot loader. With that in mind, I am going to try from scratch again following these steps and see what happens.

1. Fresh install OS X
2. Install Windows with Bootcamp.
3. Install Edgy by resizing newly installed Windows partition.

I will post back my results.

Results: That idea just doesn't work so I don't recommend it.  Vista will complain about GPT

---

### Post by anzevi on 2006-11-11
This is a great piece of manual btw... So, is it possible to use hotkeys for setting up screen brightness?

---

### Post by Per Guth on 2006-11-11
> **phersotty said:**
> 
Step 8: no grub shell at boot and  had to use live cd to fix grub
 replied with Error: 24 Attempt to access block outside partition
 replied with Unable to open /dev/hda - unrecognised disk label

The way i solved this problem:

**1.** I followed the original howto until step 5.
I chose *Manually edit partition table* and deleted the 3. partition (which was created by bootcamp). I added the following partitions:
50 MiB ext3
8 GiB ext3 
2 GiB linux swap
REST xfs.
In the next step i mounted the 50 MiB partition as /boot, the 8 GiB as /, the 2 GiB as swap and the xfs as /home.

**2.** I installed it and followed step 6 and 7 of the original howto.

**3.** I booted Ubuntu from CD, typed
> sudo parted /dev/sda set 3 boot on
into the terminal, restarted and synced the tables via *Start Partitioning Tool* and restarted.

**4.** Then i booted from CD and opened the terminal:
> sudo mount /dev/sda3 /mnt
**sudo mount /dev/sda4 /mnt**
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt grub
And at the GRUB promt:
> parttype (hd0,2) 0x83
root (hd0,2)
setup (hd0,2)
quit
I restarted and synced via *Start Partitioning Tool* and restarted again.

**5.** I booted into Ubuntu from HDD but only the GRUB promt was available. I typed
> parttype (hd0,2) 0x83
into it and restarted again.

Now ubuntu works!

Last but not least i thank Stefan Daniel Schwarz for his HOWTO. I appreciate your work!

---

### Post by enkidou on 2006-11-12
This doesn't solve the problem of dual boot.

I need Mac OS X and Ubuntu on my MacBook.

But I also have those problems:
> Step 8: no grub shell at boot and had to use live cd to fix grub
Error: 24 Attempt to access block outside partition

Thanks for your help!

---

### Post by qzio on 2006-11-14
Hi!

I think i did something wrong becouse it doesn't work for me, (unable to locate os-stuffy)

I'll make a new attempt (ie re-installing osx and everything) tomorrow.

anyways, what i wanted to ask is if anyone got the double-tap = mouse2 thingy to work? or double-tab -> scroll thingy to work.

seems like the gentoo ppl have it working

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11)

I know i will atleast try (when i get the stupid thing to boot)

*edit*

how i got it to work:

boot with live cd, do not perform the "parted" thingy, mount /dev/sda3, /proc, /dev and perform the grub-thingys; reboot into livecd
use cfdisk on /dev/sda, set the linux-partion to bootable.
reboot

ended up in grub prompt, perform grub-prompt thingy.

booted \o/

will try the gentoo-touchpad-thingy tomorrow, i really need to get some sleep now :(

---

### Post by [L|eWiOn] on 2006-11-15
> **enkidou said:**
> This doesn't solve the problem of dual boot.

I need Mac OS X and Ubuntu on my MacBook.

But I also have those problems:
Step 8: no grub shell at boot and had to use live cd to fix grub
Error: 24 Attempt to access block outside partition
Thanks for your help!

i have those too :( :( what can i do???

@per guth

sudo mount /dev/sda3 /mnt
**sudo mount /dev/sda4 /mnt**
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt grub

why do you do that sda4 thingy???

---

### Post by qzio on 2006-11-15
he is mounting sda4 becouse he have more then one partition.

have you tried my solution? (ie simple forget to do the "sudo parted /dev/sda set 3 boot on",

---

### Post by blinksilver on 2006-11-16
any word on sleep? it really is a deal breaker : /

---

### Post by blinksilver on 2006-11-16
[http://www.dadeb.it/index.php/2006/11/01/ubuntu-edgy-on-a-macbook/](http://www.dadeb.it/index.php/2006/11/01/ubuntu-edgy-on-a-macbook/)

more on sleep, and well the macbook on ubuntu in general. So apparently it can sleep but without CD room support.

---

### Post by qzio on 2006-11-17
To get synaptics support for the touchpad i were forced to install 2.6.18 kernel.

Afterwards, i found out that mactel has its own ubuntu edgy .iso. I'll propably try that out once i get a working config.

---

### Post by Technoviking on 2006-11-17
> **qzio said:**
> 
Afterwards, i found out that mactel has its own ubuntu edgy .iso. I'll propably try that out once i get a working config.
Where can I find the mactel edgy iso? The last one I saw was a Edgy Knot 2 CD.

---

### Post by snowdrop on 2006-11-17
Hi,
thanks for the manual. Unfortunatly my rEFIt shows one apple and one windows logo on the boot menu. I can not see the penguen. When I choose the (grayed) windows logo, I just see the error messagte "missing operating system". I had no triple boot or something like this before. I just installed refit,bootcamp and ubuntu acording exactly the howto.
Do you have an idea? please.

Thanks

---

### Post by Stefan Daniel Schwarz on 2006-11-18
Hey all,

I've been quite quiet for a bit, but for good reason:

I just updated the HOWTO with a new, better approach how to successfully install Ubuntu on a MacBook. **After prolonged investigation, I found an easy way to install Ubuntu without an error on a GPT disk, with working GRUB!** Check out the guide and give it another try if the previous version didn't work for you.

[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Thanks to Junichi Uekawa for the refit .deb package which made the new version possible!

See ya
-- sds

---

### Post by lyapunov on 2006-11-19
Great!
It works for me...

With the live CD I had no boot problem, but I needed "lpj=8000000" during the normal boot operations ...
(sorry for my bad english)...

---

### Post by Stefan Daniel Schwarz on 2006-11-19
> **lyapunov said:**
> With the live CD I had no boot problem, but I needed "lpj=8000000" during the normal boot operations.

Yes, unfortunately that kernel bug still hasn't been fixed. :mad: Fortunately, if you enter it at boot time before installation, it will automatically be added to the grub configuration when the installation completes successfully.

---

### Post by willnight on 2006-11-19
hi, all.

i can't seem to see the swap drive to complete the installation.

i did this part (from another how-to):

sudo su
mkdir /mnt/linux
mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
mkswap /mnt/linux/swap
swapon /mnt/linux/swap

all i see are 4 partitions: mac (sda1); wxp (sda2); ext3 (sda3); and unused (sda4).

and then i tried making a swap space and ext3 (boot) in sda3, that didn't work. it added three more partitions: so i have sda3, sda5 (zero k); sda6 (zero k); and sda7 (zero k). i am so frustrated and confused! ](*,) :confused: 

what step am i missing? what am i doing wrong?

thnx!

---

### Post by rdwtux on 2006-11-19
Is anyone having touchpad "funkyness"?  My touchpad and mouse in general will lag down periodically.  The system doesn't seem especially busy when it happens, but it does feel like a lag of perhaps USB bus resources.  I wait ~5-10 seconds and it's fine.   Annoying though. 

The other one I've seen about 5-10 times is the touchpad will start drifting.  The mouse will slowly move by itself across the screen.  When this happens the keyboard usually locks up very soon after.  The system seems fine, but input devices won't work. 

Am I the only one?

---

### Post by xfile087 on 2006-11-19
Worked perfectly on my trusty Intel Mac Mini!

Of course, the idiot that I am, I backed up my system before re-installing... only I forgot to copy the backup elsewhere!

---

### Post by snowdrop on 2006-11-20
What about my problem???
I'm using a MacBook. rEFIt does not show me the pengues. Instead I can see one apple and one windows :(

> **snowdrop said:**
> Hi,
thanks for the manual. Unfortunatly my rEFIt shows one apple and one windows logo on the boot menu. I can not see the penguen. When I choose the (grayed) windows logo, I just see the error messagte "missing operating system". I had no triple boot or something like this before. I just installed refit,bootcamp and ubuntu acording exactly the howto.
Do you have an idea? please.

Thanks

---

### Post by qzio on 2006-11-20
> **Mike said:**
> Where can I find the mactel edgy iso? The last one I saw was a Edgy Knot 2 CD.

hm, you may be right.. (i'm no good at separating the different edgy versions)

anyways, I found the link via [http://www.mactel-linux.org/wiki/HOWTO](http://www.mactel-linux.org/wiki/HOWTO) which points to the sf archive at [http://sourceforge.net/project/showfiles.php?group_id=160126&package_id=181927](http://sourceforge.net/project/showfiles.php?group_id=160126&package_id=181927) 

I'll try that out after my #"%)=/" deadline at sunday >_< *back to work*

---

### Post by Stefan Daniel Schwarz on 2006-11-21
> **willnight said:**
> i can't seem to see the swap drive to complete the installation.
To check if swap is working, use one of the following commands:
```
free
```
Check the line "Swap:", it should show swap space greater than 0.
```
cat /proc/swaps
```
Lists swap partitions and files with additional information.

You listed commands to create a swap FILE, so you won't see a swap PARTITION, of course!

Hope this helps you a little bit.

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-21
> **rdwtux said:**
> Is anyone having touchpad "funkyness"?

Mine is fine! Did you use any extra kernel boot parameters like noapic?

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-21
> **snowdrop said:**
> What about my problem???
I'm using a MacBook. rEFIt does not show me the pengues. Instead I can see one apple and one windows :(

I can only suggest you retry with the latest version of the HOWTO as there have been several important changes to make installation work better and easier...

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-21
> **qzio said:**
> hm, you may be right.. (i'm no good at separating the different edgy versions)

anyways, I found the link via [http://www.mactel-linux.org/wiki/HOWTO](http://www.mactel-linux.org/wiki/HOWTO) which points to the sf archive at [http://sourceforge.net/project/showfiles.php?group_id=160126&package_id=181927](http://sourceforge.net/project/showfiles.php?group_id=160126&package_id=181927) 

I'll try that out after my #"%)=/" deadline at sunday >_< *back to work*

Looks like a very old version so I recommend you stick with Edgy and follow the latest version of the HOWTO. Once Ubuntu is installed properly on the MacBook and works, recompiling the kernel with Mactel patches should be possible without much of a problem.

See ya
-- sds

---

### Post by qzio on 2006-11-21
> **Stefan Daniel Schwarz said:**
> Looks like a very old version so I recommend you stick with Edgy and follow the latest version of the HOWTO. Once Ubuntu is installed properly on the MacBook and works, recompiling the kernel with Mactel patches should be possible without much of a problem.

See ya
-- sds

Yeah.. but..? isn't the mactel-patches already in the mainline kernel? like 2.6.18.1? or are there more patches?

the howto is great. But it would be even greater if it included how to get the synaptics thingy to work (ie two-finger scrolling), how to get an external screen to work together with the built-in one.

I'm hoping to be able to do a complete re-install before xmas, if i get the above things to work i'll wright some shortish howto-style post about it.. (altought i hope someone beats me to it!)

---

### Post by blinksilver on 2006-11-21
also, why patch the 2.6.18.1 vanilla branch, why not just patch the ubuntu source tree? And can someone please tell me why 6.06LTS with the latest security update sleeps but 6.10 does not? i like my ubuntu as much as the next guy, but if my system does not sleep, its just not as mobile as it can be.

---

### Post by jsilve1 on 2006-11-21
> **blinksilver said:**
> also, why patch the 2.6.18.1 vanilla branch, why not just patch the ubuntu source tree? And can someone please tell me why 6.06LTS with the latest security update sleeps but 6.10 does not? i like my ubuntu as much as the next guy, but if my system does not sleep, its just not as mobile as it can be.

The 'macbook-backlight-hal' package does not seem to work properly with Edgy (6.10).  My macbook sleeps just fine with Edgy, but I had to uninstall the macbook-backlight-hal package.  The package I mean is the one referred to here: [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

Note that the macbook-backlight package (on the same web page) works fine and does not affect sleep.

---

### Post by blinksilver on 2006-11-22
so wait do you have the standard macbook-backlight (not the absence of hal) package installed?

also how which lilo did you install, elilo, or just lilo and how did you install it?

---

### Post by jsilve1 on 2006-11-22
> **blinksilver said:**
> so wait do you have the standard macbook-backlight (not the absence of hal) package installed?

also how which lilo did you install, elilo, or just lilo and how did you install it?

Yes, the "mackbook-backlight" package (No "HAL") is installed and working fine.

I don't know which LILO I installed. I think just "regular" LILO.

Here are my installation notes:

[http://www.newtnotes.com/?itemid=196&catid=3]("http://www.newtnotes.com/?itemid=196&catid=3")

I have been meaning to add even more detail, but some of the details are redundantly available on the websites from which I originally got the instructions.  The /bin/false web page is good, but could stand to be rewritten a bit.

Stefan's Edgy-on-Macbook howto was great but I could not, at all, get Grub to work as described.

seeyalater...

---

### Post by rdwtux on 2006-11-22
> **Stefan Daniel Schwarz said:**
> Mine is fine! Did you use any extra kernel boot parameters like noapic?


I have noapic.  Didn't use "lpj=8000000" since I wasn't getting a crash at boot. 

Are there other parameters?

---

### Post by zpon on 2006-11-23
My wlan card does not work, how can this be? Is it because i have the new version with core 2 duo? how can i get it working? I have tried modprobe new_wlan_scan_sta, but the module can't be found

Another thing is the backlight controle

No matter if i type  /usr/bin/macbook-backlight -10 or  /usr/bin/macbook-backlight +10 i get this error:
unexpected maximum brightness value

By the way, i like the guide :)

---

### Post by ipstacks on 2006-11-23
My airport card isn't working in edgy on the macbook. It doesn't even see it with iwconfig. I am surprised someone else hasn't posted this, if this has been a problem for others. 

The radio is on when I shutdown OS X. Has anyone had this problem? I am guessing I am missing a driver.

---

### Post by zpon on 2006-11-24
If you see the last post on the previous side you will see my wlan card isn't found neither.
Can you change the backlight?

---

### Post by ipstacks on 2006-11-24
zpon, I haven't installed any other software yet other than refit to get it installed. I am happy enough with OS X, but not having edgy on this box is making me a little edgy too.

---

### Post by JammyZ on 2006-11-24
Yesterday I received my MacBook with core 2 duo and I tried to follow the guide but I wasn't very successful. First of all I couldn't find any firmware  newer than mine (which I think it makes sense). Then I installed bootcamp and divided the HD in two, installed refit and inserted the Ubuntu Edgy x86 disc. After rebooting I see the penguin in the boot menu and I choose it. Then Ubuntu's cd boot menu shows up and here comes the problems: Sometimes the keyboard doesn't work at all (but I still see the countdown running), sometimes it works and I press Start or Install Linux but then it gets stucked, no response at all and I have to reboot the machine... I've also tried adding the lpj parameter in the boot parameters (when the keyboard works) but it doesn't seem to make a difference.
Should I try with the AMD64 version? any clue of what can be going on?

**FIXED - IT WAS AN UNREADABLE CD-R**

---

### Post by ipstacks on 2006-11-24
Jammyz it sounds like you have things out of order. My keyboard didn't work when the live cd was starting either, but it worked after it got to the login screen. I didn't install refit until I was booted on the live cd and I had to use eth0 (wired) because the wireless is MIA. It maybe that you just said them out of order, I don't know. have a great day.

---

### Post by zpon on 2006-11-24
You should not use the AMD64 version, hence your cpu is a intel.
My keyboard did'nt work neither, but i let the countdown run out, and live cd startede, and both my keyboard and mouse worked fine, and i could install as the guide descriped

---

### Post by JammyZ on 2006-11-24
Intel's Core 2 Duo is a EM64T architecture processor. If you check in [http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/) under 64-bit PC (AMD64) desktop CD you'll see that it is for both AMD64 and EM64T architectures. So I think that it makes sense to install this version in Core 2 Duo MacBooks.

For more info check: [http://en.wikipedia.org/wiki/Amd64](http://en.wikipedia.org/wiki/Amd64)

Anyway, I cannot install the X86 one yet, I let the countdown finish and then I see a couple of green "Loading" in the top of the screen but nothing happens in a few minutes, so I think that it is stucked...
**FIXED - IT WAS AN UNREADABLE CD-R**

---

### Post by JammyZ on 2006-11-24
I'm suspecting a cd reading error, could be the DVDRW-drive or the cd itself (seems a bit too scratched :P **FIXED - IT WAS AN UNREADABLE CD-R**). I'll update as soon as I can get another cd. Anyway I think that we should consider the possibility of trying the AMD-64 version anyway. I'll give it a try during the next days.

---

### Post by zpon on 2006-11-24
I'm sorry, i didn't know that :$.
I'm still looking fore some ideas to how i get my wlan working on my macbook

---

### Post by horvatj on 2006-11-25
Thanks for your superb howto! Evertything works, instead of my airport - wireless card...

> johann@macbook:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
johann@macbook:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Has anyone the same problem?

Thanks 
Johann

---

### Post by zpon on 2006-11-25
If you read the post just above  your own you will see I have the same problem ;). My lspci and iwconfig gives the same output as yours

---

### Post by Stefan Daniel Schwarz on 2006-11-25
> **rdwtux said:**
> I have noapic.  Didn't use "lpj=8000000" since I wasn't getting a crash at boot. 

Are there other parameters?

Touchpad "funkyness" is a known problem when using "noapic", so don't use that parameter! If you get a crash at boot, use "lpj=8000000" (for 2 GHz MacBooks) instead.

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-25
> **qzio said:**
> the howto is great. But it would be even greater if it included how to get the synaptics thingy to work (ie two-finger scrolling), how to get an external screen to work together with the built-in one.

While I haven't tried the synaptics thingy yet because of reported problems with it, I did spend some time figuring out how to make an external screen work together with the built-in one.

I've added instructions about dual-head modes to the [MacBook]("https://wiki.ubuntu.com/MacBook") HOWTO!

See ya
-- sds

---

### Post by rdwtux on 2006-11-25
> **Stefan Daniel Schwarz said:**
> Touchpad "funkyness" is a known problem when using "noapic", so don't use that parameter! If you get a crash at boot, use "lpj=8000000" (for 2 GHz MacBooks) instead.

See ya
-- sds

Thanks sds.  I'll remove noapic from my boot options.

---

### Post by cdinz on 2006-11-27
Hey everyone...can someone confirm if the macbook-backlight thing is working? That is the only thing stopping me from installing Edgy on my MacBook...

---

### Post by Stefan Daniel Schwarz on 2006-11-27
> **cdinz said:**
> Hey everyone...can someone confirm if the macbook-backlight thing is working? That is the only thing stopping me from installing Edgy on my MacBook...

Yes, it sure does! macbook-backlight-hal no longer works with Edgy and has been reported to cause problems with software suspend/sleep, so I removed it from the guide. The HOWTO does explain how to install macbook-backlight without HAL support, though, and even gives detailed instructions how to make the brightness adjustment keys work in Ubuntu's GNOME.

---

### Post by zpon on 2006-11-27
The adjustment key doesn't work on my macbook though (and the same with my wireless connection)

---

### Post by Stefan Daniel Schwarz on 2006-11-27
> **zpon said:**
> The adjustment key doesn't work on my macbook though (and the same with my wireless connection)

Did you follow my guide?

```
wget http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb
gdebi-gtk macbook-backlight_0.0-1_i386.deb
sudo chmod u+s /usr/bin/macbook-backlight
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"
```

This downloads the macbook-backlight package, installs it, and makes /usr/bin/macbook-backlight executable by non-root users. The "gconftool" lines create keybindings which make the brightness adjustment keys work in Ubuntu's GNOME desktop.

Of course, this was written for the original MacBook, I don't know how well it translates to the MacBook Pro and the new generation of both.

---

### Post by cdinz on 2006-11-27
> **Stefan Daniel Schwarz said:**
> Yes, it sure does! macbook-backlight-hal no longer works with Edgy and has been reported to cause problems with software suspend/sleep, so I removed it from the guide. The HOWTO does explain how to install macbook-backlight without HAL support, though, and even gives detailed instructions how to make the brightness adjustment keys work in Ubuntu's GNOME.

Thanks Stefan... :KS

---

### Post by Etiene on 2006-11-27
Quick question, I can get all the way to the downloading of the .deb file, but I can't get the file because the wireless doesn't work.

How do I get that file? Do I need to plug in through ethernet?

---

### Post by zpon on 2006-11-28
> **Stefan Daniel Schwarz said:**
> Did you follow my guide?

```
wget http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb
gdebi-gtk macbook-backlight_0.0-1_i386.deb
sudo chmod u+s /usr/bin/macbook-backlight
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"
```

This downloads the macbook-backlight package, installs it, and makes /usr/bin/macbook-backlight executable by non-root users. The "gconftool" lines create keybindings which make the brightness adjustment keys work in Ubuntu's GNOME desktop.

Of course, this was written for the original MacBook, I don't know how well it translates to the MacBook Pro and the new generation of both.

Yes I did follow your guide, and when the keys didn't work i tried to execute the comand from a terminal and got this error

```
$ /usr/bin/macbook-backlight -10
unexpected maximum brightness value
```
(The same with +10)

I guess it is because I got the "new generation", I got these problems, but hopefully some one will find a solution to them

---

### Post by zpon on 2006-11-28
> **Etiene said:**
> Quick question, I can get all the way to the downloading of the .deb file, but I can't get the file because the wireless doesn't work.

How do I get that file? Do I need to plug in through ethernet?

I guess that will be the easiest way, and I had to do that as well

---

### Post by Stefan Daniel Schwarz on 2006-11-28
> **Etiene said:**
> Quick question, I can get all the way to the downloading of the .deb file, but I can't get the file because the wireless doesn't work.

How do I get that file? Do I need to plug in through ethernet?

That's the way I did it. Alternatively, you can put it on a memory stick, of course. Or you might be able to install network-manager-gnome and connect to your WLAN from the live CD, if it's included on the CD, but I haven't tried this.

---

### Post by Nelson-Ray on 2006-11-28
I installed via the guide and everything worked good. My problem is upon reboot at refit I can select between OS X and Linux. Once I select Linux...I just get a black screen with no output on the screen. I have to do a cold reset (take out the battery and unplug ac) and then reboot, pick Linux in refit again...then Edgy will boot up fine. This happens every time. Anybody has a similar problem or know a fix? I do have "lpj=8000000" as a boot parameter in grub.

---

### Post by Stefan Daniel Schwarz on 2006-11-29
> **Nelson-Ray said:**
> I installed via the guide and everything worked good. My problem is upon reboot at refit I can select between OS X and Linux. Once I select Linux...I just get a black screen with no output on the screen. I have to do a cold reset (take out the battery and unplug ac) and then reboot, pick Linux in refit again...then Edgy will boot up fine. This happens every time. Anybody has a similar problem or know a fix? I do have "lpj=8000000" as a boot parameter in grub.

What model and generation of MacBook do you have?

Does a "normal" reset work as well, instead of taking out the battery and unplugging ac, by keeping the Power Button pressed until the system shuts down?

Does the problem also appear when you start the system, reboot by choosing the rEFIt menu entry "Restart", and then try to boot Linux?

---

### Post by zpon on 2006-11-29
I found a (temporary) solution to the problem with the wifi problem on the new version of macbook, using ndiswrapper, read more here [http://ubuntuforums.org/showthread.php?p=1822454#post1822454](http://ubuntuforums.org/showthread.php?p=1822454#post1822454)

---

### Post by michaels on 2006-11-30
hi, guys.

I'm new to ubuntu. I have a problem about my macbook pro keyboard mapping.

According to the wiki, I find the following command:

sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/pc

could somebody tell me what the "pc" in the "/etc/X11/xkb/symbols/pc" means?

And after installing, the default keyboard layout is set to "Generic 101-key PC". With it, my "F1" to "F10" don't work. Is there some idea for it? Moreover, ideally, I wanna enable the mouse emulation on the right apple key. Is there some command for it?

Soryy for full of a little stupid problems. I'm a totally newbie and need some help. Thanks a lot!

---

### Post by gnufede on 2006-11-30
Hi guys,

I've got some backlight control on Macbook "new generation" (core 2 duo) by editing desrt's macbook-backlight just changing:

```
#define VIDEO_CARD_ADDRESS    0x**9**0380000 /* taken from lspci, 512K region */
```

by:

```
#define VIDEO_CARD_ADDRESS    0x**5**0380000 /* taken from lspci, 512K region */
```

Hope you find it useful.

---

### Post by PetrB on 2006-12-01
Hi,

we have got our dual boot up and running on our 1.83 GHz Macbook  but screen ratio is rather wrong - we have got elipses instead of circles (and rather fat people on photos...). 915resolution was installed. 

Is it a problem of configuration?

---

### Post by Stefan Daniel Schwarz on 2006-12-01
> **michaels said:**
> could somebody tell me what the "pc" in the "/etc/X11/xkb/symbols/pc" means?

It's the generic PC keyboard. I modified this file so the mouse emulation would work no matter which localized keyboard is actually used. This way it works with US and European MacBooks, for example.

> **michaels said:**
> And after installing, the default keyboard layout is set to "Generic 101-key PC". With it, my "F1" to "F10" don't work. Is there some idea for it? Moreover, ideally, I wanna enable the mouse emulation on the right apple key. Is there some command for it?

F1-F10 have been swapped with fn+F1-F10. I reported the bug here: [MacBook keymap broken](https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/69061)

If you want mouse emulation on the right apple key instead of the lower enter key (which is better for international keyboards where you need the Alt Gr functionality), try something like the following:

```
key <RWIN> {        [       Pointer_Button3, Pointer_Button3, Pointer_Button2, Pointer_Button2      ]       };
```

This code should be added to the appropriate file in /etc/X11/xkb/symbols/. Which one to use depends on your actual keyboard layout. Some trial and error might be in order. All that said, I recommend you use the lower enter key instead, it's easier and more reliable. At least until touchpad emulation is better supported...

---

### Post by michaels on 2006-12-01
Thank you, guy.

Your answer helps me a lot!

:D :D :D

---

### Post by zpon on 2006-12-01
I got the backlight function working, with the new source file [http://desrt.mcmaster.ca/code/macbook-backlight/macbook-backlight.c](http://desrt.mcmaster.ca/code/macbook-backlight/macbook-backlight.c) (alhough i had to out comment some of it
```
//#ifdef GENERATION_2
#define VIDEO_CARD_ADDRESS    0x50380000
//#else
//#define VIDEO_CARD_ADDRESS    0x90380000 /* taken from lspci, 512K region */
//#endif

```)
I have tried to use
```
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"
```
to make a shortcut to lower or raise the light, but i doesn't work (and yes I have put the compiled file in /usr/bin/ :) ). Is there another way?
BTW the delete function does not work neither

---

### Post by derlinger on 2006-12-02
Does anyone know a workaround for beryl to install it on a macbook with the server down?
I installed ubuntu using parallels, has anyone experienced problems with this?

---

### Post by rdwtux on 2006-12-03
> **derlinger said:**
> Does anyone know a workaround for beryl to install it on a macbook with the server down?
I installed ubuntu using parallels, has anyone experienced problems with this?

There are quite a few mirrors for beryl.  Just search Google for "beryl mirror" the 2nd match is a mirror. 

Using Beryl in Parallels isn't going to be joyful.  Beryl needs 3d acceleration from the video card, which Parallels doesn't support. 

I did see Parallels has added a pretty cool feature call "Coherency" which hides the virtualized OS desktop, integrating the virtualized OS's apps with the native Mac OS X apps.  Very cool.  I'm thinking it only works with XP at this point, unless someone else knows different.
[http://flickr.com/photos/gruber/311690002/](http://flickr.com/photos/gruber/311690002/)

---

### Post by undead-monkey on 2006-12-07
Great tutorial. Installed Edgy on my Blackbook without a hitch. WiFi is even working without any extra hassles. Just need to buy a bigger HD so I can give  Ubuntu more than the 12 Gb it has now.

---

### Post by nnutter on 2006-12-08
I have a question about the Xinerama setup.

I copied the stuff into my xorg.conf but I don't know quite how to modify it. I want to use the mini-DVI out with Apple's video adapter so I can watch movies on my TV. I tried turning on Xinerama and modified the second screen to be 800x600. When I restarted X there was no picture on the TV but my desktop was shifted over and the mouse seemed like it was aware of another screen. I tried looking on Google and Gentoo's wiki (they are often helpful) but it seemed like the results were mostly related to using TV out on high end cards and tuner cards. I also noticed that many were for twinview and not Xinerama.

Does anyone have any suggestions on how to configure the screen/device to best work with a TV?

---

### Post by michaels on 2006-12-09
I install edgy on my macbook pro

However, while running it, my computer gets very hot!!

and I check /proc/acpi/fan, there's nothing in it. I want know how about the situation like on your macbooks? is it so hot?

Thank you.

---

### Post by zpon on 2006-12-10
> **michaels said:**
> I install edgy on my macbook pro

However, while running it, my computer gets very hot!!

and I check /proc/acpi/fan, there's nothing in it. I want know how about the situation like on your macbooks? is it so hot?

Thank you.

I have a macbook with core 2 duo, and is normally around 60 °C, you can use
```
sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp
``` 
(found here [http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+temperature](http://ubuntuforums.org/showthread.php?t=198453&highlight=macbook+temperature)) to see the your cpu temperatures

---

### Post by Stefan Daniel Schwarz on 2006-12-10
> **michaels said:**
> However, while running it, my computer gets very hot!!

and I check /proc/acpi/fan, there's nothing in it. I want know how about the situation like on your macbooks? is it so hot?

There has been a firmware update for (at least first generation) MacBooks which modified fan behavior. It still gets quite hot despite this, though, because Ubuntu can't get the fan information (as you noticed), so it can't control the fans properly. This is one of the most important bugs, IMHO, so I hope it gets fixed with a kernel update as soon as possible.

The bug report is here: [https://launchpad.net/distros/ubuntu/+bug/52852](https://launchpad.net/distros/ubuntu/+bug/52852)

You're welcome to add your voice to it so it may be fixed more urgently...

---

### Post by michaels on 2006-12-10
Thanks a lot! guys!

One more advice: if it is possible to use AC adapter, please take off the battery of you macbook. The nearly 60-degree temperature will obviously shorten the life of bettery.

Good luck, everyone!
:D

---

### Post by hesee on 2006-12-11
I just bought a new core 2 duo macbook and paid a lot of money for it. Is it safe to install (k)ubuntu into it because of this overheating issue? I don't want to risk anything. :-k 

Also, what is the right kernel for this? Probably i686-smp in theory, but is that what is best in practice (or i386?)

---

### Post by tgomas on 2006-12-11
Hi,
I used successfully the howto and installed edgy eft on my macbook C2D.
Thanks a lot for that work.

I'm now looking to connect my bluetooth mighty mouse. I have installed bluez packages and set the HIDD_ENABLED=1 option in /etc/default/bluetooth but it looks like there is no hci interface.

Has anyone some experience with bluetooth on macbook?

---

### Post by zpon on 2006-12-12
> **tgomas said:**
> Hi,
I used successfully the howto and installed edgy eft on my macbook C2D.
Thanks a lot for that work.

I'm now looking to connect my bluetooth mighty mouse. I have installed bluez packages and set the HIDD_ENABLED=1 option in /etc/default/bluetooth but it looks like there is no hci interface.

Has anyone some experience with bluetooth on macbook?

I haven't tried my bluetooth yet, but I will give it a try later this week and see if works. Have you hat the opportunity to test your wireless card on your core 2 duo?

---

### Post by tgomas on 2006-12-12
> **zpon said:**
> I haven't tried my bluetooth yet, but I will give it a try later this week and see if works. Have you hat the opportunity to test your wireless card on your core 2 duo?

yes, working fine with network-manager and gnome for gui. since madwifi still   does not work with ubuntu edgy's kernel, ndiswrapper used.

---

### Post by Jason DeRose on 2006-12-13
Firstly, thanks Stefan for the great howto!

I have 2.0 GHz Core Duo White MacBook, bought just about a week before the Core 2 Duo models were released. I followed the instructions exactly, but it didn't work... after the reboot, refit was gone and it booted directly into Ubuntu.

The howto seems to imply that grub should be installed on partition 3, but dosen't give explicit instructions. So should grub be installed on (hd0) or on (hd0,2)? I tried both, but neither worked. (hd0,2) resulted in a "No operating system found" error on reboot. I'll gladly edit the wiki to make this clearer, once I find out which is correct.

Also, the howto currently has one sync the GPT / MBR only once... is that all that is needed?

I ended up doing a single boot setup, the method for which I described at [https://wiki.ubuntu.com/MacBookSingleBoot](https://wiki.ubuntu.com/MacBookSingleBoot)

Lastly, ever since I started using the lpj=8000000 boot parameter, I've been getting a weird DVD drive error frequently. The end result is that it kicks the drive out of DMA. Has anyone else had this problem?

Here is some dmesg output resulting from this problem:

[17187562.424000] hda: ATAPI reset complete
[17187563.592000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17187563.592000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17187563.592000] ide: failed opcode was: unknown
[17187564.772000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17187564.772000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17187564.772000] ide: failed opcode was: unknown
[17187566.452000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17187566.452000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17187566.452000] ide: failed opcode was: unknown
[17187566.452000] hda: ide_intr: huh? expected NULL handler on exit
[17187566.500000] hda: ATAPI reset complete
[17187566.500000] end_request: I/O error, dev hda, sector 9149972
[17187566.500000] Buffer I/O error on device hda, logical block 2287493
[17187567.916000] hda: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17187567.916000] hda: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17187567.916000] ide: failed opcode was: unknown

---

### Post by hesee on 2006-12-17
Hi,
Is there any difference if i install kubuntu instead of ubuntu? Is the desktop environment the only difference or are there bigger differences between kubuntu and ubuntu? Of course it would be possible to install ubuntu first and then kubuntu-desktop, but if that's not necessary, i wouldn't want to do it....

Edit: oops... ;)

---

### Post by zpon on 2006-12-17
> **hesee said:**
> Hi,
Is the desktop environment the only difference or are there bigger differences between kubuntu and kubuntu?
I don't think there is any different between kubuntu and kubuntu :P ;)

---

### Post by Stefan Daniel Schwarz on 2006-12-18
> **hesee said:**
> Is there any difference if i install kubuntu instead of ubuntu? Is the desktop environment the only difference or are there bigger differences between kubuntu and ubuntu? Of course it would be possible to install ubuntu first and then kubuntu-desktop, but if that's not necessary, i wouldn't want to do it....

Kubuntu and Ubuntu are basically the same, just a different choice of packages, so you can follow the guide and simply skip GNOME-specific commands.

To be specific, instead of installing network-manager-gnome, simply install knetworkmanager. And instead of running gconftool-2 to configure keyboard/mouse shortcuts, use KDE's mouse and hotkeys control panels to set it up graphically.

If you need further help or more detailed instructions, let me know, personally I run Kubuntu instead of Ubuntu.

---

### Post by hesee on 2006-12-19
> **Stefan Daniel Schwarz said:**
> Kubuntu and Ubuntu are basically the same, just a different choice of packages, so you can follow the guide and simply skip GNOME-specific commands.

To be specific, instead of installing network-manager-gnome, simply install knetworkmanager. And instead of running gconftool-2 to configure keyboard/mouse shortcuts, use KDE's mouse and hotkeys control panels to set it up graphically.

If you need further help or more detailed instructions, let me know, personally I run Kubuntu instead of Ubuntu.

Thanks, that was what I wanted to hear. I don't think there will be any big problems, but if there is, I know where to ask. 8)

---

### Post by hesee on 2006-12-19
Ok, first of all, many thanks to you sds! I have kubuntu running fine. :D 

One problem: I installed backlight package, but don't know how to set keyboard shortcuts for it? I found System settings-> keyboard & mouse->keyboard shortcuts. But how is it done here?

Stupid question, this shouldn't be so difficult ](*,)  This is almost first time for me actually with kde...

---

### Post by hesee on 2006-12-19
> **gnufede said:**
> Hi guys,

I've got some backlight control on Macbook "new generation" (core 2 duo) by editing desrt's macbook-backlight just changing:

```
#define VIDEO_CARD_ADDRESS    0x**9**0380000 /* taken from lspci, 512K region */
```

by:

```
#define VIDEO_CARD_ADDRESS    0x**5**0380000 /* taken from lspci, 512K region */
```

Hope you find it useful.

Ok, "unexpected maximum brightness", but there's this solution.

But, how is this done. Do i have to compile the package?

---

### Post by Stefan Daniel Schwarz on 2006-12-19
> **hesee said:**
> One problem: I installed backlight package, but don't know how to set keyboard shortcuts for it? I found System settings-> keyboard & mouse->keyboard shortcuts. But how is it done here?

Great, I'm glad you got so far!

This is unfortunately quite hidden because it's not where one would expect it to be set up (Keyboard shortcuts, where you looked for it), instead it's part of the accessibility settings (I don't know what it's called in English, but it's the blue symbol with the wheelchair). There it's the second option, keyboard gestures or hotkeys or whatever it's called. (Or simply run: **kcmshell khotkeys**)

There you can create simple actions which run the /usr/bin/macbook-backlight command with +10 or -10.

---

### Post by moaxey on 2006-12-19
not sure why 915resolution didnt work for me straight off,
maybe because i had an external monitor plugged in 

no-one seemed to have posted on the topic

was able to fix by following the directions in this post

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

and manually selecting the 1280x800 resolution in the 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mustang on 2006-12-19
hesee:

are you encountering any heat issues with your laptop & kubuntu?

---

### Post by mebaran on 2006-12-19
Quick question.

Why is macbook-backlight-hal broken?  I thought it was just a collection of scripts.  I tend to run my battery to its limits and the autodimming backlight is a must.  I know some shell, so I could try to debug them, except I don't know how a shell script woudl interact with the sleep/hibernate system.

How does sleep and hibernate work on the macbook anyway?

Thanks,
Mark

---

### Post by moaxey on 2006-12-20
got this error on starting x after following dual head configuration instructions

```
Data incomplete in file /etc/X11/org.conf
Undefined Monitor "Color LCD" referenced by Screen "MonitorLayout Screen".
```

which was a fatal server error.

my original xorg.conf was generated (after messing it up) with 
sudo dpkg-reconfigure -phigh xserver-xorg

the example file had 
```
Section "Monitor" 
    Identifier "Color LCD"
```

I had 
```
Section "Monitor" 
    Identifier "Generic Monitor"
```

so after finding and replacing all "Color LCD" with "Generic Monitor" it worked,

and have a fantastic dual head two screen configuration, something i've never managed before under ubuntu on any hardware!

---

### Post by hesee on 2006-12-20
> **mustang said:**
> hesee:

are you encountering any heat issues with your laptop & kubuntu?

So far, it seems that it is not heating more than in OS X, although I have not done anything really CPU-intensive yet. Only problem I have is with the backlight, the same package don't work with new generation(c2d) macbooks (see couple of posts above). Apparently I have to compile the new version somehow. Also I have not been able to test wlan yet.

---

### Post by dani_bcn on 2006-12-20
First and foremost thanks for this awesome guide, I have all the stuff almost working.

So far things not working are:

- Wifi (I know, madwifi does not work with new macbook version, I've to try ndiswrapper)
- fn key

So my problem now is the fn key not working, so I do not have the home,end, av.pag,re.pag functions and some more.

Any idea where I can fix this?

Thanks for the help.

---

### Post by hesee on 2006-12-20
> **hesee said:**
> Ok, "unexpected maximum brightness", but there's this solution.

But, how is this done. Do i have to compile the package?

Still "unexpected maximum brightness value" although I changed the VIDEO CARD ADDRESS and compiled new version :confused: 

If anyone is experienced with compiling, can you see something wrong here:

```
gcc -Wall -DGENERATION_2 macbook-backlight.c -o macbook-backlight
```

Edit: Problem solved, the appication should be placed to /usr/bin/, I tried to run it from home folder. Now it is working! Should have read the manual :)

---

### Post by rzrobecki@gmail.com on 2006-12-20
hi there,
i have a black macbook pro, everything went very well with installation of ubuntu, however there is still an issue with wlan card. Network manager seems to be working, but wlan interface is missing there. Any hints?

Second thing, anyone knows how to emulate 'insert key'? I need it for VIM :)

thanks,
raf

---

### Post by dani_bcn on 2006-12-21
Raf, I think you have the same problem as me. Probably your wlan card has the new atheros chipset and madwifi still does not support it.

There is some people using it with ndiswrapper.

Check [http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)

---

### Post by Stefan Daniel Schwarz on 2006-12-23
> **rzrobecki@gmail.com said:**
> Second thing, anyone knows how to emulate 'insert key'? I need it for VIM :)

To bind the Insert function to another key on the MacBook keyboard, for example Fn+Function Keys, create a **~/.Xmodmap** configuration file (which Ubuntu will automatically use after confirmation during GNOME login):

fn+F7 = keycode 214
fn+F8 = keycode 215
fn+F9 = keycode 216
fn+F10 = keycode 217

Example: Bind Insert to fn+F7:

_~/.Xmodmap_
```
keycode 214 = Insert
```

As a work-around, just use the "i" key, it's the same as insert in VIM.

---

### Post by dani_bcn on 2006-12-23
Err I don't know if it's a problem in the new version of Macbook's or what, but my fn key does not work.  So it's the same to press fn + F1 than F1 or any othe combination.


Any idea how to fix it?

---

### Post by pouns on 2006-12-24
I've got the same problem of fn with a new macbook. This key doesn't show anything in xev. I'm still looking for a solution :)

---

### Post by moaxey on 2006-12-25
unclear as to why this is happening

its an annoyance really...

but when I switch around my xinerama setups... i have one for working dual screen in studio, one for doing projections, and another for single screen

but when i switch between them, my 'lower enter key as right mouse click' breaks

i can run the script again, and it goes, but its a bit boring.

perhaps i need to do something special in restarting gnome???

I'm trying working on a more versatile keyboard setup for me, where right command key is right mouse and lower enter key is delete-to-the-right.

---

### Post by macmatt on 2006-12-27
This is all well and good but seems more trouble than it is worth to simply have Ubuntu on a Mac which is a better solution and zero hassle. I can see why people want to do it, but it just not worth the hassles and tearing out of hair imho.

:)

---

### Post by hesee on 2006-12-28
> **macmatt said:**
> This is all well and good but seems more trouble than it is worth to simply have Ubuntu on a Mac which is a better solution and zero hassle. I can see why people want to do it, but it just not worth the hassles and tearing out of hair imho.

:)

I can understand your opinion, mac and os x are a combination that "just works". But I cannot stay in os x, I feel too restricted... :-|  Anyway, use what suits you best.

---

### Post by macmatt on 2006-12-28
:) thanks dude! :)

---

### Post by voights on 2006-12-28
I've installed Ubuntu this way, but when I reboot and start linux, it shows a grey screen with a penguin, that never goes away.

Thank you

---

### Post by macmatt on 2006-12-29
Personally I would recommend that people run ubuntu/*nix etc inside "parallels workstation" which is a virtual machine environment for Mac OS X, the same way that Vmware is for Windows.

Basically, you install Parallels Workstation in Tiger, then you install Linux inside a virtual machine, inside of Parallels Workstation. What this means is that you have whatever OS you choose, running inside an application window, as if it were an application itself.

handy or what!!

This is 'Feisty Fawn' beta running in Parallels Workstation, inside Mac OS 10.4.8 Tiger
[IMG]http://i61.photobucket.com/albums/h48/unlokia/feisty_on_parallelsWS.png[/IMG]

---

### Post by zviad on 2006-12-29
In order to get synaptics and other things to work in my MB first generation, I fetch kernel 2.6.19-7-386 from Feisty. Indeed, it runs better than 2.6.17. But, exactly 28 times per second, every second, prints

keyboard.c: can't emulate rawmode for keycode 0

Other than annoying my console, I think it prevent the laptop from going to sleep, since when I suspend it, it seems to wake up almost immediately. Any idea? The kernel is Feisty stock kernel with config from the stock 2.6.17-10 and make oldconfig accepting all defaults options. Thanks.

---

### Post by macmatt on 2006-12-30
Just got my MacBook :D 
----------------------------

I must say, (and this is not slating Ubuntu, as it is a great Linux) there is nothing even vaguely tempting about installing Ubuntu, for me. OS X is doing and will do, everything I need it to *without* hassle of any kind. Seamless and pretty, not flaky and *sh_tty* (Windoze :mrgreen: )

Have a nice day

---

### Post by loyd86 on 2006-12-30
Is anyone having trouble starting the edgy live CD with the new macbook updates. I have macbook 10.4.8 with 1.83Ghz

---

### Post by macmatt on 2006-12-31
I give up on this before I have even started - pointless.

---

### Post by bsantos on 2007-01-01
> **macmatt said:**
> I give up on this before I have even started - pointless.

If you're happy with just OSX and don't know how to help people who want to install Linux, you've already said enough. Posting to this forum, using a mac related nickname and a mac related avatar gives your messages a biased aroma. :-k

Being a Linux user since '97, I recently needed to invest on a laptop and went with a Macbook for the sake of the growing support Linux has for it. I had never used Mac OSX though I felt almost no learning curve using it. The whole system is well integrated, the eye candy is very nice. I understand why people use to like it so much and can say Windows can't reach it's simplicity, integration, stability. I have to say I liked it, but it's not such a big deal, at least for me, standing in my Linux biased point of view. ;)

As far as what I'm concerned related to my OS of choice, Linux (Ubuntu for some time), I can see we ain't very far to be close to OSX (in my eyes at least, and related to Tiger). The way OSX and Ubuntu develops is different, they may have a better startup point for each version, and they have paid developers working fully on it. Ubuntu and major distros have a more organic way of development, which has a wider scope of overall improvement (related to the itches each developer wants to scratch), and the downside of that is looking like there hasn't been much changes in every version. It's like when you have contact with someone whole your life and suddenly you realize they are old... That will happen when you have at last a thoroughly consistent version, with every application behaving like it's supposed to, all interconnected, the eye candy above it all, and things just work. IMHO we're still not there (I feel great in my personal computer, free, empowered, I can do almost everything I need to do), at least for people new to something other than Windows, which are able to learn, but some won't as soon as something goes wrong (I've seen people stressed with the notion of mounting/umouting floppy drives :confused:), but at the same time still not very far away, and I believe Mark knows where we should be heading, so Ubuntu will get there sooner than later. :cool:

Sorry for going off topic... 8-[

As for loyd's question, I haven't tried yet. I've been messing with VMWare Fusion and will try double boot next... :-k

---

### Post by macmatt on 2007-01-02
> **bsantos said:**
> If you're happy with just OSX and don't know how to help people who want to install Linux, you've already said enough. Posting to this forum, using a mac related nickname and a mac related avatar gives your messages a biased aroma. :-k

Being a Linux user since '97, I recently needed to invest on a laptop and went with a Macbook for the sake of the growing support Linux has for it. I had never used Mac OSX though I felt almost no learning curve using it. The whole system is well integrated, the eye candy is very nice. I understand why people use to like it so much and can say Windows can't reach it's simplicity, integration, stability. I have to say I liked it, but it's not such a big deal, at least for me, standing in my Linux biased point of view. ;)

As far as what I'm concerned related to my OS of choice, Linux (Ubuntu for some time), I can see we ain't very far to be close to OSX (in my eyes at least, and related to Tiger). The way OSX and Ubuntu develops is different, they may have a better startup point for each version, and they have paid developers working fully on it. Ubuntu and major distros have a more organic way of development, which has a wider scope of overall improvement (related to the itches each developer wants to scratch), and the downside of that is looking like there hasn't been much changes in every version. It's like when you have contact with someone whole your life and suddenly you realize they are old... That will happen when you have at last a thoroughly consistent version, with every application behaving like it's supposed to, all interconnected, the eye candy above it all, and things just work. IMHO we're still not there (I feel great in my personal computer, free, empowered, I can do almost everything I need to do), at least for people new to something other than Windows, which are able to learn, but some won't as soon as something goes wrong (I've seen people stressed with the notion of mounting/umouting floppy drives :confused:), but at the same time still not very far away, and I believe Mark knows where we should be heading, so Ubuntu will get there sooner than later. :cool:

Sorry for going off topic... 8-[

As for loyd's question, I haven't tried yet. I've been messing with VMWare Fusion and will try double boot next... :-k

:o It was a *personal* point of view, based upon the fact that *personally* I deemed it a waste of my time, when I could, more easily, install it on "Parallels". Don't take it to heart please - that was not what I intended - was speaking aloud is all. Parallels affords you the same thing, except a whole heap easier to do. That, as I said, is ONLY *my* opinion :D

Happy New Year - please don't take things quite so seriously.

---

### Post by bsantos on 2007-01-02
Sure ;) I didn't take it too seriously! Sorry if it sounded like I did, my bad.

I was just pointing out that certain comments could make people give up an otherwise good solution for them. I gave up trying dual boot for now since it would take too much fiddling with xmodmap and etc to have a usable setup for my needs (mainly C and Java coding for now). I've settled with fusion for now and will wait for Feisty. :)

Happy New year enjoying your MB, its a sexy piece of hardware. :twisted:

---

### Post by macmatt on 2007-01-02
> **bsantos said:**
> Sure ;) I didn't take it too seriously! Sorry if it sounded like I did, my bad.

I was just pointing out that certain comments could make people give up an otherwise good solution for them. I gave up trying dual boot for now since it would take too much fiddling with xmodmap and etc to have a usable setup for my needs (mainly C and Java coding for now). I've settled with fusion for now and will wait for Feisty. :)

Happy New year enjoying your MB, its a sexy piece of hardware. :twisted:

Hehe point taken indeed - was in a funny mood when I posted that - maybe sometime I *shall* try and install Ubuntu *natively* on MacBook - just don't wanna FUBAR it, just to recreate a "proof-of-concept" situation. I better back out of this thread until I have input to contribute to it. Bye!

---

### Post by EriCKY on 2007-01-04
I have problems trying to install this on a macbook. I get the LiveCD to boot up just fine. But when trying to download refit.deb, it just doesn't work.

There's something wrong with my internet, I assume. It's really wierd because the ONLY online things I can do is search google and go to Yahoo! in firefox. NOTHING else loads.

Is this a common problem, and how can I fix it?

Thanks :)

---

### Post by voights on 2007-01-05
You have to download that in OS X, not on the live cd.

---

### Post by EriCKY on 2007-01-05
You actually needed to install them in both.

It's fine though, I solved my problem
 
Thanks anyway :)

---

### Post by moaxey on 2007-01-07
am i the only person who cant get sound capture working?

---

### Post by Laerte Andrade on 2007-01-08
Hello! First of all, I would like to congratulate all the people responsible for the great HOWTO available at help.ubuntu.com/community/MacBook. I've just bought a MacBook Core 2 Duo and got a working Ubuntu system working in very little time. :D However, a few things are still not working, even after I tried some of the procedures described in this thread. ](*,) 

[LIST]
[*]sound capture
[*]wireless card
[*]the fn key
[/LIST]

Has anyone had problems setting those things up too? Thanks again.

---

### Post by mustang on 2007-01-08
Stefan Daniel Schwarz, thank you **so** much for the guide. It helped tremendously. There are still a couple issues I am having that perhaps people have the solution to:

Suspend--if I close my the macbook lid or if I explicitly put into suspend, the screen turns off but the hard drive remains on. Furthermore, it gradually gets hotter and hotter and eventually, I cannot login to it---I have to do a hard reboot. Is there anyway to fix this?

Wireless seems to timeout frequently---something I do not encounter in OSX. I am using ndiswrapper.

Even though I put xbindkeys in the startup program list in sessions, for some reason it doesn't work. I always manually have to run xbindkeys from the terminal to get access to the lcd brightness keys. 

Is there anyway to map the apple (Super_L) key to the Control key?

Thank you

---

### Post by Reb on 2007-01-09
If I was upgrading to Feisty, I'd just want to run gpt-sync again, and then grub-install? Can you offer any guidance there?

---

### Post by macmatt on 2007-01-10
Would someone tell me why it is so important to get Ubuntu running on a perfectly good machine, with an already perfectly running OS??. No offence meant, but it seems kinda pointless, unless you are a tinkerer and just want to do it to prove it can be done, in which case I can see why.

I can see nothing that Ubuntu offers extra, that Tiger does not. Just asking why, is all.

---

### Post by cdevos on 2007-01-11
> **macmatt said:**
> Would someone tell me why it is so important to get Ubuntu running on a perfectly good machine, with an already perfectly running OS??. No offence meant, but it seems kinda pointless, unless you are a tinkerer and just want to do it to prove it can be done, in which case I can see why.

I can see nothing that Ubuntu offers extra, that Tiger does not. Just asking why, is all.

Freedom.

---

### Post by phetre on 2007-01-11
> **macmatt said:**
> Would someone tell me why it is so important to get Ubuntu running on a perfectly good machine, with an already perfectly running OS??. No offence meant, but it seems kinda pointless, unless you are a tinkerer and just want to do it to prove it can be done, in which case I can see why.

I can see nothing that Ubuntu offers extra, that Tiger does not. Just asking why, is all.

Okay, I'll bite.  I switched to Ubuntu a couple years ago from Windows, having used Firefox, OpenOffice, and other high-profile FLOSS applications.  (Actually, I had a brief fling with Red Hat back in 2000 or so, but Linux isn't much fun without a working network card! :))

(Disclaimer:  Although I see this as much more than a "proof of concept" installation, I have become a tinkerer thanks to Ubuntu.  Also I'm a graduate student, so Ubuntu's price point is attractive as well.)

So when I got the MacBook last fall, it was for use primarily as a Linux machine.  It's a beautifully designed laptop, and -- with the promotion Apple was running at the time -- cheaper than any comparable machine.  OSX is fun, attractive, and very fast, but Apple's affinity for DRM and proprietary formats makes me nervous.  I can do everything I need to in Linux -- and almost everything I want ;) -- often more easily than in OSX.

Some specific examples:

[LIST]
[*]Desktop navigation:  Compared to Metacity or Beryl, OSX's window manager feels clumsy at moving and resizing windows.  When I maximize a window, it should fill up the whole desktop.  When I click on any window border in Ubuntu, I can expand or shrink the window in that direction; there's no need to click in the lower-right corner.  Not to mention virtual desktops!  How did we Windows users ever live without those??
[*]Support for my formats:  I use .ogg for my music and OpenDocument for my work.  For some reason, iTunes is just awful at .ogg, and although NeoOffice is handy, it feels less natural and less responsive than OpenOffice on Linux.
[*]Killer apps:  Obviously OSX has more than its share of killer apps too, but I love each of these to death:  Quod Libet, Gnucash, Gourmet Recipe Manager, and the Nautilus SSH integration.  They're not as flashy as Photo Booth, but they're elegant, powerful, and very easy to use.  (I'm also crazy for MythTV, but that's not on my laptop, obviously.)
[/LIST]

Finally, I should mention that a native installation has a few advantages over a Parallels VM.  Chief among them is Beryl, whose eye candy surpasses OSX's, but the speed and memory increases are exhilarating too.

Whew, that's enough.  Now, if I could only get this printed on a T-shirt!  Or maybe a bumper sticker...

---

### Post by bsantos on 2007-01-11
> **cdevos said:**
> Freedom. =D>

---

### Post by pouns on 2007-01-12
> **Laerte Andrade said:**
> Hello! First of all, I would like to congratulate all the people responsible for the great HOWTO available at help.ubuntu.com/community/MacBook. I've just bought a MacBook Core 2 Duo and got a working Ubuntu system working in very little time. :D However, a few things are still not working, even after I tried some of the procedures described in this thread. ](*,) 

[LIST]
[*]sound capture
[*]wireless card
[*]the fn key
[/LIST]

Has anyone had problems setting those things up too? Thanks again.

You can use ndiswrapper for wifi. Search this thread.
I'm still looking for solutions for sound and fn key :(

---

### Post by macmatt on 2007-01-12
Freedom to get on with what I want to do, fuss free, is wayyyy higher up on my list of priorities, than political correctness in software.

I admire and commend Linux, but it is still too fiddly in part. Macs have all the Unix benefits, without the hassle. I used Ubuntu for a LONG LONG time, but eventually gave it up, for something that just works, without pestering me and complaining that it cannot configure this/that/the other.

Nonetheless, I admire you all for the great work you are doing - who knows, maybe one day Linux *will* be the Mac OS of the future... simple to use, gorgeous to look at, and fuss free.

---

### Post by moaxey on 2007-01-13
I have an intermittent fault with power management indicators.

(macbook c2d gen2)

its happened a couple of times now, that the battery indicator is suddenly empty although the power plug is in and indicating a charged state.

after removing power plug it states that the 'system is running on AC power and now battery is present' 

system runs for some time, although you never get notification of running out of power as its already below warning threshold.

restart does not seem to fix.

it is actually working properly, just the indicators go.

---

### Post by sjatkins on 2007-01-13
This did not work for me.  The grub install broke as per usual even with the sync during system initialization.  My / is on sda3 and swap on sda4.  I noticed that the sync set sda3 as some wierd EFI partition which looks odd.  But I told it ok in any case.  So what is likely to have messed me up?  Where are the lilo instructions in case all else fails?   I may have the patience to delete the two partitions and try once more but that is it for experimental installs.

---

### Post by das_syndrom on 2007-01-14
Hi!

This is my first post in this forum :-)

Thanks for the guide. It worked perfectly for me on my Macbook Core 2 Duo.

The Kernel (2.6.17) shipped with Edgy doesn't support the Fn-Keys on the Core 2 version.
I compiled a 2.6.19 kernel from kernel.org, and HEUREKA the Fn-keys are working perfectly. Also with the new kernel, i have working suspend to ram!

Andi

---

### Post by pouns on 2007-01-14
> **das_syndrom said:**
> Hi!

This is my first post in this forum :-)

Thanks for the guide. It worked perfectly for me on my Macbook Core 2 Duo.

The Kernel (2.6.17) shipped with Edgy doesn't support the Fn-Keys on the Core 2 version.
I compiled a 2.6.19 kernel from kernel.org, and HEUREKA the Fn-keys are working perfectly. Also with the new kernel, i have working suspend to ram!

Andi
Hi,
can you tell me which kernel version you have compiled ?
Do you change something in the .config?
thanks

---

### Post by das_syndrom on 2007-01-14
> Hi,
can you tell me which kernel version you have compiled ?
Do you change something in the .config?
thanks

2.6.19.1
I simply took the .config from the standard ubuntu kernel to test if there was any difference in the appletouch-module for using the synaptics-touchpad drivers.

Be sure to enable the new Serial-ata-drivers in the device-drivers section.
btw: The new kernel was hanging on startup the first time when changing from a 2.6.17 kernel. The second and following bootups were ok. Maybe this has to do with the new serial-ata-drivers, i don't know.
And be sure to have any opportunity to edit the /boot/grub/menu.lst if there is something wrong with the kernel, because most of the time my keyboard isn't working in grub.

Andi

---

### Post by tmad40blue on 2007-01-15
Hi there. Just a warning, but this is going to be an extremely n00b-ish question, so don't do anything horrible to me. :-# 

Anyway, I'm stuck in the install process. I have a 2GHz Blackbook with Intel Core Duo (note the absence of the 2). Everything works fine until I get to downloading and using refit in Ubuntu to sync GPT and MBR before I click the "Install" button. When I download it in Firefox and open it up in Package Installer, I get this error:

"Error: Dependency is not satisfiable: libc6"

I have no idea what this means, so naturally I don't know what to do about it.

If anyone could take some time to help out a n00b, that would be extremely helpful. :) 

Thanks,
~tmad40blue

---

### Post by mustang on 2007-01-15
> **das_syndrom said:**
> 2.6.19.1
I simply took the .config from the standard ubuntu kernel to test if there was any difference in the appletouch-module for using the synaptics-touchpad drivers.

Be sure to enable the new Serial-ata-drivers in the device-drivers section.
btw: The new kernel was hanging on startup the first time when changing from a 2.6.17 kernel. The second and following bootups were ok. Maybe this has to do with the new serial-ata-drivers, i don't know.
And be sure to have any opportunity to edit the /boot/grub/menu.lst if there is something wrong with the kernel, because most of the time my keyboard isn't working in grub.

Andi

Hi Andi,

I just installed the 2.6.19.2 kernel. I did what you did and used the ubuntu kernel config and enabled the intel sata drivers during the configuration process.

It booted up fine (on the first try) but suspend still doesn't seem to work: everything is still on when I shut the lid. 

Although I have the first generation Core duo, not the core 2 duo like you--dunno if that makes a difference.

edit: doh, I didn't enable suspend in gnome-powermanager. Anyways, it does suspend (albeit incompletely--lcd off, HD off, fans still on) but even then, it doesn't wake out of suspend--I have to reboot.

oh, and wifi isn't detected at all. Perhaps I needed to enable that during the kernel configuration?

On the plus side, battery life is *slightly* better. On a fresh battery, I get around 2:50 versus 2:30 on the old kernel. Still no where near the four hours on osx.

edit2: 

from [http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/](http://www.dadeb.it/index.php/macbook-and-ubuntu-linux/) 

> UPDATE - I managed do sleep to ram in a reliable way !! I&#8217;m using kernel 2.6.18.1. The fix is to DO NOT LOAD &#8220;piix.ko&#8221;. I tried to delete the file from /lib/modules/* but the initrd seems to load it anyway, so I recompiled the kernel without the piix support (commenting &#8220;# CONFIGBLKDEV_PIIX&#8221; in kernel .config). Of course you won&#8217;t be able to use the CDROM without this module&#8230; oh.. and to wake up the video propely you have to follow instructions of desrt. I report the useful part :

&#8220;One thing about sleep: vbetool needs to save and restore your video state in order to have working video on resume. Currently, on Macbooks this is broken. This is caused by a mistake: the vbesave init script comes before the acpi init script. This means that laptop-detect will report to vbesave that you are not on a laptop and vbesave will not save your vbestate. Matthew Garrett is working on a fix, but in the mean time a workaround is to edit /usr/sbin/laptop-detect and insert a line &#8216;exit 0&#8242; right after the #!/bin/sh (always report that we&#8217;re a laptop).&#8221;

But the ubuntu .config file I used has all lines with "piix" commented out already...quite confused.

---

### Post by mustang on 2007-01-15
> **tmad40blue said:**
> Hi there. Just a warning, but this is going to be an extremely n00b-ish question, so don't do anything horrible to me. :-# 

Anyway, I'm stuck in the install process. I have a 2GHz Blackbook with Intel Core Duo (note the absence of the 2). Everything works fine until I get to downloading and using refit in Ubuntu to sync GPT and MBR before I click the "Install" button. When I download it in Firefox and open it up in Package Installer, I get this error:

"Error: Dependency is not satisfiable: libc6"

I have no idea what this means, so naturally I don't know what to do about it.

If anyone could take some time to help out a n00b, that would be extremely helpful. :) 

Thanks,
~tmad40blue

That's odd tmad because it didn't prompt me for any other dependencies. Are you sure install Edgy Eft 6.10 and not dapper 6.06?

---

### Post by tmad40blue on 2007-01-15
Oh yeah, I am using Dapper... Sorry about not specifying that.

Would using Dapper pose any other issues? Because I don't have the Internet speed capabilities to download a full .iso of Edgy.

If there is a way to get this to work under Dapper, I'd love to know it. :-)

---

### Post by mustang on 2007-01-15
Dapper probably has an older version of libc6. 

Not sure how to install dapper. It seems most of the guides lean towards edgy.

---

### Post by Laerte Andrade on 2007-01-16
> **mustang said:**
> I just installed the 2.6.19.2 kernel. I did what you did and used the ubuntu kernel config and enabled the intel sata drivers during the configuration process.

Hey, can you confirm if everything else is working with the new kernel (sound, beryl, fn key, camera, microphone, etc.)? I'm thinking of compiling one too.

---

### Post by earth2mark on 2007-01-16
I have an Intel Mac Mini running Edgy that was upgraded from Dapper.  I've been booting with lilo and I'm trying to use the suggestions in this thread to switch to grub.  Here's what I get after using aptitude to remove lilo and install grub:

```

$ sudo update-grub -y
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,2)

grub> setup (hd0,2)

Error 17: Cannot mount selected partition

```

Here is my partition map:

```

$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        1331    10485760   af  Unknown
/dev/sda3            1331        9385    64693359+  ef  EFI (FAT-12/16/32)
/dev/sda4            9385        9730     2766788   82  Linux swap / Solaris

```

Can someone help me troubleshoot this?  Do I have the wrong partition in my grub commands, or is my partition formatted inappropriately for grub?

Thanks!


UPDATE:

I solved that problem.  Seems that the partition Id was wrong, left over from the Bootcamp partitioning, I suppose.  I changed the Id of /dev/sda3 to 83 (ext3) which is what it is.  After clearing out some old grub cruft left over from an unsuccessful Dapper install, I got grub working great on my Intel Mac Mini!

Thanks!

---

### Post by mustang on 2007-01-17
> **Laerte Andrade said:**
> Hey, can you confirm if everything else is working with the new kernel (sound, beryl, fn key, camera, microphone, etc.)? I'm thinking of compiling one too.

Sound and fn key for sure---I have yet to try the others.

---

### Post by pouns on 2007-01-18
Hi,
i try kernel 2.6.19.1 and 2.6.19.2. Both seems to work great but they have a problem with ndiswrapper. The system freeze when i try to modprobe ndiswrapper. I tried with the last ndiswrapper version.
 fn key and sound work.
Do you have access to your keyboard in the grub menu? I can't choose the kernel to boot on. I have to change menu.lst every time i want to change kernel :(

---

### Post by das_syndrom on 2007-01-18
Hi!

Kernel 2.6.19.2 works great on my Macbook C2D.

sound... ok

beryl... ok

fn-keys... ok

touchpad in synaptics mode... ok
finally! i love it -> had to modify [FONT="Courier New"]/drivers/usb/input/appletouch.c[/FONT]
changed
[FONT="Courier New"]#define GEYSER3_JIS_PRODUCT_ID  0x0219[/FONT]
to
[FONT="Courier New"]#define GEYSER3_JIS_PRODUCT_ID  0x021B (<- my Touchpad ProdID)[/FONT]

camera... works only with ekiga (i tried mplayer, mencoder, xawtv, camorama)
-> linux-uvc

suspend... ok

iRemote... ok
-> [FONT="Courier New"]appleir.patch[/FONT] from mactel-linux

apple smc (system management controller) .. ok
-> [FONT="Courier New"]applesmc.patch[/FONT] from mactel-linux

mic... not tested yet

ndiswrapper... ok
it even works after wake up from suspend
@pouns: i wonder why your system freezes... I use ndiswrapper 1.34 with the windows-driver from lenovo
did you do a [FONT="Courier New"]make uninstall[/FONT] before [FONT="Courier New"]make[/FONT] and [FONT="Courier New"]make install[/FONT] when compiling ndiswrapper for a new kernel?

Andi

---

### Post by pouns on 2007-01-18
> @pouns: i wonder why your system freezes... I use ndiswrapper 1.34 with the windows-driver from lenovo
did you do a make uninstall before make and make install when compiling ndiswrapper for a new kernel?
yes, i've done this. But i use the driver from dlink...
I'll try to compile 2.6.19.2 with the same patch as you and try ndiswrapper 1.34 with the lenovo driver.
I'll post the result here.
Thanks for your advise !

---

### Post by pouns on 2007-01-18
das_syndrom, you're my new hero !
the good driver is the one in 7iwc21ww.exe !
Thank you very much for your help !

---

### Post by Laerte Andrade on 2007-01-18
> **das_syndrom said:**
> Hi!

Kernel 2.6.19.2 works great on my Macbook C2D.

Hi, Andy! That's great news! Since I have the exact same Macbook as you (C2D), could you please send your .config, as well as list all the mactel patches you have used? Thanks, that would help me a lot! :)

---

### Post by CrazyDesi on 2007-01-19
Does anyone know how to disable the bootup sound?  I have to use it for school and the bootup sound is really really disturbing my class lol.

---

### Post by Laerte Andrade on 2007-01-19
You just have to boot up Mac OS X and disable the sound (mute). That worked for me.

---

### Post by CrazyDesi on 2007-01-19
I only have ubuntu installed :(.  I guess I'm going to have to reformat and install OS X :(.  I really don't want to though lol :).  Also for the new macbooks with the Intel Core 2 Duo should I install with amd64 ubuntu?  Right now I can't get any videos to play unless I open up xine media player and then totem(don't ask it just works) anyone know why this is?

---

### Post by das_syndrom on 2007-01-19
Hello again!
> Hi, Andy! That's great news! Since I have the exact same Macbook as you (C2D), could you please send your .config, as well as list all the mactel patches you have used? Thanks, that would help me a lot!

I applied the applesmc-patch and the appleir-patch from [http://svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.19/]("http://svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.19/")
I copied the standard-ubuntu config from 2.6.17-generic kernel (and selected of course the applesmc and appleir module). When i have the time i will kick out all the unnecessary modules but until then its okay for me...

> Does anyone know how to disable the bootup sound? I have to use it for school and the bootup sound is really really disturbing my class lol.

Some clever guy has written a MacOs-application for that purpose.
[http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html]("http://www5e.biglobe.ne.jp/~arcana/StartupSound/index.en.html")
It works great - no noise anymore :mrgreen: 

> Also for the new macbooks with the Intel Core 2 Duo should I install with amd64 ubuntu?

If you have a c2d your macbook is likely to have the new wireless chipset, which is not supported yet by the madwifi-project. So you're forced to use ndiswrapper, and afaik there is only a 32-bit windows-driver available at the moment. So i would recommend the i386-ubuntu-version

Andi

---

### Post by mustang on 2007-01-19
Andi,

what kind of battery life do you get on Ubuntu? Also, does suspend work perfectly (as in, does it shut down everything including the fans?)

Thanks

---

### Post by bsantos on 2007-01-20
Does anyone know where can I post my modified keymap for a suggestion of inclusion in the keyboard chooser?

It is for a Portuguese Macbook C2D, if there's anyone needing it you can grab a zip with Xmodmap [here]("http://azulebanana.com/bluey/2007/01/02/xmodmap-do-macbook-portugues-para-ubuntu-para-usar-no-vmware-fusion-ou-parallels/wp-content/uploads/2007/01/xmodmap.zip").

I have to say that Feisty will be almost perfect on the Macbook. Who needs OSX anyway? Nautilus is better than Finder any time. :P Multiple desktops, the sweetness of beryl... It's perfect!


macbook backlight bin has to be compiled with an option for the 2nd generation. It works.

iSight isn't yet working out of the box on feisty, because the firmware isn't yet included and loaded on startup. I'm loading it manually on rc.local and reloading the module uvcvideo. [This]("http://i-nz.net/2006/12/10/isight-on-linux-with-automatic-firmware-loading/") will eventually end upstream I hope! ;)

Can't get ndiswrapper to work though. I get a kernel panic on modprobe. Is it a problem in 2.6.20? I've seen someone stating this issue was present on 2.6.19...

There's still a couple of months till launch, I hope Feisty has this issues solved by then. :)

---

### Post by MichaëlVD on 2007-01-27
I used this guide to install ubuntu on my 20" iMac. Most things work (sound, beryl, resolution, etc...), except for:

- I don't get the option to boot os X anymore. I know that all my files are still there because I can copy them to my ubuntu partition.

- less important in the short run: the microphone does not seem to work. The camera does however. Is there a solution for this? 

Thanks!

---

### Post by bsantos on 2007-01-27
> **MichaëlVD said:**
> I used this guide to install ubuntu on my 20" iMac. Most things work (sound, beryl, resolution, etc...), except for:

- I don't get the option to boot os X anymore. I know that all my files are still there because I can copy them to my ubuntu partition.


That happened to me the first time I tried. I notice that the tutorial is missing a note to change the grub install to point to the boot partition (the root partition). This way you overwrote the disk mbr with grub. Boot OSX disc 1, reboot and choose to boot to OSX. Rebless refit on the mbr. Boot with the Ubuntu Live CD, mount the root partition, bind the dev, proc partitions, chroot to the root partition and do a grub-install to the root partition (/dev/sda3..4). Reboot and refit should also show a Tux to boot Ubuntu.

> **MichaëlVD said:**
>  - less important in the short run: the microphone does not seem to work. The camera does however. Is there a solution for this? 

The camera works right after you boot from OSX (the firmware is still loaded or something). When you reboot, at least the last time I tried, you will need to upload the firmware to the camera again. There's a patch to the camera module that does that, but it isn't yet on the kernel nor used by Ubuntu, I think. You'd have to copy the firmware from the OSX partition to /lib/firmware, though.

I still can't use the mic either... :(

---

### Post by MichaëlVD on 2007-01-27
The following was enough to bring up Tux in the rEFIT menu:

> **bsantos said:**
> That happened to me the first time I tried. I notice that the tutorial is missing a note to change the grub install to point to the boot partition (the root partition). This way you overwrote the disk mbr with grub. Boot OSX disc 1, reboot and choose to boot to OSX. Rebless refit on the mbr.

I was glad I didn't have to find out what all this means:
> **bsantos said:**
> Boot with the Ubuntu Live CD, mount the root partition, bind the dev, proc partitions, chroot to the root partition and do a grub-install to the root partition (/dev/sda3..4). Reboot and refit should also show a Tux to boot Ubuntu.

Thank you very much!

---

### Post by bsantos on 2007-01-27
> **MichaëlVD said:**
> I was glad I didn't have to find out what all this means

8-[ Sorry!

I perfectly understand what you mean. I wrote that in a hurry, and you'd understand it if you already knew what I was talking about. I'd be more explicit if you needed me to be, of course. I'm glad you got it working. ;)

---

### Post by babelfishi on 2007-01-28
This might sound silly, but I'm having trouble installing the package (refit) in step 6. I've downloaded the .deb file, and when I run the Package Installer, it said "Error: Dependency is not satisfiable: libc6".
Can anyone help me out? :confused:

---

### Post by martinbures on 2007-01-28
So I've been trying to find a way to lower the temperature on my macbook and I came across the speed scale control on the Debian install guide.  I have tried this on my macbook and it seems to run a bit cooler.  I don't have any longterm data but here is what I did:

[http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook)

CPU frequency scaling is governed by SPEEDSTEP_CENTRINO kernel module.

echo speedstep_centrino >> /etc/modules


Also, has anyone gotten GSyaptics working to get two-fingered scrolling?

I used the configuration in the gentoo forums and installed gsynaptic but it is telling me that I need to add the line "SHMConfig"  "true" to my synaptics block in my xorg.conf file which I have done.

Here is what I have.

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "auto-dev"
       Option  "LeftEdge"      "100"
       Option  "RightEdge"     "1120"
       Option  "TopEdge"       "50"
       Option  "BottomEdge"    "310"
       Option  "FingerLow"     "25"
       Option  "FingerHigh"    "30"
       Option  "MaxTapTime"    "180"
       Option  "MaxTapMove"    "220"
       Option  "MaxDoubleTapTime"      "180"
       Option  "VertScrollDelta"       "20"
       Option  "HorizScrollDelta"      "50"
       Option  "MinSpeed"      "0.79"
       Option  "MaxSpeed"      "0.88"
       Option  "AccelFactor"   "0.0015"
       Option  "SHMConfig"     "on"
       Option  "VertTwoFingerScroll"	"1"
       Option  "HorizTwoFingerScroll"   "1"
       Option  "SHMConfig"	"true"
EndSection

The config line in [system] -> [preferences] -> [sessions] -> [startup programs]
gsynaptics-init --sm-disable

any ideas would be great
thanks
martin.

---

### Post by martinbures on 2007-01-28
I also realize that the Option "SHMConfig" string appears twice.  Without the second entry, it did not work properly.  Without the first entry, it did not work either...

martin.

---

### Post by mustang on 2007-01-28
> **babelfishi said:**
> This might sound silly, but I'm having trouble installing the package (refit) in step 6. I've downloaded the .deb file, and when I run the Package Installer, it said "Error: Dependency is not satisfiable: libc6".
Can anyone help me out? :confused:



Someone else had this problem as well.

Dapper has an older version of libc6. refit needs the one in edgy.

---

### Post by Pantheon on 2007-02-01
Hi!

I have just installed Ubuntu on my MB (excellent guide by the way), and it all works fine when I reboot. But if I choose to upgrade all the recommended packages, and choose to sync MBR/GPT under the partition tool in rEFIt, then my Ubuntu won´t start again. When I try, I only get the Grub commando line, and I don´t know what to to with it :(

Is someone familiar with this problem? I guess one solution is NOT to sync MBR/GPT after the upgrade!?

---

### Post by Meck1982 on 2007-02-02
Hi all,

I have been running Edgy without major problems by using this guide. But still the microphone does not work for me. Also suspend is not reliable. So I thought about trying Feisty Herd 3. Here my experiences:

Booted the CD from rEFIt boot menu and did the installation WITHOUT the gptsync-hack as the guide says it will not be necessary for Feisty.

Bad thing: At the end everything installed but on reboot it does not start the Ubuntu, when I select it.

Did I miss something? Any experiences? I am still hoping for a out-of-the-box-running Feisty :-)

---

### Post by Gen2ly on 2007-02-03
Pantheon goto this Ubuntu thread.  

[How to restore Grub from a live Ubuntu cd.]("http://www.ubuntuforums.org/showthread.php?t=224351")

You'll need to use the section thats below the red lettering.  I just compiled my kernel and it updated grub incorrectly.  rsync must write to the MBR?  Anyways, with the liveCD it's pretty easy.

I just compiled the kernel and it works pretty good.  wifi doesn't work, and adding the i810 drivers - well I don't know how to do that yet.

Apparently, only the i810 drivers are available!?  I this is for previous models but works on the 950 chipset.  I reason I want to fix this isbecause 3D modeling is all done with software.

---

### Post by fduprat on 2007-02-03
Thanks Stefan!

Your step by steap worked 100%

I did partition the hard drive with the apple system utilities...

Now I am working to have the airport available trough Linux.

My daughter is studying  Computer Ing (second year) ... and is not common to have a mac with linux... she is happy now

Again thanks!

Fernando Duprat

---

### Post by Laerte Andrade on 2007-02-05
Hi, I managed to get the wireless card working on my C2D MacBook using ndiswrapper and the Lenovo driver. However, I cannot use NetworkManager to see what wireless connections are available. What is the best thing to do? Thanks again.

EDIT

Nevermind. The problem was solved when I removed the wireless card configurations in System->Administration->Networking. However, I've noticed that the speed of the same connection in MacOS X and Ubuntu is very very different (in the first, ~280 kb/s, the latter, ~8 kb/s!!!). Is this an issue with ndiswrapper, or am I still doing something wrong? Thanks for any help.

---

### Post by hesee on 2007-02-07
Hi,

I think I'm gonna change to Feisty soon. Probably I'll do a new installation, since I have installed so much experimental sw into edgy.

What would be the right way to do the installation? If I use existing partitions, do I need to do any special tricks (like gptsync), like when installing ubuntu first time to macbook?

Is there yet anyone running feisty in macbook?

---

### Post by mustang on 2007-02-07
I'm running the feisty kernel on edgy. No improvement thus far for us macbook owners :/

---

### Post by hesee on 2007-02-09
> **hesee said:**
> Hi,

I think I'm gonna change to Feisty soon. Probably I'll do a new installation, since I have installed so much experimental sw into edgy.
[B]
What would be the right way to do the installation? If I use existing partitions, do I need to do any special tricks (like gptsync), like when installing ubuntu first time to macbook?[/B]

Is there yet anyone running feisty in macbook?

Can someone confirm that the installation of feisty is done without any extra steps now that i have existing linux partitions which i'm going to use?

---

### Post by Meck1982 on 2007-02-09
After trying to install Feisty Herd 3 without any special tweaks, I now used the way described in the edgy howto. And it worked! So in Herd 3 you HAVE to do step 6 described in the tutorial. At least I think so. What you gain from switching to Herd 3 is not too much. fn-Keys and Volume switch work. But I have problems to use the F6-Key. And the ndiswrapper-tutorial I used in Edgy doesn't work either.
Nevertheless I like the Feisty. Especially network configuration, codec installation look promising. I installed Herd 3 with my edgy partition layout and didn't lose any data.

---

### Post by martinbures on 2007-02-09
Hey - with regard to the microphone, good luck.  It doesn't work in Dapper/Edgy.  You can get the webcam to work but the microphone is no dice.  If you look on the gentoo forum, it looks possible but requires some code changing and recompiling.  I'm not terribly interested in doing this.  Several people, including myself, have posted a bug against this on the Ubuntu bug tracking forums, along with the information that we have found that supposedly fixes this problem(it seems to be a kernel issue).  So that might be a benefit to going to Feisty.  If someone has it installed, if they could check to see if the microphone works, that would be helpful.

martin.

---

### Post by jck77 on 2007-02-09
> **Stefan Daniel Schwarz said:**
> Touchpad "funkyness" is a known problem when using "noapic", so don't use that parameter! If you get a crash at boot, use "lpj=8000000" (for 2 GHz MacBooks) instead.

See ya
-- sds

Hello Stefan, I have that problem, so i removed the noapic and I still having the same funkyness with the touchpad or mouse. even the keyboard don't works good as well. 
Is there another solution to this? 

Hope some can help me here with this.

Thanks

---

### Post by jck77 on 2007-02-09
> **rdwtux said:**
> Is anyone having touchpad "funkyness"?  My touchpad and mouse in general will lag down periodically.  The system doesn't seem especially busy when it happens, but it does feel like a lag of perhaps USB bus resources.  I wait ~5-10 seconds and it's fine.   Annoying though. 

The other one I've seen about 5-10 times is the touchpad will start drifting.  The mouse will slowly move by itself across the screen.  When this happens the keyboard usually locks up very soon after.  The system seems fine, but input devices won't work. 

Am I the only one?

you're not the only one! I reply to the supposed fix because didn't work for me, I still having this problem, rdwtux did you fix that? what exactly you do? I just removed the noapic option from de /etc/lilo.conf  then restart the macbook but still the same! 

Who can tell me whats wrong? and how to fix that?

Here is my /var/log/message for any clue!

[http://pastebin.ca/348244](http://pastebin.ca/348244)

Thanks.

---

### Post by EmuBite on 2007-02-10
I've followed the Edgy guide for my first generation MacBook, and most things are working great.  However, I've yet to get suspend or hibernate to work properly.  (The microphone also isn't working, although this isn't a terribly big deal for me.)

Has anyone gotten suspend to work on a MacBook?  I've searched the forums and tried just about everything suggested (including installing Feisty's latest pre-release kernel), but nothing works.  I've also tried installing Feisty from scratch, but the installation fails at 90% with the sk98lin module.  (See [Launchpad #79340]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/79340") for details.)

If anyone has gotten suspend or hibernate to work on the MacBook, please (PLEASE!) post detailed instructions on how you did it.  I found this [Launchpad comment]("https://launchpad.net/ubuntu/+source/hal/+bug/72287/comments/6") with a possible fix to the problem, but I don't know how to incorporate the code into the kernel/X server/HAL/system resume scripts.  (I'm new to Linux.)

Any help would be GREATLY appreciated.  If I can get suspend/hibernate working, I would ditch OS X altogether and make the move to Ubuntu.  I've been wanting to switch to an Open Source system, and I feel like I'm teetering on the verge -- if this would just work!

Thanks in advance for any help.

---

### Post by mustang on 2007-02-10
> **EmuBite said:**
> I've followed the Edgy guide for my first generation MacBook, and most things are working great.  However, I've yet to get suspend or hibernate to work properly.  (The microphone also isn't working, although this isn't a terribly big deal for me.)

Has anyone gotten suspend to work on a MacBook?  I've searched the forums and tried just about everything suggested (including installing Feisty's latest pre-release kernel), but nothing works.  I've also tried installing Feisty from scratch, but the installation fails at 90% with the sk98lin module.  (See [Launchpad #79340]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/79340") for details.)

If anyone has gotten suspend or hibernate to work on the MacBook, please (PLEASE!) post detailed instructions on how you did it.  I found this [Launchpad comment]("https://launchpad.net/ubuntu/+source/hal/+bug/72287/comments/6") with a possible fix to the problem, but I don't know how to incorporate the code into the kernel/X server/HAL/system resume scripts.  (I'm new to Linux.)

Any help would be GREATLY appreciated.  If I can get suspend/hibernate working, I would ditch OS X altogether and make the move to Ubuntu.  I've been wanting to switch to an Open Source system, and I feel like I'm teetering on the verge -- if this would just work!

Thanks in advance for any help.

I'm pretty much in the same boat as you. Suspend is really the dealbreaker.

Some things you can try:

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Suspend_to_Ram](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Suspend_to_Ram)

[http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00093.html](http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00093.html)

From desrt's new [edgy guide:]("http://desrt.mcmaster.ca/macbook.xhtml")

> 

     Even though sleep got fixed for Dapper, something in Edgy broke it again.
     You can, however, install the Feisty prerelease kernel on your system
     and then everything will work great.

     It turns out that one does not need to do a full vbetool save/restore of
     the video BIOS.  The only register of interest that is clobbered by the
     suspend/resume cycle is the backlight control register.  See
     Launchpad #72287 for a
     temporary workaround to this problem.
    
     If you want to use vbetool, you need to know that currently, on Macbooks
     this is broken.  This is caused by a mistake: the vbesave init script
     comes before the acpi init script.  This means that laptop-detect will
     report to vbesave that you are not on a laptop and vbesave will not
     save your vbestate.  Matthew Garrett is working on a fix, but in the
     mean time a workaround is to edit /usr/sbin/laptop-detect and insert
     a line 'exit 0' right after the #!/bin/sh (always report that we're
     a laptop).


I installed the Feisty kernel but it didn't fix anything which echoes your experience so I am not sure what he is talking about.

Let us all know if anything works. I am desperate!

---

### Post by Major Lockup on 2007-02-10
In feisty herd 3, the microphone is still not working. This is frustrating.. no skype :(

---

### Post by Azathoth_ on 2007-02-13
In a few days i will have a MB white. I have read all this post and i will try it. I don't know if i can use a triple boot, or i have to use a dual boot and windows in parallels. I am not going to use windows a lot, but when i need to use AutoCAD and some programs of industrial chemistry.

Does anyone know if feisty or edgy works well on triple boot?
If i patch to kerne 2.6.19 i will be able to use microphone and keys... (everything)?

Thanks a lot

---

### Post by mustang on 2007-02-13
> 
Good news,

using 2.6.20 and latest patches i submited today,
sleep works the first time on the Core 2 Duo Macbook.

cu

Edgar (gimli) Hucek


Would anyone mind trying the 2.6.20 kernel? There is also a .config here:
[http://sourceforge.net/mailarchive/forum.php?thread_id=31597572&forum_id=47881](http://sourceforge.net/mailarchive/forum.php?thread_id=31597572&forum_id=47881)

I tried it but I got some weird kernel unrecognizable/unbootable error.

2.6.20 patches here:
[http://svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.20/](http://svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.20/)

Here's another guide (for gentoo) but there's a .config and the mactel patches zipped up:
[http://www.odi.ch/prog/macbookpro/index.php](http://www.odi.ch/prog/macbookpro/index.php)
(in the kernel section)

---

### Post by ahaller on 2007-02-13
Maybe we can gather some things that work regarding configuration with FEISTY on a new [wiki page]("http://wiki.ubuntu.com/MacBookProFeisty") ?

---

### Post by martinbures on 2007-02-14
I have another question.  Does anyone have any issues with sound?  When I am running with OS X, I get normal sound(for the macbook).  When I switch to linux, even when fully cranked-up, you can barely hear it.  Is there a setting somewhere that I am missing?  When I open the sound panel, it is all of the way up.

thanks.
martin.

---

### Post by das_syndrom on 2007-02-15
> When I am running with OS X, I get normal sound(for the macbook). When I switch to linux, even when fully cranked-up, you can barely hear it. Is there a setting somewhere that I am missing? When I open the sound panel, it is all of the way up.

Hi!

Open the sound mixer. Go to preferences. And enable the "front"-controller. Maximize this and the sound should be ok.

I have a question too, concerning sound.
I am using a 2.6.20-kernel with all mactel-patches except the sigmatel_audio patch.
My alsa-mixer doesn't show a master-control, only PCM. Sound and volume-control works fine for me.

When compiling the kernel with the sigmate_audio patch, the mixer shows a master control.
BUT: Sound is quit dull and playing around with the master-control doesn't effect the volume at all. The only consequence of maxing it out is that the sound sounds a little bit clearer (like on kernels without the patch).

Can anybody tell me why? I am just curious... :) 

Andi

---

### Post by jajajavi on 2007-02-15
I have ubuntu installed in my macbook c2d. I can't connect to internet with my adsl router or with
a dhcp network, but I can do it in macosx. Sorry for my poor english. What can I do? Muchas gracias!!

---

### Post by nicolaos on 2007-02-17
Hi all,

Great How-to. Ubuntu is running smooth. But... I lost the dual boot. Can't get back to OSx. When it boots, it goes straight to GRUB.
I figure out it has something to do with refit but I've followed the steps very carefully. How can I make sure the tables are sync (i don't know what i'm talking about :p but the problem might be there...) ? And what should I do to get refit working at the beginning ?

Thanks for support. :)

nicolaos

---

### Post by anzevi on 2007-02-20
Anyone tried to install Kubuntu on MacBook? :?:

---

### Post by zpon on 2007-02-22
I have used this guide to install ubuntu on my macbook (c2d), worked out great.
Is there any way to mount my mac os x drive from linux? I can easily mount it with $mount /dev/sda2 /dir/to, but it is read only, and i want to write to it, i have tried both hfsutils and hfplus, the last one gives back the error that it is not HFS+ volume.

Can anybody help me?

---

### Post by oskarloko on 2007-02-24
Well, now writing from a MacBook ( Core 2 Duo at 2Ghz ) with Egdy :KS 

Thanks Stefan Daniel Schwarz  to your [UbuntuWikiPage,]("https://help.ubuntu.com/community/MacBook") has been very helpful

But on these new Apple laptops, wireless won't work; as is said [in this Debian wiki]("http://wiki.debian.org/MacBook") (also helpful) 
See **caveat** at Wireless section
I love wikis like this [Gentoo]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Enable_.22normal.22_FN-key_behaviour") one !!
If you don't like freezing kernel panics ](*,) , use version 1.01 of the winxp driver with ndiswrapper.

Grab it from [here]("ftp://ftp.dlink.com/Wireless/dwa645/Drivers/dwa645_drivers_101.zip")

Or just type

```

sudo -i
wget ftp://ftp.dlink.com/Wireless/dwa645/Drivers/dwa645_drivers_101.zip
unzip dwa645_drivers_101.zip
cd Driver/
depmod -a
modprobe ndiswrapper
ndiswrapper -i net5416.inf 
ndiswrapper -m

```

Expecting help you !! :biggrin: 

And now...
... something di ffe rent

¿ How to make *fn* key - and combo with other keys - works ?
¿ Does integrated microphone work for you ?

Thanks ! !

---

### Post by Azathoth_ on 2007-02-24
Hola oskarloko:

**I have the same macbook and madwifi drivers doesn't work with edgy and with livecd'st. Does dwa645 drivers work??? I have tried it, but it doesn't work for me... and now it (maybe it) has broken my system and i cannot select other kernel image to start... i'm now reinstalling all. But i prefer using madwifi instead of ndiswrapper.**

I have the last same problems...
¿ How to make fn key - and combo with other keys - works ?
¿ Does integrated microphone work for you ?

And one more...
Why iSight doesn't work with aMsn but it works with ekiga??

Thanks a lot

Mario García

---

### Post by dysphoric on 2007-02-25
Uggghhh!!!

So here is where I am at with the install...

I followed the instructions exactly, using a freshly installed copy of OSX and all the updates.

When I restarted after a successful (or apparently successful) installation I got the dreaded "bin/sh: can't access tty; job control turned off" message. 

I attempted to restart again, but to no avail. 

So figuring I must have screwed something up, I started all over again, with a clean formatted HD, and a clean copy of OSX again. 

BAH!!

I get the same tty message again. 

So 7 hours later, and after reading at least 200 forum posts, a good 30 different websites, and nobody seems to have a working solution. 

Ok, so lets give up OSX, and do a single boot install of Edgy. 

HMM, again it looked like it succeeded, however when I restarted I get the dreaded grey folder with a question mark on it. No matter what I do it won't boot. 

I inserted the Live CD and asked it to boot from the first HD, but alas it just freezes after showing a blank page and a cursor. 

Well anyone have any ideas or will I just have to shoot myself?

Thanx in advance for your help, it is much, much appreciated.

---

### Post by cocoia on 2007-02-25
Dysphoric, do you have rEFIt  on both disks? Both your Ubuntu and the OS X directory need a refit, and the OS X one is always 'blessed' in OS X to make it boot from EFI so you can select OS'es like FreeBSD or GNU/Linux.. Also, you need to install Boot Camp and run it after the updates. 

Also, you can make your laptop single-boot by inserting the DVD that came with your Mac, go to Utilities > Disk Utility, go to your disk in the left column, select the 'partition' tab. From here, choose MS-DOS / MBR Table instead of GPT, and reformat the disk. You should now be able to use the MBP as a regular PC.  (CAUTION: USE THIS WITH BOOT CAMP. WITHOUT BOOT CAMP, NO BIOS EMULATION IS USED AND YOUR LAPTOP COULD GET SEVERELY SCREWED UP).

> **zpon said:**
> I have used this guide to install ubuntu on my macbook (c2d), worked out great.
Is there any way to mount my mac os x drive from linux? I can easily mount it with $mount /dev/sda2 /dir/to, but it is read only, and i want to write to it, i have tried both hfsutils and hfplus, the last one gives back the error that it is not HFS+ volume.

Can anybody help me?

It is not really recommended. For unspeakable reasons, the HFS driver that allows writing can corrupt entire disks and is best left untouched.

Now, could someone help me? I am trying to compile a new kernel, and being new to it, I have no idea why the mac-tel-patches seen to fail in the build process. I get this error about blacklist-acpi;  there is a missing include "efi_enabled". It has come up on the Mactel-mailinglist, but there are no answers. DId someone succesfully build a kernel on Debian with the Mactel-patches, and if so, what version kernel, what patches, and how?
I would really like to know, as I cannot use my MB (pro) because of heat right now, which should be fixed with the applesmc patch.

---

### Post by Unding on 2007-02-25
> **cocoia said:**
> Also, you can make your laptop single-boot by inserting the DVD that came with your Mac, go to Utilities > Disk Utility, go to your disk in the left column, select the 'partition' tab. From here, choose MS-DOS / MBR Table instead of GPT, and reformat the disk. You should now be able to use the MBP as a regular PC.  (CAUTION: USE THIS WITH BOOT CAMP. WITHOUT BOOT CAMP, NO BIOS EMULATION IS USED AND YOUR LAPTOP COULD GET SEVERELY SCREWED UP)

I'm running a linux-only system and didnt have to to any partition configuration like you described. Kernel 2.6.20 works fine so far, but still i got some problems with the touchpad. Advanced touchpad features don't work, maybe something is missing or need to be configured. Some Good news though, the funkyness of the touchpad has disappeared and fn-key for sound on/off, sound volume up/down, home, end, page up/down work well without having to adjust configurations.

There are some patches left for kernel 2.6.20 i would like to apply. I just wish i could find a simple explanation on how to apply these patches, because i still dont know how to do that.

BTW: Hello all, i'm new. My english isn't very good, hope you understand what i wrote.

---

### Post by oskarloko on 2007-02-25
> **cocoia said:**
> 
I would really like to know, as I cannot use my MB (pro) because of heat right now, which should be fixed with the applesmc patch.

What are the applesmc patch ??

(sorry for not having a correct response, I'll try building kernel )

---

### Post by oskarloko on 2007-02-25
You have rebuild a linux 2.6.20 kernel or downloaded it from.. ?

(I've heard a 2.6.20 is a new abd stable kernel, Linus Tovarlds says... )

My case is the opposite: I've a triple booting system with 6 partitions, which works fairly well..
Simply making them with gparted when installin linux

---

### Post by cocoia on 2007-02-25
> **oskarloko said:**
> You have rebuild a linux 2.6.20 kernel or downloaded it from.. ?

(I've heard a 2.6.20 is a new abd stable kernel, Linus Tovarlds says... )

My case is the opposite: I've a triple booting system with 6 partitions, which works fairly well..
Simply making them with gparted when installin linux

That's very strange, because I have always been convinced that the EFI  can only handle 4 partitions on the startup disk. Does this create any problems for you?

> **oskarloko said:**
> What are the applesmc patch ??

(sorry for not having a correct response, I'll try building kernel )

The applesmc module allows to interface with the mainboard services, like fan speed, temperature sensors, and even the motion sensors. In OS X, there is a utility to make your Mac run cooler, which  I really miss (especially when running Beryl or making code).

I have created a thread in the mactel forum on building a kernel with the patches. Once I get someone around who has done it succesfully, I will post all the howto's. as I find this lacking as well. I have no idea how to compile a new kernel, and I am trying it now, but it doesn't seem to work &#8212; see thread I mentioned before here:  [http://www.ubuntuforums.org/showthread.php?t=369932]("http://www.ubuntuforums.org/showthread.php?t=369932")

---

### Post by oskarloko on 2007-02-26
> **cocoia said:**
> That's very strange, because I have always been convinced that the EFI  can only handle 4 partitions on the startup disk. Does this create any problems for you?


EFI partitioning system can handle a lot  of primary partitions on HDD, it sees all correctly ( I don't know the maximun number )
I don't know if refit can handle a boot OS from more than 4th partition, I'll try. ( I bet for it )

MBR can handle 4 primary and X extended. Both can work together on the first four primary.

As I´ve a **triple booting** system, I ve ( with rEfit  boot manager )
[LIST=1]
[*]efi hidden
[*]MacOs X
[*]Ubuntu Egdy
[*]winxp
[*]Swap
[*]Shared data on _Ext3
[/LIST]

Both MacOsX and Ubuntu can see last partition.
[INDENT]*See [_here_]("http://www.bmannconsulting.com/macosx/how-to/ext2-for-mac/ext2fsx-readme") for a ext2/3 for MacOsx, I used beta version*[/INDENT]
Windows can see Ubuntu partition, but as is tied to MBR, not swap nor shared data
[INDENT]*And see [_here _]("http://www.fs-driver.org/")to a ext3 filesystem utilities for WinXp*[/INDENT]

Sometimes ext3 partitions *fails *to mount... I think it's caused by:
[LIST]
[*]Using a beta on MacOsx
[*]Three systems, three drivers... some strees
[*]I've some kernel panics with a not-very-good ndiswrapper driver...
[/LIST]

A not perfectly sync and checked ext3 filesystem won't work on any system... and I expect it is the only caveat, but I don't know...


Let's try !!

(maybe I will install Fesity on 6th partiton when it comes to final release - with [**_ELILO_**]("http://en.wikipedia.org/wiki/Elilo"), an efi aware LILO boot loader to Linux )

---

### Post by cocoia on 2007-02-26
Wow, that is impressive :D. It's great to know that it all runs well. I guess I was completely off with that 4 partitions thing ;).

I am still struggling with the kernel, by the way, I will keep you informed by PM how it goes. I actually managed to build a working kernel with the patches, but it didn't manage to boot. Tough luck, trying the 2.6.20-1 today, so... fingers crossed!

---

### Post by hansoffate on 2007-02-26
I forgot to do this command:

To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)
N.B.: It will automatically be applied to the installed system so you won't have to enter it manually ever again!

When i installed edgy on my macbook.  How do i fix this?

Thanks
-Hans

---

### Post by Chrisj303 on 2007-02-26
I;ve been gagging to install ubuntu on my macbook for a while now - decided to take the plunge this morning, it all went swimmingly! Thankyou STEFAN for the guide - there is no way i could have done it as quickly and easily without it (i'm a complete linux virgin!).
I'm only having a little trouble with wireless, but i'm sure i'll get it sorted. It's a very nice to be learning from my OS, like i am with ubuntu.

Thanks again,
chrisj303:mad:

---

### Post by davidseibert on 2007-03-07
Hi all,

I used this method once, and it went perfectly, but then I messed something up trying to get the wireless working, so instead of figuring out the problem I tried to just reinstall Ubuntu. But now the gptsync command that I used before returns 'command not found' no matter what I do...

I don't know how it's possible...it worked fine before...

Anyone have an idea?

Thanks,
Dave

---

### Post by Meck1982 on 2007-03-09
Hi all!

I have problems to get my external monitor (Eizo FlexScan L778) working with my MacBook C2D. I am using a mini-DVI-2-DVI-adapter, which works flawlessly in Mac OS. My system is Feisty Herd 5 and I followed the steps of the Edgy howto from Stefan. After pasting his code in my config I had to change the monitor labels to get the config working.

My big problem is that I do not see any reaction on my external monitor... whatever I am setting, it stays black. It seems the monitor cable is dead. (But it is not, it works in OSX)

I am not a total newbie in editing config files. And I would really appreciate some hints. Don't get me wrong, for now I would be satisfied, if I just got the external monitor working... it does not matter in which mode.

Can anyone confirm, weather the DVI on a MacBook C2D is working at all in theory?

---

### Post by amb1s1 on 2007-03-11
> **davidseibert said:**
> Hi all,

I used this method once, and it went perfectly, but then I messed something up trying to get the wireless working, so instead of figuring out the problem I tried to just reinstall Ubuntu. But now the gptsync command that I used before returns 'command not found' no matter what I do...

I don't know how it's possible...it worked fine before...

Anyone have an idea?

Thanks,
Dave
The same thing happen to me. What I did was when you finish installing Refit on the Package installer, I click INCLUDED FILES. I notice that GPTSYNC was located on /sbin/
so before I hit install, I went into terminal and I type cd /sbin/ and then gtpsync /dev/sda && sfdisk -c /dev/sda 3 83, don't hit enter on the terminal, I hit the install button. I waited until the install went into copying files and then I hit enter on the terminal

---

### Post by jajajavi on 2007-03-12
I have a macbook c2d (kernel 2.6.17-11-generic) the fn key doesn't work!! how can I fix it? gracias!!

---

### Post by Meck1982 on 2007-03-12
Just install the unstable develpment version of ubuntu (Feisty Fawn Herd 5) or wait until the final version gets out. From my experience fn key just work there...
But you should be warned: Herd 5 installs, but you get some strange error messages, when using aptitude/synaptics and wifi with the ndiswrapper does not work like in edgy.
I guess the best thing you could do is just wait for the beta (after herd 5) or the final release.

---

### Post by pilotopirx on 2007-03-12
I have just one complain so far. I have had linux for years, but I also had time (was undergrad) and use to use Slackware. It was frustrating not being able to "install the package asdfadsf.deb" just because I didn't remember how to install packages in debian at all. You should state that explicitly.

---

### Post by spidie on 2007-03-12
Hi All

Thanks for the great instructions so far - I followed these instructions along with a few other posts to install Kubuntu Feisty (Herd 5) on my new Macbook.

One thing is different for me - I am not interested in the slightest in MacOSX or windows - so I just want to blow away everything and single boot. Is it ok to just let ubuntu partitioner autopartition removing all existing partitions (including 200Mb system partition)? 

I tried this last night, everything appeared to work, but on reboot it doesn't boot. I can still boot with the live CD and of course I can put osx back on there and get everything recreated if necessary.

I'll try it again tonight with Edgy to see if it is just a Feisty thing - but just thought I'd check here first.

Happy to start a wiki page or update existing page if necessary - I see lots of pages on double and triple boot - but not a lot relating to full linux only installs.

Thanks in advance.
Steve

---

### Post by spidie on 2007-03-13
Hi All

Looks like it's a Feisty problem - works fine with Edgy (I am writing this from newly installed distro!). I'll have another go with Feisty soon and report back.

Oh - and you don't need refit or system partition or anything for single boot... nice and simple.

Steve

---

### Post by shivathreya on 2007-03-13
> **jajajavi said:**
> I have a macbook c2d (kernel 2.6.17-11-generic) the fn key doesn't work!! how can I fix it? gracias!!
Just create a file in /etc/modprobe.d/ with the following

**options usbhid pb_fnmode=2**

and reboot

---

### Post by spotthreen on 2007-03-14
Spam.

---

### Post by niworst on 2007-04-18
I've installation problem, the GRUB Install fail again in Kubuntu installation. I done everything said on the MacBook/Ubuntu Community Documentation. Even the GPT/MBR sync. Look the result of the sync:

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1       90587176    153563738  EFI System (FAT)
 2         409640     90587175  Mac OS X HFS+
 3      153563739    156301454  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    156301487  ee  EFI Protective

Status: MBR table must be updated.

Proposed new MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    153563738  ee  EFI Protective
 2 *       409640     90587175  af  Mac OS X HFS+
 3      153563739    156301454  82  Linux swap / Solaris

May I update the MBR as printed above? [y/N] y
Yes

Writing new MBR...
MBR updated successfully!

Done


Could Somebody help me please to pass thru it.!!!!!!!!!!!!!!!!:(

---

### Post by Meck1982 on 2007-04-18
@niworst: for me it seems like you forgot to create a kubuntu root partition. You only have a swap (besides osx and efi). Or *did* you create it during the installation process and the problems is elsewhere? I have ubuntu feisty beta running on my macbook. Installation was (having installed refit from osx) boot the beta and do a normal installation creating all the partitions needed. Then reboot and go to the efi menu to do the sync. Hope this helps...

---

### Post by niworst on 2007-04-18
:confused: what do you mean by reboot and go to the efi menu to do the sync. and how??
by the way I was doing exactly what the documentation said.

---

### Post by Meck1982 on 2007-04-18
Are you using the Ubuntu 6.10 Edgy Eft guide? If so, you just can follow the instructions of it, but make sure you are using a live cd version with Edgy.
As you might have been heard the new Ubuntu Version 7.04 Feisty Fawn will be released **tomorrow**. I have been running the Beta for a while on my MacBook. With this version, you can just install the system without this sync *during* installation. You can do this later on a reboot in the refit shell. I think the command in the shell is:

gptsync.efi

Then you see something like you saw in the sync-tool you used in edgy during installation. I think it is actually the same programme. By the way: Do not install Edgy on the MacBook now, wait until tomorrow until Feisty comes out. It's worth waiting.

---

### Post by niworst on 2007-04-18
yeah I'm this guide step by step.
but still with the GRUB install error.
did Kubutu Festy Final Version really release tomorrow????
and by the way how the sync will work??

---

### Post by Meck1982 on 2007-04-18
Hum, I think you either made a mistake using the guide, or were using not using the Edgy Final CD. I did the installation several times using that guide. But now with Feisty, which will indeed be out tomorrow or at last the day after tomorrow everything is easier: Just normal install then: On the refit menu (where the penguin and the apple show up go with the arrow keys to the refit shell or something like this. If it is started you can type **gptsync.efi** to run the sync.

Concerning your Error: Are you familiar with Linux or are this your first steps? If it is the latter I'd guess your problem is the correct partitioning during installation. Perhaps the Ubuntu default layout did not work for you. But perhaps just wait for Feisty :)

Sometimes problems are solved over time without doing anything... :guitar:

---

### Post by niworst on 2007-04-18
Nope I'M a NooBz. but I did'nt make a mistake because during the step of partition it only said to:
   5.

      To install Ubuntu, double-click Install on your desktop, then click through the installer as usual. The defaults are fine most of the time. For the default partition scheme, follow these steps:

    *

      At step 5, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3 (and /dev/sda4 if it exists) from /dev/sda. Click Forward, then Apply, finally Close. Still at step 5, "Prepare mount points", click Back and Back again. Now choose Use the largest continuous free space and click Forward.

      /!\ At step 6, "Ready to install", DO NOT click on Install JUST YET!

---

### Post by Meck1982 on 2007-04-18
OK, I am already experienced with Linux partitioning, so I never chose the default partition scheme. If I were you, I would wait for Feisty and then make a custom partitioning:

1 efi
2 osx
3 linux root (/, ext3)
4 linux swap

If you are planning to use the ubuntu more often, it is recommended to have a seperate home partition (so you do not need to backup your personal data which is stored there, just mount it within the new system)

It is always a good idea to read some stuff about partitioning in linux. I am sure you will find some information on the web that you can understand. And don't give up, Linux is worth the work :)

---

### Post by niworst on 2007-04-18
and how to do that??
and where the GRUB will installed???
and can I explain to do that with Edgy because I've buy the official cd of edgy and I don't waste it.

---

### Post by Meck1982 on 2007-04-18
I will not explain you the partition setup in detail, but I think you should be able to do it with the graphical interface provided by the kubuntu installer. I do not know where the Grub is installed, simply because I never had problems with that. I always had success with the default settings here. Please understand that most people here in the forum will not anser questions like "My installation failed, please help me". It's generally a good idea to be more specific and do a lil research before you post. Here is my personal way of doing things:

- Search the web to find some information to my problem
- Get some basic knowledge by finding general information websites about the topic -- in your case this is partitioning in linux
- If this does not solve the problem, post in this forum with a **detailed** description of what you did and what is working/not working

Always be aware that people don't want to spend more time on solving your problems, than you did. So -- concerning your problem: First read [this]("http://tldp.org/HOWTO/Partition/") or something similar to get a basic understanding of what you are doing. Then again follow the Edgy guide by choosing the manual partition step instead of default layout. Create the layout I proposed. (You will still have to sync during installation process) Then, if you still have the problem, post here again. And please try to understand what you are doing, don't follow the guide blindly. Good luck!

---

### Post by DesertSun on 2007-04-21
The final release of feisty fawn does not correctly boot due to a problem with the X configuration.  These instructions are for kubuntu although ubuntu should be similar.  The way to get around this is to boot on 6.10 live and then look at /etc/X11/xorg.conf.  It should also be possible to use 7.04 beta live if you have it.  For a 15 inch MacBook Pro here are the correct settings:

Section "Device"
     Identifier     "ATI Technologies, Inc. ATI Default Card"
     Driver         "vesa"
     BusID         "PC:1:0:0"
EndSection

Section "Monitor"
     Identifier      "Color LCD"
     Option         "DPMS"
     HorizSync    28-72
     VertRefresh 43-60
EndSection

Section "Screen"
      Identifier      "Default Screen"
      Device          "ATI Technologies, Inc. ATI Default Card"
      Monitor        "Color LCD"
      Default Depth 24
      SubSection "Display"
             Depth     1
             Modes    "1440x900"
      EndSubSection
    
      *Repeat for Depths 4, 8, 15, 16, & 24*

EndSection

Boot on feisty fawn (7.04) live and press F6.  I had some problems sometimes with the keyboard working but try several times if keys are not working.  Then delete "quiet splash" from the boot line and press return.  Ubuntu did not hang but ended up at a prompt so this may not be necessary for it.  The boot will hang after kdm is run.  Press Cntrl-C to get to a prompt.  Then edit /etc/X11/xorg.conf with the settings from 6.10.  Save and then enter "startx".  This should start kdm and put you into your desktop.  If there is still a problem, look at /var/log/Xorg.0.log to find the problem.  Once you have fixed xorg.conf you can install to the hard disk and the correct configuration will end up there.  If you shutdown before installing, the configuration will not be retained.

---

### Post by abdalma on 2007-04-21
I am sorry to say that the the [MacBook Wiki entry]("http://wiki.ubuntu.com/MacBook") seems not correct anymore as of the release of Feisty Fawn ("...without any errors..."):

- Sound is not muted anymore (in comparision to 6.10) if F3 is pressed. More detailed: I have the feeling that upgrading to 7.04 gives me "two sound sources" of which only one is muted if I press F3 and therefor the other remains at 100%. Double-clicking on the speaker at the top-right corner of the desktop reveals that for playing sound there are indeed two sources listed: "Master" and "PCM". While "Master" reacts on pressing F3, F4 or F5, "PCM" does not care and remains at 100%. I can of course edit the volume of the "PCM" level manually but thats not an option.

- ctrl + click for a right mouse click does not work anymore. With 6.10 I had uninstalled the Ubuntu mouseemu-package as it was buggy (starting-up the mouseemu daemon froze the mouse cursor). I have just created my own mouseemu package according to the patch proviced at [Debian]("http://packages.qa.debian.org/m/mouseemu.html"). After upgrading to 7.04 the Ubuntu package was automatically reinstalled and even a manual installation of my own mouseemu package did not fix the "lost" ctrl + click functionality again. So: no ctrl + click with Feisty anymore. Manually starting (the Ubuntu packaged) mouseemu with "mouseemu -debug -right 29 272" gives "No uinput device found! Make sure the uinput module is loaded
or CONFIG_INPUT_UINPUT is compiled into the kernel.". uinput is loaded but "/dev/uinput" does not exist (which is the default device)

---

### Post by SarahDavies on 2007-04-22
Hi 

I'm completely new to linux, and I'm installing Feisty Fawn on a black macbook.  Your instructions were quite helpful.  Still took some ingenuity to get my wireless card working without any sort of windows, but I like a good challenge.  I just had one question for you:

When I hold down the option key during boot up, it still shows me a Mac partition and a "Windows" partition.  Is there any way to rename the "Windows" partition?  Also, is there any way to make it boot into Feisty Fawn rather than OS X when I don't hold down the option key?

Thanks for your help!

---

### Post by szines on 2007-04-24
If I connect a wire network cable, than freez everything... wifi is working correctly...
i use first serial macbook with core duo.
does somebody meet with this problem?

---

### Post by tonymorgan on 2007-04-27
I'm having a similar problem, also mini-dvi 2 dvi adapter doesn't work in ubuntu, but works in os x. However s-video out works in both, which indicates to me that the original poster was using VGA converter perhaps? and something extra needs to be done to get DVI working? Any advice appricated, or reports of working DVI out + xorg.conf. Cheers Tony

> **Meck1982 said:**
> Hi all!

I have problems to get my external monitor (Eizo FlexScan L778) working with my MacBook C2D. I am using a mini-DVI-2-DVI-adapter, which works flawlessly in Mac OS. My system is Feisty Herd 5 and I followed the steps of the Edgy howto from Stefan. After pasting his code in my config I had to change the monitor labels to get the config working.

My big problem is that I do not see any reaction on my external monitor... whatever I am setting, it stays black. It seems the monitor cable is dead. (But it is not, it works in OSX)

I am not a total newbie in editing config files. And I would really appreciate some hints. Don't get me wrong, for now I would be satisfied, if I just got the external monitor working... it does not matter in which mode.

Can anyone confirm, weather the DVI on a MacBook C2D is working at all in theory?

---

### Post by Meck1982 on 2007-04-28
Hi, in the meantime I managed to get things work like I want: See my post [here]("http://ubuntuforums.org/showthread.php?p=2514196#post2514196").

---

### Post by martinbures on 2007-04-28
This question is about synaptics.  I would like to get two-finger scrolling, etc working.  There is nothing in the ubuntu macbook wiki about this but there is some information in the debian macbook wiki.  I have installed the correct modules and made the necessary changes to my /etc/X11/xorg.conf file.  The part that I am stumped on is this:

"
If you want to use the Synaptics touchpad add these lines to /etc/modprobe.d/

install usbhid /sbin/modprobe appletouch; /sbin/modprobe --ignore-install usbhid $CMDLINE_OPTS

Then add  appletouch  to /etc/initramfs-tools/modules and then run  update-initramfs  
"

Ubuntu seems to be laid out slightly differently from debian.  There doesn't seem to be a /etc/modprobe.d file.  There is a /etc/modprobe.d directory.  How do I add modules to it?  

Maybe I am going about this all wrong.  Let me know if anyone has ideas or if this is better answered elsewhere.

thanks.
martin.

---

### Post by jajajavi on 2007-04-30
I've upgraded ubuntu with upgrade manager, when the system is rebooted the keyboard is dead (touchpad only works). I can't typ username/password, I can't use ubuntu in my macbook c2d!! I have tried with an external usb keyboard but it does not work either. What can I do? Thanks!

---

### Post by dsapoki on 2007-05-01
hello stephan daniel, thanx for nice how to. however I have some troubles with wifi. i have followed your guide, but make and make install shows error message. is it because of kernel path? i have downloaded it to desktop and start it from there. next problem is how to have acces to my personal files from macbook, I can see them but cannot open since I have no rights...? any idea? i am completely new to macbook(black, 2ghz,inel core 2 duo), and ubuntu I know only few months since I made beautiful install on asus a6k-q023h(lot of work, but now i am proud of it, single boot, not even a trace of windous). thanks

---

### Post by peterl on 2007-05-09
hello!

would like to bump sarahdavies question: how do i make `windows' the default in bootcamp? i've tried going into startup disk in osx, but i guess that that won't help because bootcamp happens after it's used the hfs partition in the first place...

anyone know if it's possible to make windows the default if you're only using osx/mswin? guess that'd be a starting point...

peter

p.s.: thanks for the great howto. i got my macbook yesterday and was up and running ubuntu before i left the apple shop!

---

### Post by hesee on 2007-05-09
> **Meck1982 said:**
> Hum, I think you either made a mistake using the guide, or were using not using the Edgy Final CD. I did the installation several times using that guide. But now with Feisty, which will indeed be out tomorrow or at last the day after tomorrow everything is easier: Just normal install then: On the refit menu (where the penguin and the apple show up go with the arrow keys to the refit shell or something like this. If it is started you can type **gptsync.efi** to run the sync.

Concerning your Error: Are you familiar with Linux or are this your first steps? If it is the latter I'd guess your problem is the correct partitioning during installation. Perhaps the Ubuntu default layout did not work for you. But perhaps just wait for Feisty :)

Sometimes problems are solved over time without doing anything... :guitar:

Hi. I had edgy installation on my macbook, but it was quite a mess after all the experiments i had done so i decided to do a new installation to feisty. I did the basic installation (i didn't do the gptsync during installation) and rebooted, but when i went to refit shell and input: 

gptsync.efi, 

it told that no syncing is needed. However, i cannot boot to feisty, is there anything i can do to fix this?

Edit: Clarification: I had edgy earlier, so there is that rEFIt boot system installed, but when I startup and choose linux(that penguin logo), logo stays only there forever and nothing else happens...

Edit2: Problem disappeared. When I booted second time, everything works now.

---

### Post by peterl on 2007-05-12
> **peterl said:**
> hello!

would like to bump sarahdavies question: how do i make `windows' the default in bootcamp? i've tried going into startup disk in osx, but i guess that that won't help because bootcamp happens after it's used the hfs partition in the first place...

anyone know if it's possible to make windows the default if you're only using osx/mswin? guess that'd be a starting point...

peter

p.s.: thanks for the great howto. i got my macbook yesterday and was up and running ubuntu before i left the apple shop!

answer: i downloaded rEFIt and installed using osx... now it seems to have replaced bootcamp, and i alter the config file to make ubuntu the default.
peter.

---

### Post by hesee on 2007-05-15
Hi, one question:

Is it so that wireless networking with madwifi works only without authentication (WEP)? I cannot get my wlan working with WEP, only without it (anyone can connect to it :( ). I  read somewhere that madwifi does not support WEP yet, but is this true?

---

### Post by Seamyst on 2007-05-18
Love the guide, it's very useful and easy to understand for a newbie!

One thing, however, that you might want to change.  I cannot get 915resolution by pasting the code you provided for Feisty:

```
sudo software-properties -e universe
sudo apt-get update
sudo apt-get install 915resolution
```

When I try it, it says that "software-properties" isn't recognized or some such.  I did this both before and after installing all the updates, and it gave me the same thing.

Here's what to do instead.  Download all the updates, then open Synaptic Package Manager and search for 915resolution.  (It won't return any results if you search before the updates.)  Install it, reboot and it should work.

Just wanted to let you know so you can update that part of the guide.  Thanks!

---

### Post by peterl on 2007-05-23
> **hesee said:**
> Hi, one question:

Is it so that wireless networking with madwifi works only without authentication (WEP)? I cannot get my wlan working with WEP, only without it (anyone can connect to it :( ). I  read somewhere that madwifi does not support WEP yet, but is this true?

i can't remember how i did it (sorry) but i'm using wpa2 personal right now with my macbook 3rd generation... worked with my 2g too until i took it back for the upgrade (and £160 back on the credit card!)

so i can tell you that it's possible, but not how to do it!
p

p.s. it took me a long time to work out that the ap i was using had mac address filtering turned on... but perhaps you've already thought of that!

EDIT: was the mactel-linux wiki: macbook dual boot wifi-with-wpa howto

---

### Post by omax on 2007-06-04
I did as the guide says...

Until I shall boot up Ubuntu for the first time.

Then it says:

GRUB Loading stage2...


And there it stops. I'm installing with Ubuntu 6.06 because I'd like to just update it later.

---

### Post by hesee on 2007-06-04
Hi, what would have gone wrong, when i cannot type this mark any more:
{

I used to type it by pressing right apple button and 7. I can't remember if i have tried this with feisty earlier, but that's how it worked with edgy.

Edit: Is these settings defined here: /etc/X11/xkb/keycodes/xfree86 ?, 
if someone could post his/her version, that could help.

---

### Post by Rod_Myers on 2007-06-08
That's why I bought the Macbook, was the very difficulties in setting up wirless networking, using WEP.

One of my wifi adapters does not do WPA, so stuck with wep

If anyone finds out a way to get wep woring, I would also be very interested.

---

### Post by arijarot on 2007-06-10
> **Stefan Daniel Schwarz said:**
> Hello world!

Here's my guide **[how to install Ubuntu 6.10 "Edgy Eft" on a MacBook]("https://wiki.ubuntu.com/MacBook")**.

Why another HOWTO? There are others available already. But this one is different:
[LIST]
[*]Using only GRUB instead of LILO bootloader
[*]For the latest Ubuntu release
[*]Made for the official wiki
[*]Designed for Copy and Paste
[*]**Installation completes successfully without error, yes, on a MacBook!**
[/LIST]
I'm posting here to let you know about it, and so it can be discussed in a forum, which is more appropriate for discussion than a wiki.

Have fun with Ubuntu on the MacBook!

See ya! :cool:
-- StefanDanielSchwarz

I followed the directions and ubuntu works without error, thank you, but now when I try to boot into osx, I keep on getting this message:
> you need to restart your computer. hold down the power button for several seconds or press the restart button. this is said in four different languages, in a box in front of a power button picture. then when I restart... the same message appears over and over again. any ideas what's going on here?

EDIT:
attached is a jpg of the message
I should also mention the procedure that led up to this: installed boot camp, made a win driver cd just in case, partitioned the drive successfully, was asked whether I wanted to install win or restart mac: I chose restart mac (this was after the mac slept for a few hours), on reboot I got this message (I hadn't installed ubuntu or changed anything yet, but since I couldn't boot into mac at this point I decided to install ubuntu  on the new partition)

**EDIT: SOLVED**

---

### Post by arijarot on 2007-06-10
OK, I'm stuck at this step:

```
export AUTOBUILD=1
fakeroot debian/rules binary-debs flavours=generic

```

it just keeps running and running in the terminal for hours and it never completes... any ideas what's going on here?

---

### Post by Yaten on 2007-06-14
(My apologies if this question was answered earlier in the thread; a basic search didn't provide me with the solution I'm hoping for)

I've been using Boot Camp with Ubuntu for about a month now, and while I really enjoy the experience, I'm short on disk space on my Mac partition.  I don't have anything on my Ubuntu HDD that's not backed up, so the simplest solution for me was to uninstall, remove the partition with Boot Camp, and try again with a smaller partition for Linux.  But when I try to uninstall Ubuntu from Boot Camp, I get the following error:

"The startup disk cannot be partitioned or restored to a single partition: the startup disk must be formatted as a single Mac OX Extended (Journaled) volume or already partitioned by Boot Camp Assistant for installing Windows."

Any tricks here?  This is presumably an error from the original Ubuntu installation, since I partitioned the Linux partition itself during Ubuntu installation.

Thanks!

---

### Post by roostishaw on 2007-06-14
How can I do this while still allowing Boot Camp Assistant to remove Ubuntu and return my drive to a single partition at a later date?

Using the 7.04 instructions from [ [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) ], will I be able to later remove Ubuntu using Boot Camp Assistant? If not, how can I install Ubuntu in such a way that I will be able to remove it later on using Boot Camp Assistant?

Do I need to specify where GRUB must be installed? (using the alternate install CD?)

Thanks!

---

### Post by siddhuwarrier on 2007-06-16
Hi,

Would be much obliged if you could help. Need to run tinyos 2.x on Ubuntu on my iMac with Intel Core2Duo. 

Installed Ubuntu x64 on my iMac. Now, I dont' have a wired internet connection, so I installed build-essentials from the CD, and got the madwifi tar gz downloaded using OS X. I copied it into my root directory, and ran the sudo make and sudo make install.

No errors encountered.

But I am not able to detect my wireless network, and the card does not appear on Network.

I ran lsmod and found that ath_pci module was loaded, but when I run modprobe, it gives me NO messages at all.

Additionally, when i try to scan using: sudo wlanconfig ath0 list scan, it tells me that there is no device called ath0. :(

I tried reading the INSTALL file that came with the driver tar.gz, but there is no info on this.

Could somebody please advise? Has anybody got wireless working on Ubuntu running on a new iMac?

---

### Post by t64030 on 2007-06-20
I followed the instructions step by step and i still couldn't get the wireless to work on my white macbook. and when i tryed to do it again it showed that the drivers were already installed and then it said they were invalid. I am really tired of hooking up the either net cable every time i want to use my ubuntu. someone please help.!!!

---

### Post by stuporglue on 2007-07-08
Thanks for the instructions!

I just used them to get Gutsy tribe 2 installed. 
I'm using a 2 GHz white MacBook.


The only real difference from the Feisty instructions was that the partitioner in Gutsy seems to be a work in progress and would freeze if I tried to create new partitions. I ended up having to run gparted ("sudo gparted", from a command line), deleting the windows partitions and saying "Use existing free space", and then it worked. 

I'm having some issues with nm-applet and random GUI freezing (have to Ctrl+alt+delete) if I try to log in more than once each boot...but I don't know if that's configuration, hardware, or Gutsy...

--Stuporglue

---

### Post by davidstodolsky on 2007-07-09
This To Do doesn't work for a Mac (not Ubuntu) user.

"Get the  Live CD and boot on it. Choose your language and/or keymap."

Note that the default burn from in Mac Finder is iso, which doesn't work, and leaves you hanging in a bad place.


"To prevent a kernel panic which might occasionally occur, press F6:"

Couldn't get this to work.



"To install Ubuntu, double-click Install on your desktop, then click through the installer as usual. The defaults are fine most of the time. For the default partition scheme, follow these steps:
At step 4, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3"

Simply couldn't find any way to delete.

---

### Post by djsubsonik on 2007-07-13
I have been tying to triple boot for the past few days now and its a no go... i got osx and ubuntu fine.. but when i tried to do xp it failed with disk error... i redid the whole drive with a new partition scheme.. installed osx.. then xp .. but when i try to boot xp after it loads setup files on to disk it says "fail to load ntldr" or "fail to load nt kernel" .. and other messages of the like.. i followed the recommended diskutil resizeVolume command and thats what i got :( .. please help!

---

### Post by Stu09 on 2007-07-27
Apologies if this has already been covered
> To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)

What should be written for one of the new 2.16GHz MacBooks ?

---

### Post by zachdhudson on 2007-08-05
Hi!

This is my first post here, and I'm doing it from the latest core 2 duo macbook, 2.16 Ghz.  I've tried in the past to get feisty working properly on a macbook, but sound has always been an issue.  Sound can't be muted, and if you adjust what the volume up/down does, it might fix it, but overall, sound quality is horendously bad.  Also, if the volume isn't on >90%,  sound only comes out of hte right speaker.  As I keep my macbook hooked up to a nice stereo system, sound is highly important to me.  Does anyone know of a fix for this?  I haven't seen anyone really make an issue of it, so maybe everyone just already knows how to fix it, as it's highyl noticeable on install.  Thanks!
-Zach

---

### Post by Gen2ly on 2007-08-07
Yes the new 2.6.22 kernel includes the driver that fixes this problem.  See the Apple Intel forum on howto compile a kernel for the MacBook.

---

### Post by gavin8or on 2007-08-08
Is there any way to use the DVD-R burner?

---

### Post by bmitchell33 on 2007-08-11
Well, I'm a little frustrated right now.  Following the exact descriptions, the partitioning tool in Ubuntu has completely erased the Mac OS X partition.  I have no idea where to go from here, except reminisce about all the data I lost.  Thanks Stefan.

---

### Post by fizz on 2007-08-14
Hello all! I'm using a Macbook Pro (the one with ATI graphics chipset). I downlaoded the 7.04 Live Install CD per recomendations on this thread and have two issues before I can install.

A. Keyboard doesnt work while at the boot: screen, i have to wait for the timer to run down before it continues to load Gnome.

B. It gives me a warning saying its not able to load X to restart GDM once i have it working. I noted that its trying to use the VESA driver in the Xorg.conf file.

Any insight would be great, thanks.

---

### Post by Meck1982 on 2007-09-14
@gavin8or:
DVD-Burning should work out of the box. I burned some CD-RWs on my MacBook. Just install gnome-baker with synaptics or use the burning facility in Nautilus.

---

### Post by austratton on 2007-09-15
Will work with Kubuntu?

Great HowTo:)

---

### Post by Meck1982 on 2007-09-15
Yes, Kubuntu and Ubuntu are basically the same. They use different standard programmes though, for example Adept instead of Synaptics for program installation management.

---

### Post by mnml on 2007-10-05
thanks a lot for the how-to , btw the link for madwifi doesn't work anymore

---

### Post by Ghola28 on 2007-10-05
Let me add my thanks for putting together this how-to for MacBook owners.  It gave me the courage to give Ubuntu a try.

However, I'm still having trouble with getting Wifi to work.  I'm using Feisty Fawn on a 2.0 GHz Core 2 Duo Macbook.  I installed the latest MadWifi drivers according to your (and their) instructions.  But I continue to get a "no device found error" whenever I use one of the wlanconfig commands.

Anyone else having this problem?  Do I need to go back to an older version of the MdWifi drivers?

---

### Post by nnutter on 2007-10-05
I'm not sure why, but for me WiFi works out-of-the-box. I didn't need to mess with ndiswrapper or madwifi. I think way back when I did need to install gnome-network-manager or whatever. And it definitely works out-of-the-box for Gutsy. I have a first-gen MacBook.

---

### Post by mnml on 2007-10-07
anyone know how to configure X11 with 3d accel etc?
I tried to launch some 3d games on my macbook, but i get a really slow FPS rate :/

---

### Post by Ghola28 on 2007-10-07
Fixed the Wifi problem.  Replaced the link to the madwifi drivers in the install instructions to the one given for "gutsy" installs: wget [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz).  Rest of the instructions given got it working after reboot!

---

### Post by mnml on 2007-10-07
works fine with madwifi-ng aswell

---

### Post by Zaff on 2007-10-16
Hi I just installed Ubuntu on my Macbook and I'm having an issue with the dual screen thing. I upgraded to Gutsy before doing anything because it seemed to handle MacBooks better. Maybe I was wrong...
Anyway, I can't get my second Monitor to work. I tried using the Ubuntu Screen and Graphics dialog in the System>Administration menu. I selected the i810 driver and tried to set it up from here but whenever I try to set a second extended screen and I restart, I only have display in my main screen and the resolution is messed up.
Can someone help me ?
Here's my xorg.conf : 

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"L226WA"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"L226WA"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x960@60"	"1280x1024@60"	"1280x1024@75"	"1280x960@75"	"1152x864@75"	"1400x1050@60"	"1024x768@60"	"1400x1050@75"	"1024x768@70"	"1600x1200@65"	"1024x768@75"	"1600x1200@60"	"832x624@75"	"1792x1344@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

Thanks

---

### Post by stuporglue on 2007-10-16
You should start a new thread since your problem a) isn't with Ubuntu 6.10 and b) Isn't about getting Ubuntu installed (at least, it sounds like you got it installed all right)

You'll probably get more/better responses if people don't think you're working with Ubuntu 6.10. :-) 

Also, check this page if you haven't : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by Zaff on 2007-10-16
Sorry, I'll do that right away
Thanks

---

### Post by mnml on 2007-10-29
> **macmatt said:**
> Would someone tell me why it is so important to get Ubuntu running on a perfectly good machine, with an already perfectly running OS??. No offence meant, but it seems kinda pointless, unless you are a tinkerer and just want to do it to prove it can be done, in which case I can see why.

I can see nothing that Ubuntu offers extra, that Tiger does not. Just asking why, is all.

hum, actually i switched to linux on my mac because there is a lot of things i cant do with OsX. Osx is cool, at least it's better than windows but; with osx:
- You don't get the apt-get system
       -> you have to pay to upgrade your system, and the system doesn't update your softs
- The finder environement or whatever is not so "cool" and if you want to use something                   else you can't really do it.
- You can't really change anything, and thats maybe why so many people loves it.. it's a perfect noob operating system, runing on the unix pattern.

---

### Post by PetrB on 2007-10-29
There are things which seem to be better in Linux - I prefer Gimp to iphoto, Krusader to finder and gqview is IMHO perfect viewer and entry gate for specialised editors. I may be wrong - there may be similar or better programs in OS X shareware depositories. I also have some special scripts I collected over the years and I need them. Some of them would be difficult or even impossible to use in OS X.

This aside, there are IMHO two basic approaches to work on computer. I would call one of them program centric ad the other data centric. 

Most of my work on computer is data related (photos, diaries, various text documents, drawings...)- and I wish to keep these data forever, certainly over number of SW generations. To do it I keep all my data in single storage area, in format, which is open, widely used and compatible with number of SW packages. (BTW it sits currently on USB HDD, so I can just carry it to another machine.) And I need full control over fate of my data.

Program centric software is centered around programs and data are basically treated as property of program. Typically you "import" your photos by program, it is stored in some database and used as required. Quite often you have no choice of editor from that point. That may be OK for time being - until you need to do something your editor does not offer. Or until supplier of that program disappears or decides to radically change style and you are no longer happy with it. Or until you decide to migrate to different system for whatever reason. 

Linux - Ubuntu - is perfect tool for data centric system. OS X (and Windows) prefer program centric approach. Partly because suppliers of program do not cooperate as well as authors of GPL SW, partly in full knowledge that program centric system tends to "lock in" users. 

I have both OS X and Linux on my MacBook but OS X is used mostly for fun and I am using Linux for work. The result is that I usually boot to OS X only, when I need something difficult or impossible from Linux (like driving my plasma TV as an outside monitor...).

---

### Post by xwhisky on 2007-11-03
Hello,

I have question on hibernation. I tried to make swapfile instead of swap partition as you can read in "How to install Ubuntu Gutsy on a MacBook". It create swapfile and I can use it - but unfortunatelly I can't hibernate .... ? What's wrong? Do you have anybody same problem?

Tomas

---

### Post by stuporglue on 2007-11-03
> Hello,

I have question on hibernation. I tried to make swapfile instead of swap partition as you can read in "How to install Ubuntu Gutsy on a MacBook". It create swapfile and I can use it - but unfortunatelly I can't hibernate .... ? What's wrong? Do you have anybody same problem?

Tomas

Tomas, 

This thread is (was) about Ubuntu 6.10. Since you are not using Ubuntu 6.10, but rather Ubuntu 7.10 (Gutsy) you should start a new thread. 

The advice and how-tos in this thread are very likely not going to work correctly on any other version of Ubuntu other than Ubuntu 6.10.

---

### Post by mnml on 2007-11-04
when I insert a DVD-R blank or a DVD-RW blank, ubuntu eject it,
anyone has got the same issue? any solution?
thanks

---

### Post by stuporglue on 2007-11-04
> when I insert a DVD-R blank or a DVD-RW blank, ubuntu eject it,
anyone has got the same issue? any solution?
thanks

Can you upgrade to Ubuntu 7.10?

---

### Post by mnml on 2007-11-04
> **stuporglue said:**
> Can you upgrade to Ubuntu 7.10?

I am using 7.10

---

### Post by stuporglue on 2007-11-04
> **mnml said:**
> I am using 7.10

Then you should start a new thread, this thread is about "How to install Ubuntu 6.10 "Edgy Eft" on a MacBook" (note the title). 

Feel free to start a new thread for each problem you encounter, having the thread titles and the thread contents match makes finding solutions easier for everyone. 

Thanks, 
Stuporglue

---

### Post by mnml on 2007-11-27
there is no dvd burner in a macbook that was the reason :(

---

### Post by Thuz on 2007-11-28
Hello,

I am currently using 7.10, but I believe the same problem may be in 6.10, so thus I am asking it here. 

I have just set up Ubuntu on my MacBook, and it's working wonders. However, I have lost my button with the ' on. It is usually on the §-button to the left of 1 (and above TAB), but it has mapped it to the same as Windows computers use: |. 

I suppose it can be set in /etc/X11/xkb/keycodes/xfree86, but I have no idea what to look for there. Are there any suggestions? :)

Best regards,

Thuz

---

### Post by zeh on 2007-12-04
Hi everyone.

 I have always used Ubuntu on regular PCs, and now i finally got my Macbook.
So, I'm stuck in a very basic point. I started the mac with 7.10 live cd and done the install process.
After the successful installation, Mac bootloader can't see my Ubuntu partition and give only the option to boot into Leopard. The thing is that i don't want to instal rEFI and keep the mac original bootloader. Is this possible?

Thanks.

Zeh

---

### Post by stuporglue on 2007-12-04
Thuz, Zeh, start new threads about your topics.

---

### Post by RelativelyQuantum on 2007-12-21
Hi all. I followed the information on this thread, but I came up with an x server error; one of those "no screens found," BSOD-like jobs. Any input?

---

### Post by bretonfou on 2008-01-27
Hello thanks for the tutorial i would never had figured out myself what to do. 

I still have small problems, to fix the suspend issue you propose to install an older kernel, it works fine but then the wifi do not work anymore.

I tried to recompile the driver module (since modules are tagged by kernel version)
and i checked that rc.local load them, i even tried manually
but got something like

no IOCTL for ath0 

That's all.

I wonder if the Bluetooth transmitter works .. same for the camera but i can do without. 

As soon as i get the external display to work i will totally remove MaxOSX 
i dislike it much, even if it get close to linux  the co-existence of Fink and of regular Max OS application is quite messy.

---

### Post by bretonfou on 2008-01-27
> **zeh said:**
> Hi everyone.

 I have always used Ubuntu on regular PCs, and now i finally got my Macbook.
So, I'm stuck in a very basic point. I started the mac with 7.10 live cd and done the install process.
After the successful installation, Mac bootloader can't see my Ubuntu partition and give only the option to boot into Leopard. The thing is that i don't want to instal rEFI and keep the mac original bootloader. Is this possible?

Thanks.

Zeh


I did as follow :

I instaled MAxosX only on a part of the disk letting 2 additionnal partitions. 
Then i booted with the live cd holding the c key and used a custom partitioning.

Now when i boot holding Option i can choose maxos or linux, 
linux will load Grub.

The Max bootloader load the last bootstrab he ran, so after booting on linux once
you may simply forget the option key unless you want to boot MacosX. 


To install MacOSX on a part of the disk, simply use the diskutil from mac boot cd
and then install MacOS where you want.

---

### Post by arijarot on 2008-01-27
> **bretonfou said:**
> Hello thanks for the tutorial i would never had figured out myself what to do. 

I still have small problems, to fix the suspend issue you propose to install an older kernel, it works fine but then the wifi do not work anymore.

I tried to recompile the driver module (since modules are tagged by kernel version)
and i checked that rc.local load them, i even tried manually
but got something like

no IOCTL for ath0 

That's all.

I wonder if the Bluetooth transmitter works .. same for the camera but i can do without. 

As soon as i get the external display to work i will totally remove MaxOSX 
i dislike it much, even if it get close to linux  the co-existence of Fink and of regular Max OS application is quite messy.

Which kernel/ubuntu version are you using? I'm on 7.10 with kernel 2.6.22-14 and my suspend and hibernate work out-of-the-box. I'm on the macbook core duo 1.83. the only thing that I haven't gotten to work is dual head, but I will investige that through the "screen and graphics" app when I get around to it.

---

### Post by bretonfou on 2008-01-29
> **arijarot said:**
> Which kernel/ubuntu version are you using? I'm on 7.10 with kernel 2.6.22-14 and my suspend and hibernate work out-of-the-box. I'm on the macbook core duo 1.83. the only thing that I haven't gotten to work is dual head, but I will investige that through the "screen and graphics" app when I get around to it.

\Thanks i will investigate and reply as soon as possible.

---

### Post by bretonfou on 2008-01-29
I did  try to hibernate on 2.61224 and well now i lost the keyboard ..
i tried to boot in safe mode and the pc got stuck after launching X, 
if i plug an external usb keyboard it works. 

I tried to boot on the two kernel in safe and total mode 
and well the keyboard is not there anynmore ... 

I don know what is going on.

---

### Post by arijarot on 2008-01-29
> **bretonfou said:**
> I did  try to hibernate on 2.61224 and well now i lost the keyboard ..
i tried to boot in safe mode and the pc got stuck after launching X, 
if i plug an external usb keyboard it works. 

I tried to boot on the two kernel in safe and total mode 
and well the keyboard is not there anynmore ... 

I don know what is going on.

weird... did you custom configure the keyboard in anyway? can you not reboot and log in normally?

---

