---
title: "Strange problem in VAIO: if I try to use 1280x800, the computer slows down"
date: 2013-06-16
forum: Hardware
---

### Post by srfito on 2013-06-16
Hello.

I've been using Lubutu (first 12.10 and then 13.04 when realeased) without any problem on my Sony VAIOVGN-SZ71MN. But since last week I have a very strange problem that I will try to explain:

1. The resolution changed from 1280x800 to 1024x768.

2. I changed it back to 1280x800 and two strange things happened: (i) the wallpaper kept the small size and (ii) Firefox wouldn't maximize in 1280x800 but in 1024x768, on the left side of the screen.

3. And even worse: after using it for some minutes in 1280x800, the computer dramatically slows down and it's almost unusable, as if I were downloading a huge file at maximum speed.

I wasn't very worried because I thought that I had an easy solution: reinstalling Lubuntu 13.04. But I was mistaken. I tried four different things:

1. First I installed it as a simple re-installation (keeping all the personal files). Nothing changed.

2. I re-installed it without keeping files... and nothing happen either.

3. I re-installed manually (formatting the partition!)... and nothing happened again!

4. I tried the 64bit version (I had 32bit)... and nothing changed!!!

You might think that it's clearly a hardware problem but

- The 1280x800 resolution works perfectly on Windows XP.

- It also works perfectly using Lubutu Live CD (without installing).

I know that all this sounds crazy, but I'm quite used to deal with setup problems and this is the first time I cannot fix it.

Any idea about the origin of the problem or the solutions for it?

Thank you very much in advance.

srfito

---

### Post by gordintoronto on 2013-06-17
Does this laptop have hybrid graphics, or just the Nvidia 8400? Have you installed an "additional driver" and run Nvidia X Server Settings?

---

### Post by srfito on 2013-06-17
> **gordintoronto said:**
> Does this laptop have hybrid graphics, or just the Nvidia 8400? 

I have no idea... but I guess just Nvidia (when I bought it I didn't ask for anything special)

> **gordintoronto said:**
>  Have you installed an "additional driver" and run Nvidia X Server Settings?

No, I never needed it. This laptop never had problems with the resolution, nor in several versions of Ubuntu and Lubuntu, neither in Windows XP. As I said, it still works on Windows XP and with Lubuntu live CD, but not in a Lubuntu installation (even in a clean one). But since April until last week, it also worked.

However, what should I install exactly?

By the way, I have realised that when starting Lubuntu I can read this (only for several seconds):

[13.870064] uvcvideo: Failed to query (129) UVC probe control: -32 (exp. 26)
[13.870066] uvcvideo: Failed to initialize the device (-5).
[13.909177] kvm: disabled by bios
[13.914741] kvm: disabled by bios

Thank you very much again.

---

### Post by user_of_gnomes on 2013-06-17
It sounds a bit like you might be better off using the propietary Nvidia driver. You're probably using the open source Nouveau now which may not be as efficient on higher resolutions.

---

### Post by srfito on 2013-06-17
Well, it's not exactly less efficient: it's just that the laptop becomes so slow that I can't even use it!. But I could before.

However, what should I install exactly?

Thank you again!

---

### Post by srfito on 2013-07-16
Hello again.

Just in case someone is interested, it seems that the problem is related to the "Stamina/Speed" button. The mistery remains, because I've always used Lubuntu in Stamina mode, but at least now I can solve the problem switching the button to Speed.

Not an orthodox solution, but at least it works :-)

---

