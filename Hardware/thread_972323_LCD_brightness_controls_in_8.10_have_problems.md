---
title: "LCD brightness controls in 8.10 have problems"
date: 2008-11-05
forum: Hardware
---

### Post by radu.c on 2008-11-05
Hi,

I recently upgraded from 8.04 to 8.10 and had a few problems. I dealt with most of them, but don't know what to do about these:

- When I wake my laptop from suspend, sometimes the screen remains black (backlight off). Pressing the brightness keys, Control key, or moving the mouse cursor don't change this. Changing to a console and back displays X again

- At other times, my laptop decides, unprovoked, to play with the brightness, slowly dimming the screen, and then slowly increasing the brightness back.

- When using the brightness controls after a fresh wake or boot, the controlling objects freeze for 20-30 seconds, after which they start working normally. That's both for the brightness applet and the Fn+Brighness keys. The brightness keys do their thing, but the overlay window showing the intensity either doesn't show up, or it does but then stays on top until the brightness app unfreezes.

- Using the brightness keys, my screen goes black at about 70%. With 8.04 I could get the backlight progress bar all the way to 0% and still see a picture. Why? Even more: it's not totally black. I cab still see a backlight on the right side of the screen (can see the mouse cursor clearly in that area, although the rest of the screen is pitch black).

- When removing the AC power cord, I hear the click that means "power source changed" but it takes forever to switch to battery mode (display battery icon, possibly warning popup), it dims my screen in another eternity, and after it's done dimming my screen, I can't really see anything on it). When I connect the power cord back, it takes forever again to notice it.

I have a Dell Latitude X1 laptop. The brightness controls worked without a glitch in 8.04. Any ideas what changed in this area that broke it so bad?

This feels like something is timing out somewhere.

Thanks,
    Radu C

---

### Post by Yonoz on 2008-11-14
> **radu.c said:**
> - At other times, my laptop decides, unprovoked, to play with the brightness, slowly dimming the screen, and then slowly increasing the brightness back.

- When using the brightness controls after a fresh wake or boot, the controlling objects freeze for 20-30 seconds, after which they start working normally. That's both for the brightness applet and the Fn+Brighness keys. The brightness keys do their thing, but the overlay window showing the intensity either doesn't show up, or it does but then stays on top until the brightness app unfreezes.

- Using the brightness keys, my screen goes black at about 70%. With 8.04 I could get the backlight progress bar all the way to 0% and still see a picture. Why? Even more: it's not totally black. I cab still see a backlight on the right side of the screen (can see the mouse cursor clearly in that area, although the rest of the screen is pitch black).

- When removing the AC power cord, I hear the click that means "power source changed" but it takes forever to switch to battery mode (display battery icon, possibly warning popup), it dims my screen in another eternity, and after it's done dimming my screen, I can't really see anything on it). When I connect the power cord back, it takes forever again to notice it.
I'm having these same problems with my ThinkPad X41, I also noticed these:
When the screen dims slowly, the brightness setting will not respond, or it will respond only to the first keystroke.
Sometimes the brightness setting will allow me to dim the screen to near-pitch black, also with the bottom right corner showing some light, and sometimes it will not. I rather like the option of dimming the screen to near-black.
When the brightness controls freeze, the area where the window with the brightness bar will freeze, sometimes with the window showing, and sometimes it simply shows a frozen image of whatever happened to be in that part of the screen when it froze.

Also, at boot I get "EC and CMOS do not agree on brightness".

---

### Post by viritrilbia on 2008-12-01
I'm seeing similar issues on my Thinkpad X41 after upgrading to 8.10.  The spontaneous dimming of the screen is quite unnerving.  Also, after waking up from suspend, often (always?) the brightness-display popup in the middle of the screen (that usually shows briefly whenever I press the brightness-up or -down keys) shows for a while before disappearing.

---

### Post by cragged on 2008-12-01
The second reboot after upgrade to 8.1 I was having similar symptoms on Dell xps m1330. Going through some of the postings I started with a simple Ctl-Alt-Bckspc to reboot X and resolution and brightness issues seem to have settled out.

---

### Post by walkeraj on 2008-12-03
> **Yonoz said:**
> I'm having these same problems with my ThinkPad X41, I also noticed these:
When the screen dims slowly, the brightness setting will not respond, or it will respond only to the first keystroke.
Sometimes the brightness setting will allow me to dim the screen to near-pitch black, also with the bottom right corner showing some light, and sometimes it will not. I rather like the option of dimming the screen to near-black.
When the brightness controls freeze, the area where the window with the brightness bar will freeze, sometimes with the window showing, and sometimes it simply shows a frozen image of whatever happened to be in that part of the screen when it froze.

Also, at boot I get "EC and CMOS do not agree on brightness".

My issues are identical, I am also using a Thinkpad X41

---

### Post by xhero0 on 2008-12-05
same type of issue with a sony vaio vgn-tx750p

I am also having weird video issues like when I start up I get vertical lines flash by, and when I start a video using VLC or totem...Sound it quarky,like if I use firefox and I HAVE TO kill firefox and then watch a video!

I also upgraded from 8.o4 to 8.1o

Lates!

Joe M.

---

### Post by cupevampe on 2008-12-10
Same issue, happens with vlc mostly but i've seen it in other occasions too

i have a fjitsu siemens amilo pi2515, graphics card x3100 intel... i use 8.10 :)

any idea?

---

### Post by radu.c on 2009-01-16
I downgraded to gnome-power-manager 2.22.1-1ubuntu4, which is found in Ubuntu 8.04 LTS, and my dimming problems were fixed. Now I'll have to pin it so it doesn't show in updates, but it will have to do until someone fixes it. I didn't even port it. Installed it straight from Ubuntu 8.04

[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_i386.deb)

[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_amd64.deb)

There's another package that connects my display brightness hot keys to the display brightness popup, and as soon as I find out what that one is, I'll downgrade it as well.

And I think there are a few others too, as there's a lag between me unplugging the AC power and Ubuntu telling that to me. Same goes when I plug the AC power back.

---

### Post by uberlinux on 2009-02-21
> **radu.c said:**
> I downgraded to gnome-power-manager 2.22.1-1ubuntu4, which is found in Ubuntu 8.04 LTS, and my dimming problems were fixed. Now I'll have to pin it so it doesn't show in updates, but it will have to do until someone fixes it. I didn't even port it. Installed it straight from Ubuntu 8.04

[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_i386.deb)

[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.22.1-1ubuntu4_amd64.deb)

There's another package that connects my display brightness hot keys to the display brightness popup, and as soon as I find out what that one is, I'll downgrade it as well.

And I think there are a few others too, as there's a lag between me unplugging the AC power and Ubuntu telling that to me. Same goes when I plug the AC power back.

This package has made things much easier on me, though I'm now stuck just a little brighter than I'd like to be.  
I can't control brightness up nor down now.  Sony Vaio VGN-NR498 Intel GMA X3100
Thanks so much,
 - Kodiak

---

### Post by nickstephens on 2009-03-24
This issue has been around for a while now and I am more than curious if downgrading is the best/ only solution. I am also a little concerned as from my understanding, the dim controls (through power management) are inherently linked to the desktop. If you downgrade won't you compromise other programs related to the desktop? The deinstallation of acpi seems risky and I can't see if gnome-power-manager 2.22.1-1ubuntu4 will work in parallel. Any comments or suggestions?

---

### Post by Gerhardt on 2009-04-03
having similar issues with a lenovo/ibm thinkpad x61 7676

intrepid worked fine. auto dim worked great. then i installed all the updates that were recommended. at first, screen seemed fine. then i suspended and when i came back, everything was super dark. after a reboot, normal brightness occured. (and btw, the buttons for bright+up and bright+down work fine on the keyboard so far as displaying the on screen display, but nothing changes)

but now when i unplug the AC power, i get the notification just fine, and the onscreen display pretends it is changing the brightness, but it remains at full bright.

the auto-dim after a certain amount of idleness does seem to be working still, however, and did bring itself back to full brightness after moving the mouse.

i would like lower brightness to save battery though.

i am exactly 1 day new to linux/ubuntu, so i'm hesitant to install old packages unless someone can recommend to me that this absolutely works. thanks.&#9830;

---

### Post by nickstephens on 2009-06-06
I know upgrading to 9.04 supposedly solves this issue and there are plenty of others that seem to have encountered similar issues with the power management program

[http://ubuntuforums.org/showthread.php?p=7133174](http://ubuntuforums.org/showthread.php?p=7133174)

and even a potential solution if you work through the example given below. 

[http://ubuntuforums.org/showthread.php?t=1137705&highlight=brightness+controls](http://ubuntuforums.org/showthread.php?t=1137705&highlight=brightness+controls)

Is there a solution to this problem I can't appear to find on the forums for 8.10 that somebody else has come across? Upgrading to Jaunty isn't an option with this computer :(

Nick

---

### Post by iluii on 2009-06-07
When it comes to the brightness on battery power, a quick work around is to under power management disable Dim display when idle and reduce backlight brightness and also make sure to pick when laptop screen is closed do nothing and allow computer to sleep never. this worked for me in xubuntu 8.10 Ill provide a screenshot for you guys, just make sure u close the lid if ur gonna leave the computer alone!

---

