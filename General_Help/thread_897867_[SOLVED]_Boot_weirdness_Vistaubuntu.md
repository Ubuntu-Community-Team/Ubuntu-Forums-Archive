---
title: "[SOLVED] Boot weirdness Vista/ubuntu"
date: 2008-08-22
forum: General Help
---

### Post by medfojo on 2008-08-22
History: Vista was initially installed on this machine, I then installed ubuntu and repartitioned the drive with the ubuntu install wizard.  I now have both vista and ubuntu successfully running on my machine.

However, in order to boot to ubuntu I must hit F10 (which is the command for getting the boot screen).  F10 will give me a list of drives to boot from.  I then select my drive that has vista/ubuntu.  Now I am faced with the option of starting ubuntu (default) or vista.  Selecting ubuntu works perfectly.

If I do not hit F10 vista loads without asking me which OS I want to boot.  This is lame because I want ubuntu to be my default OS.

This tells me that the windows boot manager does not know that ubuntu exists, and somehow hitting F10 lets GRUB(maybe? I'm a n00b) take over where I can boot ubuntu.  Ok, so what I did next is installed EasyBCD on Vista so that I can tell the windows boot manager that ubuntu is there.  I add the entry for linux, tell it what drive/partition it is istalled to, give the obvious name of "ubuntu", save, reboot.

Ok, now the windows boot manager knows that ubuntu is there and now gives me the option of starting vista or ubuntu.  I choose ubuntu and:

[I]Booting 'Ubuntu 8.0.4.1 Kernel 2.6.24-19-Generic'

root(hd1,4)

Error 27: no such partition[/I]

I'm not the brightest guy in the world, but I thought ubuntu root was installed to (hd0, 1) which I would think is hard drive 0, partition 1.  I don't know.  

Before I posted this I spent 2 days on this forum reading similar issues, but I never found a single post that was exactly like my situation.  So here is my post.  Can any of you good people help me get to where I want to be: _ubuntu as my default OS_.

Thanks ahead of time.

---

### Post by Alaric on 2008-08-22
Boot in with your ubuntu desktop install disc/livecd.  From there, run 'cat /etc/fstab' and send us back the details. 

Alternately, if you can figure out which line looks like your hard drive (which is most likely formatted in ext3) look for the part that says the hard drive's device location (a.k.a. the thing under the "file system" header); it should look something like /dev/sda3.  Then run the command sudo grub-install /dev/sda3 (or whatever your device was).  That should install the linux bootloader and auto-configure it to boot Ubuntu first, while still giving you the option of Windows.  If you still have the "press f10" message, then it's most likely a problem with your BIOS, and we'll go from there.  If you have any errors, or you can decide which one looks like your linux install partition, post back here.

---

### Post by medfojo on 2008-08-22
Thanks for the reply, but you may be under some misconceptions.  First, I can boot into ubuntu, so why should I use the live cd?.  Second, It's not a "press F10" message, I have to press F10 (which is the boot menu command for my bios), select the drive with vista/ubuntu installed (which gives me the linux boot manager as opposed to the windoes boot manager), then select the OS I want in order to boot ubuntu.  Otherwise (no F10 interaction) it boots to vista without giving me an option.

I'm sorry this is probably confusing to read, but this is a fairly complicated issue to explain.

Does any of this change the instructions you gave me?

Here is the results of 'cat /etc/fstab' (however running from installed ubuntu, not livecd)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=adce3550-603e-4535-a103-14af959361f2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=63a32ce4-7010-4aee-863e-911f4a3f83f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mb_webguy on 2008-08-22
Do you have multiple drives on your computer?  If so, check your BIOS settings for the boot sequence.  It could be that your "primary" HD with the bootloader is not the first disk in the boot order.

---

### Post by medfojo on 2008-08-22
mb_webguy, thanks!  you are the dude!  I'm kinda upset that the solution was so simple though, what with all the aggrivation I've suffered...and the fact that I didn't think of that.  Again, thanks a zillion.

---

