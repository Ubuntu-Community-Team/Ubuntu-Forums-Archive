---
title: "Completely UNABLE to activate any drivers"
date: 2009-12-13
forum: Hardware
---

### Post by rtyb on 2009-12-13
Ok, so this is my (anoying) problem

It's imposible to activate any Hardware Drivers (proprietary)
I just installed ubuntu, so i don't see why this would happen.
I haved installed ubuntu and activated drivers before.
But this time, just as soon as i click the ''activate'' button, it hangs in there, for ever, and for ever, for ever...

The small windows saying ''downloading and installing driver...'' appears, but just that, it doesn't download, neither install, anything at all, it just hangs in there, for eternity...

When i first noticed this was when trying to install "Broadcom STA Wireless''
(as i have a Broadcom Wireless card, i don't really know which model though..)

So then i thought ''hey, maybe it's the driver/repositories, let try by installing the nvidia graphics driver'' (i have a GeForce Go 6150)

This time, the load bar did move.... till the middle (half), then again, stopped, hung in there, for ever...

So please....

how the hell do i get this to work and have my graphics and wireless cards to work... please:(

PS: I'm using Ubuntu 9.10

---

### Post by madverb on 2009-12-14
Just make sure the corresponding linux-headers are installed that match your kernel.
I had a similar problem and it was because the headers weren't installed when the kernel was updated.

---

### Post by rtyb on 2009-12-14
Uhm...i don't know what you're talking about

I'M NEW to linux...so you know ;)



:)

---

### Post by rtyb on 2009-12-14
Please:(

Help!

I need WiFi, i need my GPU, please.....

---

### Post by fooman on 2009-12-14
you need a working internet connection in order to download/install the drivers.

is the ethernet connected and working?

---

### Post by Chesamo on 2009-12-14
1. as fooman mentioned, make sure you're connected to the Internet (wired connection).
2. System > Administration > Software Update. Run that, and you should get the latest kernel. Then, run```
sudo apt-get install build-essential
```to get the headers. You should be able to enable the restricted drivers now.

---

### Post by rtyb on 2009-12-15
@Chesamo: THANKS!!!!!!!!

I did as you sayed...and it worked =D!!!!

Thanks....

now i have the nvidia and broadcom drivers.... thanks!

Although i wonder why this happened this time... (yes, i had Internet access, don't worry)

---

### Post by KdotJ on 2010-04-19
> **Chesamo said:**
> 1. as fooman mentioned, make sure you're connected to the Internet (wired connection).
2. System > Administration > Software Update. Run that, and you should get the latest kernel. Then, run```
sudo apt-get install build-essential
```to get the headers. You should be able to enable the restricted drivers now.

Thank you so much for this!! +1
And thanks to the good old "search" feature on this forum!!

---

