---
title: "Getting Toshiba Portege M400 Soon, Want An Ubuntu Checklist"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by jbizzler on 2007-07-31
Hi. I'm getting a Toshiba Portege M400 soon, and I think I want to install Ubuntu on it. I know things won't work automatically, and I want to know exactly what won't work out-of-the-box, and be ready to fix them. Thanks.

Edit: Not only what won't work, but also maybe things I can enhance?

---

### Post by Eagleon on 2007-08-01
Hi....

I own a toshiba portege m400.... and my first advice to you is this: I highly recommend that you do not purchase this laptop. Especially if you are going to be using ubuntu. From the day I got this computer I have regretted it. Let me explain why I feel this way.... there is a possibility that the reasons I feel this way may not apply to you:

1) Ubuntu will not support the SD flash memory card 
2) Ubuntu will not allow you to take advantage of the special tablet features that make this such a cool computer. You will be able to write on the screen.... but that is where it ends. None of the special tablet keys will work on the tablet panel. 
3) They only ship you the laptop itself.... they do not send you any CD's along with it. You have to make your own recovery CD... and that is OK for most people. I didn't mind at first either. The only problem is that, the recovery CD you make will not let you recover anything. At least this was the situation in my case. I wiped out the windows partition after creating the recovery CD so I could put ubuntu and put windows back into a new partiton. Sadly, the recovery CD kept giving error messages. Trust me.. I tried a lot of things to get the data back, and no luck. Also, if you plan to install  windows from scratch.... good luck if it is XP. In XP you need to provide SCSI drivers manually through a floppy (and only floppy)... unless you slipstream a XP installation... which also failed in my case for some reason. 
4) Lousy support. The support angents dont know why this happened. They don't have e-mail support and keep you on hold for hours on the phone. Then they tell you to take the machine to a 3rd party repair service affiliated with them. When you contact them, they tell you it will take 4 weeks to process. 
5) Fingerprint scanner will not work in ubuntu
6) all the features you will not get to use in ubuntu make this investment a bad one.... if you are going to buy this laptop stick with windows. Toshiba sucks with linux support.....

Good luck....

---

### Post by Eagleon on 2007-08-01
...then again, if you do end up buying this laptop.... let me know if you figure out how to get everything to work in ubuntu. :) thanks....

---

### Post by jbizzler on 2007-08-01
HAHA gotcha. My school is requiring every new students to get a tablet, and they had special deals on 3. The M400 was the best of the 3, IMO, and it comes with Vista Business backrevved to XP Tablet Edition. The school encourages us to experiment with different operating systems, and I know Ubuntu is really popular right now.

I'll give it a shot and report my results.

---

### Post by dna on 2007-08-04
Yeah, the SD slot doesn't seem to work, haven't looked into it yet. Shows up on lspci so probably just an automounting or driver problem.

Been working on this [page]("http://www.math.upenn.edu/~vincentb/UbuntuPortege.html") to try to get the tablet buttons and such to work but with limited success. Only worked on it for a few minutes though. Going to try the fingerprint scanner after I get these keys mapped properly.

I had to modify the script a bit to get rid of some errors. Also don't know about the keycodes in the second section since the one in the link was written for a Canadian keyboard.

Everything else works just fine. I didn't make a backup disk so don't know about that, I just compressed down the winders partition to ~15G and netboot installed Feisty since it doesn't have a CD player. Did come with a Vista install and driver disks.

Also added *Option          "Button2"       "3"* to the 'stylus' section of xorg.conf so the stylus button acts like the right mouse button. 
 
```
#!/bin/sh

orientation=`/usr/bin/X11/xrandr --query | /bin/grep "Current rotation" | /usr/bin/awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
	/usr/bin/X11/xrandr --orientation right
	/usr/bin/X11/xmodmap -e "keycode 11 = Left"
	/usr/bin/X11/xmodmap -e "keycode 13 = Up"
	/usr/bin/X11/xmodmap -e "keycode 10 = Right"
	/usr/bin/X11/xmodmap -e "keycode 12 = Down"
	/usr/bin/X11/xmodmap -e "keycode 14 = KP_Enter"
else
	/usr/bin/X11/xrandr --orientation normal
	/usr/bin/X11/xmodmap -e "keycode 11 = 2 quotedbl twosuperior oneeighth twosuperior oneeighth"
	/usr/bin/X11/xmodmap -e "keycode 13 = 4 dollar onequarter currency onequarter currency"
	/usr/bin/X11/xmodmap -e "keycode 10 = 1 exclam onesuperior exclamdown onesuperior exclamdown"
	/usr/bin/X11/xmodmap -e "keycode 12 = 3 section threesuperior sterling threesuperior sterling"
	/usr/bin/X11/xmodmap -e "keycode 14 = 5 percent onehalf threeeighths onehalf threeeighths"
fi
```

---

### Post by kiwioperator on 2007-10-28
The M400 series (I have the M405) has been a pain in the *** since day one. XP was alright but there seems to be a common freezing with the system out of nowhere and in different applications.

With Ubuntu installed (Gutsy) it has been even more of a pain in the ***. And I *do* like Ubuntu but finding a way around the hdd protection that is offered with the XP installation is killing me. Slightest movement and the system crashes- have to hard reboot. Forget the cool tablet functionality of the XP tablet OS. Linux has along way to go and it's just not user friendly yet. The biometrics for Ubuntu, Thinkfinger, is next to useless. I have set it up correctly but have found no use for it yet. You CANNOT login with Thinkfinger. I liked that with XP.

Overall, both OS's have problems with this tablet but XP has less. I do like the functionality (when it functions consistently) of the tablet. I like to flip that screen around sometimes and read an e-book on the couch. But with this one, I am ready to give it to my wife and get a regular laptop. Gusty is going on it of course.

I would like to be able to run Adobe CS3 (you can have gimp) and Office Suite 2007 (OpenOffice is fine most of the time but 2007 just has more features) in VMware or virtual box (or similar) without having to do dual boot. 

I know I need more RAM (1024mb doesn't cut it). The M405 can be upgraded to 4gb RAM but I think I am going to put that cash into another laptop.

---

### Post by payado on 2007-11-02
I agree with Eagleon.  I have had an M400 for 18 months and it has been trouble since day one.  I was originally on XP and had some problems (overheating/lock up was a major one).  I decided to blow away all the Toshiba Craplets and do a clean install.  When I went to restore from the restore discs I had to create it wouldn't work.  I scraped XP and put Vista on it, which I have issues with, but works better than XP.  I finally installed 7.04 and it worked great from a stability standpoint.  Functionally, the tablet PC functions are useless.  I was hopeful that 7.10 would help resolve some issues but it appeared to create more problems (can't do a clean install on the sata drive yet).  Since then, I have tried Sabayon (looks good, but a functional disappointment) and OpenSuse (half decent tablet support).  But in the end, I think I will go back to Ubuntu and try to apply what I can from my OpenSuse experience: [http://en.opensuse.org/TabletPCs](http://en.opensuse.org/TabletPCs)

I guess the bottom line is that Ubuntu is great and the M400 is a mediocre tablet PC at best.  

Doug
:confused:

---

