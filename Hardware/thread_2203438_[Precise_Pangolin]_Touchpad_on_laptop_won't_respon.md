---
title: "[Precise Pangolin] Touchpad on laptop won't respond, and buttons do nothing."
date: 2014-02-03
forum: Hardware
---

### Post by packetpirate on 2014-02-03
I have a Dell Latitude D630 (not exactly a new computer) and I recently loaded Ubuntu 12.04 LTS (Precise Pangolin) onto it. Everything was working great yesterday, but this morning when I went into class, after a few minutes, the touchpad stopped responding. I then tested the nub and it wouldn't move the mouse either. Also, trying the right mouse button for both the nub and the touchpad yields no results. Same for the left mouse button.

I'd really hate to have to bring along a USB mouse to class, being that the desks aren't even big enough for the laptop itself. Does anyone know what the problem might be? There are several things I can't figure out how to do without the mouse (accessing system tray icons, for example; so I can't login to the campus wi-fi), so it's pretty essential.

I appreciate any help or pages you can direct me towards.

---

### Post by Kirboosy on 2014-02-03
Are there any special function keys that allow you to turn off and on the touchpad? I know my Dell laptop has FN+F3 I believe it is to disable and enable the touchpad. Perhaps you have something similar? Or the BIOS is somehow in flux causing it to turn off the internal mouse. Check those two places.

I would have a better time believing that its hardware if it was only one input that quit working. I suppose a wire could of come loose in there but I would try software fixes first. 

Also have you recently done and updates or changed anything right before it quit working?

Hope that helps!
~Caboose

---

### Post by packetpirate on 2014-02-03
No, like I said, I just installed the OS, so I haven't installed any updates yet. There are no function keys for disabling the touchpad on this particular laptop. I checked the BIOS and the touchpad is definitely enabled.

---

### Post by Kirboosy on 2014-02-04
I just ran across this guide on the wiki. Hopefully it helps

[Debugging Mouse Detection]("https://wiki.ubuntu.com/DebuggingMouseDetection")

~Caboose

---

### Post by packetpirate on 2014-02-04
I just plugged in a USB mouse to try to use that for now, but that  doesn't work either. Also, I can't figure out how to connect to Wi-Fi  without that system tray icon, so I probably can't follow that guide.  Any ideas?

---

### Post by Kirboosy on 2014-02-04
Please run the following commands in a terminal and paste the output. (CTRL + ALT +T to open terminal) 

```
lsusb | grep ouse
```
```
xinput
```

~Caboose

PS if push comes to shove you could just screenshot the terminal if you are unable to get a text copy.

---

### Post by packetpirate on 2014-02-04
Ok, so I'm pretty sure this must be a bad install, because it's one problem after another. Earlier, when I boot up, I got a message about the monitor configuration being blank, and now, upon bootup, it doesn't go to the login screen, but instead goes to a command-line interface called "BusyBox" and the input line says "(initramfs)". What the hell is going on?

---

### Post by Kirboosy on 2014-02-05
Hmmm, How did everything run on a LiveCD before you installed it? Perhaps since its an older laptop you should try a lighter version of Ubuntu. Such as Xubuntu or Lubuntu.

---

### Post by packetpirate on 2014-02-05
Ubuntu 12.04 LTS ran just fine on my Dell D620, a model down from this  one, for years, so it's not the laptop. It has 2 GB of RAM and a fairly  decent processor. I didn't try it on the LiveCD. I just installed it.  I'm going to try re-installing from USB. The first time I installed, I  had forced the 706 MB image onto a 702 MB CD, so I'm thinking maybe  something got corrupted?

---

### Post by Kirboosy on 2014-02-05
It is totally possible that you had a bad install but I would also think that there would be errors while trying to install. I would recommend a re-install like you mentioned above. If things persist you can go from there.

---

### Post by packetpirate on 2014-02-05
I just wonder how I'm going to re-install it without a mouse... I hope tab works for navigating the installation menu...

---

### Post by Kirboosy on 2014-02-05
So even during the install the Mouse won't work? If its a problem with that installation the LiveCD installer should work no problem. If there is something else wrong you will experience problems with the LiveCD

---

