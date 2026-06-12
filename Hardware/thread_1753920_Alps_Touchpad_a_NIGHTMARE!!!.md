---
title: "Alps Touchpad: a NIGHTMARE!!!"
date: 2011-05-09
forum: Hardware
---

### Post by zombolo on 2011-05-09
I lost any hope: on my Aspire 3820t my touchpad (Alps) goes crazy randomly. The problem is tap to click. After 1 or 2 hours is almost impossibile to use it. I have to press two or three times to click, without any apparently reason.
Is there any patch I may use to disable tap to click? I LOVE Ubuntu, but this problemn is getting me mad. I am going to come back to Windows (no problems with Seven)... :(

Please HELP, I alredy tried proto=imps and modprobe command without any luck.

Damned Alps...

---

### Post by Ashfaque on 2011-05-10
Completely disabling tapclick shouldn't be a problem. It was in my Mouse settings.

---

### Post by zombolo on 2011-05-10
Not in mine... :/

---

### Post by Ashfaque on 2011-05-10
In Ubuntu Software Center, look for a program called Pointing devices. Maybe that will help.

---

### Post by eyedeal on 2011-05-29
Is it maybe overheating issue? I had erratic touchpad behaviour before on my old Aspire when the whole laptop overheats.

---

### Post by MarjaE on 2011-05-29
Okay. I have been having an insanely difficult time trying to disable my ALPS touchpad to enable typing. You might want to get pointing devices. You might also want to check:

1. Is your touchpad enabled as a touchpad or a PS/2 mouse? Because ALPS has not released its drivers, the standard Linux solution seems to treat the ALPS touchpads as PS/2 mice.

Unfortunately, the system doesn't offer the same controls/preferences for mice as for trackpads.

2. If it is enabled as a mouse, does it treat tapping as button1 clicks or button4 clicks? Apparently, some machines treat them oe way, and others the other way.

I don't have any fixes though. I am not an experienced user, and not one who sees much use for tap-to-click unless the touchpad is out of the way of the keyboard.

---

### Post by zombolo on 2011-05-30
> **eyedeal said:**
> Is it maybe overheating issue? I had erratic touchpad behaviour before on my old Aspire when the whole laptop overheats.

It could be. I am now using ubuntu with powersave governor at boot (933 mhz) just to test if it is an overheat bug (kernel problem?).
With windows 7 no problems with touchpad.

@MarjaE: many thanks for your info. I'll update my status as soon as I have other input info.

---

### Post by teotihuacano on 2011-06-07
Yes it is a kernel problem: it doesn' t even see the touchpad as it is. I was looking for news on it as it is driving me crazy as well. There was a comment saying you can blok touchpad from BIOS.
Arghhhh: it is so complicated to write...

---

### Post by zombolo on 2011-06-07
Yep, it's a kernel bug.
My ALPS touchpad stop clicking (tap-to-click) after a variable period of time...
I am not able to disable tap to click, it-s very annoyng... 

Coming back to Win7... :(

---

### Post by zamarax on 2011-06-09
this bug is so annoying! they only broke it in ubuntu 11.04 it used to work perfectly before!

---

### Post by MarjaE on 2011-06-15
> **zamarax said:**
> this bug is so annoying! they only broke it in ubuntu 11.04 it used to work perfectly before!

It was also broken on 10.10.

---

### Post by zombolo on 2011-06-16
Still waiting for a kernel fix or a workaround to disable tap-to-click in my Acer TimelineX.

---

### Post by zamarax on 2011-07-06
I can also confirm that this is a bug in 11.04 that used to work before with no issues.

---

### Post by MarjaE on 2011-07-07
> **zombolo said:**
> Still waiting for a kernel fix or a workaround to disable tap-to-click in my Acer TimelineX.

Are you using Gnome?

In Gnome, I suggest opening system > preferences > keyboard shortcuts

Add two new shortcuts, one to turn the touchpad off and one to turn it back on.

"Touchpad Off" should activate the command:

xinput set-prop PS/2\ Mouse "Device Enabled" 0

"Touchpad On" should activate the command:

xinput set-prop PS/2\ Mouse "Device Enabled" 1

---

### Post by zamarax on 2011-07-08
I never had an issue in 10.10

as of the latest kernel 2.6.38-10-generic it is still a problem.

---

### Post by orn on 2011-07-28
This is also a problem on a Dell Inspiron N5110 -- unbelievably annoying.

---

### Post by zamarax on 2011-08-02
it's actually terrible, I went over to MINT and no problems :-)

---

### Post by zombolo on 2011-08-03
> **zamarax said:**
> it's actually terrible, I went over to MINT and no problems :-)

Which version?

---

### Post by zamarax on 2011-08-03
Mint(y) 11 :p

---

### Post by nrune on 2011-08-05
That's odd as I have been following this issue for two years or so, and I have never seen a solution as it is a kernel issue.

---

### Post by zamarax on 2011-08-08
well, I will say that in 10.10 it worked flawlessly.

---

### Post by MarjaE on 2011-08-14
> **zamarax said:**
> well, I will say that in 10.10 it worked flawlessly.

That hasn't been my experience. I started with 10.10 and upgraded to 11.04 hoping that 11.04 would solve the [s]issue[/s] malfunction.

---

### Post by zombolo on 2011-08-15
> **MarjaE said:**
> That hasn't been my experience.

I agree. Never worked for me (form Mint 9 to 11).
Please fix this damn touchpad.

---

### Post by MarjaE on 2011-08-17
I have a hotkey to disable the touchpad, but I don't always notice when the computer re-enables the touchpad until I'm typing something and the cursor moves and I lose what I'm typing. NOT GOOD.

---

### Post by raghukr on 2011-08-27
[http://patchlog.com/linux/fix-inspiron-n7110-alps-touchpad-in-ubuntu/](http://patchlog.com/linux/fix-inspiron-n7110-alps-touchpad-in-ubuntu/)

---

### Post by tryten on 2011-09-30
A fix is available är [http://people.canonical.com/~sforshee/alps-touchpad/]("http://people.canonical.com/%7Esforshee/alps-touchpad/"). 
Look for the latest psmouse-alps deb package and install. Restart your computer and it should work.
For more info see the bug report at [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625").
I guess it will be implemented in a future kernel version.
Regards
/Simon

---

### Post by BigEastBeast on 2011-10-28
So far, it seems to be the answer for my Dell Inspiron 15, as it made the needed "Touchpad" tab of the "Mouse" settings available.

How well it goes for others with an Alps GlidePoint remains to be seen.

If my lappy is any indication, you've got the win, mate. :D

---

### Post by quarara on 2011-10-29
> **BigEastBeast said:**
> So far, it seems to be the answer for my Dell Inspiron 15, as it made the needed "Touchpad" tab of the "Mouse" settings available.

How well it goes for others with an Alps GlidePoint remains to be seen.

If my lappy is any indication, you've got the win, mate. :D
Sorry, but what is the solution that worked for you?

---

### Post by savagenights on 2011-10-30
I recently switched over to 11.10 on a laptop (with some difficulty, but another time/place), and about 2 minutes after first logging in the touchpad stopped working. its a toshiba a15-s127 with an Alps glidepoint touchpad, and i spent 1/2 hour trying to find a fix online. no success. so i said what the heck, might as well try. rebooted the laptop into the bios and disabled legacy emulation for USB KB/mouse and USB ports. viola, problem went away.

(disclaimer; it could have just as likely been the act of restarting the laptop, i do not know, and cannot confirm otherwise, i'm simply reporting what worked for me. if it doesnt work for you, i apologize)

---

### Post by ubun_two on 2011-10-31
> **tryten said:**
> A fix is available är [http://people.canonical.com/~sforshee/alps-touchpad/]("http://people.canonical.com/%7Esforshee/alps-touchpad/"). 
Look for the latest psmouse-alps deb package and install. Restart your computer and it should work.
For more info see the bug report at [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625").
I guess it will be implemented in a future kernel version.
Regards
/Simon
I have Acer TimelineX 3830T with Core i3 laptop that has ALPS touchpad.  It didn't work at all for the longest time, but this fix seems to make it work.  Thanks!

---

### Post by robn30 on 2011-11-08
OMG!!  I am thrilled.  The fix worked and now I have scrolling and all.  Happy again.  Thanks.

---

### Post by BigEastBeast on 2011-11-20
> **quarara said:**
> Sorry, but what is the solution that worked for you?

I used what tryten said:

	 		 		 			 			 			 			 		   		 		 		A fix is available är [http://people.canonical.com/~sforshee/alps-touchpad/]("http://people.canonical.com/%7Esforshee/alps-touchpad/"). 
Look for the latest psmouse-alps deb package and install. Restart your computer and it should work.
For more info see the bug report at [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625").
I guess it will be implemented in a future kernel version.
Regards
/Simon

---

### Post by quarara on 2011-11-21
Unfortunately it doesn't work for my hardware.

It seemed we were near to an end [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238"), but the main contributors haven't chimed in anymore.

---

