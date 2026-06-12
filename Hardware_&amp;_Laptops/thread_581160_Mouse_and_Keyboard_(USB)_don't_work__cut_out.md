---
title: "Mouse and Keyboard (USB) don't work / cut out"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by hawkeye0203 on 2007-10-19
Hello all!  This is my first post here so I apologize greatly if it's in the wrong area.

I'm having problems with my USB keyboard and mouse.

Keyboard: Logitech G15
Mouse: Logitech G5
[B]
System Specs:[/B]
core 2 duo e6400
2gb corsair
asus p5nsli mobo
nvidia 7950gt
250gb hdd

I'm dual-booting with winXP.

I first loaded Fiesty a few months ago and it was great!  But my mouse would cut out after a random amount of time.  I continued to use the keyboard to get around to try to fix this issue.  I've googled every term / phrase I can think of to find the solution, but still no go.  I did end up finding something that I thought would work and it involved editing the menu.lst file.  Needless to say, I'm a noobie and I could no longer get Ubuntu to load anymore after that and I wasn't sure how to restore the back-up of menu.lst through Grub.  So I scrapped the restoration effort and decided to wait for Gutsy.

I downloaded Gutsy yesterday and installed it on the cleaned partition that Fiesty was on.  During the use of the live cd, my mouse locked up on me again.  Grr...  I thought it may have just been the live cd so I limped along with my keyboard.  After installation, I restarted and when I got to the log in screen, my keyboard didn't work.... at all.  I rebooted a few times and still no go...  I'm so frustrated because I would looooove to move away from windows.

Can someone offer some insight on my dilemma?

Thanks in advance!

---

### Post by daou on 2007-10-19
The does keyboard and mouse work in Windows?

Because I was troubleshooting a friend's comp today, Asus P5something mobo, and it would cut the power to USB mouse and kbd when Windows booted. BIOS sometimes complained of CMOS battery being low. He's going to replace that as we speak. I don't know if this will fix it, yet. Or perhaps a BIOS update.

Can you tell whether the power to the keyboard and/or mouse is cut sometime during boot? Keep an eye on any LEDs the devices might have.

---

### Post by hawkeye0203 on 2007-10-19
Thank you for responding so quickly!

The keyboard and mouse do work flawlessly in Windows.

when they stop working, the LED's, LCD display (kbd), etc. are still on.  They're getting power, but it seems as if Ubuntu has stopped processing them.  If I unplug and plug back in, the lights stay off as if they aren't even getting power now.

As a side note, both are gaming-grade.  The mouse never sleeps and transmits 500 reports / second.  Does anyone suppose that might be messing up Ubuntu's processing of them?  A friend of mine has a USB mouse hooked up to his laptop with Gutsy and he has never had a problem and it's a standard mouse...

Thanks.

---

### Post by Leviel on 2007-10-19
I have the same problem - fortunately I have a laptop, so I can at least keep working.  The BIOS-thing seems to be a common problem - for instance, see [this]("http://ubuntuforums.org/showpost.php?p=3475370&postcount=7") thread and the link they mention.

From what I can gather, it's a pretty common problem, so I shouldn't think it's specifically because you have a gaming mouse.  Mine is just some stupid Microsoft "Basic Optical Mouse".

I *do* wonder whether dual-booting doesn't influence it - a lot of people with this problem seem to be doing that.  But if it's the BIOS, I guess not.  It could just be that a lot of beginners start off by dual-booting, so it seems as if the two are related.

---

### Post by hawkeye0203 on 2007-10-19
Thanks Leviel, I wonder if dool-booting is an issue as well because my friend that is flawlessly working with it has only Ubuntu and nothing else on this machine.  Hmmm...

I'm going to try to update my BIOS and see what happens there.  Thanks!

---

### Post by Leviel on 2007-10-19
I've read some more - see [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/84762")  bug report (and even [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/43305") one from Dapper/Edgy).

The two main solutions seem to be
*acpi=force irqpoll*
or a variation of
[I]modprobe -r ohci_hcd
modprobe ohci_hcd
modprobe usbhid[/I]
although neither works every time.  But it's worth a try, I guess.
L

---

### Post by hawkeye0203 on 2007-10-19
acpi=force irqpoll

That is what I messed up with the first time that caused Fiesty to not load...  :-)

I'll keep trying what you suggest and looking around.

thanks!

---

### Post by Leviel on 2007-10-19
Hmmm, well, I updated my BIOS, which is making it work **better**, without fixing the problem.  acpi=force irqpoll sent my entire system into very very slow mode, with the mouse (using both USB and touchpad) hopping painfully across the screen.  I took that out, and it worked fine for about an hour.

At the exact same moment the mouse went dead, my internet connection also did something funny - half the things went dead, but I'm still online.  Previously, my external harddrive would get disconnected the moment the mouse went dead.  I'm also noticing an error message whenever I start up - something about the BIOS, can't remember now.  *sigh*, wish there was a solution!

---

