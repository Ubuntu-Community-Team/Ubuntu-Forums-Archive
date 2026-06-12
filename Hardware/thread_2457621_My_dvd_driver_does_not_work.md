---
title: "My dvd driver does not work"
date: 2021-02-05
forum: Hardware
---

### Post by ioriaperlinux on 2021-02-05
Hi,
I have xubuntu 20.04.2 LTS, on a fujitsu Lifeboof A series.

Looks like there is no way to make the dvd internal drive to work, even if it worked perfectly with Windows before.

Any help? Sorry, I am not so skilled.
Thanks in advance...
Ioria

---

### Post by CelticWarrior on 2021-02-05
What type of DVDs are you trying it with? DVD-ROM or DVD-Video?
The former should just work, the latter needs additional software.

If a DVD-ROM isn't recognized then very likely your drive is faulty. Please note that it may still read CDs (different laser).

---

### Post by ioriaperlinux on 2021-02-05
I have tried a verbatim DVD-R I burned.
Then an original DVD-VIDEO.
Then also Compact Disk.
I load the drive, making noise for some seconds (like for revolving in the driver) and nothing happen. I tried to open also VLC, media --> open disk, click on play it does not work. I don't know, I feel it is like the driver. I mean, before installing xubuntu, there was windows and it worked perfectly... Did it crash just when changing OS? yes, it could be... is there any check I can do to verify that?

Thanks.
Ioria

---

### Post by CelticWarrior on 2021-02-05
For DVD-Video: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Regarding the other formats... A DVD-R that you burned says nothing about what type it is. You can as easily burn a DVD-ROM or a DVD-Video using any blank DVD-R or DVD+R media. And which "Compact Disk", what contents, what were you expecting to happen, exactly? Please note that by default Ubuntu does not do "auto-play"...

---

### Post by ioriaperlinux on 2021-02-05
Thanks celtic worrior.

I have followed instructions at the page you linked, trying to play original DVD Video. Installed **libdvd-pkg. **the using vlc, enabling flag on "no dvd menu". Installed regionset and...
```
rosa@rosa-ordenador:~$ sudo regionset /dev/sr0
[sudo] password di rosa: 
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "/dev/sr0"!
Please ensure there is a readable CD or DVD in the drive.
rosa@rosa-ordenador:~$ 

```

But the dvd is there.
 
About the burned dvd, it is a DVD-R, burned with DVD data.

CD was original, content is music. What should I supposed to do to make it to play? I have even tried from VLC... I don't know, could it be not supported by Ubuntu?
Ioria

---

### Post by crip720 on 2021-02-05
Good chance that the DVD drive died.  They are known for working one day perfectly, the next not.  Would get a new USB drive and be happy.  Have four or five dead DVD drives/players.  Ubuntu supports most DVD drives.  Can try to take it out and cleaning, google cleaning DVD drives, but think you be happier buying a new one, they are usually cheap.

---

