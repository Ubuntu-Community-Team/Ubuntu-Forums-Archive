---
title: "Force nVidia GPU to re-detect displays"
date: 2011-09-30
forum: Hardware
---

### Post by theyranos on 2011-09-30
I've got a kubuntu machine that's hooked up to my television through a home theater receiver as an HTPC. Under normal circumstances, everything works as I'd like.

However, if the computer reboots while the receiver is off (or set to a different input) the computer boots to a black screen. It's clearly working, because I can actually hear system event notification sounds and ssh into the machine from my laptop. The only problem is that I can't get it to start the display. (The TV says "No signal" at this point, even if I bypass the receiver and connect it directly to the PC.)

The following do not work:
[LIST]
[*]sudo service kdm restart
[*]sudo rmmod nvidia && modprobe nvidia-93
[*]CTRL+ALT+F1 
[/LIST]

It seems like, once it's in this state, the only way to get the display back is to reboot the machine with the TV on and the receiver set to display the computer. Ordinarily, I wouldn't care, but unfortunately my HTPC also acts as a server for a bunch of things. Rebooting it cleanly consequently takes about 10 minutes and disrupts most of my home network in the meantime.

So, I post here in the hopes that somebody knows something else I can try to force the GPU to re-detect displays.

**uname -a**:
```
Linux blue 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:41:54 UTC 2011 x86_64 GNU/Linux
```

**cat /etc/issue**:
```
Ubuntu 10.10 \n \l
```

**lspci | grep -i nv**:
```
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
```

**lsmod**: see Ubuntu Pastebin [http://paste.ubuntu.com/700047/]("http://paste.ubuntu.com/700047/")

---

### Post by diasf on 2011-09-30
one very sloppy and weird way of solving this (temporarly) is to have vino-server running on the desktop, that way you can vnc into the desktop and change the monitor settings. It's also useful to control xbmc from the bed :)

---

### Post by papibe on 2011-09-30
Hi theyranos, I have the same exact card! ;)

I also have my computer connected to the TV, although mine is in dual head configuration.

Are you using nvidia-93? That's a little odd to me. The card is recent enough to be using nvidia-current (that's the version I'm using actually).

Could you post your /etc/X11/xorg.conf ?

Regards.

---

### Post by theyranos on 2011-09-30
> **diasf said:**
> one very sloppy and weird way of solving this (temporarly) is to have vino-server running on the desktop, that way you can vnc into the desktop and change the monitor settings.

I can VNC in (using x11vnc rather than vino since I don't use gnome) and change the display settings, but my choices are limited to 640x480 and 320x240. Neither option results in the "No Signal" message going away.

> **diasf said:**
> It's also useful to control xbmc from the bed :)
That's what the remote is for :)

> **papibe said:**
> Are you using nvidia-93? That's a little odd to me. The card is recent enough to be using nvidia-current (that's the version I'm using actually).

nvidia-93 was an intentional downgrade. The last time I tried nvidia-current, I couldn't get X11 to load at all. However, since it's apparently working for you with the same card, I decided to give it a try.

```

root@television:~# apt-get update 2>&1 >/dev/null
root@television:~# service kdm stop
kdm stop/waiting
root@television:~# rmmod nvidia
root@television:~# apt-get -qq install nvidia-current
root@television:~# modprobe nvidia-current
root@television:~# service kdm start
kdm start/running, process 11530

```

And lo, my TV turned itself on! Thanks!

> **papibe said:**
> Could you post your /etc/X11/xorg.conf ?
Not that it matters anymore, but [http://paste.ubuntu.com/700096/](http://paste.ubuntu.com/700096/)

---

### Post by papibe on 2011-09-30
:D Glad it's working!

Just want to make sure, Did you try rebooting while the receiver is off? 

That's works OK on my computer, but there's old tricks (previous cards, previous nvidia drivers) to force X to use the monitor, even if it's off:

```
Section "Screen"
...
	Option		"UseDisplayDevice" "Monitor0"
...
EndSection
```
Or even this one:
```
Section "Screen"
...
	Option		"ConnectedMonitor" "Monitor0"
	Option		"UseDisplayDevice" "Monitor0"
...
EndSection
```

Regards.

---

### Post by theyranos on 2011-09-30
> **papibe said:**
> Just want to make sure, Did you try rebooting while the receiver is off? 


Yup. Problem solved :)

---

