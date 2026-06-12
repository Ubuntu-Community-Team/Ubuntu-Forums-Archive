---
title: "GRUB fixing due to SafeBoot hiding old MBR and because of /boot partition"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-10-08
FYI only:
So here are my notes to myself on how to fix/create a dual
boot machine where as the MBR was created by SafeBoot.
(SafeBoot is a Windows encryption tool)
When SafeBoot is installed, it copies the old MBR to a secret
place and then installs its own MBR. This SafeBoot MBR must never
be changed by GRUB. WHen the machine boot up it loads
the SafeBoot MBR and then eventually loads that old MBR.
This machine was correctly working as a dual boot, but
I deleted the existing Linux partition (partition #3) cause I wanted
to re-install Linux with hard disk encryption.
Thus I have to be careful, cause that old MBR is a GRUB MBR
and it still wants to go to partition #3 to find the rest of GRUB.
And not only partition #3, but specifically the directory of
/boot/grub.

These notes are rather raw:
---begin of my notes ---

So this is what I have surmised about GRUB.

Machine is turned on.

the 1st 512 bytes, the MBR on the machine is loaded, 
   (446 bytes which represents a small SafeBoot binary and the rest is the partition table)

SafeBoot spits up it’s username/password screen.
User logs in.

SafeBoot then loads the old MBR that is squirreled away when SafeBoot was installed.

 (This old MBR, was created when Linux was installed on the machine a year ago, clobbering
the Windows MBR.)

This old MBR, the 1st 446 bytes is GRUB’s “stage1” binary plus the location of 
where it should find “stage2”.

At the time that Linux was installed a year ago, GRUB stage2 was found on partition #3
under the directory of /boot/grub.

When I most recently deleted your partition #3 and partition 4,(the SWAP partition),
and re-isntalled Linux on partition #3 (the non-encrypted version), the stage1 GRUB in the
old MBR could still find the stage2 GRUB on partition#3 under /boot/grub directory.
No problems.

But, when I tried to install the encrypted version of Linux, the install directs me to 
create a partition #3, that is just the /boot partition. Then directs me to create
the root “/” partition on partition #4.

At this point, GRUB stage1 could NOT find /boot/grub/stage2 on partition#3.

Why? Because when you create the “/boot” partition on partition#3, there is actually
no “/boot” directory. There is a “/grub” directory. If the machine was actually able
to boot into linux, that partition #3 would be mounted to “/boot” via the /etc/fstab file.

That is how it would “appear” that you have a “/boot” directory.

But at the time that GRUB is loaded there is no /etc/fstab file to do this mounting.

There is only a “/grub” directory.

So the solution is to edit the old MBR file, which we can’t cause
we don’t know where SafeBoot squirreled it away. We would just install grub to (hd0) and it
would re-install stage1 to the 1st 446 bytes and embed the location to find the stage2 to be 
at partition #3 in the shortened directory path of “/grub/stage2”.

That would probably work.

 

So what I needed to do was somehow mount the partition #3 via the Live CD,
create a /boot directory and move the entire directory root down one directory.

These are the steps:

 
 Boot up Live CD.

 In a terminal window:
 sudo /     # this root directory is the fake one while the Live CD is running
 sudo mkdir pig
 sudo mount -t ext3 /dev/sda3 /pig
 sudo cd /pig
 sudo mkdir boot  # this actually creates a directory on partition #3
 sudo mv grub boot
 sudo mv *all the other files* boot

Had to edit /boot/grub/menu.lst and preface all the paths with "/boot"
since they were not put in on the initial install. (which was correct at the time)

Without this edit, the kernel can’t be found.

So on reboot, i am faced with a "grub" command line,

rather than the grub menu.

 
The following loads the grub menu.

  `configfile (hd0,2)/boot/grub/menu.lst`

It puts up the grub menu, I choose the 1st entry, and Wow! it boots up the Linux.

 
I also had the problem of now having a “/boot/boot/grub directory”

once Linux was booted up.

To fix this:

Need to edit /etc/fstab and change line of :

   UUID=<ID>  /boot  ext3  relatime 0 2 
To:
   UUID=<ID>  /pig  ext3  relatime 0 2 

Then ran on command line: sudo ln -s /pig/boot /boot

Reboot.
(perfect)

So once Linux was running I ran the `strings` command against all the binaries in the /boot/grub menu.

$ sudo strings stage2 | grep menu
/grub/menu.lst
/menu.lst

So the binary stage2 had a hardcoded path of where to find the GRUB menu.

It should be /boot/grub/menu.lst. (/grub/menu.lst was correct at the time that I installed Linux)

So then I re-installed GRUB, to partition #3. (NOT partition 0, the MBR) by doing this:

boot up machine until it craps out with just the GRUB command line:

grub > find /boot/grub/stage2
grub > root (hd0,2)
grub > setup (hd0,2)
...

reboot.


Everything is running as it should.

---

