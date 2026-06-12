---
title: "removal of libesd-alsa0 removes half of entire system"
date: 2008-10-17
forum: General Help
---

### Post by Neftronics on 2008-10-17
:confused:
OS: Hardy Heron, Kernel 2.6.24-19-generic
X:  Gnome 2.22.2

Hello, I am a noob to Linux but learning quickly (I think). I was trying to get youtube working in Firefox and saw a suggestion to remove libesd-alsa0 and replace it with pulseaudio, so I did this via Synaptic, not noticing the long list of additional packages to be removed....
I noticed it taking a long time to remove, so looked at the log....
```
Commit Log for Fri Oct 17 11:58:02 2008 


Removed the following packages: 
alacarte 
brasero 
bug-buddy 
compiz 
compiz-gnome 
contact-lookup-applet 
deskbar-applet 
ekiga 
eog 
evince 
evolution 
evolution-data-server 
evolution-exchange 
evolution-plugins 
evolution-webcal 
f-spot 
fast-user-switch-applet 
file-roller 
firefox-3.0-gnome-support 
firefox-gnome-support 
gconf-editor 
gedit 
gimp-gnomevfs 
gnome-applets 
gnome-control-center 
gnome-games 
gnome-media 
gnome-netstatus-applet 
gnome-orca 
gnome-panel 
gnome-pilot 
gnome-pilot-conduits 
gnome-power-manager 
gnome-session 
gnome-settings-daemon 
gnome-spell 
gnome-terminal 
gnome-user-guide 
gnome-utils 
gnome-volume-manager 
gtkhtml3.14 
libbonoboui2-0 
libdeskbar-tracker 
libebook1.2-9 
libecal1.2-7 
libedata-book1.2-2 
libedata-cal1.2-6 
libedataserverui1.2-8 
libeel2-2 
libesd-alsa0 
libexchange-storage1.2-3 
libgail-gnome-module 
libgnome-desktop-2 
libgnome-window-settings1 
libgnome2-0 
libgnome2-perl 
libgnome2.0-cil 
libgnomeui-0 
libgtkhtml3.14-19 
libgtkhtml3.16-cil 
liblpint-bonobo0 
libpanel-applet2-0 
mousetweaks 
nautilus 
nautilus-cd-burner 
nautilus-sendto 
nautilus-share 
network-manager-gnome 
python-gnome2 
python-gnome2-desktop 
python-pyatspi 
rhythmbox 
seahorse 
sound-juicer 
system-config-printer-gnome 
tomboy 
totem 
totem-gstreamer 
totem-mozilla 
totem-plugins 
tracker-search-tool 
tsclient 
ubuntu-desktop 
ubuntu-docs 
update-notifier 
vino 
xulrunner-1.9-gnome-support 
yelp 

Upgraded the following packages: 
evolution-common (2.22.2-0ubuntu2) to 2.22.3.1-0ubuntu1 
evolution-data-server-common (2.22.2-0ubuntu2) to 2.22.3-0ubuntu2 
libcamel1.2-11 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu2 
libedataserver1.2-9 (2.22.2-0ubuntu2) to 2.22.3-0ubuntu2 
libpango1.0-0 (1.20.1-1) to 1.20.5-0ubuntu1 
libpango1.0-common (1.20.1-1) to 1.20.5-0ubuntu1 
 
Reinstalled the following packages: 
pulseaudio (0.9.10-1ubuntu1) 

```

What on earth is going on here? Is the dependency list corrupted? It uninstalled half my system for no good reason. 
I'm not sure if I did the right thing, but I selected each one of these packages in the list for reinstallation, before rebooting, then rebooted and everything worked as before. Also, as a bonus youtube works with sound and video.

Can anyone explain why this happened? Is it a bug or am I missing something important? If I go into synaptic and select remove libesd-alsa0 again, the list of packages to be removed does infact contain all the above packages! :?

---

### Post by Pro-reason on 2008-10-17
I'm running Kubuntu Intrepid, and the removal of that package would do the same to me.  It appears to be essential.  It is normal that its removal should remove a lot of stuff.

The anomaly is not in that, but in the suggestion that removing it is a good idea.  Perhaps the tutorial that you are following has further information, but since you didn't link to it, I can't tell.

---

### Post by Neftronics on 2008-10-17
Here is the thread:
[http://ubuntuforums.org/showthread.php?t=765368](http://ubuntuforums.org/showthread.php?t=765368)
(at the bottom)

It seems I misread in an attempt to get it sorted as quickly as possible! They did not suggest **uninstalling** at all, just **unloading**
I still don't see why all those packages should be removed along with a sound daemon. I mean, gedit is in that list!

Thanks for the quick reply by the way!

---

### Post by Pro-reason on 2008-10-17
Gedit doesn't depend on it directly.  The sound daemon is required by several important bits of GNOME, and those in turn are required by gedit.

These GNOME dependencies are a consequence of gedit being a GNOME app.  The assumption is that you only have gedit installed if you have a full GNOME desktop, and that you are therefore not having to install any libraries that you don't already have.  If you want something stand-alone, there are plenty of programs to choose from (vim, emacs...).

Good to hear that you fixed your problem.  Perhaps you could mark this thread as “solved”.

---

