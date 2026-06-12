---
title: "Acer Aspire 5738PG TouchScreen"
date: 2010-02-10
forum: Hardware
---

### Post by HeWhoWas on 2010-02-10
Hey Guys,

I'm a recent adopter of Karmic, using Kubuntu but whatever variant this works under will become my new flavour.

The Acer Aspire 5738PG (Via Web Searches), or 5738PZ (Based on what it says on the chasis), or 5738PZG (Based on the sticker), or more specifically the 5738PZG-434G32Mn is a new-ish multi-touch screen laptop.

Everything picks up find under ubuntu, the only issue is that the touchscreen doesn't work. Don't get me wrong, it's still a great laptop even without the touchscreen but it would be nice for it to work.

Does anyone know of any projects that are looking into this area, or if there is some way to get it working? There seems to be nothing being said about it on the forums, so I assume either it's not a popular laptop, or most linux users are savvy enough to get it working.

Thanks.

---

### Post by HeWhoWas on 2010-03-08
B-b-b-bump.:p

---

### Post by bitnix on 2010-04-27
I have the same problem, have you solved?
does anyone knows how to use touchscreen with lucid lynx?
thank you

---

### Post by MurkMenthaa on 2010-05-12
Bump. Same Issue. Anyone ?
[This]("http://ubuntuforums.org/showthread.php?t=158666") thread is supposed to be helpful but I'm stuck at finding out where the heck is my touchscreen plugged in! Its built-in. How do I find out ?

---

### Post by chi*a on 2010-05-28
Looking at this too.

Ubuntu 10.4  Acer Aspire 5738PG

If open terminal and enter:[INDENT] [B]sudo cat /dev/hidraw1
[/B][/INDENT]Enter password then touch the touch screen and see many esoteric things appear in the terminal in response to movements.

Guessing this the touch screen device.  Haven't touched xorg.conf yet.

---

### Post by spencerthayer on 2010-08-14
I have the 5738PG and just installed 10.4. No HID for the touch screen in fact I only have the one hidraw0 which I assume is my touchpad. Has there been any progress made with this? Also since y'all have the same laptop as me anyone know how to assign the big "P" button to something?

---

### Post by arobase40 on 2010-10-22
I don't own this Acer Aspire 5738PG or any other laptops of this size, but for what I know it use a Cando touchscreen...

So refer to the Acer Aspire 1825PT or 1825PTZ, here :

[http://ubuntuforums.org/showthread.php?t=1486671](http://ubuntuforums.org/showthread.php?t=1486671)

[http://ubuntuforums.org/showthread.php?t=1483973](http://ubuntuforums.org/showthread.php?t=1483973)

French Ubuntu Forum :

[http://forum.ubuntu-fr.org/viewtopic.php?id=395954&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=395954&p=1)

French wiki based on Gentoo :

[http://fr.gentoo-wiki.com/wiki/Acer_1825PTZ](http://fr.gentoo-wiki.com/wiki/Acer_1825PTZ)

On the french Ubuntu forum, Imarune (a french user of the 1825PTZ) is using Fedora 13 distribution...

You will probably find some or all the informations needed for you laptop, specially about the touchscreen, accelerometer (if one exists) or other sensors or devices.

Regarding the touchscreen, only mono-touch works for the moment. Nothing specific to the Acer laptop or Cando touchscreen, but mostly to any new touchscreens (capacitive touchscreens ?)...

Best regards

Chac

---

