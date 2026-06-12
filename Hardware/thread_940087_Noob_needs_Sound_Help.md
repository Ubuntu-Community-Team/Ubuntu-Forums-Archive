---
title: "Noob needs Sound Help"
date: 2008-10-06
forum: Hardware
---

### Post by LINUX_ID10T on 2008-10-06
I have spent the better part of the last week trying to get sound through my speakers on a laptop. The driver is there and sound does come out of my headphone jack, but NOTHING I do helps the speakers.

Can someone please send me NOOB level instructions....PLEASE?

I have the alsamixer unmuted.
I do not have a external Amp box in preferences
The driver is listed in hardware
Sound does come from headphone jack
I am running latest greatest 8.04 with no updates being required

The two test machines are:
Tecra A8 with alc262
Alienware Area 51 M9750 with 82801G aka realtek alc882/885

This is for testing in a professional environment on a project in South Africa (home of the ubuntu) and audio and video is a requirement not just a nice to have.

I have run command after command, and just need a simplified (up to date) guide on how to perform these tasks. 

I am a Microshaft (ab)user and I am trying to become a born-again Penguin.... :)

Mods if you are reading this please for the love of god please send me some links, I will read my butt off just need a valid starting point.

Thanks

The Linux_ID10T

---

### Post by Sealbhach on 2008-10-06
This is a great step-by-step troubleshooting guide. Have a look and see if it can help you.

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")


.

---

### Post by LINUX_ID10T on 2008-10-08
Thanks for the link. I tried all and I must be doing something wrong. I still do not have sound from my speakers. 

The sound card does render sound through the headphones, but not through speakers. 

The devices accurately show in aplay -l / lspci -v / and the hal hardware list. 

I am being to think this is more of a pain than it is worth, yet remember that i accually got into windows pc's based on a sound issue i was having in win3.11 and that i spent days configuring IRQs/DMA's dip switches and jumpers to make it work.... so then i feel like i need to accomplish this as a first step.

ALSAMIXER also sees the card and when i mute the headphones the card responds, so I am lost to why I am not getting sound from speakers.

Anyone else want to speculate as to what my problem is other than I am the LINUX_ID10T?

---

### Post by Sealbhach on 2008-10-09
Are these external speakers or are they built into the PC or laptop?

Can you give the result of:
```

cat /proc/asound/modules
```

.

---

### Post by LINUX_ID10T on 2008-10-09
The return on the command was 0 snd_hda_intel

Headphones and external speakers work but onboard speakers do not. This will not be acceptable for my purposes.

Not giving up though. The fact that sound works via speakers and headphones just tells me that the card is installed and working (all be it limitedly) in this OS.

---

### Post by Yellow Pasque on 2008-10-09
Perhaps your ALSA needs upgraded. There's a script for that: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

Also, configure alsa-base if you have not already. [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by Sealbhach on 2008-10-10
Yes, I thinking configuring the modules in alsa base might fix it.


Looking up Toshiba laptops in this list of module options:
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#886](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt#886)

we see "Toshiba laptop support" at line 886 so we try adding the name suggested which is "toshiba." 
 
So for your Toshiba laptop Tecra A8, open up the config file in your terminal:

```
sudo gedit /etc/modprobe.d/alsa-base
```

and at the very end of the file add this line:
 
```

options snd-hda-intel model=toshiba
```

Save close and reboot.

Doing this for my Vaio solved all my sound problems, hopefully it will work for you. I was getting sound in the left speaker only, and no sound in the headphones.


.

---

### Post by LINUX_ID10T on 2008-10-11
I have tried all of the suggestions above.

I even added other optional snd-hda-intel entries to see if there was any affect... to my disappointment none.

I then reloaded the unbuntu os thinking that I may have inadvertently screwed something else up by fooling around. After which I ran updates (226) updates from my base install disc.

And that is where it currently stands fresh, unmolested by the linux_id10t, and still no sound from speakers. 

I once found a post about creating an additional switch in sound, but cant seem to locate it again. 

Additionally I will spend the weekend doing research to see if I find any other fresh ideas on other sites.

---

### Post by Sealbhach on 2008-10-11
Try the module option "laptop".

Other than that, I don't know. Have you tried alsamixergui?


.

---

### Post by markbuntu on 2008-10-11
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

