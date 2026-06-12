---
title: "Slow-buntu 8.10"
date: 2008-10-20
forum: General Help
---

### Post by wizardfait on 2008-10-20
I am on a considerably slow computer (IBM ThinkPad 600e; 366Mhz PII; 544MB RAM; 60GB HDD) but still decient enough to still work to this day and prove useful for simple tasks. I attempted to use Ubuntu 8.04 on this laptop, and it was perfect except for my wireless card (Cisco Aironet, but I fixed it by blacklisting that via padlock and geo thing) and sound.
Now, when it was on there, it was BLAZING fast for this old comp. It was even comparable to 2k/XP!

Now, using the beta of 8.10, it's quite slow actually. I attempted to view the processes to see how much was in use to find 100% processor when idling with a few things open (Update manager, and Firefox, yet both were no longer working, and were waiting for input). Is this an issue anyone else has had?

I'm currently doing updates now, and will notify you if it gets better or worse, but does anyone know why there is such a massive speed difference between the two 'buntu releases?

---

### Post by cicatrix1 on 2008-10-20
There is likely some kernel "feature" (maybe a bug? who knows) or some driver incompatibility.  I hope the updates help.  If not, try a faster window manager like fluxbox or something similar.  I'd be suprised if Gnome or KDE are snappy on that machine :)

---

### Post by wizardfait on 2008-10-22
Actually, the updates didn't help... They proved to cause the machine to be un-bootable. Upon this discovery, I switched back to 8.04, and again, it was MUCH faster.

However, sorry about this impending rant...
But as far as I know, Ubuntu's been going for 4 years now, right? Now, a machine as well known to be used with Ubuntu as the 600e (At least going off of the number of posts I've seen on many forums from different people about 600e's and Ubuntu) should work, right? I understand we don't have all the available resources someone like Microsoft has for drivers, and such... But I mean, come on! This machine's been "perfect" since Windows 98, yet Ubuntu can't even self-correct the sound issue? Also I hear something about if you get the modem working, the serial port won't work, due to a common irq or something. Again, last I checked, this was not an issue 10 years ago!
*Sigh* Okay, sorry about the rant, I just think that as well known problems as these should be able to be fixed, even if not in the release (Upon the CD) but at least through the auto-updater.

Granted, I only know VB and a *little* Java, so I can't really help with programming... But isn't there something that even someone like I can do to help something? Hell, even if it means I "beta test" some stuff for you guys, I'd be happy to if it means better support for things that should have been flawless a long time ago.

Side-note: Under 8.04 and earlier, Yes, Gnome *IS* fast. Fast enough I don't need Fluxbox or KDE. It's actually decient enough that I can have a game like ZDaemon running at a decient speed through Wine, and be working with other things in teh background, without any issues... (Except for the understandable things like if 500 rockets go by, of course the 366 can't handle it at 400 fps. :P  ).

EDIT: Also, with the newest BIOS, in windows I have NO problem going into standby, Hibernate, closing the screen, including when restarting, the keyboard doesn't re-initialize (The NumLock ScrollLock and CapsLock lights do not flash) and the RAM isn't re-counted... Yet in Ubuntu I don't even have the choice for standby, hibernate fails, if I close the screen even after telling it to "Do Nothing" it'll attempt sleep, and become oddly-unresponsive (Will explain below) and when restarting, it acts as if I fully power-cycled it...

Explanation: If the screen is closed (Or the little "trigger" is pressed down) the standby light will flash, as though going to sleep, and the screen will go black, once the screen is opened or the "trigger" is lifted once more, the screen remains black, but with the backlight on. After about 30-ish seconds, the light stops blinking, the desktop shows back up, and keyboard commands work (Such as Alt+F1 to open the menu) yet the mouse doesn't. And sometimes some of the icons dont' reload. Then when attempting to enter TTY1-6 it goes to a black screen, without any text, and no ability to type, yet returning to TTY7 (Gnome in this case) it shows back up again, but nothing is different. Also, even if I didn't attempt one of the other TTYs, it becomes unable to load anything. If I go to Quit, it freezes before bringing up the shutdown options, I can't load an application without it freezing. One time... Yes ONLY ONE time was I able to get to one of the other TTYs, and I typed in my username, and it never asked me for a password, only froze the TTY. I'm assuming in this case the HDD was asleep, and so, couldn't load any of the commands, and it waited for a response which never came... (BTW, the HDD was spinning, just not reading/writing)

Sorry for the immense amount of text, and here it's getting late... (15 mins to Midnight) so I apologize for anything that isn't clear. If someone is willing to work on me with this issue, please do, and if you wish for any clarification, I am willing to oblige. Hopefully when I'm a little more coherent. :D

---

### Post by Vadi on 2008-10-22
give [http://fluxbuntu.org/](http://fluxbuntu.org/) or [http://www.xubuntu.org/](http://www.xubuntu.org/) a try, I think you'll be better off with that :)

---

### Post by snowpine on 2008-10-22
I vote to stick with 8.04 if it works well with your hardware. :) Hardy is a LTS release that will be supported for 3 years. 8.10, as you pointed out, is still in beta and might still be a little buggy.

Fluxbuntu 7.10 RC would be a big step backwards for you--don't do that!

---

### Post by pPrdrm on 2008-10-22
Hi there wizardfait,
If you are using **system monitor** to check your system's CPU usage then they didn't fix a known bug that is related with the nVidia's driver. Try installing **htop** from the repos and see if you get the same CPU usage. If not, then it's system monitor's fault. Also you can quickly check if it's system monitor that's causing the problem you can do this: Maximize the system monitor's window and see the CPU usage it's reporting and then try minimizing it as far as posible. If the ratings are different then Bingo! Hope it helps.

---

### Post by wizardfait on 2008-10-22
> **snowpine said:**
> I vote to stick with 8.04 if it works well with your hardware. :) Hardy is a LTS release that will be supported for 3 years. 8.10, as you pointed out, is still in beta and might still be a little buggy.

Fluxbuntu 7.10 RC would be a big step backwards for you--don't do that!

> **pPrdrm said:**
> Hi there wizardfait,
If you are using **system monitor** to check your system's CPU usage then they didn't fix a known bug that is related with the nVidia's driver. Try installing **htop** from the repos and see if you get the same CPU usage. If not, then it's system monitor's fault. Also you can quickly check if it's system monitor that's causing the problem you can do this: Maximize the system monitor's window and see the CPU usage it's reporting and then try minimizing it as far as posible. If the ratings are different then Bingo! Hope it helps.

Agreed, I'll stay with 8.04... If I can get my sound working... But I really would like 8.10 if I can get it to work just as well, (If not better) Once it's released as stable.

And again. I'm NOT taking any other -buntu's as an option. Either U or bust. :D (I just love gnome)

And as I've said, in 8.04, and earlier, Gnome is NOT an issue! This computer seems to be more powerful than it lets on... I mean, it handles XP fully, no problem with speed, and under Gnome, it's not an issue.

As for System Monitor, no, that's not the issue, Granted, yes, I know it impacts performance... Yet NO, it is not the issue, I only opened it up because it was ALREADY that slow, and I wanted to see what was the cause. Even using top, it works just fine. Rather than installing htop, I just used the normal top.

Is there something better about htop than top?


Lastly, when the full release comes out on the 30th, is it any different if I install the beta, upgrade, or use 8.04 and upgrade as opposed to just installing 8.10 fresh? Other than obviously the extra step... My issue is I'm out of CD-Rs, and I don't know when I'll get a chance to get some more any time soon.



Also, I've searched these forums for solutions to the sound, and it's got a LOT of editing, including totally changing my bios (CMOS actually) settings by reinitializing, and turning off quick boot. Again, Windows has NO problem with NOT doing this... Is there any way to enable sound without having to go through all that?

EDIT: When booting, it states my processor doesn't support scaling. This in incorrect. In Windows XP, it will go from 366, down to (I believe) 270 when scaled down. Granted, it's not much, and I don't want it to scale down unless it's idle anyway, just figured I'd state this so people in charge who might look at this might know.

---

