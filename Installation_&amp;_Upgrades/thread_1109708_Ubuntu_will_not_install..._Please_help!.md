---
title: "Ubuntu will not install... Please help!"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by I eat coffee! on 2009-03-29
I have been trying for the last 4 days to install Ubuntu and everything I try wont work. It usually boots and loads gnome then it allows me to start the install but, at some point during the install(always seems to be a different spot) it either hangs or crashes. If Ubuntu crashes it reboots and if it hangs the CD drive stops blinking. 

I was wondering if anyone had ever used a separate computer to install Linux using a external hard drive. The external hard drive enclosure is used to interface to another computer and that computer installs and sets up the partitions on that hard drive. Next, that hard drive is reinserted into the computer and you can simply boot from the hard drive. I am able to boot fine, I just cant install and it seems to be random. 

I am really scratching my head here and all the hair has long since been removed.

HELP :confused:

---

### Post by sacreno on 2009-03-29
> **I eat coffee! said:**
> I have been trying for the last 4 days to install Ubuntu and everything I try wont work. It usually boots and loads gnome then it allows me to start the install but, at some point during the install(always seems to be a different spot) it either hangs or crashes. If Ubuntu crashes it reboots and if it hangs the CD drive stops blinking. 

I was wondering if anyone had ever used a separate computer to install Linux using a external hard drive. The external hard drive enclosure is used to interface to another computer and that computer installs and sets up the partitions on that hard drive. Next, that hard drive is reinserted into the computer and you can simply boot from the hard drive. I am able to boot fine, I just cant install and it seems to be random. 

I am really scratching my head here and all the hair has long since been removed.

HELP :confused:

:)   I feel your pain...

I have dl'd a copy of 32bit and 64bit from 11 mirrors, purchased a new dvd/cd r drive...and have tried to install it/burn it with 4 programs and 3 diferent comps....i get the same thing

it hangs up..the boot cd fails....the cd is corupt....help us Guru's

Please before i go postal on my neighbor...;0

---

### Post by GlebeCS on 2009-03-29
Most likely cause is bad RAM, try substitution if you can or run a memory test (Prime95 if possible, this will show up ANY memory issues)

---

### Post by I eat coffee! on 2009-03-29
Ram seems fine, I ran a ram check.

---

### Post by heiNey on 2009-03-29
did you try running the 'check cd for defects' option when you first boot up with the livecd?

---

### Post by I eat coffee! on 2009-03-29
I have tried it all.. can I install Ubuntu on the hard drive from a different computer using a external hard drive enclosure? I'm going to try it, I will let you folks know how it goes.

---

### Post by spcwingo on 2009-03-29
I had one machine that Ubuntu refused to install to using the live CD or alternate CD.  Here is what I did to get around it.

First, make sure you're connected to the internet via a fast connection.  Then download the mini CD, here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Burn to CD as an image (slowly) and boot with the new CD.  Follow the prompts to install the base system.  (Note: that this will only install the text based system)  When prompted to reboot, do so.  Upon reboot, login via the terminal (when typing your password you won't see any "*s", this is normal) and type these commands:

```
sudo apt-get install ubuntu-desktop
```

This will prompt for your password.  Again, you won't see any feedback from the terminal.  When that command gets done, run this one:

```
sudo apt-get clean && sudo reboot
```

This will clean your apt cache and reboot into your Ubuntu desktop (or laptop) system.  Enjoy!

---

### Post by I eat coffee! on 2009-03-29
The computer does not have a working internet connection. Could I install minimal then install from a flash drive or something? Will minimal provide the drivers for a flash drive? If it does what commands should I use to install from flash drive?

---

### Post by sailthesea on 2009-03-29
I don't see why your idea shouldn't work Get HD installed on another machine then ship it over to the offending article If nothing else you may get a clearer picture of where its letting you down (some weird problem there I think)  You'll probably have to do something with the boot script in the second machine 
 Good Luck!

---

### Post by I eat coffee! on 2009-03-30
Is it possible this is all due to a dirty dvd drive? The drive i am using is quite old...

---

### Post by spcwingo on 2009-03-30
> **I eat coffee! said:**
> Is it possible this is all due to a dirty dvd drive? The drive i am using is quite old...

Could be.  The last machine I installed Ubuntu on the CD rom was on it's last legs, so I did the install as I described above to at least have a working system.  If I were you, I would give that drive a good cleaning, then try again....if that doesn't work, then I would do what sailthesea suggested.

---

### Post by Cybie257 on 2009-03-30
> **I eat coffee! said:**
> Is it possible this is all due to a dirty dvd drive? The drive i am using is quite old...

Sometimes older drives have a problem reading CDs/DVDs that were written at high speeds. Maybe you can try burning the CD at the slowest speed and try that. Also, some brands of CDs/DVDs can be a problem for some older drives as well. 

For now, my suggestion is to try burning at a slower speed and/or trying a different brand of medium.

-Cybie

---

