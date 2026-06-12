---
title: "Ubuntu won't suspend properly"
date: 2009-10-11
forum: Hardware
---

### Post by Eagles18 on 2009-10-11
As the title states,Ubuntu won't suspend properly on my laptop.Whenever I try to suspend it,the screen turns off like it's supposed to.However,when it "wakes up",it will either stay blank or it will resume,but I will be unable to do anything.Does anyone know how to solve this problem?
If it helps,I have a Compaq Presario CQ60 220US.
Thanks in advance :guitar:

---

### Post by ceratophyllum on 2009-10-11
Join the club.  I've had this issue intermittantly on various laptops, since 2005.  On my old PPC iBook, there was some sort of problem with DPMS.  Later, when I got a macbook, suspend had crashes and there was a kernel downgrade to work around the problem.  With Jaunty, suspend works again on the macbook out of the box, no configurating required.  However, on my Ideapad Y730, suspend does not work and I have no idea why. (The ideapad boots quickly and I'm using fglrx 3D drivers.)

**try booting with pci=nomsi**. See the link below.
 
Check this out:
[http://www.linlap.com/wiki/hp-compaq+presario+cq60](http://www.linlap.com/wiki/hp-compaq+presario+cq60)

---

### Post by Eagles18 on 2009-10-14
> **ceratophyllum said:**
> Join the club.  I've had this issue intermittantly on various laptops, since 2005.  On my old PPC iBook, there was some sort of problem with DPMS.  Later, when I got a macbook, suspend had crashes and there was a kernel downgrade to work around the problem.  With Jaunty, suspend works again on the macbook out of the box, no configurating required.  However, on my Ideapad Y730, suspend does not work and I have no idea why. (The ideapad boots quickly and I'm using fglrx 3D drivers.)

**try booting with pci=nomsi**. See the link below.
 
Check this out:
[http://www.linlap.com/wiki/hp-compaq+presario+cq60](http://www.linlap.com/wiki/hp-compaq+presario+cq60)
I tried it,but it didn't work :(

---

### Post by Windows Nerd on 2009-10-14
I had the same problem on my laptop. See my thread [here]("http://ubuntuforums.org/showthread.php?t=1242156") for the solution that worked for me.

Note: Sorry, I have yet to get around to updating the guide for 64-bit users.

Scott

---

