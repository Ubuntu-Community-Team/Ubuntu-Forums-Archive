---
title: "[SOLVED] Mysterious Beep of Death"
date: 2008-10-09
forum: General Help
---

### Post by ubunny on 2008-10-09
I have an intermittent but never ending beep, like a key buffer being overrun, but I can't get rid of it.

I tried sudo rmmod pcspkr but it only turned off for a moment then continued.  This only works once.  

When it starts, I can barely type due to a noticeable lag.  I can't see anything in ps aux or top that indicates a program and otherwise I run fine when not under the BEEP OF DEATH.

The only means of killing it, is to shutdown or reboot/restart.  Note that on restart, the lights go off for the mouse and blink the caps lock but the system still doesn't reboot at that moment when it normally would.  At that point the beep changes pitch up and still does not reboot.  I then have to manually shutoff.  This doesn't happen on shutdown.

This is a new Hardy install.  Is it some program (FF3?) or setting that needs reconfiguring?  I can't predict when but when it happens I have to abandon ubuntu.

If I play a song it will play plus the beep will continue as if on another channel.  

any help appreciated.

---

### Post by solitaire on 2008-10-09
I'm assuming it's a desktop PC?

First thing first, try a different keyboard if that is not possible. check your current keyboard for any sticky keys. try opening up a terminal window and press every key on the keyboard and see if any don't respond or keep popping up..

If you go to the volume icon, right click and select "open volume control" click on "Preferences" and make sure "PC Speaker" is ticked. That controls the volume of the Beeping.

Other than that I'm out of ideas....

Hopefully someone else can think of something on the Software side that might be causing it.

---

### Post by ubunny on 2008-10-10
Sorry, it's a laptop.

I reedited my reply.  Thanks for the advice.  Sure enough, the zero key had a lot of hair and bits that might have caused the beeps.  I want a conspiracy but alas not today ;)

good point to bring up; laptop keyboards are magnets for gunk.  If you have what I did, you have to:

1) take the entire keyboard piece off the laptop so that you can get the full tactile feeling from the keys the best.  I didn't notice the zero key softness until I took the board off, then it was obvious.

2) if you have to take a particular key off, do so from the *bottom* or *top* of the key.  In my case it was the bottom.  Think of a swingset, you don't want to pry it off from the side or else you will break the tinywiny plastic bits that keep the key attached.  Think of a hood of a car and gently pop off the key.

3) clean the key and around the button area.  I used a small piece of scotch tape, rolled into a small funnel so that it could take up the debris easily enough.

4) in my case there were two plastic pieces under the key.  Bear in mind to thread the pieces back into their sockets without breaking them.  be patient.

done (for now)

---

