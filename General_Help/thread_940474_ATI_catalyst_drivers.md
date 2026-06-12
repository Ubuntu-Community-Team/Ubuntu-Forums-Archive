---
title: "ATI catalyst drivers"
date: 2008-10-07
forum: General Help
---

### Post by porchrat on 2008-10-07
Hi once again!

I have noticed that my 4850 is getting rather hot and from what I've read it is a fan issue and is solved with newer drivers that allow you to set the fan speed.

I would like to update my 8.6 catalyst driver to the newer 8.9 (or 8.8 as it seems like 8.7 and above will work just fine).

Do I need to remove my old 8.6 catalyst drivers and if so how would I go about doing that?  Unfortunately I can't remember exactly how I installed the darn thing.  I didn't use envyng.  Can I get away with just modifying the xorg.conf?  or do I actually need to remove the drivers before I start? or will the new drivers simply write over the old ones?

Anyway thanks for your help on this guys.


Edit:  One more thing...I don't know exactly what temperature it is running at as this command (got it off another thread here at good old ubuntuforums) is not recognised:

```
aticonfig --adapter=0 --od-gettemperature
```

---

### Post by porchrat on 2008-10-07
I was going to do a sudo apt-get remove xorg-driver-fglrx but somehow I don't feel that is a good idea.  Unless I first modify the xorg.conf?

Incidentally here is the section of the xorg.conf relating to the video driver:

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection
```

---

### Post by porchrat on 2008-10-07
Nevermind I sorted it myself.

With a little more googling I was able to discover that the ati catalyst driver has an uninstall script under /usr/share/ati

Ran the uninstall script and it set everything back the way it was, even returned the xorg.conf to the original pre-fglrx state.

I then downloaded the ati catalyst 8.9 install script file, ran it to create the .deb files.  Then used dpkg on them and was A for away.

I probably didn't have to bother with all that anyway, probably would've just overwritten, but you can't be too careful.

Hope this helps someone else in the future.

---

### Post by ft23002 on 2008-10-07
Glad to hear you got it worked out and for mentioning catalyst. I have ATI’s Mobility Radeon™ X1400 on a dell notebook and was wondering how well catalyst runs on ubuntu 8.04. Heard mixed thoughts, so whats your opinion on this. Have you had any problems with running catalyst? Any unresolved bugs that most would find bothersome?

Occasionally connect to an external monitor, but have not done so yet with ubuntu and not sure if catalyst is even needed to do this. When running winduds catalyst does aid in switching back and forth between monitors with hot keys and remembers the monitors resolution, refresh rates, and alike.

---

### Post by porchrat on 2008-10-08
I haven't experienced any problems yet, except that the fan on my 4850 doesn't run (although that is less a driver issue and more a firmware problem) so I have to force the fan to run permanently with a command to the aticonfig program.

Other than that everything was configured correctly pretty much out of the box.  It is without a doubt, better than the linux ati drivers that come with the machine.  It is also worth getting catalyst 8.9 as it solves a lot of the problems associated with older drivers (some used to do all sorts of strange things...like prevent hibernation).

---

### Post by Alpha-geek on 2008-10-08
I've been using the latest version of Envy-NG to install ATI Catalyst on my main box (Radeon 3850) & Nvidia drivers on my 2'nd box (8800GT). Seems to work quite well. Makes install & uninstall of video drivers painless.

---

### Post by porchrat on 2008-10-08
> **Alpha-geek said:**
> I've been using the latest version of Envy-NG to install ATI Catalyst on my main box (Radeon 3850) & Nvidia drivers on my 2'nd box (8800GT). Seems to work quite well. Makes install & uninstall of video drivers painless.

Envyng is OK, but it does sometimes have problems loading the .deb files into the kernel properly in which case you end up with those pesky mesa drivers trying to handle all the 3D and everything on the desktop ends up choppy (especially when you move windows around etc.) and you can forget compiz when that happens.

That and the envyng drivers are always older than the ones you get off the ATI website.  I think the current catalyst driver that envyng offers is catalyst 8.6.  As opposed to the latest 8.9.  The 8.7 and up catalyst drivers are the ones that offer the temperature check and fan commands for the card.  I needed those to stop the card from melting as the fan doesn't kick in when the card builds up heat.

Besides installing the drivers yourself is **_EASY_**. You merely follow this guide (ATI only):
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Your 3850 should be fine though as it seems to be a firmware issue isolated to the early releases of the 4850.

---

