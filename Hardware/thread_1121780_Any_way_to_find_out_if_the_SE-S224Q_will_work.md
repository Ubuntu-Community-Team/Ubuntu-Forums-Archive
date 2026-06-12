---
title: "Any way to find out if the SE-S224Q will work?"
date: 2009-04-10
forum: Hardware
---

### Post by Daminator on 2009-04-10
Hello all,

I've been looking at external DVD burners since my internal drive died and I'm tempted by this one:

[http://tiny.cc/vRgnB](http://tiny.cc/vRgnB)
[http://www.scan.co.uk/Products/Samsung-SE-S224Q-RSMN-22x-External-DVDRW-Retail-with-Software](http://www.scan.co.uk/Products/Samsung-SE-S224Q-RSMN-22x-External-DVDRW-Retail-with-Software)

Is there any way to find out if it will work ok in Ubuntu? Any reason to suspect that it wont? I've searced [http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/) but I can find no memtion of it.

I have found this post which seems to raise concerns:
[http://forum.ubuntu-fr.org/viewtopic.php?id=300419](http://forum.ubuntu-fr.org/viewtopic.php?id=300419)
and this one that seems to say it's ok:
[http://ubuntu-se.org/phpBB3/viewtopic.php?f=163&t=35131](http://ubuntu-se.org/phpBB3/viewtopic.php?f=163&t=35131)

If no one knows. Can anyone highly recommend an alternative external DVD burner?

As a side note, can you boot from a disk that's put into an external burner?

Also, can external (usb) burners play music cd's? I assume they can, but know that internal drives have a music lead that goes directly from the drive to the sound card and I don't know if that's built into the USB connection or not?

Thanks
Damian

---

### Post by Daminator on 2009-04-20
I bought one, and it's working fine!

Had a few problems with it being too noisy while watching a DVD or playing music, but used

hdparm -E 2 /dev/scd0
and
hdparm -E 0 /dev/scd0

to change the speed depending on what I'm doing and all is well.

Just need to automate those now somehow and then set up the remote control.

Damian

---

### Post by itix on 2009-10-15
Great, thanx, I'm gonna buy one too.

We should really have some sort of community based hardware compatibility wiki for Ubuntu.

---

