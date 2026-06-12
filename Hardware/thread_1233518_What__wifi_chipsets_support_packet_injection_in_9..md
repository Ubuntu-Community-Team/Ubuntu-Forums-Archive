---
title: "What  wifi chipsets support packet injection in 9.04?"
date: 2009-08-06
forum: Hardware
---

### Post by DejitaruJin on 2009-08-06
Okay, so, with a great deal of research I've confirmed that the injection patch for my IPW2200 wireless card just doesn't do anything, as of 9.04 (or maybe 8.10). So, apparently, I'm in the market for a new wireless card - ideally, PCMCIA or USB, with a removable/upgradeable antenna.

Most importantly, I need a card with a chipset that can be patched to allow packet injection and monitoring, and the patch has to work *with 9.04*. So, does anyone know of any? Specifically looking for chipsets, not whole card model numbers ;)

---

### Post by lswb on 2009-08-06
I am running jaunty with a 2.6.30 kernel because my laptop has intel graphics. I was pleasantly surprised to find that the ipw2200 driver shipped with this kernel has working packet injection support compiled in. I'm currently using the 2.6.30-02063003-generic kernel available from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 

You will have to download the appropriate kernel and headers packages (image packge, headers...all, and headers to match your image pkg) for your architecture and install with dpkg. The ipw2200 driver does not yet support all of the features that some other cards so it can't perform all the pen tests some other cards can. There are details about that on the aircrack web site and the backtrack website.

---

### Post by jaxxstorm on 2009-08-06
Nearly every card I've used has supported packet injection as of Jaunty.

you can test packet injection using this simple command (after installing aircrack)

```
sudo aireplay-ng -9 mon0
```

if you get a response along the lines of

```

 16:20:26  Trying broadcast probe requests...
16:20:26  Injection is working!
16:20:28  Found 3 APs

```

Give it a try before you give up and buy another card.

---

### Post by DejitaruJin on 2009-08-06
> **lswb said:**
> I am running jaunty with a 2.6.30 kernel because my laptop has intel graphics. I was pleasantly surprised to find that the ipw2200 driver shipped with this kernel has working packet injection support compiled in. I'm currently using the 2.6.30-02063003-generic kernel available from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Wha?! I never knew you could manually update the kernel. I feel like a n00b. A n00b trying to be 1337 h4x0rz :P

If you can make it work, than so can I, with the right research. I'll get on that immediately. Thanks for the info.

Of course, I'd still like info on other chipsets that work, if only because I can't attach a large antenna to an internal card ;)

As for the IPW2200 its self, I have absolutely, completely confirmed that it won't work. Multiple methods, multiple patches, no results. The patched drivers compile perfectly fine, but it's as though the modifications no longer have an effect. No responses to any of the potential ways to test using aireplay-ng. There's a big topic elsewhere here with dozens of reports of the same thing, with not one success in 9.04. An updated kernel may be the fix we all need...

---

### Post by DejitaruJin on 2009-08-07
Well, shoot. A night of compiling (and re-compiling) kernel 2.6.30 got me nowhere. In fact, now the IPW2200 inexplicably resets its entire configuration when aireplay-ng is run, instead of just becoming temporarily unassociated (which is also bad - the IPW2200 must remain associated at all times when testing injection). Maybe it has something to do with ieee80211 being replaced by lib80211. The rtap0 interface is still there (though still with "no wireless extensions"), so at least it's got part of the patches right. Google doesn't seem to have any specific information relating to the IPW2200 in kernel 2.6.30.

So, still in the market for a new card. Hopefully I'll see something cheap at Best Buy later.

---

### Post by skyline2412 on 2009-08-11
Well I am in the same situation but i am not going to buy a new card...sooo i will have to search better in google ..

---

### Post by mpw on 2009-08-17
Does anybody know which kernel supported injection with the ipw2200?
Is Ubuntu 8.10 old enough? Because I'm going to install a small image with an older ubuntu as this is definitivly not a daily function.

---

### Post by skyline2412 on 2009-08-25
Hello mpw,

well i finally got it
Intel PRO/Wireless 2915ABG -> ipw2200
ubuntu 9.04 + kernel 2.6.28-15-generic

it works perfectly.
;)

---

