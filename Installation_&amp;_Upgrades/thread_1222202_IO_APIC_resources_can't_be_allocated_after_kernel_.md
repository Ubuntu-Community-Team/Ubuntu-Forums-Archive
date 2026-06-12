---
title: "IO APIC resources can't be allocated after kernel upgrade"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by pgibson on 2009-07-24
[INDENT]Long post trying to provide all the details ... (Moderator, please move this if it would be better located elsewhere).[/INDENT]

**The problem thus far:**

[INDENT]The short version is that something went amiss during huge the-computer-has-been-off-for-months upgrade, which included a kernel upgrade from 2.6.28-11 to 2.6.28-13.

The system in question is running Ubuntu 9.04 with an XFCE desktop, on our old Micron PIII.

Grub comes up, the new kernel is listed there, choose it and ...

The Jaunty-Cylon-eye splash screen comes on and then disappears and drops into a shell after 5 or ten seconds.  The resulting text, (which I've transcribed by hand, as I cannot figure out how to copy it or print it or what-have-you) says:[/INDENT]

```
Boot from (hd0,2) ext3 a21c4ab7-e6ee-44c3-8afe-44bef9723ee6

Starting up ...

[       4.050772] IO APIC resources could not be allocated.
Loading, please wait ...
udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device. Common problems:
	-Boot args (cat /proc/modules; ls /dev)
		-Check rootdelay= (did the system wait for the right device?)
		-Missing modules (cat /proc/modules; ls /dev?)

ALERT! /dev/disk/by-uuid a21c4ab7-e6ee-44c3-8afe-44bef9723ee6 does not exist, Dropping to shell.

Busybox v1.10.2 (Ubuntu 1:10.2-2 ubuntu 7) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)
```


**My (valiant and failed) efforts to fix this, thus far:**

[INDENT]I typed "help," read the resulting list of commands, but really didn't see anything that I recognized as helpful (but, I didn't recognize much).

I followed some prompts and fsck stuff, and (being naive and trusting and lucky) I have managed to boot the prior kernel 2.6.28-11.  The resulting desktop was mostly functional, though couldn't connect to the internet.  And this was only to see what was there.  I may have made things worse, I don't know.  

However, poking around I found files in the /home directory I don't remember seeing before, such as vmlinuz.new vmlinuz.old ... ah HA!  I don't really know if it's significant but ah HA! all the same.[/INDENT]


**A few other (possibly useful) facts and details:**

[INDENT]/dev/sda1 is winXP
/dev/sda2 is /home ext3
/dev/sda3 is /     ext3

I think the technical term is "borked."  I've borked the downstairs desktop computer, because I was rushing to do other things, the warning of which I didn't pay close enough attention to now remember.  Oops.  

The pop-up told me there was some sort of problem asked if I wanted to quit, so I clicked that then clicked to close Synaptic, which subsequently hung, for like a minute or two.  I was rushing and simply clicked the "leave" button, and chose "shut-down."  Boop. No problem ... Until I went to start it back up.[/INDENT]

My deepest appreciation in advance,
:)

---

### Post by Rocket2DMn on 2009-07-24
It looks like it doesn't see the HD, at least by its UUID.  If the computer booted when you first turned it on after pulling it out of storage (or whatever), I expect the disk is still OK.  Did you fiddle with partitions at all?

Try booting from a LiveCD, and seeing if the drive is detected there.  A simple
```
sudo fdisk -l
```
will show you the drives and partitions on the machine.  You can run
```
sudo blkid
```
to see the UUIDs for each partition.  If the drive is there, then grub probably just needs to be updated, assuming that the only cause of your problem is that the UUID of the partition changed.  Post the output of those commands above from the LiveCD.  Then I can help you fix grub on the hard drive by mounting it and editing the grub configuration file.

---

### Post by pgibson on 2009-07-24
Thanks for the response Rocket :)

Here's the info from fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50c0b2fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2043    16410366    7  HPFS/NTFS
/dev/sda2            2044        3406    10948297+  83  Linux
/dev/sda3            3407        4743    10739452+  83  Linux
/dev/sda4            4744        4865      979965   82  Linux swap / Solaris
```

and from blkid: 

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2800B68F00B6640A" LABEL="MICRON" TYPE="ntfs" 
/dev/sda2: UUID="dd4567b4-d1e8-46b9-86db-638fe5f0e6d6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="a21c4ab7-e6ee-44c3-8afe-44bef9723ee6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="c5cc958c-eddf-4d91-a73f-63c1ba886f3c" TYPE="swap" 
/dev/ramzswap0: TYPE="swap"
```

Looking forward to the learning to be had in figuring this out.

Thanks :)

---

### Post by Rocket2DMn on 2009-07-24
Well actually it looks like it's OK, the UUID hasn't changed and maps to /dev/sda3 which is your root partition and matches (hd0,2).

Are you able to boot into the older kernel?  Perhaps we need to fiddle with your kernel boot options.  For whatever reason, the newer kernel may not be properly detecting your hardware, though I've never seen a regression quite like that.  Perhaps the disk isn't responding fast enough?  We could try adding a "rootdelay=<#sec>" option to the kernel boot line.

---

### Post by pgibson on 2009-07-25
Your response sent me scurrying to learn a bit about [grub]("https://help.ubuntu.com/community/GrubHowto") and kernel boot options.  And running up and down the stairs then made me crazy enough to find out how to use ssh to get to my hard drive via the live cd --- thanks for that inspiration).

Would the grub/menu.lst be useful here[SIZE="3"][/SIZE]?

To answer your questions:

> Are you able to boot into the older kernel? 
I am now. That was one of the first things I tried.  Initially it wouldn't.  I don't remember details, but I had to do a "manual" something-or-other, where something was missing or corrupt and should I fix it?  I said "yes."  (This is why I said I may have made things worse, in my original post).

> Perhaps we need to fiddle with your kernel boot options. For whatever reason, the newer kernel may not be properly detecting your hardware, though I've never seen a regression quite like that. Perhaps the disk isn't responding fast enough? We could try adding a "rootdelay=<#sec>" option to the kernel boot line.

I've read about doing this by choosing "e" when the initial grub menu comes up, and in so doing the change is simply for that boot, as a means of testing things.  Let me know what you'd like me to try.

Break it, fix it, learn. :)

---

### Post by Rocket2DMn on 2009-07-25
Editing the kernel boot line at bootup is a good way to test - see [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
If you are able to boot into the older kernel, it may be worth it to just remove the new kernel and try to reinstall it, esp. given your comment about having to fix something to get into the older kernel after your upgrade.

If you want to do a quick test though, try booting into the new kernel with the following additional options.  Also remove "quiet" and "splash" so you can better see what is happening.
```
noapic nolapic acpi=off rootdelay=10
```
If it does boot, you may not have full hardware or power configuration support, but it would be interesting to see nonetheless (since you seem enthusiastic about this).  Also, if it does boot, you can try different combinations of the above options to see which one(s) actually allow you in, and which don't matter.

If you want to read a bit more about boot options, I keep this pdf handy, though some options may have been added/removed since it was published - [www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf](www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf)

To remove a kernel, open Synaptic and search for "linux-image".  Find the one you are looking for (e.g. linux-image-2.6.28-13-generic), right click and "Mark for complete removal".  I believe 2.6.28-11 and 2.6.28-13 are the only available ones in Ubuntu Jaunty.  You can then try to upgrade again and see what happens.  If you have any data on the system that is important to you, I would back it first though, it's always better to play it safe.

---

### Post by pgibson on 2009-07-28
**Whew!**  
I've learned a ton by trying to understand what I'm doing, which is ironic because in the end I've no idea what went wrong. I did, however, get the computer wroking again, and that's enough for now.  

**Symantec, windows managers, and gremlins ... oh my!**
When I ran symantec, it threw out an error, told me to run "sudo dpkg -a" and I did and restarted and then the windows manager in xfce crashed, so I restarted into gnome, and the windows had no frames and couldn't be moved.  Grrr.  However, symantec ran fine from its immobile, beige rectangle in the center of the screen.  I was able to remove the 2.6.28-13 kernel.  Tinker tinker tinker tinker and now I have metacity mostly back to being the compositor (compiz never liked my old Nvidia legacy card ... it has gremlins).

Editing the kernel got me nowhere.  Thanks for the .pdf, though.  It was a bit beyond my ken, but nevertheless did a lot to improve my feel for what I was dealing with.
 
After using symantec to remove 2.6.28-13, I restarted the computer and told it to check for updates.  It installed 2.6.28-14.  Okay, cool as far as I can tell, but left 2.6.28-11 the default in grub.  HA!  Gremlins!

**Marching onward**
It seems to work though.  I'll use what I've learned in this experience to edit the kernel line in grub so it'll boot the 2.6.28-14 kernel.  Again. Yay!

This has been my first problem-solving session and it's time to get some new threads going about some other quirks and probs I'm looking forward to tackling.

Thanks for all your help.

---

### Post by Rocket2DMn on 2009-07-28
Cool, glad you got it working.  BTW, the package manager is Synaptic, not symantec.  Symantec makes virus scanners for Windows, which isn't a problem for us :).

The command you needed to run was
```
sudo dpkg --configure -a
```
It gave you that message because apparently a package manager didn't shut down correctly beforehand, which requires that command to be run before it will let you back in.

Cheers.

---

### Post by pgibson on 2009-07-29
Eek!  Yes, synaptic, as in the gap between neurons.  Apparently a very large gap in my case.  HA!

And yes, bonus points on your karma!  "sudo dpkg --configure -a" was the full line I had to type in!  

Hmm.  Given the size of my own synaptic memory gap, I should probably get to work on doing back up sooner rather than later.  Speaking of which, I've gotta start a thread about my external USB drive ... though maybe since I can do (break) everything in the house over rsync, I'll make it an internal... well, not right now.  Right now I have to go work on rebuilding an outbuilding on my property.

Yep.  Gremlins.

Thanks again Rocket!

---

