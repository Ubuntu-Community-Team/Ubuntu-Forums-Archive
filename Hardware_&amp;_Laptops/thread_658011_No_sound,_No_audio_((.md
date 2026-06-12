---
title: "No sound, No audio :(("
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Beowulf.1000 on 2008-01-04
I can boot up Ubuntu 7.10 i386 live CD on my new Acer Aspire 5520 (5520-5716) but I get no audio. Not through the "5.1 Surround Sound" built in speakers, not through headphones. I have tried the Preferences->Sound and the different choices for drivers (ALSA, OSS,) but no soiund is heard even though the "Testing" slider makes it appear that audio is playing. I can play the "Experience Ubuntu" Nelson Mandela video and it plays but no audio is heard.

System: AMD Turion 64 x2 mobile cpu,  2GiB RAM, nvidia GeForce 8400mG 128MB, [COLOR="DarkRed"]nvidia MCP67 High Def Audio[/COLOR].

If I can not get audio to work on this system I am thinking I will need to sell it on ebay, I just can no handle having linux on a notebook without audio. Luckily I have not yet sold m Compaq notebook that works great with dual boot WinXP and Ubuntu linux. But I really like the look of the Acer, and the fact that is is a dual core and has nvidia graphics, if I could just get audio.

What are the chances I will get audio working on the Acer if I install it? Any ideas on how to get audio from the live CD of Ubuntu 7.10?

---

### Post by Beowulf.1000 on 2008-01-04
Sorry, never mind. I searched here on the forums for "Aspire 5520" and found others with the same problem, and solution given, so I am now hopeful. Sorry I did not search before posting a new thread. Now I am excited to go out today and buy a new internal hard drive for the laptop to put WindowsXP and Linux on,  I will take out the original drive with Windows Vista (I hate it) and store it in the box for when I need to put it back in to return the laptop for warranty repair etc. (thus not voiding my warranty).

> **Beowulf.1000 said:**
> I can boot up Ubuntu 7.10 i386 live CD on my new Acer Aspire 5520 (5520-5716) but I get no audio. ...

---

### Post by frodon on 2008-01-04
Compile the latest alsa drivers, almost all aspire laptop require the latest version (the one in the repositories is too old), i did this on my aspire 5720 laptop and it works great.

Instructions here :
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720)

Then install the backport-modules and reboot :
```
sudo aptitude install linux-backports-modules-generic
```

So install ubuntu and fix your sound ;)

---

### Post by Beowulf.1000 on 2008-01-04
Thank you, I am hopeful now. I printed the instructions. I also ordered a nice Hitachi 200MB fast laptop hard drive to put into the Acer notebook and yank out the original (that has Microshit Vista on it) so I can put WinXP and Ubuntu 7.10 on the better hard drive, and keep the original drive safe for when I need to return the notebook for repair (so as not to void the warranty). :guitar:

> **frodon said:**
> Compile the latest alsa drivers, almost all aspire laptop require the latest version (the one in the repositories is too old), i did this on my aspire 5720 laptop and it works great.
Instructions here :
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720)
Then install the backport-modules and reboot :
```
sudo aptitude install linux-backports-modules-generic
```
So install ubuntu and fix your sound ;)

---

