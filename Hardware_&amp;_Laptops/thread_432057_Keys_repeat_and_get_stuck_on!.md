---
title: "Keys repeat and get stuck on!"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by mink on 2007-05-03
Posting as an ubuntu newbie!  I installed Dapper Drake as part of a Linux/Windows dual boot on my Acer Aspire 5000 laptop last year in the summer and have been using it happily since, or at least until last week.  I have an AMD 64 processor and was trying to get Mozilla to work with Flash player (which apparently is impossible since Flash doesn't support 64 bit processors at the moment,  at least for linux).  Anyways, in the process of trying to work around this I added a bunch of software using the syntaptic package manager.  Shortly after doing this my keyboard started behaving badly (well, not really my keyboard, but linux), keys will get "stuck" on the repeat and I'll get either a ton of repeated letters in my documents or, for instance, 200 tabs open in Mozilla which then crashes my browser.  Often the ctrl/alt/shift/enter keys as well as the two mouse buttons (touchpad and usb mouse) get stuck "on" as well.    This is making my life most difficult!  I know it's not a hardware problem because the keyboard/mouse work fine when I boot in windows.  I found some suggestions when I checking the last time I had my Linux partition up, but it crashed and I haven't been able to find those links again.  I did try setting some mouse command to 40, which was one suggestion (I can't remember the exact syntax and now can't locate the post that it came from) but that didn't work.  I've tried turning the key repeat off, which works to some extent, but the ctrl/alt/shift/ keys and the mouse buttons still won't work properly even with the repeat off.  I keep seeing the word "overclocking" bandied about but I'm not sure that this is the problem I'm having.  I checked my cpu usage and it's not abnormally high (25% with a bunch of processes running).  Any suggestions?!  This is preventing me from getting my dissertation work done!!

Thanks much!

---

### Post by cornelius2 on 2007-05-10
I have the same problem. It happens once or twice every day at most and happens randomly.
I sometimes get Alt-Tab repeat like crazy, sometimes Ctrl-Tab in Firefox, sometimes keyboard command shortcuts (opened up a hundred terminals once). It's pretty annoying when it happens.
I don't know if they are related but I'm using compiz and Xgl.

---

### Post by BadTm on 2007-06-14
Can anyone provide any insight on how to fix this problem?  When I type, it almost seems like I'm missing random characters and repeating others...  very frustratinnnng!  <-case in point!

---

### Post by Magneto on 2007-06-14
same problem here
BadTM - a temporary solution is to go to System-Preferences-Keyboard and disable repeat but that means hitting arrows keys a million times from a terminal inside Gnome. Im gonna scrap this installation and move to another distro if this and my pointer issue remain a problem.

---

### Post by carlkhabbaz on 2007-06-23
~phew! and I thought I needed to replace my keyboard!
the same is happening with me.. it's a bummer when I press ALT+F4 and all the windows close suddenly.. hehe
anyone can provide a solution please?

---

### Post by guyg on 2007-07-05
Same problem here. I'm using Feisty + Xgl + Compiz Fusion. This problem didn't used to happen when I used Edgy + Xgl + Beryl. It also doesn't happen in Windows.

I filed a bug with Compiz Fusion, and they helpfully commented that this is a well-known Xgl problem.

---

### Post by atulprasad on 2007-07-05
Hey guys.. same problem with my PC also... i installed it just yesterday.. with nothing extra... guess this is a problem with Ubuntu 7.04.. because 6.06 and 5.10 were working just fine

---

### Post by myoungf1 on 2007-07-05
Probably a different problem but I think it relates to this anyways.  I get my mouse cursor, from time to time, that starts to move randomly without me moving it.  It opens new windows and programs, randomly, and until I do an alt+tab I can't get it to stop.  It is as the keyboard problem very annoying and would like if anyone has a fix.

---

### Post by guyg on 2007-07-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/124406](https://bugs.launchpad.net/ubuntu/+bug/124406) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[Filed a bug about this problem]("https://bugs.launchpad.net/ubuntu/+bug/124406")

---

### Post by guyg on 2007-07-06
Can anyone confirm that this happens with Xgl + Compiz? (I mean standard compiz, not compiz-fusion, which is unsupported)
cornelius2 perhaps?

The bug I filed was closed because I'm using fusion. If someone can confirm it happens with standard compiz, I will reopen it.

---

### Post by Zega on 2007-07-09
I had the same problem on my Asus G1 Laptop running Kubuntu and it turned out to be a sensitivity issue.  The fix I used was at the console type "xset r rate # #"  without the quotes.   The two numbers are the time till autorepeat starts, and the second number is the delay between repeated characters.  I have had success with xset r rate 1000 50.  Hope this helps.  Also for what it's worth I am running Beryl as well, but the problem existed under the basic kde window manager.

---

### Post by guyg on 2007-07-13
Changing the repeat rate made the problem disappear almost completely. Thanks!

---

### Post by thomascj on 2007-07-16
I'm having the exact same problem, and I'm not running xgl, or compiz fusion.  I am, however, running fglrx.  Turning off keyboard repeat fixed it -- but I do use the terminal and it really sucks having to press backspace that many times...

Anyone else fixed this problem?

---

### Post by Magneto on 2007-07-23
wow glad to see I wasnt the only one but not glad no one has a fix beyond disabling repeat

---

### Post by goodhorsehymn on 2007-07-28
Same problems here - presumed it was a problem with my setup, but now see that it is more widespread.  

Anyone made any progress?

---

### Post by guyg on 2007-07-29
goodhorsehymn, you can help by adding a comment about your problem, including your setup, at the bug report I posted above.

---

### Post by bean77 on 2007-08-22
I have this issue as well.

---

### Post by 0x656b694d on 2007-09-03
The same problem. But as i can see it is related to my compiz session. In normal Gnome session have never met such a problem.
(compiz 0.5.5 with fusion plugins)

---

### Post by SwollenGoat on 2007-09-05
I just started having this problem as well.  The severity of it will be obvious from instances of the repeating problem in this post.

In my case, it is independent of     the gui.  It happens in bbbbbboth GNOME and a raw xsession.  The console (C-M-F1) is immune to the problem, howwwwever.

None of the suggessssted fixes on this thread have worked fooooor me, and turning repeat keys off is an unacceptable solution.

Does anyone have any other ideas?

---

### Post by brownbat on 2008-03-26
I had never had this problem until upgrading to Hardy, now it's happening once or twice a day. My down key just got stuck, and I gave it a few hours for it to resolve, to no avail. Unplugging the keyboard and replugging it in (even to other usb ports) also has no effect. 

I agree it seems to occur at high load. I was still able to control my mouse, however.

Not sure how to further diagnose this.

---

### Post by 0x656b694d on 2008-03-26
Please look at the following bug:
'Keys get "stuck" down
[https://bugs.launchpad.net/bugs/194214](https://bugs.launchpad.net/bugs/194214)'
Chris Halse Rogers shared a fixed package.
You may want to try it and check if it solves your problem.

---

### Post by carlosbrolotobar on 2008-03-29
SOLVED:

My keyboard is PS2, but the problem on DMESG said:
usb 2-3: reset low speed USB device using ohci_hcd and address 2
x100 times.... so was not a problem of my keyboard..... something on the USB needed to be reseted...

INSTRUCTIONS:
1.-Unplug all your USB devices
2.- Wait 10 seconds
3.-Plug them again

The problem of the keys being stuck should be gone... if persist, try to follow the steps 1 to 2....
then use the keyboard without plugin back the usb devices.... if it works, you have a bad mouse / or usb device.... if not..... is something else....

---

### Post by foresto on 2008-05-16
This problem is also discussed here:
[https://bugs.launchpad.net/ubuntu/+bug/124406](https://bugs.launchpad.net/ubuntu/+bug/124406)
[http://ubuntuforums.org/showthread.php?t=772773](http://ubuntuforums.org/showthread.php?t=772773)
[http://bugzilla.kernel.org/show_bug.cgi?id=9448](http://bugzilla.kernel.org/show_bug.cgi?id=9448)

---

