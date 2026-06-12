---
title: "OSX has &quot;Archive &amp; Install&quot;. What about Ubuntu?"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by rumplestilts on 2009-05-21
If you're not an OSX user, you may not be familiar with the phrase "archive & install". This is an installation choice that permits all the user accounts to be retained while the OSX installer disc completely replaces all of the operating system and original applications (apps that come with OSX, not 3rd party apps which are ignored and will be retained).

Is there such an option in Ubuntu? Or is the Ubuntu OS so intertwined with any existing user accounts that to do this renders the user accounts *out of sync* with the installed software?

I ask this because I recently let my machine upgrade from 8.1 to 9.04. It asked me one question (something about whether I wanted to retain a specific config file - I told it to replace it) during the upgrade process. Once the machine rebooted, I discovered that my installed printer didn't work and couldn't even be deleted (whether in the Printer app or web CUPS page). I had to do what I guess Ubuntu calls a "clean" install but this erased the hard drive and I lost my user account (but had my important data backed up so no harm).

Thanks!

---

### Post by maflynn on 2009-05-21
wouldn't keeping your /home folder on a separate filesystem the same thing?

Installing a newer version of Ubuntu would then keep your /home folder untouched

---

### Post by rumplestilts on 2009-05-22
"separate filesystem". Okay, I guess you mean another partition (in OSX parlance). So when I wanted to do the "clean install" I mentioned, what would I have to select when I come to the partitioning choices in the process? By this I mean during the *first* installation in order to get that separate partition/filesystem, and then during the "clean install" procedure when I again would come to this partitioning choice?

Thanks for your assistance

---

### Post by rumplestilts on 2009-05-27
I discovered the process but I did it when doing a fresh install. I let Ubuntu do an automatic partitioning, then interrupted the installation process and ran it again. I then looked at the newly created partitions and modified them so I had a "/" and a "/home"; I used the "/" partition and split it, then assigned the "/" and "/home" to them and, finally, let the process (and subsequent installation) proceed normally.

I'll have to actually try the clean install to see if I understand what has to be done at that point.

---

### Post by presence1960 on 2009-05-27
when doing a clean install choose manual option at partitioner screen. highlight root partition and click Edit. set primary or logical, filesystem and mountpoint (/). Then highlight /home partition. Click Edit. set Mountpoint as /home. _**Make sure format box is unchecked or you will format the partition!**_ Continue with the install. This will automount your /home partition when you run Ubuntu. It will be seamless you'll never know the difference but you will have your data on a separate home partition.

---

