---
title: "Laptop Feature Button Failure"
date: 2008-11-18
forum: Hardware
---

### Post by thatsmychin on 2008-11-18
I'm almost completely bald after ripping my hair out over this problem.  I'm working on a Gateway M305CRV for a friend, Windows was installed but was unusable since IE/Firefox (whatever was the default) would open or refresh the homepage continuously.  I would end up with 50 IE windows open and as soon as I try to change pages, it would change back to the default homepage.

So after figuring out that the behavior was a result of a faulty hardware feature button (you know the help/email/internet buttons).  So I try out a live CD to see what I get, and sure enough those stupid buttons don't work and my problem is solved, until I install Ubuntu.  Now I'm back to square one and I'm wondering if anyone has any idea where I can disable whatever it is that reads inputs from these buttons.

I've tried k/x/ubuntu live CD's and I've installed k/x/ubuntu 8.04 and 8.10 (yes all 6 flavors) just to see if I could get things working. 

Please throw some thoughts out there.

---

### Post by bonestonne on 2008-11-23
take it apart and clean under the buttons and the contacts. a simple flat-bladed screw driver will pop off the plastic bezel you need to remove, it's right by the base of the LCD. you can see if anything is causing the buttons to be stuck down, or any dirt causing a short (causing the laptop to think the button is always pressed).

while you're working on one as well, if you get audio in Ubuntu, would you be able to tell me how it is set up? i'm not getting any audio, and cannot find a working setup from what i have. i'd like to know what is working for others so that i can get mine working. i'm sick of reinstalling for nothing.

thanks a lot, and i hope that helps you.

---

### Post by thatsmychin on 2011-11-25
Follow-up 4 years later.  I literally pulled the laptop keyboard out of the chassis, along with pulling the "internet' feature button off the mainboard.  after all of the tinkering, there was a problem with the chipset, had to use keytweak to find which key was being triggered, then I mapped it to a key that wasn't used...like F7.  Problem solved.

---

