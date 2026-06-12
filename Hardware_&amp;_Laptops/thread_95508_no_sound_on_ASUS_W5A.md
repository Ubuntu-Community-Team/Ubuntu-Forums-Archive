---
title: "no sound on ASUS W5A"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by mengqing on 2005-11-26
I tried all the solutions on this forum about solving intel HDA... but unfortunately none of them worked..

i got the following warnings when booting up, but i am not sure what they mean
[I]
/etc/init.d/alsa Warning: The `start` method is deprecated and will be removed
/etc/init.d/alsa Warning: Use alsa-utils initscripts instead.
Setting up ALSA.....
/etc/init.d/alsa-utils Warning: `alsactl restore` failed with error message `No state is present for card Intel`[/I]

the sound driver appears to be loaded, because I can see HDA Intel at sound property and i have unmuted everything. But there is still no sound at all..

I tried everything... changing kernel from 2.6.12.9-386 to 2.6.12-10-686 to 2.6.14a-386, downloaded and installed the driver from Realtek website..aa
none of them worked...aa

can someone help me..? I thought Ubuntu 5.10 should've supported ALC880 already..

---

### Post by LeTon on 2005-11-26
I got sound on my asus Z33A-V  ONLY after following this how to and installing Vanilla kernel:

[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

Nothing worked before...if you have tried this already and it does not work...
But I believe that we have the same - Intel ICH6 audio device, right?
Good luck

---

### Post by adduds on 2005-11-26
[QUOTE=LeTon]
But I believe that we have the same - Intel ICH6 audio device, right?
Good luck[/QUOTE]

I have an Intel ICH6 Audio Device, and my sound doesn't work either

---

### Post by mengqing on 2005-11-26
[QUOTE=LeTon]I got sound on my asus Z33A-V  ONLY after following this how to and installing Vanilla kernel:

[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

Nothing worked before...if you have tried this already and it does not work...
But I believe that we have the same - Intel ICH6 audio device, right?
Good luck[/QUOTE]

Hi, I just upgraded to kernel 2.6-14 vanilla version

unfortunately, i still get the same Warning, and the sound still does not work...

thx for the help anyway.

---

### Post by adduds on 2005-11-26
i tried that aswell, and my sound does not work either still. and now my wireless card is not recognized anymore either

*frustrated*

---

### Post by mengqing on 2005-11-26
[QUOTE=adduds]i tried that aswell, and my sound does not work either still. and now my wireless card is not recognized anymore either

*frustrated*[/QUOTE]

lol looks like we are on the same boat..

I really dont like dual booting XP and linux...

---

### Post by mengqing on 2005-11-27
I installed the latest driver from Alsa-project which is 1.0.10

and now the sound finally WORKED

woohoo:cool:

---

### Post by garconcn on 2006-01-10
Glad to see this, I'm using W5A too.;)

---

