---
title: "Lenovo G555 Headphone/Speakers and Mic Issues"
date: 2011-06-13
forum: Hardware
---

### Post by LeapingLlama on 2011-06-13
Hi all!
I recently decided to upgrade from 10.04 to 10.10 and have been experiencing some sound issues. My laptop (a Lenovo G555) speakers work perfectly, but whenever I plug in headphones, the headphones will neither mute the speakers nor play sound. Also my mic does not pick up any sound. I experienced similar issues in 10.04, but was able to find a [COLOR=Blue][solution]("http://ubuntuforums.org/showthread.php?t=1517261")[/COLOR]. However that solution does not work for me in 10.10.

I already went ahead and ran alsa-info.sh and posted the results [COLOR=Blue][here]("http://www.alsa-project.org/db/?f=fa1c1bdb49bf7e8463e555a0b1be85ad585171e0")[/COLOR]. Hopefully the solution will be no more difficult than upgrading alsa, adding some lines to alsa-base.conf, or a combination of both. All help, time, and suggestions given are greatly appreciated!

---

### Post by LeapingLlama on 2011-06-23
I poked around the forums a bit and was able to fix my headphone jack issue by adding a line to alsa-base.conf:
```
options snd-hda-intel model=ideapad
```

However, my microphone still refuses to work.
Also, I first tried installing the linuxant driver, but that seems to have issues compiling with the newer kernels used in 10.10 or something, so I had to reinstall alsa. If anyone has managed to get their microphone working with a Conexant CX20585 chipset, please do share! :grin:

EDIT: here is the [NEW output]("http://www.alsa-project.org/db/?f=fc4dcf7072d4f0095900c18fd8c5ee68188c9fbf") for alsa-info.sh

---

### Post by LeapingLlama on 2011-06-24
I found a very simple solution that fixed everything. My mic and headphones function properly now. I installed the [latest upstream development alsa code]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"), and everything works fine.

But before I did that, I removed the line I had added to /etc/modprobe.d/alsa-base.conf earlier, i.e.
```
options snd-hda-intel model=ideapad
```

Now everything works great!

---

### Post by Photon-ub on 2011-07-01
Thank you very much for posting. I had the same issue with my laptop for a while, and Google eventually redirected me to your thread. ^^

Almost the same problem: sound still coming out of the speakers when plugging something in the headphone jack (sound playing both through speakers and headphones), solved with:
> **LeapingLlama said:**
> I installed the _[COLOR=RoyalBlue][latest upstream development alsa code]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")[/COLOR]_, and everything works fine.

For reference: 

[LIST]
[*]my laptop is a MSI FX-603 (may affect all MSI FX-60* models),
[*]my sound chip is reported by *lspci* as an "Intel Corporation 5 Series/3400 Series Chipset High Definition Audio",
[*]occurs on Linux Mint 11 (Ubuntu 11.04) and earlier releases
[/LIST]
 
Is there anywhere we  could report this fix, to hopefully make it mainstream? The wiki page you linked doesn't mention any contact&#8230;

---

### Post by kb738 on 2011-07-26
Thanks for the post!

Like the previous poster, I'm on a MSI FX model (FX-602).  Running Linux Mint 11 64 bit, had the same issue with sound playing in both the speakers and headphones.  I tried editing the alsa-base.conf using

options snd-hda-intel model=targa-2ch-dig

I tried others as well for the model but nothing worked.  Finally after installing the [latest development code]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules") it worked!  Hope this helps others.

---

