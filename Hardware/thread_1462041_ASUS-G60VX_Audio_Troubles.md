---
title: "ASUS-G60VX Audio Troubles"
date: 2010-04-25
forum: Hardware
---

### Post by Overclock757 on 2010-04-25
I have installed Ubuntu 10.04 on my ASUS-G60VX Laptop and everything is awesome except when I plug my headphones in I don't get any sound out of them.

I can hear audio coming from the laptop speakers, it's just when I plug the headphones I have no sound. I looked at all the options in audio and everything looks fine but I can't seem to figure this out.

EDIT: It looks like my headphone volume is 0% but I have no option in Alsa control panel to raise it.

[[IMG]http://img193.imageshack.us/img193/6092/alsamixer.th.png[/IMG]](http://img193.imageshack.us/i/alsamixer.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Max Derner on 2010-04-25
I'm having the exact same problem in reverse my speakers won't work but the head phone jack does

---

### Post by Overclock757 on 2010-04-25
I found an answer but it's for opensuse. [[COLOR="Blue"]Opensuse Fix[/COLOR]]("http://forums.opensuse.org/get-help-here/laptop/431492-particular-audio-problems-asus-g60vx.html")

The problem here is I don't know what to do or if the fix in the link will work on Ubuntu as well, I'm a bit new to Linux.

Any help would be greatly appreciated.

---

### Post by lidex on 2010-04-25
> **Overclock757 said:**
> I found an answer but it's for opensuse. [[COLOR="Blue"]Opensuse Fix[/COLOR]]("http://forums.opensuse.org/get-help-here/laptop/431492-particular-audio-problems-asus-g60vx.html")

The problem here is I don't know what to do or if the fix in the link will work on Ubuntu as well, I'm a bit new to Linux.

Any help would be greatly appreciated.

To implement that fix. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by Overclock757 on 2010-04-25
> **lidex said:**
> To implement that fix. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default


You are so awesome it worked! Thank you so much for the help. :KS:KS:KS

---

### Post by lidex on 2010-04-25
You're welcome! Go forth and enjoy.

---

