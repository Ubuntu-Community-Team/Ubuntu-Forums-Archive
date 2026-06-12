---
title: "Getting a new clean install of 8.04"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Z0d1@c on 2009-04-02
I have an install of Ubuntu 8.04 (dual boot with WinXP) on my computer that I accidentally screwed up (nothing bad, just that ndiswrapper won't install anymore, means no Internet for me) and I want to reinstall it. I don't really know how this can be done and I couldn't find anything with the forum search. And I probably need pretty accurate instructions: I am quite good at using the computer but it's better to be safe than sorry when you can accidentally format your hard drive. :D

---

### Post by Therion on 2009-04-02
You're asking how to do a fresh install?  

[confused look]

Am I missing something here?

To re-install you boot to the LiveCD and use the Installer...

---

### Post by Z0d1@c on 2009-04-02
Hmm, I tried it but it just gave me an option to install another Ubuntu, cropping the alerady-cropped WinXP partition of my HDD. Perhaps I missed something? :D

---

### Post by Therion on 2009-04-02
OH!  I see what you're asking about... You want to reinstall but you're unsure about how to prevent overwriting your existing WinXP install.

You'll need to use the Manual partitioning option for that so you can tell the installer to ignore the NTFS (Windows) partition and instead install only to the existing Ext3 partition.

---

### Post by Z0d1@c on 2009-04-03
Oh thanks, it worked :)

---

