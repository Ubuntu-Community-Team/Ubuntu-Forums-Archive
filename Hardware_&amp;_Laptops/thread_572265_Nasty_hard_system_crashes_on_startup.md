---
title: "Nasty hard system crashes on startup"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by Aelf on 2007-10-10
Wotcha.

I've been having some problems with my ~5 year old desktop machine. Up to now I've been using it as a web server, music server, mail server and a general excuse to mess about with serving stuff. Up to last month the PC was on 24 hours a day, every day. I must have had to restart it only a handful of times in the years I've used it. (including upgrading through breezy to dapper).

I got in trouble with my wife because my postfix tinkerings would frequently break our email, and when I broke apache and her photo album went offline she gave me an ultimatum. So I moved our email and web stuff to a hosted provider (not as fun :(), formatted the machine, installed Feisty and now my trusty server just handles MP3s and for me to watch videos while working. Obviously the machine now gets switched off when it's not in use, which is where the problems started.

When I switch it on, it crashes the first 10 or so attempts. I get past grub, and just when the log in screen is about to show, *click* (like you hear when resetting the machine), and the screen goes black. The machine is still humming, but there is no output. I hit the reset button and pray.

about 50% of the time it crashes before the log in screen appears. 40% of the time I get to log in, then as my desktop appears it crashes.

The final 10% of the time it crashes when I try to open an application that has video, like Totem or VLC. Everything else works fine.

Curiously, reliably after 10 or so crashes it will work perfectly! Even curiously-er if I leave that memcheck program on grub running for an hour or so before rebooting, it will work too! Almost like it needs to be warmed up?!

I figure it is some kind of hardware fault, but how do I narrow down the cause? I can't afford to replace the whole machine but if I knew for sure which component was the problem I could replace that. You may be asking why this is an Ubuntu problem - I have XP on dual boot (not that I ever use it) and that works perfectly every time (more confusion!).

Finally something I observed today - there was a dead mouse behind the tower (we have cats). Can't find any nibble damage though...
Also, there is a rusty organic looking build up on the metal tops of the bigger capacitors on the motherboard - is this cause for concern? Again I figure it isn't since the fault is only when starting up and when it does work the machine works fine.

I'm really lost here so if anyone has any suggestions I'd be grateful!

---

### Post by jnorthr on 2007-10-10
Just to clarify this one: machine works ok as a server; it works ok as an XP system; it does not work well as a desktop ?
Did you completely wipe the disk before installing ubuntu desktop ? or could tere be bits of the server installation left from it's life as a server ?

There have been several reported errors on timings for the video displays, and this rather random set of failures may (or may not) signal that. What kind of video card does your machine have ? Let's see if it's supported under 7.0.4 ... put your video card name in the search box above and 'go' to serach for any other reported errors with your card.

There is also an outside chance it is a memory issue, but you've tried memcheck to confirm good memory ?

---

### Post by tgalati4 on 2007-10-10
Once a 5-year-old hard disk as seen a lot of use as a server drive, it's bearings are worn and there is more torque during startup.  This explains the startup failures.  When the disk warms up and the platters get up to speed it will start to work again.  When cold, the platters are slow and unreliable.

Your options:  continue to use it as a non-essential server.  Keep it running and don't reboot it, even for updates.  Every reboot will risk a stuck machine.

Buy a new drive for desktop use.  Choose a good-quality 7,200 rpm drive of moderate size.  Jumbo drives may give you reliability problems for desktop use.

Yes, it could be other things.  Check the memory with memtest86+.  Reseat the memory cards, clean the dust out of the machine.

On one of my servers, I had a loose power cable in the back of the drive.  After 165 days of uptime, this machine had rattled the power connector off!  I had to use pliers to pinch the connector tight.

---

### Post by Aelf on 2007-10-10
> Just to clarify this one: machine works ok as a server; it works ok as an XP system; it does not work well as a desktop ?
Did you completely wipe the disk before installing ubuntu desktop ? or could tere be bits of the server installation left from  it's life as a server ?

There have been several reported errors on timings for the video displays, and this rather random set of failures may (or may not) signal that. What kind of video card does your machine have ? Let's see if it's supported under 7.0.4 ... put your video card name in the search box above and 'go' to serach for any other reported errors with your card.

There is also an outside chance it is a memory issue, but you've tried memcheck to confirm good memory ?
When it was mainly a server, it had the Ubuntu desktop distro installed and has always had no problems there. The disks were all wiped before the reinstall. I don't know the type of video card (its a 128mb GeForce something or other) but as I say its worked fine in the past and works fine once the crashes stop. This was my first guess as to what was wrong since the crashes only happen when something video-y happen (switching res, playing video) but I couldn't fathom why it works perfectly when not crashing.

> **tgalati4 said:**
> Once a 5-year-old hard disk as seen a lot of use as a server drive, it's bearings are worn and there is more torque during startup.  This explains the startup failures.  When the disk warms up and the platters get up to speed it will start to work again.  When cold, the platters are slow and unreliable.

Your options:  continue to use it as a non-essential server.  Keep it running and don't reboot it, even for updates.  Every reboot will risk a stuck machine.

Buy a new drive for desktop use.  Choose a good-quality 7,200 rpm drive of moderate size.  Jumbo drives may give you reliability problems for desktop use.

Yes, it could be other things.  Check the memory with memtest86+.  Reseat the memory cards, clean the dust out of the machine.

On one of my servers, I had a loose power cable in the back of the drive.  After 165 days of uptime, this machine had rattled the power connector off!  I had to use pliers to pinch the connector tight.

This seems like the obvious solution! The box has 3 drives in it, and windows has it's own, so presuming the one I use for the Ubuntu OS is suffering this damage (it did get a lot of use) then that would explain the difference.
I'm going to try installing ubuntu on the windows drive and see what happens.

Cheers for pointing me in the right direction!
p.s. is there any log files in linux that would have any record of these crashes for further investigation?

---

### Post by dabl on 2007-10-10
That "click" is probably the monitor deciding it's time to power down, due to some communication, or failure  to communicate with the display adapter.  But of course that begs the question "what's wrong with the display signal?".  It may be that there is a change in the "hibernate" or "standby" settings for a more recent kernel, or something like that.  In other words, it's not necessarily a "crash" or failure mode, it could be just a badly-timed "hibernate" signal.

You don't have to use the power button to restart it.  Hold down Alt and SysRq (aka PrtScn), and while holding those two down, carefully press, in sequence, R S E I U B.  It will restart, and in the process you'll skip the nice voltage surge through all the electronics on the motherboard.

I'd first try re-configuring the x server, and then maybe try a different (cheap/used) monitor.

BTW, organic stuff on the caps is not a confidence-builder -- hopefully you are saving your nickels for the replacement system.  :lolflag:

---

