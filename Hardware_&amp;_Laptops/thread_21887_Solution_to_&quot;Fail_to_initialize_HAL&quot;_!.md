---
title: "Solution to &quot;Fail to initialize HAL&quot; !"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by Linowin on 2005-03-24
Hi everyone, 

            Ubuntu is far the best distrib i tryed. Somehow i noticed a great bug. When i Tryed it for the first Time with LiveCD, all was ok. Then i Installed it and i got at boot : "FAIL to initialize HAL" wich meant no USB key nor CDROM operationnal, wich is quite annoying.

            Then by luck, i left a CD audio at reboot inside the CDROM reader. When the system loaded, i noticed that the message has gone and that i could access to USB Key and CDROM.

             In conclusion, HAL is clearly still buggy ! but you can make your temporarly make it work by having a CD inserted at boot.

Please if any programmer are looking at it, solve this issue for the final version :)
You are doing a great JOB CONTINUE !!!!

Just in case, I have a MEDION 40653 Laptop, AMD Mobile 64bits 3000+, Chipset VIA, Radeon 9600, HDD 60 Go 7200 rpm

---

### Post by alastair on 2005-03-24
Maybe the system logs provide some information? This is quite strange. Check :

/var/log/syslog

Both for a non-working boot (HAL problem) and compare to the working (with CD) logs.

Also, worth researching the problem (error message) and seeing if others have a similar problem.

---

### Post by Linowin on 2005-03-24
I ll try to post tomorow a log with the two differents boot 

See ya and thanks for your help

---

### Post by kagou on 2005-03-25
Linowin please contact me, i have the same notebook
kagou at kagou.org (for information i'm french)

I added "hdc=noprobe hdc=cdrom" to grub. All is ok except that i can't have DMA access to the cdrom/dvd.

---

### Post by marsopia on 2005-06-01
The same was happenning to me. I have a new, clean Hoary final installation. I was recieving the Hal error advice since a couple of weeks. I thougt It was due to an update. 
This didnt happen always, I could not realize when it would happen, and I  realize now that was when I had a CD on my CDR/DVD (this is hdd; hdc is a CDR, hdc is bootable).

I can actually boot and ñpg on kde, but not un gnome, unless I log as root on recovery mode, and then choose my username on gdm.

Reading this thread I realized that I had a music cd on my cdr/dvd drive, I just removed it and logged w/o problems.

How can this bug be fixed?

Mariano

---

### Post by saintpa on 2005-06-03
I have the same problem with gnome: "Fail to initilize HAL." Sometimes it is solved by rebooting 2-3 times. I just tried the method with a cd in the dvd burner, and I got in to gnome with no problem. I hope this gets fixed soon.

---

### Post by Efwis on 2005-06-03
I have had hoary for a while now, today I had to reinstall it becasue Gnome failed to start properly. Now everytime I start without a cd in one of my drives I get the error "fail to initialize HAL"

This was not an issue until today! is any one looking into this. It seems as though no one is interested in it. 

HELP ME PLEASE

l

---

### Post by BKonkle on 2005-06-06
I've been having a problem with this too, and I'm currently searching for a solution.  Here is a workaround for the time being.  I am doing this without any CDs in my drives whatsoever.  When I get the "Failed to Initialize HAL" message, I hit CTRL+ALT+F1 to get to a login terminal.  I login using my normal username and password, and then enter the following code.

```
sudo killall gdm
```

This will produce no output at all.  Then I type:

```
sudo gdm
```

This will restart the Gnome Desktop Manager.  I have found that the "/etc/init.d/gdm restart" command does NOT work, but this workaround does.  Sometimes I have to do this two or three times before it will work, but it's much faster than rebooting two or three times.

Hope this helps!

---

### Post by ktogias on 2005-06-06
There is also an other thread about the described problem, that may help:
[http://ubuntuforums.org/showthread.php?t=28805](http://ubuntuforums.org/showthread.php?t=28805)

---

### Post by thoffland on 2005-06-25
Actually, I either messed with my config too much or this fix didn't work for me. I've been trying to customize everything to get it how I like it (i'm picky) and I couldn't even boot without getting an error. I fixed it (I think) yesterday by re-configuring the xorg.conf file. 

/etc/X11/xorg.conf

# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Maybe this will help some of you too.

NOTE: THIS WILL UNDO CHANGES YOU MIGHT HAVE MADE TO YOUR XORG.CONF FILE.

---

### Post by mseddon on 2005-07-30
[QUOTE=ktogias]There is also an other thread about the described problem, that may help:
[http://ubuntuforums.org/showthread.php?t=28805](http://ubuntuforums.org/showthread.php?t=28805)[/QUOTE]
 I have a similar problem, at present the way I "fix" it is to run

/etc/init.d/dbus-1 start

which starts hal. It seems that this init script doesnt run at boot so when the user logs in hal isnt running (see $HOME/.xsession-errors for error messages). Dont understand why though

---

### Post by Juzz on 2005-08-25
I also just started getting this error - so I thought back on what I have done...

I have enabled dma on my CD/DVD drives - but I also remember doing an upgrade on DBUS... Just rambling on the previous notes from others...

But hope it can help enlighten things.

---

### Post by nicolas314 on 2005-08-28
I am experiencing the same seemingly random start failure from hal here.
What I could gather so far was:

I have a number of hard drives in the box. Since I am never using all of them
together and they can get quite noisy, I set a short spindown time with hdparm,
around 3 minutes or so. Now if I log into gdm immediately after the machine
has booted I do not get hal failures. But if I let gdm run more than 3 minutes
unattended before logging in, the hard drives spin down and that seems to
disturb hal enough to fail starting. After that the machine is a complete mess,
seems easier to reboot than try to fix things by hand.

Seems to me like a timeout issue. Could be that the same is happening with
various USB devices failing to respond within the allocated time. Anyway...

My 2c on the topic. Would be nice to get that fixed, it is definitely annoying.

---

### Post by OpposingForce on 2005-08-28
Actually its the opposite for me...I get the bug whenever I LEAVE a cd in the reader...sometimes I do and sometimes I dont...

---

### Post by sumday on 2005-08-31
[QUOTE=OpposingForce]Actually its the opposite for me...I get the bug whenever I LEAVE a cd in the reader...sometimes I do and sometimes I dont...[/QUOTE]
 it's the same for me. i just booted today with an audio cd in the drive and got the "failed to inititalize hal" error. then i'd hit ctrl+alt+backspace and try again, with the same luck. then i took the cd out and had no problems. very odd bug.

---

### Post by torrent on 2005-09-11
what i do is not very spectacular, but it works, so i want to tell you: i just wait.

one day i didn't reboot immediatly and  -  after a few minutes - the whole dektop appeared and everything was fine.
works every time.
today it took 4 minutes.



cd or no cd/cdrom - that does not matter with my computer

---

### Post by thegargravarr on 2008-02-22
I recently encountered this error coupled with my machine seemingly auto logging out. I too thought it was related to an update, as the computer had been running fine for a long while before that.

I found out however that just before i began to receive this error, my house mate had accidentally powered off the machine by unplugging it at the wall :-|

I fully shutdown the system and left it unplugged for a few minutes, then booted up, and have not had  either problem since :)

Hope this helps some people.

---

