---
title: "Disc sometimes won't mount"
date: 2008-07-29
forum: General Help
---

### Post by pikaia on 2008-07-29
Hey everyone.

This one has me very baffled and quite a bit frustrated.  I thought it had gone away, but clearly I just haven't used it enough lately.  

So I upgraded to Hardy 64 a couple weeks ago, and since then my DVD drive fails to mount any disc *sometimes*.  I say sometimes because right after boot, if a disc is in the drive it'll show up.  After some indeterminate amount of time, everything will fail to mount, DVDs, CDs, data discs... everything.  The drive worked great in Gutsy and Feisty and works great on the XP side of my dual boot.  

My fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db4a997f-0e0e-453b-adff-6517e30ea5c7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bb1f9ae6-a236-4906-a25f-04cc96f2fdd0 none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec     0       0

This doesn't make sense to me, and I don't see a trend as in when it'll stop working.  Sometimes its between discs sometimes its after a couple minutes or hours of running.  

Any assistance is greatly appreciated.  Thanks.

---

### Post by caljohnsmith on 2008-07-29
After the DVD/CD fails to mount, check the end of the output of "dmesg" to see what errors it might give. That would probably give some idea of what is going on.

---

### Post by pikaia on 2008-08-03
Ok.  This is driving me out of my mind.  

I just burned a disc 15 minutes ago.  I just inserted another to copy it and now nothing.  So, I ran the dmesg and I get a long stream of this:

ut)
[ 1676.603439] ata3.00: status: { DRDY }
[ 1676.603451] ata3: soft resetting link
[ 1676.826959] ata3.00: configured for PIO0
[ 1676.826971] ata3: EH complete
[ 1690.447506] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1690.447517] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1690.447518]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1690.447519]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1690.447522] ata3.00: status: { DRDY }
[ 1690.447535] ata3: soft resetting link
[ 1690.671055] ata3.00: configured for PIO0
[ 1690.671063] ata3: EH complete
[ 1704.291603] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1704.291614] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1704.291615]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1704.291616]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1704.291619] ata3.00: status: { DRDY }
[ 1704.291632] ata3: soft resetting link
[ 1704.515155] ata3.00: configured for PIO0
[ 1704.515170] ata3: EH complete
[ 1704.515203] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00


I see the CDROM error at the end there, but I have no idea whats going on or how to fix that.  Any thoughts?

Again, it pops back up after a reboot and will work for sometime (varies).

---

### Post by pikaia on 2008-08-12
Does anyone know why my drive stops reading?  I'm going to try to swap the hardware, but if it works for 3 hours and then stops, I'm going to assume its not the drive.  (Not to mention there are no issues in XP).

Please, its an amazing pain to reboot whenever I want to burn something, or listen to a cd or watch a movie or whatever.

Thanks.

---

### Post by newagelink on 2008-08-12
[COLOR="Indigo"]Wish I had something helpful to say; I'm only a novice. It might help others here if you put your quotations in quote tags, though. (I think it makes it a bit easier to read.)

Hope things work out for you. I had considered upgrading, but then read an article from some network administrator who commented that "unless you have a reason to upgrade (some new feature, change, support, etc.), you typically shouldn't." So I'm gonna hang on to my 7.10 for a bit.[/COLOR]

---

### Post by mc4man on 2008-08-12
you may want want find out your motherboard and search specific to that. It may be you need to use a kernel parameter.
there are several that have varying success in instances similar to yours.

 > sudo lshw -html > hardware.html look in home for .html

>  ata3: soft resetting link......ata3.00: configured for [COLOR="Red"]PIO0[/COLOR]
......res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
.......ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Those are seen quite often when there is a hardware/kernel incompatibility of some sort, less often when just hardware (burner, positioning on ide, ide cable itself.(40 vs. 80 wire

Similar recent thread w/ similar errors
[http://ubuntuforums.org/showthread.php?t=870797](http://ubuntuforums.org/showthread.php?t=870797)

kernel parameter that worked in above for 2 setups - post 3
[http://ubuntuforums.org/showthread.php?t=863412](http://ubuntuforums.org/showthread.php?t=863412)

different hardware than above
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

Edit: when a drive is set to **pio0** your not doing much of anything with it

---

### Post by pikaia on 2008-08-17
Thanks for the insight, I'll look into it.  A cursory look seems like my issue is similar to the one you posted.  However, what I hadn't noticed (until now) is that I can't get any of my players to play CDs anymore.  It says 'Cannot read Audio CD' or 'Attempting to insert nothing into playlist'.  I can go into Amarok and change the engine setting to /dev/scd0 (from /dev/cdrom) and it'll fetch the songs after about a minute or so, but won't retrieve the names or location or any of the information.

So thats another issue I'm working through.  I'm going to try adding the noapic to my boot kernel, and cross my fingers, if it doesn't work, I'm seriously considering a reinstall... maybe PCLinuxOS or Mandriva.  I've had good luck with that.  Its just such a pain, and I don't want to be a quitter but this is really frustrating.

---

