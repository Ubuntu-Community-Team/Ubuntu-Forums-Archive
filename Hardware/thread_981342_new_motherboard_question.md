---
title: "new motherboard question"
date: 2008-11-13
forum: Hardware
---

### Post by gregorio on 2008-11-13
I was just wondering what one would have to do if the motherboard needs replaced.  I ask because with windows, it is a song and dance one has to do to replace the motherboard with an existing hard drive, needing to do a windows repair so that windows will replace drivers and such.  Would one have to do something similar with Ubuntu?

---

### Post by zozio32 on 2008-11-13
Well, I just had to have the mother board of my Dell XPS M1330 replaced as my graphic card fried up.
Since then, i don't have the sound any more on Ubuntu. I am sure the hardware is fine because I have no problem while running the laptop with Vista.
It's funny, if I try to get a sound out of Ubuntu, I can definitely ear some creaking, like the computer was trying but not managing.
oh, I forgot to tell: I am running Ubuntu 8.10

If someone has a solution for this, like re-installing some driver, I'll be very thankful.

---

### Post by Mardoct909 on 2008-11-13
Replacing a mobo isn't really relevant to the OS. So long as the replacement mobo supports all your various hardware, you can just pull it all out and slap it in the new one, easy peasy lemon squeezy*. The OS is on the hard drive, so you can replace the mobo without affecting the OS.

Unless you aren't using an kernel that auto-detects hardware...

Which you are if you're using any Ubuntu.

*Ok, not really. It's rather tiresome to ground yourself, get all the hardware out and put it somewhere the static wont get to them, un screw the mobo, take it out, put in the new one, screw it on, place everything into its respective slot and, if you need it, modify the BIOS to your desires.

---

### Post by Skripka on 2008-11-13
It doesn't effect the OS per se--but many of the libraries might get funnied up when changing out hardware.  Duplicate which SATA ports you plug your drives into, and use the same PCIe slots as much as you can, so addresses are as close to identical as possible, and you'll minimize the need to fix things after the fact.  Many libraries on Linux are NOT smart enough to know when hardware addresses change.

---

### Post by Mardoct909 on 2008-11-13
I just keep backups of important data so I can reinstall on demand. If at all possible, reinstalling would be the best choice.

---

### Post by gregorio on 2008-11-14
Isn't it funny how windows has had such an effect on my view of what needs done on computers.  Or not.  I tend to forget that a new installation of Ubuntu is about an hour more or less, depending on how busy the servers are when updating.  A couple of weeks ago, I installed a new hard drive for Ubuntu and just did a clean install with 8.04.  The servers were quite busy and updating took about an hour itself.  I also had a drive that had a corrupted windows install.  So I wiped the drive and reinstalled windows xp.  With drivers and all, it was literally an all day job.  And I still wasn't quite done, needing to install different things such as Java.  Oh how much easier the Linux world is.

---

### Post by null_pointer_us on 2008-11-14
> **gregorio said:**
> Isn't it funny how windows has had such an effect on my view of what needs done on computers.  Or not.  I tend to forget that a new installation of Ubuntu is about an hour more or less, depending on how busy the servers are when updating.  A couple of weeks ago, I installed a new hard drive for Ubuntu and just did a clean install with 8.04.  The servers were quite busy and updating took about an hour itself.  I also had a drive that had a corrupted windows install.  So I wiped the drive and reinstalled windows xp.  With drivers and all, it was literally an all day job.  And I still wasn't quite done, needing to install different things such as Java.  Oh how much easier the Linux world is.

I'll second this!

---

### Post by zozio32 on 2008-11-14
well, i don't know about the easiness of squeezing lemons with the old mother board because Dell want it back.;)
What I am sure, is that before swaping, the sound was working fine and it is not any more now.
Any idea of how I can reconfigure my sound card without re-installing everything?
I guess it's quite possible that Dell or any other manufacturer will have updated some components from 1 year to the other, and suddenly your OS that was quietly waiting in the your HD has to deal with slightly different component.

---

### Post by zozio32 on 2008-11-15
up!

no one has a suggestion ?

I'd like not to re-install all my system for a sound problem. They must be way to check if ubuntu is finding a sound device, and to re-install it if needed no?

---

### Post by Skripka on 2008-11-15
> **zozio32 said:**
> up!

no one has a suggestion ?

I'd like not to re-install all my system for a sound problem. They must be way to check if ubuntu is finding a sound device, and to re-install it if needed no?

Go into Synaptic and re-install anything on your system that relates to whatever sound drivers you were using (this is fairly easy-if you're just using ALSA)

---

### Post by zozio32 on 2008-11-15
didn't work

I have done a re-installation of all the alsa related package, and nothing change. I just get small crackling sounds.

Is their a way to force re-list any hardware component in a way, and re-install the sound card. I guess Alsa is not edaling directly with the card itself no?

---

### Post by Skripka on 2008-11-15
> **zozio32 said:**
> didn't work

I have done a re-installation of all the alsa related package, and nothing change. I just get small crackling sounds.

Is their a way to force re-list any hardware component in a way, and re-install the sound card. I guess Alsa is not edaling directly with the card itself no?

Are you using a dedicated sound card, or on motherboard sound?

---

### Post by zozio32 on 2008-11-16
Not sure....   I am not that interested in sound in general so I didn't pay much attention to it.

How can I check in Ubuntu? (I'll probably found out how in Windows, but I am curious)

---

### Post by zozio32 on 2008-11-17
up !

no one else on this problem?

---

### Post by zozio32 on 2008-11-20
Well, I really can't get the sound back, so I am thinking re-installing everything.

Is it possible in any way to keep my settings: my bookmarks set up in firefox, my list of favourites in Picasa, etc?

and, can I re-install from my Ubuntu, or do I need to download the CD?

---

