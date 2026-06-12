---
title: "Palm Treo 680"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by nathaliefiems on 2007-07-24
I have problems syncing my Palm Treo 680 with Ubuntu Feisty. I searched for help on the internet and asked in other fora, no results Hope you can help me!

With gnome-pilot settings to device "usb:" it seems to recognize the handheld. I get connection on hotsync and on the palm-screen I can follow syncing different items. The conduits are set to sync with Evolution 2.10 but if I look in evolution after syncing, nothing has happened: not the tasks, nor the calendar have changed. checking dmesg says: "[ 1682.067997] usb 9-1: new full speed USB device using ohci_hcd and address 12'" after this trial.

I looked around on the net to find an answer but could not. I dit "sudo modprobe visor" in the terminal and changed device to dev/ttyusb0 or ttyusb1, but then the palm crashes when trying to sync and I cannot restart gnome-pilot again. After this trial, checking dmesg says
"[ 1836.497402] visor 9-1:1.0: Handspring Visor / Palm OS converter detected
[ 1836.497901] usb 9-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[ 1836.498075] usb 9-1: Handspring Visor / Palm OS converter now attached to ttyUSB1"

What goes wrong?

---

### Post by pbcartwright on 2007-07-24
the Treo 680 is not supported. I've been trying to get mine to work for 3 months. I've tried jpilot and kpilot, no luck. You might try lookin into joining the kde-pim email list, they might be able to give you some insight..

---

### Post by nathaliefiems on 2007-07-24
Hlmmm.. not a happy answer. But thank you anyway!

---

### Post by jsanta on 2007-08-01
Treo 680 IS supported, at least by jPilot. You just don't have to setup the device as said in most everyplace. 

Try syncing to "usb:" instead of "/dev/pilot"or "/dev/ttyUSB*"
[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117864.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117864.html)

---

### Post by old_salt on 2007-11-11
I just got a 680. I run Kubuntu Gutsy 64bit on my HP Dv9000z. Kpilot, Jpilot do not work however Gnome Pilot does work. Synch with Evolution is fine however I would prefer Kpilot to work to synch with Kontact, Kmail etc. I have a trusted pair under Bluethooth however that';s about as far as it goes. Can't browse, access Mem card, tether for Internet etc or hotsynch. Any assistance or info would be appreciated. I've just performed a fresh install from scratch so I have  a clean system to work with.

Thanks

---

### Post by s3ts on 2008-01-23
Can someone let me know how you got it to sync with Evolution?

My Treo 680 wouldn't sync to Evolution. All that works is the contacts sync. All else fails. I am also using the instructions described above.

---

### Post by Andy Dunlop on 2008-01-28
Well I have my Palm 680 happily syncing to Evolution, and can read my Palm directories using 'Card Reader' from Mobile Stream as long as I have an expnasion card in the phone. If I take that out then the syncing still works, but Ubuntu does not see the phone at all.

---

### Post by rhand on 2008-02-13
s3ts,

I think there is something wrong with the current conduits. Syncing was fine with the previous ubuntu, but now gpilotd reports that it couldn't connect with evolution-data-server and doesn't sync my calendar.

from [http://live.gnome.org/GnomePilot](http://live.gnome.org/GnomePilot) :
Crashes have been reported with the Evolution 'calendar' conduit. This appears to be due to a bug in evolution-data-server.

I might try to get an older version and see if that helps...

---

### Post by bujutsukai on 2008-02-26
I just bought a Palm Centro (685 / AT&T) and successfully synced it with my Gutsy install.  I'm totally excited, as this puts me one step closer to leaving Winblows forever ;-)

The sync was pretty seamless, though I initially tried with Kpilot, and that wouldn't even connect to my phone.  Gnome-pilot works great so far, and did not crash with ECalendar sync.  I'm only using the cable at this point, but hope to have to time to work on a BT sync soon.  We'll see.

---

### Post by Andavane on 2008-04-20
> **jsanta said:**
> Treo 680 IS supported, at least by jPilot. You just don't have to setup the device as said in most everyplace. 

Try syncing to "usb:" instead of "/dev/pilot"or "/dev/ttyUSB*"
[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117864.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117864.html)

Interesting.
Have just tried changing to USB and something is now happening: It makes the noise, and the information is listed in the gnome-pilot with the name of the PDA.
Troublel i, I seem nolonger to have sync setting so cannot try "/dev/ttyUSB*"
But "MyPDA" folder in home appears to be empty.
I wonder if I am missing something.
Have been fiddling about with this for ages on and off and had another go today.

---

### Post by Andavane on 2008-04-20
Hello
I fiddled about some more and
System/Preferences/Palm OS Devices #
I went to conduits and enabled everything there and synced again.
Prior to this all were disabled.
Now a whole load of files have appeared in home/MyPDA

Not sure how to access them yet,
but great progress for one day!
Regards
John

PS: Using Gutsy Gibbon

---

