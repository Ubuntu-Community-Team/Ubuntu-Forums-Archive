---
title: "A Few Issues on my Acer Aspire 3050"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by gamerfreak on 2007-07-08
Well, I got a lower end Acer Aspire 3050 laptop. It came pre-loaded with vista, and even with a ram upgrade I installed it ran like crap. It was sluggish and crashing constantly. I was getting ready to send it back, but then I but ubuntu on it and it runs like a champ. It basicly revived my laptop.

Most everything works fine, video and wifi are great however I'm having 2 issues I hope someone can help me with.

1. Sound doesnt seem to work. Probebly a driver issue or lack of.

2. kpowersave doesnt seem to be detecting my battery. It tells me when I'm running off an AC adapter, but when I'm not it says "Battery 1 not present".

Thanks.

---

### Post by Twintop on 2007-07-08
What kernel are you running? 2.6.20-13 through 2.6.20-15 broke a lot of Aspire Laptops' sound, but 2.6.20-16 fixed it for most people.

---

### Post by gamerfreak on 2007-07-08
I am running 2.6.20-16

---

### Post by gamerfreak on 2007-07-08
Am I allowed to bump here?

I guess its a bit late.

---

### Post by gamerfreak on 2007-07-30
I am still having this issue if anyone can help me :confused:

---

### Post by ugm6hr on 2007-07-30
It's worth trying editing alsamixer first:
[http://ubuntuforums.org/showpost.php?p=3103572&postcount=9](http://ubuntuforums.org/showpost.php?p=3103572&postcount=9)
If that doesn't make sense - look at the rest of the thread.

I have a different Acer - but this might help:
[http://ubuntuforums.org/showthread.php?t=457011](http://ubuntuforums.org/showthread.php?t=457011)

I had to go back to 2.6.20-15 kernel to keep my sound working without recompling ALSA.

---

### Post by gamerfreak on 2007-07-30
> **ugm6hr said:**
> It's worth trying editing alsamixer first:
[http://ubuntuforums.org/showpost.php?p=3103572&postcount=9](http://ubuntuforums.org/showpost.php?p=3103572&postcount=9)
If that doesn't make sense - look at the rest of the thread.

I have a different Acer - but this might help:
[http://ubuntuforums.org/showthread.php?t=457011](http://ubuntuforums.org/showthread.php?t=457011)

I had to go back to 2.6.20-15 kernel to keep my sound working without recompling ALSA.

From the first link when I tried 

```
alsamixer
```

I got this error:

```
alsamixer: function snd_mixer_load failed: Invalid argument
```

---

### Post by ugm6hr on 2007-07-30
I think you must have the same sound card as me!  Have a look at the second link - I've posted on page 2 ([http://ubuntuforums.org/showpost.php?p=2869640&postcount=12](http://ubuntuforums.org/showpost.php?p=2869640&postcount=12)).

I decided to just revert to the 2.6.20-15 kernel, then used alsamixer as per first post.

If you want to see my hardware:
[http://ubuntuforums.org/showpost.php?p=3100932&postcount=3](http://ubuntuforums.org/showpost.php?p=3100932&postcount=3)
(feel free to post your xorg there too).

---

### Post by gamerfreak on 2007-07-30
> **ugm6hr said:**
> I think you must have the same sound card as me!  Have a look at the second link - I've posted on page 2 ([http://ubuntuforums.org/showpost.php?p=2869640&postcount=12](http://ubuntuforums.org/showpost.php?p=2869640&postcount=12)).

I decided to just revert to the 2.6.20-15 kernel, then used alsamixer as per first post.

If you want to see my hardware:
[http://ubuntuforums.org/showpost.php?p=3100932&postcount=3](http://ubuntuforums.org/showpost.php?p=3100932&postcount=3)
(feel free to post your xorg there too).

I see.

So how do I go about downgrading to 2.6.20-15?

---

### Post by ugm6hr on 2007-07-30
> **gamerfreak said:**
> I see.

So how do I go about downgrading to 2.6.20-15?

Assuming you have Feisty - it was the default kernel.  Unless you deleted it, it should still appear as an option in GRUB.  Try rebooting - and look at GRUB boot options - it should be there somewhere.

---

### Post by miket3115 on 2008-04-04
Bit of a dead thread but it might help someone try looking for a Linux driver with AMD. Most Acer 3050's have AMD chipset I beleive.

[http://www.amd.com/us-en/ConnectivitySolutions/TechnicalResources/0,,50_2334_2452_11363,00.html](http://www.amd.com/us-en/ConnectivitySolutions/TechnicalResources/0,,50_2334_2452_11363,00.html)

---

