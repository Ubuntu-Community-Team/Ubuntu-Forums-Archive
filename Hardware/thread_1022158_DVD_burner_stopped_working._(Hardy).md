---
title: "DVD burner stopped working. (Hardy)"
date: 2008-12-26
forum: Hardware
---

### Post by Vryko Lakas on 2008-12-26
Hey guys. I've had an SATA DVD/CD burner die on me before just as I was upgrading from Gutsy to Hardy. The replacement I installed worked fine, until yesterday. 
After successfully burning an audio CD with Brasero, I opened the tray and took the disk out. I pressed the button to close the drive tray, but it wouldn't close, so I gently nudged it until the bay started closing on its own. Then, as I tried to exit Brasero, the program hung up and I did a force quit. 
A little later, I tried to insert an original audio CD so I could rip some tracks to put on a new MP3 player (my Christmas present to somebody), but the disk icon never appeared on the desktop and no program tried to play it. I tried with several other CDs, and still no dice, even after a complete system shutdown and boot up. 


Is there a way to check and see if my drive is toast, or just hung-up somehow? If the drive is actually kaput, any idea why they keep dying on me after only a few months?

---

### Post by Vryko Lakas on 2008-12-27
On someone's advice, I ran cdparanoia from the terminal with -vsQ flags. Here's what it returned:


```
***@family-desktop:~$ cdparanoia -vsQ
cdparanoia III release 10pre0 (August 29, 2006)
(C) 2006 Monty <monty@xiph.org> and Xiph.Org

FreeBSD porting (c) 2003
	Simon 'corecode' Schubert <corecode@corecode.ath.cx>

Report bugs to paranoia@xiph.org
http://www.xiph.org/paranoia/

Checking /dev/cdrom for cdrom...
	Could not stat /dev/cdrom: No such file or directory

Checking /dev/cdroms/cdrom0 for cdrom...
	Could not stat /dev/cdroms/cdrom0: No such file or directory

Checking /dev/cdroms/cdroma for cdrom...
	Could not stat /dev/cdroms/cdroma: No such file or directory

Checking /dev/cdroms/cdrom1 for cdrom...
	Could not stat /dev/cdroms/cdrom1: No such file or directory

Checking /dev/cdroms/cdromb for cdrom...
	Could not stat /dev/cdroms/cdromb: No such file or directory

Checking /dev/cdroms/cdrom2 for cdrom...
	Could not stat /dev/cdroms/cdrom2: No such file or directory

Checking /dev/cdroms/cdromc for cdrom...
	Could not stat /dev/cdroms/cdromc: No such file or directory

Checking /dev/cdroms/cdrom3 for cdrom...
	Could not stat /dev/cdroms/cdrom3: No such file or directory

Checking /dev/cdroms/cdromd for cdrom...
	Could not stat /dev/cdroms/cdromd: No such file or directory

Checking /dev/hd0 for cdrom...
	Could not stat /dev/hd0: No such file or directory

Checking /dev/hda for cdrom...
	Could not stat /dev/hda: No such file or directory

Checking /dev/hd1 for cdrom...
	Could not stat /dev/hd1: No such file or directory

Checking /dev/hdb for cdrom...
	Could not stat /dev/hdb: No such file or directory

Checking /dev/hd2 for cdrom...
	Could not stat /dev/hd2: No such file or directory

Checking /dev/hdc for cdrom...
	Could not stat /dev/hdc: No such file or directory

Checking /dev/hd3 for cdrom...
	Could not stat /dev/hd3: No such file or directory

Checking /dev/hdd for cdrom...
	Could not stat /dev/hdd: No such file or directory

Checking /dev/sg0 for cdrom...
	Testing /dev/sg0 for SCSI/MMC interface
		Could not access device 134578576 to test for SG_IO support: Permission denied
		no SG_IO support for device: /dev/sg0
		Could not access device /dev/sg0: Permission denied
		generic device: /dev/sg0
		ioctl device: not found
		Could not open generic SCSI device /dev/sg0: Permission denied
	Testing /dev/sg0 for cooked ioctl() interface
		/dev/sg0 is not a cooked ioctl CDROM.

Checking /dev/sga for cdrom...
	Could not stat /dev/sga: No such file or directory

Checking /dev/sg1 for cdrom...
	Testing /dev/sg1 for SCSI/MMC interface
		Could not access device 134578576 to test for SG_IO support: Permission denied
		no SG_IO support for device: /dev/sg1
		Could not access device /dev/sg1: Permission denied
		generic device: /dev/sg1
		ioctl device: not found
		Could not open generic SCSI device /dev/sg1: Permission denied
	Testing /dev/sg1 for cooked ioctl() interface
		/dev/sg1 is not a cooked ioctl CDROM.

Checking /dev/sgb for cdrom...
	Could not stat /dev/sgb: No such file or directory

Checking /dev/sg2 for cdrom...
	Could not stat /dev/sg2: No such file or directory

Checking /dev/sgc for cdrom...
	Could not stat /dev/sgc: No such file or directory

Checking /dev/sg3 for cdrom...
	Could not stat /dev/sg3: No such file or directory

Checking /dev/sgd for cdrom...
	Could not stat /dev/sgd: No such file or directory

Checking /dev/cdu31a for cdrom...
	Could not stat /dev/cdu31a: No such file or directory

Checking /dev/cdu535 for cdrom...
	Could not stat /dev/cdu535: No such file or directory

Checking /dev/sbpcd for cdrom...
	Could not stat /dev/sbpcd: No such file or directory

Checking /dev/sbpcd0 for cdrom...
	Could not stat /dev/sbpcd0: No such file or directory

Checking /dev/sbpcda for cdrom...
	Could not stat /dev/sbpcda: No such file or directory

Checking /dev/sbpcd1 for cdrom...
	Could not stat /dev/sbpcd1: No such file or directory

Checking /dev/sbpcdb for cdrom...
	Could not stat /dev/sbpcdb: No such file or directory

Checking /dev/sbpcd2 for cdrom...
	Could not stat /dev/sbpcd2: No such file or directory

Checking /dev/sbpcdc for cdrom...
	Could not stat /dev/sbpcdc: No such file or directory

Checking /dev/sbpcd3 for cdrom...
	Could not stat /dev/sbpcd3: No such file or directory

Checking /dev/sbpcdd for cdrom...
	Could not stat /dev/sbpcdd: No such file or directory

Checking /dev/sonycd for cdrom...
	Could not stat /dev/sonycd: No such file or directory

Checking /dev/mcd for cdrom...
	Could not stat /dev/mcd: No such file or directory

Checking /dev/sjcd for cdrom...
	Could not stat /dev/sjcd: No such file or directory

Checking /dev/cm206cd for cdrom...
	Could not stat /dev/cm206cd: No such file or directory

Checking /dev/gscd for cdrom...
	Could not stat /dev/gscd: No such file or directory

Checking /dev/optcd for cdrom...
	Could not stat /dev/optcd: No such file or directory



No cdrom drives accessible to *** found.

***@family-desktop:~$ 
```

Given that this happened after a successful rip and burn, am I right to think that this means the drive itself is toast?

---

### Post by mgmiller on 2008-12-27
I just tried this in my system to see what it would do.  The clue was the "access denied" statement.  Run the command preceded by sudo:
```
sudo cdparanoia -vsQ
```

You can also try the command with a disk in the drive.

---

### Post by Vryko Lakas on 2008-12-27
Thanks for the reply! 

Using sudo returned the same thing, except no drives were accessible to root either.

---

### Post by mgmiller on 2008-12-27
That may be significant.  In mine, if I ran it as user, it did see something a lot like yours, but access was denied, so it couldn't do anything with it.  Once I ran it as sudo, it was able to probe the drive and give me info on it.  Since yours stayed non accessible, I suspect it may be fried.

The big question now is why are you frying optical drives?

---

### Post by Vryko Lakas on 2008-12-27
Mmmyes, I'd like to know that myself. I know they have a tendency to wear out, but this one has only seen light use since I installed it a few months ago. Could just be the luck of the draw? First one was a Samsung, this one is a Panasonic. 
I don't know if it's some kind of power spike, but my PSU is supposed to be one of the more reliable models. None of the drive failures were associated with any kind of house-wide power flicker.

---

### Post by mgmiller on 2008-12-27
I think the last thing I would try would be powering down the computer and unplugging the power cable to the optical drive for a minute or so.  
While it's unplugged, try reseating the data cable at both the drive and mobo ends.
Then plug the power cable back in and boot with a Live CD.  If the drive is still not working......

Since nothing else in the machine died, and  you didn't see any power spikes, it could just be the luck of the draw.  

You should consider running a UPS to avoid power spikes anyway.


Sigh... It's always something....](*,)

---

