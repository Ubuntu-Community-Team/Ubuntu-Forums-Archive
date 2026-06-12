---
title: "Lenovo Desktop and Linux"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by rsawyer8128 on 2007-06-10
I have a new Lenovo desktop. 3000 J series. It has Vista on it. I need to either dual boot it with Linux or - if that is not possible - replace Vista with Linux. (I need a Linux development environment.)

I have a Ubuntu CD from the book *Ubuntu Unleashed*, but the machine does not boot from it. I went into the bios to see if I could change the boot load order. If one can, I don't understand how.

**Boot Protocol** - this cannot be changed
**Boot Strap Type**: Choices are BBS, int 18H, int 19H and Auto detect.
Auto detect seems to bypass the CD all together.
The other 3 *seem *to hit the CD (the light flashes a lot) but then Vista loads anyway.

I tried the Ubuntu CD on an eMachine and it boots right into Linux, so the CD seems to be good. I've googled Lenovo and Linux and all kinds of combinations but am apparently still missing a key search word, because I haven't found anything on how to do this yet...

I am willing to wipe the hard drive all together, but if the machine will only boot to Vista, I don't know how to do that. Can anyone point me to some tools or does anyone have some experience with Lenovo and Linux?

I have developed some software on Linux in the past but am by no means experienced as an admin.

---

### Post by jrusso2 on 2007-06-10
Look for something in the bios thats says boot order or boot devices.  Then see if you can put your dvd first in the order.

---

### Post by rsawyer8128 on 2007-06-10
> **jrusso2 said:**
> Look for something in the bios thats says boot order or boot devices.  Then see if you can put your dvd first in the order.

Thanks.  I did that.  The only thing in the bios referring to booting was mentioned in the OP.  From the OP:
> I went into the bios to see if I could change the boot load order. If one can, I don't understand how.

**Boot Protocol** - this cannot be changed
**Boot Strap Type:** Choices are BBS, int 18H, int 19H and Auto detect.
Auto detect seems to bypass the CD all together.
The other 3 seem to hit the CD (the light flashes a lot) but then Vista loads anyway.There is nothing else in there regarding booting.  I'm not sure what *boot strap type* means, nor what the options mean, but changing it doesn't seem to do anything.

---

### Post by Shazaam on 2007-06-10
I just went to the Lenovo/IBM site and if your pc is configured like their website is I can feel your pain.:D
I think if you have your model number and you can tough out their website they might have an answer for you.

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=HOME-LENOVO](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=HOME-LENOVO)

---

### Post by NotRoot:-) on 2007-06-10
I ran into the same issue and changed my bios settings to allow pressing the F12 function key to specify the boot media after restarting.

---

### Post by rsawyer8128 on 2007-06-10
> **NotRoot:-) said:**
> I ran into the same issue and changed my bios settings to allow pressing the F12 function key to specify the boot media after restarting.

Thank you **NotRoot**.  I came here to report that I had it sorted out (F12 is indeed the answer.)

At start up there is a prompt for cntrl-s.  This actually takes you into the ethernet bios (what I quoted above.)

The Del key will take you into the regular bios - but no boot stuff can be found there.

And finally - as **NotRoot **reported - F12 allows you boot order options.

Thanks for the help!

---

