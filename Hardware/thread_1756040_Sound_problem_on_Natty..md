---
title: "Sound problem on Natty."
date: 2011-05-11
forum: Hardware
---

### Post by atomicspin on 2011-05-11
On a gateway laptop and have upgraded to Natty.

Right now, if one program is running sound, then no other program can do it.  If Pidgin makes a sound then I can't watch anything on Youtube on Chromium or Firefox.  It seems to "lock down" the program's sound so other programs can't use it.  

Has anyone experienced this and have a fix?  What other information do you need?

Thanks in advance!

---

### Post by ghostborg on 2011-05-11
I had a problem last week when an update came down and then my machine kept muting my sound every time I booted but everything was un-muted. Everything in the sound preferences where as before and finally I figured out that I had to un-mute the card every time with alsamixer and save alsactrl. A pain but at least I had sound.

Another update came down with with a bunch of pulseaudio updates, crossed my fingers, and all of a sudden everything started working again.

So hopefully it's just a bug they are working on.

---

### Post by lidex on 2011-05-11
Could be a pulse audio issue. 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by atomicspin on 2011-05-12
> **lidex said:**
> Could be a pulse audio issue. 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**
* Ignore any 'No such file or directory' errors*


Nailed it!  Thank you!!

---

### Post by lidex on 2011-05-12
You're welcome!

---

