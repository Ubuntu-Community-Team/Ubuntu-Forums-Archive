---
title: "Chainloading Karmic (GRUB2 error &quot;invalid signature&quot;)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by GepettoBR on 2009-11-01
**Summary of the problem for the TLDR crowd: either I can't get one GRUB2 to chainload into another GRUB2 or I can't get GRUB2 to install itself into a partition instead of the MBR.**

First, a little background: I have two hard drives on this PC: One hosts my primary OSes (currently Windows 7 and Karmic) and the other, which stores my files, for safety reasons has a third OS (currently, Arch Linux). Also for safety reasons they both have a swap partition, so I can stay afloat if any one of them goes down.

Here's the cool/troublesome part: In my primary hard drive, I also have a 15MB partition that hosts a standalone GRUB, installed to the MBR. This allows me to boot up even if I manage to bork both Linux distros and can't use a LiveCD to fix things for whatever reason. The partition is owned by root and only mounted explicitly, so nothing touches it unless I want it to.

</background>

This is still going to read as a story, though.

Yesterday I upgraded both primaries, from XP and Jaunty to 7 and Karmic, both x64 and spanky-new (meaning I did fresh installs instead of upgrades). Hooray for everyone. I installed Karmic first, and then Windows 7, and the third part was restoring my MBR to the GRUB partition, which in the good old days of GRUB Legacy could be done via a simple ```
$ sudo grub
grub> root (hd0,4)
grub> setup (hd0)
```
But alas the golden days are gone, and I couldn't find a way to do that in Karmic. I hunted down an old Intrepid Beta LiveCD I had and ran the command from there, but Karmic refused to be chainloaded. Note that both Windows 7 and Arch Linux could be accessed normally at this point.

Thinking that my build of GRUB (0.97, IIRC) couldn't chainload GRUB2 (the new filesystem isn't to blame, my Arch Linux is installed to an ext4 partition), I decided to upgrade my master GRUB to GRUB2. I moved the partition's /boot/grub to /boot/grub-legacy and copied over the contents of Karmic's /boot/grub over, writing a new grub.cfg with the desired menu entries (3 chainloaders + halt). The new syntax felt weird, but Google is my friend, so all was good. I installed it to the MBR via ```
$ sudo grub-setup -r /dev/sda5 /dev/sda
```And here's the configfile:```
&#65279;# Timeout for menu

set timeout=10



# Set default boot entry as Entry 0

set default=0



# UBUNTU

menuentry "Ubuntu 9.10 Karmic Koala (hd0,6)" {

    set root=(hd0,6)

    chainloader +1

}





# ARCH

menuentry "Arch Linux (hd1)" {

    set root=(hd1)

    chainloader +1

}



# WINDOWS

menuentry "Microsoft Windows 7 Ultimate (hd0,1)" {

    set root=(hd0,1)

    chainloader +1

}

[color=red]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 5d79c87c-eb5c-4b81-870f-5fd9ca58be60
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5d79c87c-eb5c-4b81-870f-5fd9ca58be60 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}[/color]

menuentry "Power Down"{
halt
}
```
At this point, it didn't have the section in red. I'll get back to that later.

Unfortunately, nothing changed: Karmic was still the only one that refused to boot. I snooped in Karmic's own grub.cfg, saw the "insmod ext2" line and added it after the "set root=(hd0,6)" line, to no avail. I still got the "invalid signature" error. At least this means that GRUB has found something: pointing it to any non-system partition produced a different error about not finding C/H/S values or something to that effect. Adding "--force" to the chainloader argument made it reboot my computer. WTH?

At this point, I remembered my oversight during the installation and decided to reinstall Karmic, remembering to select /dev/sda6 as GRUB's destination in Step 8. Lo and behold, I still couldn't boot into Karmic. As a temporary solution, I copied over the section in red from the grub.cfg generated during the installation. I then booted into Karmic via this entry and proceeded to the Terminal to run ```
$ sudo grub-install /dev/sda6
``` which told me that installing GRUB to a partition was "a BAD idea", then complained about blocklists and eventually said it was done and displayed the contents of the device map, which were correct. Awesome. Except for the tiny detail that it didn't actually work. Output: ```
$ sudo grub-install /dev/sda6
[sudo] password for paulo: 
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Notice the "No errors reported" bit. Since it didn't work, it seems GRUB2 is hiding errors from me. BAD bootloader!

Now, I can probably change the first entry to load Karmic's configfile instead of chainloading, but that won't change the fact that for some reason GRUB2 is not installing (and is lying to me about that fact). Since I'm new to this rewritten GRUB, I'm clueless about the possibilities. Googling around for this problem  brought three things to my attention:
a) people are getting the same "invalid signature" error with their Windows partitions in a "normal" installation of Karmic,
b) they seem to blame it on Windows (probably out of habit), and
c)the people helping them are as clueless about the inner workings of GRUB2 as they are (and as I am).

Here's to hoping that someone with a little more knowledge than the average bear will read this thread and help us all out. I do believe all the relevant information is in here.

Thanks in advance to all who read this thread and all who reply. 
Regards,

Paulo Bittencourt.

---

### Post by ssican on 2009-11-01
Some Useful Links:

1)- Grub 2 Basics:
    
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

2)- GRUB2 Pages:
 
[http://members.iinet.net.au/~herman546/p20.html](http://members.iinet.net.au/~herman546/p20.html)

EDIT 1 :
TO INSTALL GRUB2 in the same partition that Ubuntu 9.10, CLICK on the BUTTON "ADVANCED" on the step "READY TO INSTALL" -THE LAST STEP- of the Installation. Step 6 of 6 :
[http://www.techarena.in/files/image/guide/092009/install_ubuntu_9.10/13_ready_to_install_setup_review.JPG](http://www.techarena.in/files/image/guide/092009/install_ubuntu_9.10/13_ready_to_install_setup_review.JPG)

EDIT 2 :
To try a NEW "DEDICATED GRUB PARTITION" by HERMAN'S METHOD :
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

EDIT 3 :
Change the default operating system for startup (multiboot) FOR WINDOWS 7 :
[http://windows.microsoft.com/en-US/windows7/Change-the-default-operating-system-for-startup-multiboot](http://windows.microsoft.com/en-US/windows7/Change-the-default-operating-system-for-startup-multiboot)

EDIT 4 :
Another LINK For GRUB2 :
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by louieb on 2009-11-01
I'm sure you'll get it figured out. I too have a dedicated grub partition. It has Grub legacy (v.097). It chainload  GRUB2 in the Karmic install   

I used the alternate install CD to install Karmic. Had not problem getting GRUB2 in the boot sector of the / (root) partition. 

Just about to link you to Hermans site but I see ssican beat me to it.

---

### Post by GepettoBR on 2009-11-02
Thank you both very much! Unfortunately, none of those links had the information I wanted. GRUB2 is not being installed to /dev/sda6, yet it reports itself as correctly installed. I also still don't know what to make of the "invalid signature" error.

---

### Post by perspectoff on 2009-11-11
> **GepettoBR said:**
> Thank you both very much! Unfortunately, none of those links had the information I wanted. GRUB2 is not being installed to /dev/sda6, yet it reports itself as correctly installed. I also still don't know what to make of the "invalid signature" error.

I use chainloading on all my computers. What's weird is that Karmic (i.e. grub2 on the Karmic partition) chainloads successfully on 3 computers, but not the fourth.

It gives the same error you mention. I had to edit the Grub-Legacy menu.lst file (on my boot partition) to read:

title        Kubuntu Karmic Koala
rootnoverify (hd0,6)
kernel       /vmlinuz root=/dev/sda7

the old fashioned way, instead of using the chainloader.

Ubuntu Karmic Server edition installer allows you to install GRUB2 to the local partition (and/or the MBR), but the Desktop edition does not offer that option.

Therefore, I installed the Server edition and then just added the kubuntu-desktop.

---

