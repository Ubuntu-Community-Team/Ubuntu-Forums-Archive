---
title: "/dev/hda1 not detected"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Poptart on 2005-10-21
Hey all. I've been using Ubuntu since the beginning of the year. Mostly I seem to be able to fend for myself, but this has me boggling.

I installed Breezy with the dist-upgrade command. Seemed to work fine. I booted into it a few times okay. Then I bought a new computer case and moved all my stuff over. Now, when I boot up, it gives me the following:
[I]
ALERT! /dev/hda1 does not exist. Dropping to a shell![/I]

And then it goes into the shell. Problem is, I don't seem to be able to get a keyboard working with the machine. I've tried both USB and PS2 as well as all my ports for said items.

So I guess the problem is two fold. How can I get my keyboard working, and then what do I need to do to fix the hda1 problem?

---

### Post by stoeptegel on 2005-10-21
You might have connected the IDE kabel the wrong way. The kabel has a red line on one side. 
When you look in front at the harddisk to the pins, the red line has to go to the right side.

For keyboard i dunno.

---

### Post by Poptart on 2005-10-21
The cable thing isn't it. I learned that lesson the hard way about three months ago, so now I'm careful about it. The harddrives themselves are recognized just fine at startup, it's just when Ubuntu starts to boot that we have issues.

---

### Post by Ocxic on 2005-10-21
>   I bought a new computer case and moved all my stuff over. Now, when I boot up, it gives me the following:
[I]
ALERT! /dev/hda1 does not exist. Dropping to a shell![/I]

And then it goes into the shell. 

So I guess the problem is two fold. How can I get my keyboard working, and then what do I need to do to fix the hda1 problem?

it possible the partitoning scheme could have been miessed up sumhow, it's happend to me, check that you can mount it manually, if not get a boot disk with partioning software and check out the drive.

---

### Post by Craig Pemberton on 2007-04-29
It is possible that your new computer does not uses sata? Do you have two hdd's now?

---

