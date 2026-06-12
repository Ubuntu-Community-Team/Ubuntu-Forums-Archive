---
title: "ATI fglrx 8.16.20 broke after recent x.org update."
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by fragmental on 2005-09-13
I ran the automatic updates and then tried to run a game, but direct rendering has suddenly stopped working.  Everything loads up fine.  The xorg.0.log says direct rendering is enabled and dmesg says everything works.  however, glxinfo says that direct rendering is not enabled and it doesn't list the ATI glx. It does have sgi twice as 1.2 and 1.4 though.

I'm willing to bet that it was the x.org update that I let automatically update.  The new version is, 6.8.2-10.1.  It's possible that it could be something else, though.  This is incredibly annoying. Does anyone know why this is happening?

I feel like this is not my fault and I'm not sure who to ask to get some answers.

Edit:  Either the new X.org version, or more likely a new mesa gl version, in the update overwrites ATI's opengl library.

Reinstalling the drivers fixes the issue.  For me, I used the [ATI installer method](http://www.ubuntuforums.org/showpost.php?p=341738&postcount=63) and all I had to do was run the installer(no need to shut down X), pick the defaults, and that was it. I didn't even have to restart X.  Direct rendering worked imediately. 

Afteward I did this:
```
cp /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2-ATI
``` 
in the hope that I can just copy the library back if this happens again.


You can find help on the rpm method [here](http://www.ubuntuforums.org/showthread.php?p=348911) .

---

### Post by mlomker on 2005-09-13
[QUOTE=fragmental]I feel like this is not my fault and I'm not sure who to ask to get some answers.[/QUOTE]

It's free software.  If you want someone to get angry at then install Windows.   O:) 

Have you tried [reinstalling the driver?](http://www.ubuntuforums.org/showthread.php?t=64286&highlight=mlomker+ATI) In your case I'd check the contents of the /etc/X11/xorg.conf file first to see if the file was overwritten during the upgrade.  Under the Device Section you should see Driver = "fglrx".

---

### Post by fragmental on 2005-09-13
[QUOTE=mlomker]It's free software.  Welcome to linux.

Have you tried [reinstalling the driver?](http://www.ubuntuforums.org/showthread.php?t=64286&highlight=mlomker+ATI) ?[/QUOTE]

If I had a nickle for every time someone "welcomed" me to linux.  I should hold an annual "welcome to linux" convention where all the experts pretend like their noobs.

Edit: not that I'm an expert...because I'm not, but I've been using it for probably 5 or 6 years now, off and on.

---

### Post by mlomker on 2005-09-13
Sorry, I thought it was 5 posts and not 50.  Vision problems.  Regardless, your attitude doesn't reflect that.

---

### Post by fragmental on 2005-09-13
[QUOTE=mlomker]Sorry, I thought it was 5 posts and not 50.  Vision problems.  Regardless, your attitude doesn't reflect that.[/QUOTE]

So, being inquisitive and believing that a breakage is somhow not your fault is a bad or otherwise noobish attitude?  You probably just misunderstand my meaning.

Besides, even if I had 5 posts on the ubuntu forums, that doesn't mean I'm new to linux or forums or ubuntu or anything else for that matter.

---

### Post by mlomker on 2005-09-13
[QUOTE=fragmental]I feel like this is not my fault and I'm not sure who to ask to get some answers.[/QUOTE]

This came across as confrontational to me.  Regardless, take a look at the thread that I had created and let me know if it works for you.  I'm working on a how-to based on that thread.

---

### Post by fragmental on 2005-09-13
[QUOTE=mlomker]This came across as confrontational to me.  Regardless, take a look at the thread that I had created and let me know if it works for you.  I'm working on a how-to based on that thread.[/QUOTE]
 The reinstalling the driver thread?  That's the only one I see.  [This thread](http://www.ubuntuforums.org/showpost.php?p=341738&postcount=63)  pretty much explains everything about how I got my driver installed.

I will probably repeat at least some of those steps, but at the moment, I just want to play a game, and the drivers happen to be on another unhooked hard drive because I'm trying to diagnose why my new computer is freezing up.  too much effort and stress when I just want to play a game. I'll fix it later.  I'm just going to reboot into windows and play games there(I'm a pc gamer, and a 3d design student whose college uses 3dsmax.  Therefore I basically need to keep windows around.  I typically switch back and forth when one of the Operating systems is pissing me off or when I want to see if something is a hardware or software failure. Besides, the school gave me XP and 2k gratis.)

I assumed, since I'm probably not the only one with the drivers, and there may be other people upgrading, that others might have run into the same issue.  I also assumed that someone who created the packages that cause the issue might have some idea about how to fix them.  That's what I meant by "I feel like this is not my fault and I'm not sure who to ask to get some answers."  Poor choice of words most likely; especially for a forum.

---

### Post by mlomker on 2005-09-14
[QUOTE=fragmental]get some answers."  Poor choice of words most likely; especially for a forum.[/QUOTE]

No problem!  I wrote a detailed [HOW-TO](http://www.ubuntuforums.org/showthread.php?p=348911) yesterday on how to install/reinstall the latest drivers.  Give it a whirl and let me know if I can help.  I'm just one of the guys looking for work-arounds...not sure if developers read these forums (they're probably too busy).

---

### Post by fragmental on 2005-09-16
[QUOTE=mlomker]No problem!  I wrote a detailed [HOW-TO](http://www.ubuntuforums.org/showthread.php?p=348911) yesterday on how to install/reinstall the latest drivers.  Give it a whirl and let me know if I can help.  I'm just one of the guys looking for work-arounds...not sure if developers read these forums (they're probably too busy).[/QUOTE]

The ATI linux installer has ubuntu install support now, and I think that's easier than using alien(albeit, a larger download).  Check the link I linked to earlier for that.

---

### Post by mlomker on 2005-09-17
[QUOTE=fragmental]The ATI linux installer has ubuntu install support now, and I think that's easier than using alien(albeit, a larger download).  Check the link I linked to earlier for that.[/QUOTE]

That was the second method that I had tried, after the built-in drivers, and it didn't work for me.  I've had good results walking people through the alien routine.

You'll also discover that future operating system updates will knock out your driver because there isn't anything in Synaptic to give you a warning.  You can always reinstall when you notice things get slow, of course.

---

### Post by fragmental on 2005-09-17
[QUOTE=mlomker]That was the second method that I had tried, after the built-in drivers, and it didn't work for me.  I've had good results walking people through the alien routine.

You'll also discover that future operating system updates will knock out your driver because there isn't anything in Synaptic to give you a warning.  You can always reinstall when you notice things get slow, of course.[/QUOTE]
 Yeah, not everyone seems to have luck with the installer.  I think, usually, if it doesn't install for me it was my error because I didn't do something I should have done.  You could add it to the howto as an alternative method, but I could always write up a detailed howto and post it too.

This might be why the driver doesn't work, because the driver is installed, it's just the gl drivers which are wrong:
> Whenever they decide to update the xlibmesa-gl package (usually in a security update for Xorg) you will get an error that it cannot overwrite the /usr/X11R6/lib/libGL.so.1.2 file. This file was overwritten by the new ATI package and we need to keep it.

In your terminal:

Code:

cp /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so.1.2-ATI apt-get update --force-yes cp /usr/X11R6/lib/libGL.so.1.2-ATI /usr/X11R6/lib/libGL.so.1.2

I went away on a trip and just got back yesterday. I think my computer has stopped crashing so it seems like the time is right to reinstall the drivers.  Hopefully everything will work.

---

### Post by mlomker on 2005-09-17
I'll have to ask why there isn't an option to delete a posted message.  That seems odd...unless I'm just not seeing it.

---

### Post by agm642 on 2005-09-17
[QUOTE=mlomker]I'll have to ask why there isn't an option to delete a posted message.  That seems odd...unless I'm just not seeing it.[/QUOTE]
 You have to edit it and from there pick "Delete Message"

Oops, wrong, that was in another forum... Sorry. ](*,)

---

### Post by locutus42 on 2005-09-17
Not sure if this is related but recently I had to a GL update fail because fglrx had it's version installed. In the error message window, it showed where in the /var/cache/apt/archives the particular package was. What I did was run dpkg to force the install and then reinstalled the fglrx driver. It went something like this:

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite xlibmesa-gl_6.8.2-10.1_i386.deb


This might be unrelated, but if not, after installing Kubuntu 5.10 preview and the ATI 8.16.20 driver, I noticed that the Xorg DRI interface was now at v5.0 and ATI wanted the v4.x version so 3D wasn't working.

PS. 90% of this thread is wasted space... I hope people start using the Edit-Delete feature so others might find this thread more interesting and informative.

---

### Post by fragmental on 2005-09-17
[QUOTE=locutus42]Not sure if this is related but recently I had to a GL update fail because fglrx had it's version installed. In the error message window, it showed where in the /var/cache/apt/archives the particular package was. What I did was run dpkg to force the install and then reinstalled the fglrx driver. It went something like this:

cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite xlibmesa-gl_6.8.2-10.1_i386.deb


This might be unrelated, but if not, after installing Kubuntu 5.10 preview and the ATI 8.16.20 driver, I noticed that the Xorg DRI interface was now at v5.0 and ATI wanted the v4.x version so 3D wasn't working.

PS. 90% of this thread is wasted space... I hope people start using the Edit-Delete feature so others might find this thread more interesting and informative.[/QUOTE]
 I think the ubuntu update manager might automatically force update of the opengl drivers.  At least, mine were written over, and all I did was use the ubuntu auto update.

It could be different though.  All I know is that everything worked like normal except that dri didn't work and all the gl stuff said "mesa" instead of "ati".

I think it's a bit difficult to clean up the thread without the ability to delete posts. I could post an update on the first post about why it might have been broken and how to fix it, and I can append *solved* to the thread title.

---

### Post by mlomker on 2005-09-18
>  I could post an update on the first post about why it might have been broken and how to fix it, and I can append *solved* to the thread title.

I'm having a [discussion](http://www.ubuntuforums.org/showthread.php?t=66516)  about the deletion issue on the site discussion forum right now.  The change may have been well-intended but I disagree with it.

---

