---
title: "Mouse Freaking Out"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by hikaricore on 2006-08-20
Every so often my mouse spazzes out and jumps all over the screen with buttons clicking randomly.  I havn't experieced this issue before in any other distro of linux I've used or in any version of windows I have on this system.  Oddly if I use my keyboard shortcuts to switch to another virtual desktop, the mouse goes back to normal O.o very odd.  I've checked and modified hardware settings, bios settings, X settings and even updated my kernel and still no change.  Just wondering if anyone has had a similar issue to this or if maybe X is just on crack.  :P

**almost forgot to mention I'm using a generic ps2 mouse.

---

### Post by em3raldxiii on 2006-08-21
On crack.
 
Haha ... just kidding.  The only time I experience this rather irritating problem is when I switch between computers on my KVM switch.  In THAT case, I can usually just double-hit scroll lock followed by M.  This rescans the mouse and boom ... fixed.
 
Now in your case you say you are switching workspaces to fix the problem.  Wierd.  Also, which version of Ubuntu are you using?

---

### Post by hikaricore on 2006-08-21
I'm currently using Ubuntu 6.06 LTS.  Has only happened once today (at a horrible time) so I'm wondering if it is actually a hardware issue.  The only thing I can think of is maybe finding my ps2 to usb conversion plug and testing it as a usb mouse to see if maybe one of my input ports is getting shotty.

---

### Post by em3raldxiii on 2006-08-22
Could also be the adapter - do you have another around, perhaps one on your keyboard?  If so give it a try.

Okay, time for some really basic questions ... please don't be insulted, I just like to cover all my ground :D:

Is it a ball or an optical mouse?  If it is a ball, perhaps it needs cleaning.  If it is optical, what sort of mouse pad or mousing surface are you on?  I had found that same problem once on my dad's computer, and I determined that it was his 50¢ mousepad - it had fine hairline scratches on it that were almost invisible and this caused his optical mouse to jump unpredictably.  Also, plexiglass can be only so-so for mousing.  There are a number of other factors with the mouse that may not be immediately apparent such as hair on the lense.  I completely understand that these questions are kinda basic, but you never know ... sometimes the most complicated problem has the simplest solution eh?  Better to check than to rack your brains ... ;)

Keep us updated!!

---

### Post by Saibot on 2006-08-22
Cell phones can cause problems with cordless mice too.  A couple weeks ago I rearranged my desk and put the phone charger next to my mouse receiver.  All was fine - until I actually put the phone on the charger.  Mouse kept moving randomly and doing weird stuff, when I moved the phone the problems went away.

---

### Post by hikaricore on 2006-08-22
Yea it's just a regular mouse not an optical.  Still have yet to dig my usb adaptor out of my closet to test if it changes the issue.  I'm also going to disect my mouse again just to make sure the shotty plastic bits are still in perfect shape.  :) Thanks again for all the input on this. :)  I'll keep updating as I work with it.  Funny thing is I booted the install version of ubuntu off my external hd and played around in it for about 4hrs while reparting my drives (<3 gparted) and never had this happen once.

---

### Post by dancro on 2006-08-27
I have the same problem with my Logitech Cordless Track Ball and a Belkin Omni Cube 4-Port KVM.  The track ball is USB, plugged into KVM with a PS/2 adapter, and I can reset the mouse chaos by unplugging the mouse plug from the KVM and re-inserting it.

This same thing happened to me when I first installed Mandrake 10.0 and after some research  I learned it could be fixed by adding to the boot command "psmouse.proto=imps".  It fixed the problem for Mandrake and subsequently Mandriva.

So here is my question.  How can I add this to the boot for Ubuntu?  

I tried adding it by using ESC to get the menu during boot, but the command was reported as invalid, or some such, and was not effective.

Thank you in advance for any suggestions or advice.

Dan

---

### Post by dancro on 2006-08-27
Some progress to report.  

Based on other threads, here and elsewhere, I have edited /etc/modules to include "psmouse proto=imps".  Now switching between machines does not make mouse erratic.  However on the ubuntu machine the wheel is non functional.

Tried proto=bare and proto=exps with no luck.  

Shall investigate further when time permits.

Dan :)

---

### Post by Guy2 on 2006-08-28
> **em3raldxiii said:**
> The only time I experience this rather irritating problem is when I switch between computers on my KVM switch.  In THAT case, I can usually just double-hit scroll lock followed by M.  This rescans the mouse and boom ... fixed.

Same here. Thanks for the workaround - works a treat.

---

### Post by petermck on 2006-08-29
> **dancro said:**
> I have the same problem with my Logitech Cordless Track Ball and a Belkin Omni Cube 4-Port KVM.  The track ball is USB, plugged into KVM with a PS/2 adapter, and I can reset the mouse chaos by unplugging the mouse plug from the KVM and re-inserting it.

This same thing happened to me when I first installed Mandrake 10.0 and after some research  I learned it could be fixed by adding to the boot command "psmouse.proto=imps".  It fixed the problem for Mandrake and subsequently Mandriva.

So here is my question.  How can I add this to the boot for Ubuntu?  

I tried adding it by using ESC to get the menu during boot, but the command was reported as invalid, or some such, and was not effective.

Thank you in advance for any suggestions or advice.

Dan

You could put it in /etc/modules as psmouse proto=imps (note: no dot). I didn't find that this fixed the problem tohough. It appears that some mice are fine because my old one works but not the optical one.

---

### Post by petermck on 2006-08-29
Thanks for the 2 x Scrollock + M bit. That's great. My KVM is not a Belkin it's a cheap Kamakusa type and this works so maybe it works on some other KVM's too. 
The problem definitely seems to be related to the mouse wheel. I just turned off "Emulate3Buttons" in xorg.conf and the problem was fixed but at the sacrifice of my mouse wheel:( 
An old 3 button mouse works fine and dmesg throws up some mouse "lost synchronization errors".
Maybe someone with a bit more knowledge than I can have a look at the code in psmouse.c and write something to catch the lost sync message and issue a resync like in scrollock +M...if that's possible.

---

### Post by petermck on 2006-08-30
For anyone interested i just finished the update of Ubuntu after installing the LiveCD and having problems with the mouse and a cheap KVM. The crazy mouse problem is now gone, so something in the updates must have fixed it.

---

### Post by em3raldxiii on 2006-08-31
Thanks for the information!  I wish everyone updated the threads with feedback like this. :D

---

### Post by lzukausk on 2006-09-06
This is a problem with Linux and how it views certain KVM switches and how those KVM switches work with the mouse.  On a big ($800+) HP console switch, there is a signal that gets fed into the mouse port when switched to a different port on the KVM. Keeping the mouse 'present' on the off ports.  The less expensive KVM (the one I have now) switches do not do this or don't do it well.  The up-shot is the mouse gets confused when you come back to it.

The easiest fix is to switch to a pure mechanical mouse (a rollerball type).  I just finished a  fresh install of 6.06LTS and noticed the mouse problem agin.  I swapped out my KEIO (read cheap) optical mouse for a Compaq branded Logitech device.  Now I can switch systems on the KVM and experience no mouse trouble.

This problem is not specific to any particular flavor of Linux. I have experienced this with most major distributions.

I hope this helps.

---

