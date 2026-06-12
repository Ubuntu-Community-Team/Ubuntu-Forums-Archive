---
title: "Sound problem with ASUS PSKPLC -C/1600"
date: 2009-07-10
forum: Hardware
---

### Post by Completely Newbie on 2009-07-10
[SIZE=4]Hi guys, can someone help me with the sound on my desktop?  I'm using the above mainboard, 2gb ram, Nvidia 9600GT graphic card, intel core 2 duo 2.2 GHz and 350 gb of hard drive. i can not hear any sound from the SOUNDMAX A -2230 and it's a big drawback for a wonderful OS like Ubuntu. :lolflag:
[/SIZE]

---

### Post by Completely Newbie on 2009-07-11
Can someone please help?

---

### Post by b@sh_n3rd on 2009-07-11
First, Welcome to the Community! What exactly is your sound card? I'm not able to find your board on the ASUS website. I'm not quite sure of this but try the following code to find your audio card: ```
# aplay -l
``` This might not work if your sound card isn't detected (can't rightly remember). You can also try checking your user privileges by going to, System > Administration > Users and Groups. Hit unlock, then select your username from the list. At the new window that appears check in the "User Privileges" tab for something like "Audio devices" and mark that. I have an older PC with a Yamaha card that I had to load manually. To find the correct module, I need to know the type :D

---

### Post by DownTown22 on 2009-07-11
I think you mean an Asus P5KPL-C/1600, as that's the closest thing on the Asus website.

If that's the case, it looks like it's using a VIA chipset for audio.

Even though it says that, let's give this a go:

First, make sure the system is fully up to date.  If there's still no sound, try this...


Open a terminal and type:

sudo gedit /etc/modprobe.d/alsa-base


Then add the following lines to the very end of it:

options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel


If that doesn't work, you can always open that file back up, and delete those lines you added.

---

### Post by DownTown22 on 2009-07-11
Actually, before we try all that, it might be best to check to make sure all the volume sliders are turned up.

---

### Post by Completely Newbie on 2009-07-12
Well, I've tried and figured out why it hadn't worked before. however, the sound didn't meet my expectation. My soundmax speakers sound great on Windows but they deliver very small volume in Ubuntu. Still, I'll try contacting Asus for the best solution to come. Thank you guys

---

