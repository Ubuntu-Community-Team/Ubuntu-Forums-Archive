---
title: "Sony Vaio P series (P11Z) - audio and umts"
date: 2009-10-30
forum: Hardware
---

### Post by excogitation on 2009-10-30
Since 9.10 is now official - who can confirm that audio isn't working on the P series - especially the mic.

Also - am I right that UMTS only works when enabled in Win, or is there a known solution?

---

### Post by excogitation on 2009-11-01
bump

---

### Post by DShad on 2009-11-03
> **excogitation said:**
> Since 9.10 is now official - who can confirm that audio isn't working on the P series - especially the mic.

Also - am I right that UMTS only works when enabled in Win, or is there a known solution?

I need help configuring the mic with my freshly installed Ubuntu Netbook remix 9.10 on a Sony VGN-P530.

Everything else worked "from the box" except the mic.  I tried adding "model=vaio" to the "options snd-hda-intel" line but no change.

Thank you.

---

### Post by excogitation on 2009-11-03
You can try "hp-bpc" and "toshiba-s06" - I had it working a few times - but can't reproduce it atm.

Also afterwards you need to set the mic correctly with "alsamixer".

---

### Post by sunseeker888 on 2009-11-17
Guys

Need some help. I have just installed Ubuntu on my GF p-series.

But wiresless is disabled for some reasons. Can somebody tell what the heck is happening. The option is greyed out.

and secondly, did someone manage to get skype working on it with video and soung in/out (mic / speakers)

---

### Post by DShad on 2009-11-30
> **sunseeker888 said:**
> Guys

Need some help. I have just installed Ubuntu on my GF p-series.

But wiresless is disabled for some reasons. Can somebody tell what the heck is happening. The option is greyed out.

and secondly, did someone manage to get skype working on it with video and soung in/out (mic / speakers)

Still haven't managed to make it work.  Does that mean I cannot replace XP on my netbook?!! :(

---

### Post by excogitation on 2009-12-01
> **sunseeker888 said:**
> Guys

Need some help. I have just installed Ubuntu on my GF p-series.

But wiresless is disabled for some reasons. Can somebody tell what the heck is happening. The option is greyed out.

and secondly, did someone manage to get skype working on it with video and soung in/out (mic / speakers)

I'm not familiar with "GF" - but what Vaio P is it exactly?
In particular - what wlan card? (lspci -vnn if you don't know)

Regarding skype - that should now work. At least I have a working cam in cheese - and the Mic is working as well (don't know if because of an update or fiddling on my end).

> **DShad said:**
> Still haven't managed to make it work.  Does that mean I cannot replace XP on my netbook?!! :(
Apparently not ;-)

---

### Post by DShad on 2009-12-12
Are you telling me that now everything works on your side?

I installed Skype 2.1 beta and prayed that it would make my MIC to work, but still no luck.  What have you done to make your mic work again?

---

### Post by excogitation on 2009-12-30
hey DShad,
sorry for the long response.

Well apart from umts only working on warm boots ... everything is working.

I don't know if you have to change /etc/modprobe.d/alsa-base.conf - but I think I did at some point.

At the moment the last lines read:
```

# options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel model=auto

```
reboot (or restart alsa), use alsamixer to set the mic volume to high, reboot again and
sound preferences -> input should show a working mic.

After that you only need to disable "Allow Skype to automatically adjust my mixer levels" and you should be set.

[Launchpad #141445]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/141445")

---

### Post by krestfallen on 2010-06-16
- download and extract
[http://www.logic.at/people/preining/software/sony-laptop_-series-0.9np5.tar.gz](http://www.logic.at/people/preining/software/sony-laptop_-series-0.9np5.tar.gz) 
- install module
$ cd /path/where/you/extracted/
$ sudo make
$ sudo make install
$ sudo reboot

---

### Post by krestfallen on 2010-06-17
sorry, forget to mention, this is for the wwan-module - after these steps it works - well i haven't really tested it - but its visible in the network connections and i can config it

on 9.10, audio works for me

for the mic, perhaps look here: [http://ubuntuforums.org/showpost.php?p=4238790&postcount=4]("http://ubuntuforums.org/showpost.php?p=4238790&postcount=4")

---

