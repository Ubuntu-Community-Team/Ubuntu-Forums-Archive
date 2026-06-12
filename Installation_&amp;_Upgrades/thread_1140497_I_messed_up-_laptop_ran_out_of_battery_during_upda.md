---
title: "I messed up- laptop ran out of battery during update to 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ajhodges8 on 2009-04-27
I decided to update to 9.04 on my laptop, and while it was downloading I closed the lid and put it to the side (I had well over an hour of battery life) telling myself I'd check back in a few minutes.
Then I forgot about it.
When I realized what I had done, the laptop was already out of battery (i was too lazy to plug it in, the cord was in my backpack) and I was fearing turning it on because I knew that some point in the installation a prompt probably came up and just sat there, and then the power cut off thus screwing my installation.

So I booted it up, GRUB was slow to load but I was able to load xubuntu, and the new login screen came up, I put in my info... and then the screen just went blank to the background color, and it said that the desktop environment couldn't be loaded.

So is there anyway I can fix this without having to reinstall completely? Will I lose my files? I program using gcc/g++ and I have my projects backed up elsewhere but it would still be nice to not have to set everything back up the way I like it again.

I'm still somewhat of a linux n00b so I would appreciate a little bit of help.

Thanks!

p.s. no need to tell me I'm an idiot for not plugging my laptop in, I already know.

---

### Post by abn91c on 2009-04-27
> **ajhodges8 said:**
> I decided to update to 9.04 on my laptop, and while it was downloading I closed the lid and put it to the side (I had well over an hour of battery life) telling myself I'd check back in a few minutes.
Then I forgot about it.
When I realized what I had done, the laptop was already out of battery (i was too lazy to plug it in, the cord was in my backpack) and I was fearing turning it on because I knew that some point in the installation a prompt probably came up and just sat there, and then the power cut off thus screwing my installation.

So I booted it up, GRUB was slow to load but I was able to load xubuntu, and the new login screen came up, I put in my info... and then the screen just went blank to the background color, and it said that the desktop environment couldn't be loaded.

So is there anyway I can fix this without having to reinstall completely? Will I lose my files? I program using gcc/g++ and I have my projects backed up elsewhere but it would still be nice to not have to set everything back up the way I like it again.

I'm still somewhat of a linux n00b so I would appreciate a little bit of help.

Thanks!

p.s. no need to tell me I'm an idiot for not plugging my laptop in, I already know.
connect laptop by wire to network, reboot to recovery mode, if you cant get to the desktop at the command prompt type [COLOR="Blue"]sudo dhclient eth0[/COLOR] to "activate" the network, then [COLOR="blue"]sudo apt-get update[/COLOR] then [COLOR="blue"]sudo apt-get dist-upgrade[/COLOR]

---

### Post by ajhodges8 on 2009-04-27
thank you! I tried to do an update and it said I needed to run sudo dpkg --configure -a first.
once that was done, everything was already updated (apt-get dist-upgrade didn't install anything) and I tried rebooting and it works great now.

thanks again! :D

---

### Post by abn91c on 2009-04-27
Welcome :popcorn:

---

