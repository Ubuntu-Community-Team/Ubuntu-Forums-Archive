---
title: "HDD Grind"
date: 2008-07-14
forum: General Help
---

### Post by henrypootel on 2008-07-14
Hi
I'm using ubuntu hardy on my desktop, and the main drive is continuously grinding(2 other mounted drives are fine). The only time i can hear it stop this, is if i do something filesystem intensive like a file search or something. I haven't the first clue where to even start looking for the cause of this. i have attached the printout of 'ps -A', but aside from that, I'm clueless.
Can anyone help me?

---

### Post by louieb on 2008-07-14
Sounds like its giving you a warning its about to die. Back it up.
Most drive manufactures have a diagnostic utility on there web site.   
To find what kind of drive it is 
```
sudo lshw -C disk
```
the output will look something like this.
> 
       description: ATA Disk
       product: ST340016A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.75
       serial: 3HSEZ4K8
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6001c8de



---

### Post by fyo on 2008-07-14
One possible culprit is trackerd. It indexes your filesystem. You can try simply pausing it (use the magnifying glass icon in the "Notification Area").

---

### Post by henrypootel on 2008-07-14
i just tried killing trackerd and tracker-applet, but it made no difference(there was no magnifying glass icon in the tray).
I would tend to agree with you about it dying louieb, but for these reasons:
[LIST]
[*]its only about a year old
[*]the grind only happens when in the GUI. ie. it starts just as the desktop comes up after logging in, and it stops as soon as the desktop disappears on shutdown(and changes to the progress bar).
[*]when booted in WinXP on the same drive, there is no noise from the drive.
[*]when there is actual activity on the drive, it becomes quiet again.
[/LIST]

I'm not saying it's definitely not dying, i just don't think so and even if it is, theres not much i can do(it's a SATA Seagate Barracuda BTW)

Any more suggestions anyone?
If it's of any help, here's the system spec:

Intel Pentium Dual-Core 1.6Ghz
2Gb G-Skill DDR2
Gigabyte GA-P35-DS3P
XFX GeForce 8600GT Fatal1ty edition
Seagate Barracude SATA 200Gb
Ubuntu Hardy Heron, Windows XP Pro(TinyXP)

---

### Post by VMC on 2008-07-14
If it's not happening in Windows I wouldn't say it's you hard drive dying. I would suspect the hard drive indexing.

---

### Post by henrypootel on 2008-07-14
ok, and how would i disable/stop/pause/remove that?

---

### Post by fenian on 2008-07-14
> **henrypootel said:**
> ok, and how would i disable/stop/pause/remove that?

From the menu System>Prefrences>Sessions uncheck Tracker and Tracker Applet then reboot.

---

### Post by cariboo on 2008-07-14
Just to be sure you can go to Seagate's web site and download the diagnostic tools. Here is the link:

[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

Jim

---

### Post by LuxVoodoo on 2008-07-14
I once had trouble with a lot of hard drive grinding. One culprit was indeed Trackerd. The other culprit was evms (Enterprise Volume Management System). Since I didn't really need either, I uninstalled them both via Synaptic.  There's been no hard drive grinding for me since.

---

### Post by henrypootel on 2008-07-14
thanks, i'll try those tonight

---

### Post by henrypootel on 2008-07-15
OK, i tried turnig off the tracker stuff but to no avail. after messing around with killing off various apps for about half an hour, i stumbled upon 'mythtv-backend'. I don't know what it's trying to do, but it is the culprit.
I've uninstalled it(i'm using XBMC now anyway) and it's back to silent running. Yay!

thanks everyone for your help.

---

