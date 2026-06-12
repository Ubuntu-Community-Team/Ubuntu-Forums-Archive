---
title: "System files recovery"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by ComputerJy on 2009-11-10
First of all I don't know if my problem even belongs to this category but I'm blinded by desperation.
I've done a really really really really stupid thing. I deleted the /usr/bin folder by mistake. Is there anyway to recover it?

I don't want to do a fresh installation because I don't want to loose all my data and programs.

[-o< Please help.. I have to use WINDOWS for god's sake :sad: I want my Karmic back

---

### Post by ComputerJy on 2009-11-10
Anyone!! HELP

---

### Post by skatinjj on 2009-11-10
Can try [this.]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive")

---

### Post by coffeecat on 2009-11-10
Or you could try this:

Boot up with the live CD using the same version as you have installed. That is, use the 9.04 CD if you have 9.04 installed. Do **not** use a different version number.

Once you are in the live CD desktop, mount your hard disc Ubuntu root partition from the Places menu.

Now - backup all your personal files to an external drive.

Next - copy the /usr/bin folder and contents of the live CD to the hard disc root partition /usr. If any of the executables in /usr/bin have been updated since you first installed, you will, of course, be replacing them with older versions. This may, or may not, cause problems.

And - since I've never had the need to try  this I really don't know whether this will work.

---

### Post by ComputerJy on 2009-11-11
Thanks for the Suggestions guys but I tried something similar to coffeecat's way. I only copied the /usr/bin from the LiveCD to my installation.
It worked actually but I was unable to use the sudo command at first (Probably it was letting me know I was baad :D ) But I rebooted into recovery mode and changed the owner and permissions of the /usr/bin/sudo - I found this somewhere around here - but now I think I'll have to reinstall everything

---

### Post by mikewhatever on 2009-11-11
Reinstalling is really no big deal, and you don't have to loose all your data and configurations just backup the home folder.

---

### Post by ComputerJy on 2009-11-11
Actually I only had to reinstall everything from synaptic. I had a problem or 2 with some packages but It's all going fine.

Thanks guys

---

