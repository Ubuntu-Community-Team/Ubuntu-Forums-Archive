---
title: "troubles with Toshiba satellite P100"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by DCDraco on 2006-09-22
Anyone tring to install Ubuntu linux on this laptop please send me a reply. I will be installing soon I am tring to get other peoples expereinces with prolems that I could encounter with the installation and setting up of Ubuntu on this laptop. I have hear that overheating is a problem and sound doesn't work. Let me know of your experiences. I will repot to all what happens when I give it go.

Draco

---

### Post by xyz on 2006-09-22
I don't know enough about all the variety of different laptops within the same brand. I have a Toshiba Satellite A 40...Do you know it it can be compared to yours?
I bought it 2 years because it was cheap; I didn't have the slightest intention of installing a GNU/Linus distro as a motivation to buy this computer or another.
I've had no real pbm dual booting with Debian,Mandriva and OF COURSE Ubuntu.

---

### Post by DCDraco on 2006-09-22
Thank man for the input it is really helpful. This P100 is a newer model. I just bought it a month ago. I had asked the pepole there if linux is compatible they said yes, apparently they didn't really know themselves. As to the speks of this toshiba Dul core intel processores. Harman/kardon speakers this could be the problem some people are expirencing with the sound, need to know what driver I will need to get set up. As well the wireless. I had installed Suse 10.1 and no sound no internet and no wireless. So I removed it and now have read up abit about Ubuntu and is looking like the better option. I am very wired about overheating if the ACIP needs to be switched off, hope this is not going to be the case. Let me know if you find anything else. At least I know that it should work on Toshiba laptops.

---

### Post by xyz on 2006-09-22
Well if, using the LIVE-CD, you computer responds positive to Ubuntu, you should not have huge problems getting it operational once installed. 

Check the "Absolute Beginners" and "HowTo" forums if you run into sound problem or any other for that matter....and let's not talk too much about "maybe problems!" Just install it and we'll see.
Other people have had problems with this or that but YOU haven't as of yet.

Getting/installing the necessary codecs and stuff should get you on the road fine. I am a musician and obviously I need sound and I have sound.

When I have a little more time, I'll try to redirect you to some interesting threads. And we'll know more WHEN (and if) you have problems.
Good luck and if I were you, I'd be looking forward to this!!!:D

---

### Post by xyz on 2006-09-22
**Sorry man! I meant to post this on another thread!**

Did you take a look at this:
[i915Driver]("https://help.ubuntu.com/community/i915Driver")

and [Here]("http://www.dhost.info/zachstruck/") This Here 2nd link talks about installing on a different laptop than yours but it treats the subject of resolution.

---

### Post by amo-ej1 on 2006-09-22
When checking a laptop out with a livecd please also check the following issues:

a) support for wlan
b) power management (my laptop has 3hours of autonomy while i never saw it live longer than 40 minutes on battery, a previous laptop had a ACPI bug which made it unable to read the battery state)
c) support for sensor reading (try acpi -a)
d) see if it detects the highest resolution the screen can handle
e) check support for all extra's: bluetooth, acpi, cardreader, irda, ... my laptop has a single chip offering all those features but linux has only support for one of them

---

### Post by smorken on 2007-11-23
I have a Toshiba P100 laptop, and i have tried to install linux on it.  The distribution I have tried was fedora core 6.  For me there are issues:


[LIST]
[*]Recently updated kernels (sorry I don't recall the version that started causing troubles) caused the laptop to pause for a long time at startup reporting an IRQ error
[*]NO wifi support (it is some Intel driver)
[*]I had to disable ACPI to make the fan run, and for the sound to work (and in this mode the fan runs constantly, not just when it's too hot like it's supposed to)
[/LIST]

As you can see, the linux support for this laptop is poor.  I'm thinking about trying Ubuntu, but I am not aware of any reasons why it would be any different.

Also this laptop is developing cracks on the top cover near the hinges.  I am starting to regret buying it.

Scott Morken

---

