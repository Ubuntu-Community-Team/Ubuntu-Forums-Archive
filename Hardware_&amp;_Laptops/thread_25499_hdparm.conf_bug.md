---
title: "hdparm.conf bug?"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by brickbat on 2005-04-10
I made the following addition to my etc/hdparm.conf file.  I changed nothing else.

/dev/hdd {
	dma = on
}


/dev/hdc {
	dma = on
}

It worked once and then it hangs during subsequent boots.  If I reverse them, then it works once and hangs on reboot.

I also moved the S07hdparm file to S99hdparm so that it would make the changes after the CDROMS were recognised.  When it did work I checked the settings in the shell and they were changed.  When it doesn't, I have to reboot with the nohdparm kernel option and then, obviously it has not changed.

It has had me stumped for days.

ciao
bb

---

### Post by Leif on 2005-04-10
I don't mean to sound like an idiot, but are you sure that your hardware supports dma ? If you try to set dma after boot, does it work ?

---

### Post by brickbat on 2005-04-10
Thanks for the question.  You don't sound like an idiot.  In XP I can set DMA on for both drives.  Also, they work when I set them manually and it makes a huge difference to read/write performance.

ciao
bb

---

### Post by Leif on 2005-04-10
That is weird. I have no idea why it shouldn't work, my conf file looks just like yours. Maybe you could try putting the commands in another init file, this way your boot may be still slow but your session wouldn't. I'm a newb tho so I don't know which files would not require root privileges.

---

### Post by sylware on 2005-04-13
There are 2 commons issues with DMA on DVD/CD drives:



[list=1]
[*]DMA is disabled by default on ALL DVD/CD drives. Why? Because they are too many drives out there which do not work properly with DMA enabled. This is a matter that there is too much crappy hardware out there[-X. So it is ON PURPOSE that DMA is disabled.
[*]If you want to enable it, using debian sarge based ubuntu, you have to do it in /etc/hdparm.conf file... but one common issue is /etc/hdparm.conf run too early in the initialization process: for example your DVD/CD drive is /dev/hdc... well this */dev/hdc* may not be yet created when /etc/hdparm.conf is run. Usually, you can detect this at boot time when hdparm.conf is run, you can see on the screen an error message related to a "not found node". The direct solution is to delay the execution of /etc/hdparm.con later in the boot process using the init scripts.
[/list]

---

### Post by brickbat on 2005-04-14
Hi, I moved the hdparm to position 99 so that it would see the drives.  I ran xp before and dma worked flawlessly for over a year.  dma also works flawlessly in ubunto but only when i set it manually.

it is only when i add those lines to hdparm.conf that it stalls.

ciao
bb

---

### Post by Miggy on 2005-04-14
After following those instructions of writing all the hdparm stuff to /etc/hdparm.conf and moving S07hdparm to S99hdparm I had a similar strange behaviour.
The first time it booted correctly. The next time the boot process hung after "loading modules" until the message "hda: timeout waiting for dma" appeared. This error appeared in every subsequent boot process. 

My workaround now is, that I have two scripts: S07hdparm thats linked to /etc/init.d/hdparm and S99hdparm that's linked to  /etc/init.d/hdparm2.
/etc/init.d/hdparm2 is a copy of hdparm where I replaced the occurence of /etc/hdparm.conf with /etc/hdparm2.conf.
Finally /etc/hdparm.conf is the original file without any changes
while all the hdparm-commands are now in /etc/hdparm2.conf

Since i made this workaround I haven't encountered a problem anymore!
Perhaps this can help someone having the same problem as I had.

---

### Post by brickbat on 2005-04-15
Thanks Miggy. It worked.  I am intrigued about how you discovered this.

ciao
bb

---

