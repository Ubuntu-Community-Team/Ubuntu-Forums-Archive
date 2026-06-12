---
title: "Please help...ubuntu newbie and system won't boot"
date: 2008-08-22
forum: General Help
---

### Post by scott29 on 2008-08-22
Hi,

I have Ubuntu 8.04 Server installed and all was well until my power went out and I rebooted my machine.

I am getting a slew of errors on start up and my system just stops and I cannot start.  I really don't want to re-install as I have websites set up and since I am a newbie it took me FOREVER to get everything working.

Here are the two errors that have a [FAIL] message by them.  Can someone instruct me how to possibly fix this?

-Configuring network interfaces.../etc/rcS.d/S45waitnfs.sh:  106:  /lib/init/mountall-net-fs:  not found.:  11:  Can't open /lib/init/vars.sh

- Starting the Firestarter firewall...
mkdir:  cannot create directory '/var/run/screen':  Read-only file system
chown:  changing ownership of '/tmp/.X11-unix':  Read-only file system
.: 14: Can't open /lib/init/vars.sh
.: 19: Can't open /lib/init/vars.sh
init:  rc-default main process (3989) terminated with status 127


Remember, I am a newbie so any instructions will have to be very clear!!  :)

Thank you so much in advance.

Scott29

---

### Post by Alaric on 2008-08-22
If you can get to a GRUB boot menu, try logging in under "recovery mode".  From there, try to give us some more information on your system by posting the results of running "cat /etc/fstab" (without quotes).  

Alternately, try using an Ubuntu desktop install disc to mount your hard drive as read only and list us this file.

---

### Post by scott29 on 2008-08-22
I picked "Ubuntu 8.04.1, kernel 2.6.24.19-server (recovery mode)" and went to the grub> command line.  

However when I enter 'parted' is says command not found.  I did a 'tab' to see valid commands and that is not listed.  The closest I see is partnew and parttype.

---

### Post by Alaric on 2008-08-22
I mean a command line inside of recovery mode.  So press enter on the "Ubuntu 8.04.1, kernel 2.6.24.19-server (recovery mode)" option, boot into linux to get a normal command line (or terminal) screen.  Try fsck there, and if that doesn't work, post the error messages here.

---

### Post by scott29 on 2008-08-22
I'm sorry but that does nothing...I hit enter on that recovery mode option, and it goes through a bunch of stuff and then encounters those same fail messages.  It simply stops with a blinking cursor and it does nothing.  I can't do anything it this point and the system just sits there.

I said I'm new to this so if I am not doing something correct let me know.  Otherwise, this error is so bad I can't even boot into a command line.

---

### Post by scott29 on 2008-08-22
If it helps, I have Gnome installed so typically it would go to the Gnome desktop after it gets to the login screen.  However, as I said, all I end up with is a flashing cursor below "init:  rc-default main process (4169) terminated with status 127"

Thanks
Scott29

---

### Post by Alaric on 2008-08-22
Alright, try downloading the ubuntu desktop install CD/live CD.  This is a linux distribution on a CD, so burn it and restart the computer with it inside.  From there, try running the commands I mentioned earlier.  

Btw, you'll probably need to run something more like fsck /dev/sda1 or fsck /dev/hda1 (I think you should be able to get the device location from the file /etc/fstab if you don't know what it is).  adding /dev/sda1 (or whatever your device location is) tells ubuntu to check the hard drive for errors, instead of the CD.  

Good luck :)

---

### Post by colobix on 2008-08-22
Related question:
Which command do u run from a live CD to fix your Ubuntu? If that is possible offcourse.

---

### Post by scott29 on 2008-08-22
OK sorry...I had the original 8.04 Server ISO image on the disk and I thought this is what you referred to.  I am DL'ing the desktop live cd now and will run those commands and post back.

It seems to me that there is some process that is trying to start up or something...Can anybody tell from the errors what may be happening?

Thanks for your help.

-Scott29

---

### Post by Alaric on 2008-08-22
Much easier than checking /etc/fstab, try running 'sudo blkid' and look for the line that has TYPE='ext3' at the end to find the device location (the /dev/sda1 looking thing).  From there run 'sudo fsck /dev/sda1' (or whatever device location you got from blkid).  If that responds with an error, post back here.

---

### Post by Alaric on 2008-08-22
Scott, it looks like firestarter (your firewall) is trying to start in the background, but judging by the fact that your /tmp and /var directories are read only, I'm guessing you have bigger problems... On top of that, it looks like you're missing one or two crucial system files...  Although it's always possible that I'm completely wrong, I've only been using Linux for a couple of years, and I'm only a user like you.

---

### Post by Alaric on 2008-08-22
You may also be interested in [this]("http://ubuntuforums.org/showthread.php?t=763265")

It looks like you might be able to get a login console, despite that error, by switching to another virtual terminal (ctrl+alt+f2 [ctrl+alt+f1 to get back]).

---

### Post by scott29 on 2008-08-22
Running fsck didn't seem to give any error.  I tried all of the things in the other post and nothing.  There has to be a way to fix this...

Is there a way I can somehow prevent the firewall from starting during boot?  Perhaps that is causing it to fail.

---

### Post by scott29 on 2008-08-22
results from cat /etc/fstab:

unionfs /unionfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by Alaric on 2008-08-23
Alright, here's some new approaches.  First off, try this.  Maybe the verbose mode will provide some information
```

sudo fsck -pyv hda1
```

If that only returns something along the lines of
```

fsck 1.40.8 (13-Mar-2007)
e2fsck 1.40.8 (13-Mar-2007)
/dev/sdd5: clean, 178041/3096576 files, 4137652/12357993 blocks

```

Then try run this from the Live/Install CD
```

sudo chroot /media/disk
sudo aptitude reinstall initscripts
```

If that errors out then try (in the same terminal, or at least one that has run the chroot command above)
```

sudo aptitude install initscripts

```

If that still errors out, then run this again (this will give me the version from your Hard drive instead of the LiveCD/install disc, as long as you run it from a chroot'd terminal)
```
cat /etc/fstab
```

Good luck!

---

