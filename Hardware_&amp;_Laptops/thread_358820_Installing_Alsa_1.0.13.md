---
title: "Installing Alsa 1.0.13"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by ZeldaFan on 2007-02-11
I have an HP dv9000t laptop, and whenever I plug in headphones into the jack to listen to music or anything, the sound still comes out from the speakers. Apparently, I've heard that installing the latest version of Ala (1.0.13) should solve the problem, but I don't really understand how I am supposed to compile the driver and everything. I am essentially an Ubuntu beginner, so does anyone know of any easy ways to install the program or any easier ways to get the jack from working?

---

### Post by mikewhatever on 2007-02-11
Hi ZeldaFan,
[Here is a howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") on alsa driver. Post back if you need more help. You can't really see the full names of the files on the download page, but the latest version is 1.0.14rc2.

PS: and no, I do not know any other way. Personally, I had a no working mic problem on hp pavilion 5000, and used the guide.

---

### Post by charles.g.moore on 2007-02-14
Hey I used the how-to you suggested and it worked perfectly as far as my headphone jacks.

How did you get the built-in dual microphones working? 

I have a dv6000t, when I use the applications-->sound&video-->sound recorder I cant get it to work.

Any ideas which part of the how-to pertains to the microphones, I install all the alsa stuff.

Also, did the blue mute button on your laptop turn red?

---

### Post by drpaul on 2007-02-14
I installed the .13 alsa driver on my dv6150us and it got the mics working, it got the ear phone jack operating, but it doesn't turn the speakers off when you plug in the phones.

It also transferred the action of the volume controls on the desktop to the ear phones instead of the speakers :( 

Haven't been able to get any action out of the webcam.

Paul

---

### Post by mikewhatever on 2007-02-14
> **charles.g.moore said:**
> Hey I used the how-to you suggested and it worked perfectly as far as my headphone jacks.

How did you get the built-in dual microphones working? 

I have a dv6000t, when I use the applications-->sound&video-->sound recorder I cant get it to work.

Any ideas which part of the how-to pertains to the microphones, I install all the alsa stuff.

Also, did the blue mute button on your laptop turn red?

No part of the howto pertains to the microphones, because it deals with how to reinstall alsa driver. My laptop doesn't have an internal mic, it's dv5000, but you can try several things.
1.Double click on the speaker icon in the panel. You should have more controls there now. Is there intmic in the Switches tab? Is it selected?
Also make sure none of the sliders is all the way down.
2. Type alsamixer in the terminal. You'll get a window with controls. Hit Tab key twice to get them all showing. You can select a slider/control with right/left arrow keys and remove or bring back the capture function with the space key. My external mic started to work after I set the internal one to capture. See the screenshot. Try setting one or the other to cupture and see what you get.

---

### Post by charles.g.moore on 2007-02-16
I am running a dv6000t
Got the webcam working after following this post:

[http://www.ubuntuforums.org/showthread.php?t=280121](http://www.ubuntuforums.org/showthread.php?t=280121)

I had to reboot before anything would see it...

Hope it helps!

---

