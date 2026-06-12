---
title: "Are software RAID arrays supported by Wubi 9.04 ?"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by astronaute on 2009-04-26
Hello,

On this page it says it will be supported in 8.10:

[https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays](https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays)

I see lot of people have problems with software raid, so I prefer to be sure before doing something wrong :)

[As personally I can't install Ubuntu on my software Raid]("http://ubuntuforums.org/showthread.php?t=1136737"), Wubi will be my last chance before giving up.

Thank you in advance !

---

### Post by talsemgeest on 2009-04-26
I don't remember seeing an option to add a software raid array in wubi, so I think you are out of luck there. Also, are you sure you mean software raid and not fakeraid?

---

### Post by astronaute on 2009-04-26
> **talsemgeest said:**
> I don't remember seeing an option to add a software raid array in wubi, so I think you are out of luck there. Also, are you sure you mean software raid and not fakeraid?

My windows is already running on Raid 0, I just want to be sure that after installing wubi I will not be stuck on reboot :)

The raid is configured in Bios so it is hybrid one I suppose, if soft raid != fake raid, then sorry, my fault :)

(if wubi 9.04 doesn't support soft raid, someone please update [the wiki where we can read the opposite]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays") )

---

### Post by talsemgeest on 2009-04-26
> **astronaute said:**
> My windows is already running on Raid 0, I just want to be sure that after installing wubi I will not be stuck on reboot :)

The raid is configured in Bios so it is hybrid one I suppose, if soft raid != fake raid, then sorry, my fault :)

(if wubi 9.04 doesn't support soft raid, someone please update [the wiki where we can read the opposite]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays") )
Ok, if it is configured in the bios, it is almost definitely fakeraid. Ubuntu can use this using dmraid, which comes with the alternate install cd. Perhaps try again with that, and keep an eye out for the words fakeraid.

---

### Post by astronaute on 2009-04-27
After activating Raid on boot, the partitioner shows me an empty list as I explain in the other post :)

That's why I would like to know if Wubi could be the solution.

I really don't want to mess with the OS at that level, at least the installation should be simple but obviously its not...

Anyway, thank you for trying to help me, but I will not force the install of an OS who doesn't like my hardware :)

Bye !

---

### Post by talsemgeest on 2009-04-27
> **astronaute said:**
> After activating Raid on boot, the partitioner shows me an empty list as I explain in the other post :)

That's why I would like to know if Wubi could be the solution.

I really don't want to mess with the OS at that level, at least the installation should be simple but obviously its not...

Anyway, thank you for trying to help me, but I will not force the install of an OS who doesn't like my hardware :)

Bye !
Well, it is certainly worth a shot. In my experience of wubi on fakeraid, it installed fine, but when I selected it from the boot menu it threw up a bunch of errors. Then all I had to do was boot back into windows and remove it. So, in other words, you have nothing to lose in trying, so it it certainly worth a shot.

---

### Post by astronaute on 2009-04-27
Just for info (alternate CD boot) :

[IMG]http://img15.imageshack.us/img15/2343/img0690j.jpg[/IMG]

I choose yes, and it show me an empty list :

[IMG]http://img23.imageshack.us/img23/328/img0691g.jpg[/IMG]


dmraid -s

[IMG]http://img17.imageshack.us/img17/1825/img0688d.jpg[/IMG]

---

