---
title: "[SOLVED] Unable to start the settings manager 'gnome-settings-daemon'"
date: 2008-10-22
forum: General Help
---

### Post by iheartubuntu on 2008-10-22
About 50 minutes ago I did the latest package update and after restarting the computer, Im getting this error...

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Ive googled and search throughout the forum here and cant seem to come up with a fix. My top/bottom menu bars are very basic (almost a win98 look) and I no longer have any sound once booting up to the desktop. I do however have sound when I reach my login and when Ubuntu is loading up the splash screen. After that tho, forgetaboutit.

Any help please?? My system has been running very nice and my wife has some friends coming over soon and wanted to show them Ubuntu!!

---

### Post by ost2life on 2008-10-22
I'm also getting the same thing happening to me. When it logs in though I do get the sound and then I'll get a message saying that the volume control has bombed out, and sometimes that compiz.real bombed out too.
I've included the log from the last boot below 

```

Oct 22 18:09:22 upstairs bonobo-activation-server (main-7755): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vomW7RX2zm: Connection refused
Oct 22 18:09:27 upstairs bonobo-activation-server (main-7783): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vomW7RX2zm: Connection refused
Oct 22 18:10:54 upstairs dhcdbd: Started up.
Oct 22 18:11:13 upstairs pulseaudio[6150]: ltdl-bind-now.c: Failed to find original dlopen loader.
Oct 22 18:11:13 upstairs pulseaudio[6152]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Oct 22 18:11:13 upstairs pulseaudio[6152]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Oct 22 18:11:13 upstairs pulseaudio[6152]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 22 18:11:13 upstairs pulseaudio[6152]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 22 18:11:37 upstairs pulseaudio[6152]: module-x11-xsmp.c: X11 session manager not running.
Oct 22 18:11:37 upstairs pulseaudio[6152]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

```

Hopefully this is just a botched update, I don't know if it's relevant but I've tried reinstalling gnome through synaptic and I get a message saying that some of the packages can't be authenticated, after poking about a bit, packages include most of the kernel packages and lib-gnome-desktop2

EDIT:
some other packages seem to have been broken by this too including pidgin where I get:
```
ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstlibvisual.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
```
and the same again while trying to run totem.

---

### Post by iheartubuntu on 2008-10-22
Yah, I actually tried to reinstall "gnome-settings-daemon" in synaptic and it didnt help :|

---

### Post by iheartubuntu on 2008-10-22
UPDATE: nothing new. sorry. I tried switching to the older nvidia drivers and it didnt help. I tried turning off all nvidia drivers and that did nothing also. I guess we're stuck until a new patch comes out.

---

### Post by ost2life on 2008-10-22
well, that's a bugger. :(

---

### Post by iheartubuntu on 2008-10-22
A possible F I X ???

Try going into...

System > Administration > Synaptic Package Manager

then do a search on "dbus" without the quotes. Mark it for reinstallation, click "apply" and reinstall dbus. Reboot the system. Let me know if it works!!!

---

### Post by iheartubuntu on 2008-10-22
Nope. It didnt help :(

---

### Post by Mathijsken on 2008-10-22
Well jsut like you, I've found out the problem lies with bonobo not being able to connect to the dbus-service for some reason.
Usaually this means there's a file missing from /etc/dbus-1/... or there's a fault setting in it. I couldn't find a bonobo-file inside the directory so I'm stuck as well.

Oh Might Developer Gods Shine A Ligth On Us!!

I'm going to try to install a previous version of bonobo from packages.ubuntu.com

I'll tell you what happens

---

### Post by iheartubuntu on 2008-10-22
If it works I'll name my next kid "Bonobo"!

---

### Post by kaaino on 2008-10-22
Same problem, volume, appearance settings do not work. Also the shut down button disappeared from the toolbar :-(

---

### Post by iheartubuntu on 2008-10-22
Whew! It didnt work for me. No kid named Bonobo here.

I had this same problem on my laptop a few days ago and fixed it by reinstalling "dbus", but it didnt help here today on a desktop system Im using.

I found this page which might offer some more clues...

[http://ubuntuforums.org/archive/index.php/t-579167.html](http://ubuntuforums.org/archive/index.php/t-579167.html)

---

### Post by kaaino on 2008-10-22
dbus reinstal did not work for me either

---

### Post by Spad on 2008-10-22
Getting the same issue here, gnome-settings-daemon, volume control and pidgin all seem to have died following the update on 8.10.

---

### Post by randy78 on 2008-10-22
Same exact problems here... going to file a bug report

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

---

### Post by caleb12 on 2008-10-22
I was having this exact same problem today after doing some installing and un-installing of packages... And, I also had the pidgin error: 

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstlibvisual.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.

So, I did what it said:

sudo mv /usr/lib/gstreamer-0.10/libgstlibvisual.so libgstlibvisual.so.OLD

Made some notes in case I have some more problems later on... but everything seems fine now... I had found all the other pages regarding dbus and kde settings... none of that stuff helped...

---

### Post by randy78 on 2008-10-22
> **caleb12 said:**
> 

So, I did what it said:

sudo mv /usr/lib/gstreamer-0.10/libgstlibvisual.so libgstlibvisual.so.OLD

Made some notes in case I have some more problems later on... but everything seems fine now... I had found all the other pages regarding dbus and kde settings... none of that stuff helped...


This fixed it for me, but I had to re-add the volume control back to my bottom panel manually.

Thanks!

:guitar:

---

### Post by caleb12 on 2008-10-22
Likewise my volume control had disappeared as well... not sure whats up with that... I mean, gstreamer is a codec so I can understand it screwing my volume control app up but the gnome-settings-daemon??? Seems a bit random...

---

### Post by kaaino on 2008-10-22
Fixed for me as well. :-) Thanks

---

### Post by iheartubuntu on 2008-10-22
I was going to file a bug report, but came across this...

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093)

which led me to this...

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)

which recommends doing the command 

> sudo rm -f /usr/lib/libvisual-0.4/actor/actor_nastyfft.so

in the terminal. I'll give it a try right now.

BINGO!! IT WORKED!!!

---

### Post by randy78 on 2008-10-22
Yeah, kinda odd...

I filed that bug report and posted your solution on Launchpad, so hopefully other people can use it and the devs can figure out what's up :D

---

### Post by Spad on 2008-10-22
Sorted; I followed Caleb's suggestion and everything is back to normal (apart from the volume control thing).

That's what I get for beta testing I guess.

---

### Post by caleb12 on 2008-10-22
> **shirteesdotnet said:**
> 
which recommends doing the command 

sudo rm -f /usr/lib/libvisual-0.4/actor/actor_nastyfft.so 

in the terminal. I'll give it a try right now.

BINGO!! IT WORKED!!!


So, it seems connected to the libgstlibvisual.so - something to do with libvisual perhaps... who knows... maybe the bug report will produce some more info in the long run... Although, you could have also moved that file instead of killing it completely - what if you need it again - but that's personal choice. At least it works... that other theme is unbearable.

---

### Post by Maratonda on 2008-10-22
BINGO IT WORKED ON MINE ALSO!!
That's probably the first time I solve such a problem with one (!) command!

---

### Post by DeadSuperHero on 2008-10-22
Fantastic fixes in this thread. Absolutely resolved the problem, at least for now.

---

### Post by caleb12 on 2008-10-23
It looks like this mornings updates had a new libvisual-0.4 in it. I wouldn't have paid attention to it except that shirteesdotnet fix included this package.

So, I renamed /usr/lib/gstreamer-0.10/libgstlibvisual.so.OLD back to it's original name; seems that pidgin and volume control work fine now. Perhaps that fixed it...

---

### Post by markiliz on 2008-10-23
> **shirteesdotnet said:**
> I was going to file a bug report, but came across this...

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093)

which led me to this...

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)

which recommends doing the command 



in the terminal. I'll give it a try right now.

BINGO!! IT WORKED!!!

OK..so now we can expect someone named Bonobo in the near future now.... :guitar:

---

### Post by iheartubuntu on 2008-10-23
> **markiliz said:**
> OK..so now we can expect someone named Bonobo in the near future now.... :guitar:

OK. But only if you name your kid Ubuntu. :lolflag:

---

### Post by rovert1214 on 2008-10-25
I'm having the same problem on an HP Pavilion dv6000 laptop. I found this thread 2 days ago and I did what was posted as a solution and it worked for one session then I had to do it again after I restarted it later. It worked that time also but after I had done it 3 times it wouldn't work again. So I'm stuck with not being able to open Nautilus and I can't change any appearance settings because of the same Bonobo error. I have downloaded any new updates after the fix stopped working for me. If you need me to run some commands in the terminal to get more info to help someone solve it I can. Thanks for the help.

---

### Post by rfurman24 on 2008-12-16
This problem just started for me this morning. I made no changes to the system it just happened.

---

### Post by rfurman24 on 2008-12-16
How do I debug gnome-settings-daemon?

---

### Post by rfurman24 on 2008-12-16
My problem seemed to be related to the fact that I had changed the alt-control-delete key binding to open gnome system monitor. I have always set my system up this way. This particular system has been like that since install but all of a sudden it broke my system.

---

### Post by chaanakya_chiraag on 2009-03-11
Hey guys!  I've had this problem for a while on Hardy.  I just fixed it today by installing the package gnome-settings-daemon-dev.  Give it a try and let me know what happens.

- Chiraag

PS:  In the terminal, the command would be ```
sudo apt-get install gnome-settings-daemon-dev
```
The alternative would be to go into Synaptic or similar program and search for gnome-settings-daemon-dev and install it that way.

Sorry Guys!  I spoke too soon.  It didn't work :(  However, neither did reinstalling dbus!  Anyone have any other ideas?

---

### Post by landstander on 2012-07-11
.

---

### Post by wildmanne39 on 2012-07-11
Old thread closed.

---

