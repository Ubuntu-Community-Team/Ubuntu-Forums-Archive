---
title: "ThinkPad Volume Button Configuration"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by AnythingBut on 2007-07-08
I have a ThinkPad T60 (hda-intel sound) and I was noticing that the volume buttons produce very coarse/abrupt volume changes.  I guessed that the volume buttons were changing some internal (direct to speaker) volume and, because of key mappings, were simultaneously changing the Master volume found in the software volume control.

So I disabled the key mapping to the two volume controls found in System -> Preferences -> Keyboard Shortcuts.  Now the volume control is much better with the two buttons.  It behaves much more like it does in Windows.  Pushing the buttons doesn't change any of the "Software" volume, as I prefer.  Unfortunately, it also stops the nice Volume OSD from appearing (as well as a minor mute issue).

Does anyone else notice this behavior?  Any solutions for the lack of OSD (the Windows OSD shows the "hardware" volume)?

Update: A solution can be found later in the thread at [http://ubuntuforums.org/showpost.php?p=4807282&postcount=23](http://ubuntuforums.org/showpost.php?p=4807282&postcount=23)

---

### Post by JPorter on 2007-07-21
Thank you so much!

I've been frustrated by the fact that the volume control is not at all linear, and I only get volume at all in the upper 1/3 of the range... it was because the key was controlling both the hardware volume and the software volume simultaneously!

This worked great for me, thanks.


For those who are interested, especially the folks who use ALSA, changing the settings in the ALSA mixer to 0.00db gain across the board really helped audio quality for me.  Access it by typing  [FONT="Courier New"] alsamixer[/FONT] in a terminal window.  Store the settings to restore on reboot by typing [FONT="Courier New"] sudo alsactl store 0 [/FONT]

Thanks,

Porter

---

### Post by AnythingBut on 2007-11-10
Still a issue in Gutsy.  Same solution works.  But looking for a way for the nice OSD to show the Hardware volume.

---

### Post by AnythingBut on 2007-11-19
For any ThinkPad owners out there,

I mucked around with the source code of gnome-settings-daemon (gutsy's version) so that I get the volume OSD to show my *hardware* volume whenever the volume buttons are pushed (the current OSD is made to modify and display the OSS-mixer volume).  I find it much more useful to see my hardware volume on the OSD and the software volume via the volume control tray thing.  This also stops the buttons from changing the software and hardware volumes simultaneously.

If there is any interest, I can try to get the code up to a level for public consumption and maybe also submit it somewhere as a wishlist kind of patch.

---

### Post by gazrang on 2007-12-16
> **AnythingBut said:**
> For any ThinkPad owners out there,

I mucked around with the source code of gnome-settings-daemon (gutsy's version) so that I get the volume OSD to show my *hardware* volume whenever the volume buttons are pushed (the current OSD is made to modify and display the OSS-mixer volume).  I find it much more useful to see my hardware volume on the OSD and the software volume via the volume control tray thing.  This also stops the buttons from changing the software and hardware volumes simultaneously.

If there is any interest, I can try to get the code up to a level for public consumption and maybe also submit it somewhere as a wishlist kind of patch.

Wow. Thanks you, AnythingBut. I also had the same problem on my T42. I prefer old tpbcr-package([http://www.nongnu.org/tpb/screenshot.jpg](http://www.nongnu.org/tpb/screenshot.jpg))  style OSD. I hope your efforts will do work.

---

### Post by AnythingBut on 2007-12-16
Hey Gazrang,

I used the tpb package a couple distributions back.  My main issue with it is that it polls the hardware keeping my laptop from entering power-saving modes.

Also, I prefer the unified look of the GNOME osd.  Particularly the semi-transparent one that's activated with compiz.  It's beautiful.

---

### Post by AnythingBut on 2007-12-23
I've packaged the code hacks I put together.  If anyone is interested, you can find them on my launchpad PPA.  Adding the apt source
```
deb http://ppa.launchpad.net/4lorne/ubuntu gutsy main
```
will upgrade your version of gnome-control-center to one which can read the hardware sound volume of your Thinkpad and uses it for the OSD when you push the volume buttons.

To get it to work, in gconf-editor, add the key /apps/gnome_settings_daemon/hwvol with the string value 'thinkpad'.  If this is not set, it behaves like the standard ubuntu package.  Also, your volume buttons need to be set up in keyboard shortcuts (i.e., don't do what I suggest earlier in the thread).

I've only tried it on my T60.

---

### Post by gazrang on 2007-12-24
Thanks AnythingBut. I'll try this patch to my T42. I hope it will do work.

Is there any possibility its being get into official ubuntu repository? Many ThinkPad users may want that...

I really appreciate your efforts on this patch. :)

---

### Post by AnythingBut on 2007-12-24
Perhaps, if there is enough interest, I'll submit a bug report on launchpad to get it into the official packages.  But for now, let me know if it works for you.

---

### Post by gazrang on 2007-12-25
AnythingBut, your patch works like charm on my T42. Just without any problem.

I hope this patch put into official ubuntu repository. :)

---

### Post by blue212 on 2008-03-20
I can't install the update, I added the apt source but it won't install.  Is there another way to get the hardware volume control visible?

---

### Post by AnythingBut on 2008-03-20
Are you using gutsy or hardy?  When you do "aptitude show gnome-control-center" what version does it report?

---

### Post by AnythingBut on 2008-03-22
In Hardy's beta, the ThinkPad volume buttons are still handled poorly.  

Show your support to get it fixed.  You can find a bug report at [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/51537](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/51537)  Leave a comment there.

---

### Post by blue212 on 2008-03-24
> **AnythingBut said:**
> Are you using gutsy or hardy?  When you do "aptitude show gnome-control-center" what version does it report?

```
Version: 1:2.20.0.1-0ubuntu5

```

---

### Post by AnythingBut on 2008-03-24
> **blue212 said:**
> ```
Version: 1:2.20.0.1-0ubuntu5

```

Hmm.  Strange.  The one on the PPA is versioned as 2.20.0.1-0ubuntu6~ppa2 so it should update.  Do you get an error when you "aptitude update" for the ppa repository?

---

### Post by blue212 on 2008-03-24
In Synaptic it says:

Installed Version 1:2.20.0.1-0ubuntu5
Latest Version: 1:2.20.1-0ubuntu2~ppa1

Update Manager lists the ppa1 version as a possible update but it won't let me check the box (greyed out)

I updated Synaptic and apt-get and it still lists that version.

btw I'm using gutsy

---

### Post by AnythingBut on 2008-03-24
> **blue212 said:**
> 
Installed Version 1:2.20.0.1-0ubuntu5
Latest Version: 1:2.20.1-0ubuntu2~ppa1


I think I've figured it out.  I think it's because you don't have "Recommended updates (gutsy-updates)" checked in the Software Sources things.  So dependencies aren't satisfied.  (Correct me if I'm wrong)

If you check the box, I think it should then update.

P.S.: To those who already had my ppa package installed, sorry about making your update-manager say there's an update.  I was messing around in my PPA and deleted the package.  I had to re-upload.

---

### Post by blue212 on 2008-03-24
IT WORKS!!

What I did... 

Applications -> Add/Remove -> Preferences -> Updates -> CHECK Recommended Updates (gutsy-updates)

Then it showed up in the update manager... along with a bunch of other stuff (which I had to uncheck because it threatened to overrun my satellite connection bandwidth, lol)

Thanks so much AnythingBut!!!

> **AnythingBut said:**
> I think I've figured it out.  I think it's because you don't have "Recommended updates (gutsy-updates)" checked in the Software Sources things.  So dependencies aren't satisfied.  (Correct me if I'm wrong)

If you check the box, I think it should then update.


---

### Post by fluffman86 on 2008-03-26
anythingbut: could you mark one of these as an upgrade for hardy?  My current version is 1:2.22.0-0ubuntu3.  Or I guess the question is would that even work.  Maybe i'll just try it and find out.  :P

Or, how would I apply the patch that you posted on launchpad?

---

### Post by AnythingBut on 2008-03-26
> **fluffman86 said:**
>  could you mark one of these as an upgrade for hardy?

I've got the patch working on the Hardy package, but I've decided not to put it on my PPA... yet.
Since Hardy is in beta right now, they're going to be releasing updates really frequently, and it will be hard for me to keep up (I have to update my package every time they update theirs).
Also, I'd like to see the change happen in the official packages before Hardy is released.  I figure, without it on my PPA, people might be more likely to chime in at Launchpad saying they want the change.
> **fluffman86 said:**
> 
Or, how would I apply the patch that you posted on launchpad?
A bit of experience with packages and compiling might be helpful.  If you download the source package and put the patch in the debian/patch directory you can then either compile the source after applying all the patches (in order) or create your own debian source package to later produce .deb files.

---

### Post by Hudy on 2008-04-13
Confirmed on T60p, 2007-AD1.  This is sweet - I'd no idea there was anything wrong, just that the volume control was not very pleasing in its effects.

It's smooth as silk now, and does not affect the ALSA controls, nor the master switch.  Sound is appreciably better!

Thanks much for the time & effort.

Hope this makes it upstream.  I'll dig out the bug page & add my voice there, too.

/Bill

---

### Post by dr.phees on 2008-04-16
Hi. I quite recently wrote down my experiences with the tpb ThinkpadButtons manager. Especially working around the preset bindings made by gnome:
[Thinkpad buttons and gnome DO mix!]("http://blog.phees.de/index.php?/archives/2-Thinkpad-buttons-and-gnome-DO-mix!.html")
and a little help to make tpb look a lot better:
[tpb can look good.]("http://blog.phees.de/index.php?/archives/3-tpb-can-look-good.html")

Maybe someone finds it helpful.

---

### Post by AnythingBut on 2008-04-26
Some updates

Regarding the fixes in GNOME: It appears the real solution isn't to implement anything in GNOME, but rather wait until the ibm-acpi kernel module includes an ALSA mixer for the ThinkPad hardware volumes.  Let's hope that happens in time for Intrepid Ibex.

For now, as a stop gap solution, I've created a new package for Hardy.  It's pretty similar, but a few things have changed from the gutsy one.  The package of importance is now gnome-settings-daemon and my version will now detect if ibm-acpi is being used and automatically behave appropriately.  So for this package you don't have to add any gconf keys like you did for the gutsy one (though, I'm not sure whether this will work appropriately for R-Series thinkpads, since they use ibm-acpi but have no hardware volume (I think).  But then again, R-series users should be in this thread)

Here are instructions to get it installed in Hardy.

Go to System -> Administration -> Software Sources.

In the Third-Party Software tab, add my PPA by clicking Add and entering
```
deb http://ppa.launchpad.net/4lorne/ubuntu hardy main
```

Then update your system however you'd like.  I like
```
sudo aptitude safe-upgrade
```

Log out and back in.  It should work.  I hope.  I've only tried it on my T60.

---

### Post by plaa on 2008-04-30
Hi,

I'm having the same problem of no OSD when I change the volume on my T23.  I'm running xubuntu (much more lightweight and still extremely userfriendly!), and by default gnome-settings-daemon was not installed at all.  After installing it nothing has changed, there still is no OSD.  gnome-settings-daemon is not running and if I try to start it from the command line, it says

> ** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...


I was previously quite happy with the 'tpb' package.  It showed the OSD for the volume and display brightness.  However, in Hardy 'hotkey-setup' is required by 'ubuntu-desktop' and it conflicts with tpb.  Therefore installing tpb would require uninstalling both hotkey-setup and ubuntu-desktop.

I recall reading somewhere that uninstalling ubuntu-desktop is not recommended.  Is this true, or can I simply install tpb and have the same OSD I enjoyed in Gutsy?

---

### Post by AnythingBut on 2008-04-30
Hey Plaa,

I don't think my work-around will work for Xubuntu... or Kubuntu.  It's a solution which patches the Gnome desktop.  Xubuntu uses Xfce.

Maybe you'll have some luck with Dr.Phees' solution a couple posts earlier.  I think he installs tpb by building it from source.

---

### Post by plaa on 2008-05-01
> **AnythingBut said:**
> I don't think my work-around will work for Xubuntu... or Kubuntu.  It's a solution which patches the Gnome desktop.  Xubuntu uses Xfce.

The Xubuntu desktop uses many pieces of Gnome software (for example the Gnome Power Manager from Hardy), but evidently not this one.  I now installed the tpb package (which required removing hotkey-setup and xubuntu-desktop), and the OSD works immediately, no restarts even required.  I'll just have to try and remember to reinstall xubuntu-desktop before the next time I upgrade to a new Ubuntu version.  I hope it doesn't otherwise interfere with any updates etc.

---

### Post by ItsJustMe on 2008-05-08
Hi, R30 user here.

The Gnome update installed fine but doesn't appear to do anything on my laptop.  lsmod shows thinkpad_acpi being loaded.  I don't see anything unusual in the logs.  It's a brand new installation so maybe I've missed something obvious :)

---

### Post by AnythingBut on 2008-05-08
Hi JustMe,

I was under the impression that R-series laptops don't have this issue since they don't have a hardware volume.  Does the file /proc/acpi/ibm/volume exist?  If yes, does it's contents (can check with "cat /proc/acpi/ibm/volume") change when you hit the volume buttons?

---

### Post by ItsJustMe on 2008-05-08
I thought it was a lack of a hardware mixer but I could be mistaken.  In any case, the volume file exists but it doesn't change when I press the volume control buttons.

---

### Post by AnythingBut on 2008-05-09
ItsJustMe,

Yeah.  I don't think you have a hardware mixer.  It's probably best if R-Series users don't install the package.  It might make your Volume buttons do nothing.  Is that right?

---

### Post by ItsJustMe on 2008-05-11
My volume buttons haven't done anything since I installed Ubuntu, which is why I tried your package in the first place.  Oh well, it was worth a try.

---

### Post by awong on 2008-06-17
nothing has been fixed on the r31/r30 with the buttons not working?  only reason I havent upgraded from feisty was b/c my volume keys do not work in gusty and higher

---

### Post by AnythingBut on 2008-06-18
> **awong said:**
> nothing has been fixed on the r31/r30 with the buttons not working?  only reason I havent upgraded from feisty was b/c my volume keys do not work in gusty and higher

I'm not sure if this thread applies to R-series laptops.  Check to see if cat /proc/acpi/ibm/volume reports the correct sound volume.  If so, then my package might do the trick.  Otherwise, I wouldn't recommend installing it.

---

### Post by ItsJustMe on 2008-06-18
My volume buttons are working now, perhaps something did get fixed in Ubuntu.  They just don't always initialize properly at startup :(

---

### Post by MaindotC on 2008-06-18
My buttons increment the volume twice for each single press :(  Not a deal breaker but I wonder why it does that.

---

### Post by dr.phees on 2008-07-16
It might be the same problem I had with my Thinkpad. As a default, ubuntu adds key-bindings for the volume buttons which leads to a doubled volume control hardware and software mixer.

I removed the bindings with *System>Preferences>Keyboard Shortcuts*. Now only the hardware mixer is being controlled by the keys and you don't get those huge volume changes.

You might have a look over here:
[http://blog.phees.de/index.php?/archives/2-Thinkpad-buttons-and-gnome-DO-mix!.html](http://blog.phees.de/index.php?/archives/2-Thinkpad-buttons-and-gnome-DO-mix!.html)

---

### Post by AnythingBut on 2008-07-16
> **dr.phees said:**
> 
I removed the bindings with *System>Preferences>Keyboard Shortcuts*. Now only the hardware mixer is being controlled by the keys and you don't get those huge volume changes.

Yip.  That is exactly the problem I was having.  The first message in this thread suggests the same solution.  But, like you I missed having the OSD of the volume level.

> **dr.phees said:**
> 
You might have a look over here:
[http://blog.phees.de/index.php?/archives/2-Thinkpad-buttons-and-gnome-DO-mix!.html](http://blog.phees.de/index.php?/archives/2-Thinkpad-buttons-and-gnome-DO-mix!.html)
Rather than use TPB, I decided to modify a bit of gnome to make the OSD work.  I tried TPB before that, and there were two things I didn't like.  Firstly, it didn't look quite as nice as the built-in gnome one.  Second, it polled the nvram which prevented the cpu from entering power-saving modes.  I also think it might interfere with some of the other thinkpad button handling that gnome does.

---

