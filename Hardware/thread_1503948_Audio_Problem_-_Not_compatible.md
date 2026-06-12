---
title: "Audio Problem - Not compatible?"
date: 2010-06-07
forum: Hardware
---

### Post by Basti4n on 2010-06-07
Hi all,
I'm new to the forum and also to the Ubuntu world. Therefore you can imagine I had some troubles, also because I'm not IT expert.
I installed Lucid 10.04 on my HP laptop getting rid of Windows and now it is my only option to work and live. :) It worked perfectly until yesterday when I realized I didn't have sound. No audio at all. The volume control on the top bar is zero.
From the panel System > Preferences > Audio I can see that in 'Hardware' there's no sound card. It's like Ubuntu doesn't see it.
I surfed the millions of threads on this topic and I started to give it a try. My laptop is a HP Compaq 6720s processor Intel Core Duo T7250 2GHz.
When I type lspci on the terminal I get this among the other info:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

which apparently means that Lucid sees my integrated sound card.
When typing lspci | grep -i audio I get this

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

But when I type sudo aplay -l I get this

No sound card found....

And when trying to enter alsamixer from terminal I get this message:

No file or directory.

I'm confused I don't know what to do.

I also went to the alsamixer page to check the soundcard list and I found that there's no ICH8 architecture in the list of Intel compatible products. [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

Isn't that it doesn't support my card?? Yesterday everything worked fine...
Actually in the 'discussion menu' other users say they have the same problem with the same card.
Please if you know how to fix this I'll be so glad to all.
Thanks in advance..
S.

---

### Post by Basti4n on 2010-06-07
Any help please?????
:(

---

### Post by Basti4n on 2010-06-07
OK I've solved it following this guide. For those who will need it.
[http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+alsamixer+soundcard](http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+alsamixer+soundcard)
I just did this:

[SIZE=2]1) Remove these packages 	Code:
 	sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
 [/SIZE][SIZE=2]
(2) Reinstall those same packages[/SIZE][SIZE=2]
 	Code:
 	sudo apt-get install linux-sound-base alsa-base alsa-utils 
 [/SIZE]Now it works! :)

---

