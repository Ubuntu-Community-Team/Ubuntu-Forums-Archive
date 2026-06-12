---
title: "Ubuntu takes time to boot: normal?"
date: 2008-09-08
forum: General Help
---

### Post by tralogik on 2008-09-08
Hi,

I read that Ubuntu (8.04) boots faster than Windows (XP). I don't agree with that statement. Ubuntu takes about one minute to boot, and much of that time is when I see that black screen with white indications (with "not automatically fixing this" on the bottom and many "starting...").

Is this normal? I know that my PC is not the latest (P4-233Mhz, 1GB RAM, 80+250GB HD), but I imagine Ubuntu can boot faster.

I have to mention that I use a dual-boot start-up (with XP).

Thanks in advance!

JS

---

### Post by Sycron on 2008-09-08
Ubuntu boots on less that a minute, but it depends on what services are you using. You should try CrunchBang linux, is more suitable for your computer, however ubuntu works just fine,

---

### Post by tralogik on 2008-09-08
Hi Sycron,

I don't use many features/services. I would say that I use a "basic configuration".

---

### Post by Sycron on 2008-09-08
Go to System-Preferences-Sessions and deactivate what you don't need.

---

### Post by tralogik on 2008-09-08
Hi,

I will take a look at it... as soon as I log out of Windows...

Many thanks!

---

### Post by cybrsaylr on 2008-09-09
A minute sounds about right.
I have a dual boot with Hardy and Vista and Hardy takes about 80 seconds to boot up on a dual core AMD Athlon 2.0MHz w 2GB ram Toshiba laptop.

---

### Post by DancingMan on 2008-09-09
> **cybrsaylr said:**
>  AMD Athlon 2.0MHz w 2GB ram Toshiba laptop.

<funny> That's some serious underclocking you've got going on there.  I'm surprised you get an 80 second boot. </funny>

One minute boot on a P4 would seem fairly normal.  My AMD Athlon 3.0GHz boots in about 25 seconds (Gutsy).

---

### Post by Neo_The_User on 2008-09-09
I go to kernel.org, download the latest kernel stable source, turn almost everything off except for things I use and compile and install it. It boots crazy fast.

---

### Post by cybrsaylr on 2008-09-09
> **DancingMan said:**
> <funny> That's some serious underclocking you've got going on there.  I'm surprised you get an 80 second boot. </funny>

One minute boot on a P4 would seem fairly normal.  My AMD Athlon 3.0GHz boots in about 25 seconds (Gutsy).

lol
It's a lot quicker than my 11 year old P2 400mhz desktop PC that takes a good couple minutes to boot Hardy up... :)

Any suggestions to speed up the boot?

---

### Post by Vivaldi Gloria on 2008-09-09
> **tralogik said:**
> Ubuntu takes about one minute to boot, 

Yes it's normal. At least ubuntu is responsive in 3 secs when you login. XP takes ages, especially if you run a firewall and antivirus in XP (which you do not need in ubuntu desktop btw).

> and much of that time is when I see that black screen with white indications (with "not automatically fixing this" on the bottom and many "starting...").

Is this normal? 

Don't you see the boot graphic? Did you disable it?

---

### Post by Faolan84 on 2008-09-09
Dude with the P2 400 MHz, you might want to try Xubuntu and make sure you do't have any extra services running -- or just do a clean install with Xubuntu if you're not sure, just make sure to back up if you do that.

Another tip would be if you're a more advanced user and aren't intimated by the CLI or following manuals is Arch Linux. I recommend to following configuration:
- Image veiwer: GQView, Mirage, or Ristretto
- Audio player: Audacious
- Video player: Totem or gXine
- Office Suite: Abiword (word processor), Gnumeric (spredsheet)
- Browser: Firefox 3 (naturally)
- Chat: Pidgin
- Email: Thunderbird
- Torrent client: Transmission
- Editor: Medit or (if you feel like a pro) vi
- Desktop Search: Tracker

---

### Post by Faolan84 on 2008-09-09
Oh, and using the SLiM instead of GDM for logging in would also speed things up but it doesn't support remote login so if you need that feature then stick with GDM. Otherwise it's divine on a slower machine.

---

### Post by tralogik on 2008-09-12
I found the problem!

I "disabled" Vfat. The instructions are on that website: [http://www.detector-pro.com/2008/09/how-to-fix-there-are-differences.html](http://www.detector-pro.com/2008/09/how-to-fix-there-are-differences.html)

Now, I don't have that "there are differences between boot sector and its backup" screen at startup, and Ubuntu boots much faster!

Thanks for your help!

JS

---

### Post by Sycron on 2008-09-12
Can you estimate the boot time ?

---

### Post by tralogik on 2008-09-12
I would say about 30 seconds, instead of 1 minute.

---

### Post by Sycron on 2008-09-12
You might want to try this.. :P [http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html](http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html)

---

### Post by tralogik on 2008-09-12
I will take a look at it, thanks!

JS

---

