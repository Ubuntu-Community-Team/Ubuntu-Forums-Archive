---
title: "My Karmic doesn't feel like Karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Pro$pect on 2009-10-30
Is it because I upgraded from Jaunty instead of a fresh install that I don't have any of the new stuff 9.10 is supposed to have? I don't have Software Center, One, ect...my log-in window doesn't look like the new darker one that it's supposed to have either.

When I was upgrading I lost internet connection twice so I had to start and stop it a couple times, any way to check that everything installed fine?

---

### Post by XDevHald on 2009-10-30
Were you using **update-manager -d** in terminal? Running the Update Manager alone to check for updates won't do the job. Hope this helps :-)

---

### Post by magneze on 2009-10-30
Sounds like you haven't upgraded. I upgraded this way and got all that ok.

Just reinstalled so I could get ext4 and grub2 tho ..

---

### Post by Pro$pect on 2009-10-30
I used the update manager and just clicked the install button where it says a new distro is available, and it says i'm running karmic in the about ubuntu section.

---

### Post by XDevHald on 2009-10-30
Reboot and load into (recovery mode) and select **Fix broken packages** and try again. Also be sure to use **Free up space** as well in that menu. Keep us posted.

---

### Post by Pro$pect on 2009-10-30
did both things, it said update was ok and just removed 4 apps. I installed the software center and one so I guess i'll just have to do that for everything because it looks like there's nothing wrong besides missing apps.

---

### Post by picklemonkey on 2009-10-30
> **Pro$pect said:**
> Is it because I upgraded from Jaunty instead of a fresh install that I don't have any of the new stuff 9.10 is supposed to have? I don't have Software Center, One, ect..
I have the same problem.  I still have Add/Remove Programs instead of the Software Center and I can't find Ubuntu One.  I also upgraded via the Update Manager.  I didn't lose my connection while upgrading, and I know I'm running the new version because I have the new login splash screen, my bootup takes half as long as it used to, my Intel video problems are fixed, and I have the new sound/network icons in my tray.  When I go to my Application menu and go to Help, it tells me I'm on 9.10.

I'm using xubuntu... would this matter?

---

### Post by XDevHald on 2009-10-30
> **picklemonkey said:**
> I have the same problem.  I still have Add/Remove Programs instead of the Software Center and I can't find Ubuntu One.  I also upgraded via the Update Manager.  I didn't lose my connection while upgrading, and I know I'm running the new version because I have the new login splash screen, my bootup takes half as long as it used to, my Intel video problems are fixed, and I have the new sound/network icons in my tray.  When I go to my Application menu and go to Help, it tells me I'm on 9.10.

I'm using xubuntu... would this matter?


Xubuntu is XFCE of Ubuntu and can run 9.10 no matter what. If it says 9.10 then you're up to date. As to why it did not carry over the new apps and changes is possibly a download error from the servers and you just need to install them.

See: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview) <-- gives changes and what's new in 9.10 this way you can get them from Synaptic

---

### Post by picklemonkey on 2009-10-31
> **XDevHald said:**
> Xubuntu is XFCE of Ubuntu and can run 9.10 no matter what. If it says 9.10 then you're up to date. As to why it did not carry over the new apps and changes is possibly a download error from the servers and you just need to install them.

See: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview) <-- gives changes and what's new in 9.10 this way you can get them from Synaptic
thanks.  I was able to install the Software Store package "software-center" from Synaptic, and was then able to install Ubuntu One from the Software Store (I'm not sure I want this one yet!).  I still have the Add/Remove Programs link at the top of my Application menu, though.  Is there a way to remove it, or should I just leave it alone?

I also expected my Shiretoko 3.5.5pre version of Firefox to get upgraded to the standard 3.5 Firefox with the Karmic upgrade, but I'm still stuck with Shiretoko.  Any idea why this wouldn't have upgraded either?

Prospect, sorry if I hajacked your thread!  Try the Software Store stuff I mentioned.  It was successful for me and may bring you one step closer

---

### Post by XDevHald on 2009-10-31
picklemonkey: For one I am not sure about Shiretoko and the development they run and it's relationship to Firefox. Secondly, to hide (not remove just incase if you need any apps again) you can right click on the gnome menu I.E: Applications, Places, or System and select **Edit Menus**.

This will give you a side of your desktop that will allow you to hide the applications you don't want to appear for now and don't use often or at all, this way you don't remove anything that you may need later on.

---

### Post by picklemonkey on 2009-10-31
> **XDevHald said:**
> picklemonkey: For one I am not sure about Shiretoko and the development they run and it's relationship to Firefox. Secondly, to hide (not remove just incase if you need any apps again) you can right click on the gnome menu I.E: Applications, Places, or System and select **Edit Menus**.

This will give you a side of your desktop that will allow you to hide the applications you don't want to appear for now and don't use often or at all, this way you don't remove anything that you may need later on.
Maybe I'll post more about the Shiretoko stuff later once the rest of the community settles down with their post-Karmic issues.  It's not urgent, since I can still browse the web.  Don't want to take time away from others who are having bigger problems!

Seems the Xfce Menu is different from the standard Gnome menu, but I was able to find the menu file and edit it directly in Mousepad to get it pulled off.  Maybe I'll look for a Xfce Menu GUI editor package somewhere if I want to make more changes later.   Appreciate it man

---

### Post by winotree on 2009-10-31
Just a guess on my part, but perhaps you have Shiretoko 3.5.5pre because the PPA repository is still enabled?  ;-)

---

