---
title: "How do I make my USB mouse work?"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by Mikestarko on 2007-04-14
I got Ubuntu up and running, but my USB mouse doesn't work.  I'm using a laptop so I can use the touchpad, but I'm more used to the mouse.  How do I get it working?

Thanks.

---

### Post by hardyn on 2007-04-14
i plugged my in, and it worked... its interesting that yours doesnt.

I am using a MS 'wheel mouse opical' with no trouble, maybe try a different mouse?

good luck.

---

### Post by Skidpad on 2007-04-14
What brand/model, etc, is it?  Have you tried turning the touchpad off?

---

### Post by Mikestarko on 2007-04-15
> **Skidpad said:**
> What brand/model, etc, is it?  Have you tried turning the touchpad off?

It's a Logitech Opital USB Mouse.  I don't know how to turn off the touchpad.

---

### Post by Dafty on 2008-03-11
Anyone found a solution here? I've got the same problem. Acer 5100 laptop with a targus USB mouse (3 button plus wheel). Ubuntu 7.10 installed without the mouse.

Plugged the mouse in and it's powered (infra red lights up). I'm guessing it may be the Agiler, Inc. line in the following output from lsusb (from info I found on another thread):

richard@acer-laptop:~$ lsusb
Bus 003 Device 003: ID 0402:5602 ALi Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05b8:3091 Agiler, Inc. 
Bus 001 Device 001: ID 0000:0000  
richard@acer-laptop:~$ 

Again looking at other threads I've tried cat'ing /dev/intput/mouse? (There are 3 of them for some reason), but none gives any output on any mouse moves or button clicks.

Any other suggestions appreciated!


Richard

---

### Post by bred on 2008-03-11
well guys I have a toshiba notebook and a logitech mouse... 
its works fine on my pc, just plug and play normally
try to restart

---

### Post by Dafty on 2008-03-12
As an ex windows user restarts have already been tried :-)

Must be something a bit technical causing the problem I guess. The only solution I've seen suggested anywhere for this so far is to re-install with the mouse plugged in. Although I really don't fancy doing that. Still no big deal, didn't get the mouse specifically for the machine.

---

### Post by magnat2 on 2008-03-12
> **Dafty said:**
> As an ex windows user restarts have already been tried :-)

Must be something a bit technical causing the problem I guess. The only solution I've seen suggested anywhere for this so far is to re-install with the mouse plugged in. Although I really don't fancy doing that. Still no big deal, didn't get the mouse specifically for the machine.
I have the exact same problem with the targus wheelmouse, and ive allready tryed to reeinstall with the mouse pluged in, still not functioning... If anyone find a solution it would be appreciated:)

---

