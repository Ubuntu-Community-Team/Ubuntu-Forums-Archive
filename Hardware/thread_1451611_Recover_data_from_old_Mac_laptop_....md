---
title: "Recover data from old Mac laptop ..."
date: 2010-04-10
forum: Hardware
---

### Post by pmooney78 on 2010-04-10
I have an old Mac G3-series PowerBook that won't boot, and hasn't for years. I've given up on solving the hardware problems and just want to recover the data off of the hard drive. I'm willing to destroy the computer to get the hard drive out, if that turns out to be necessary. 

Theoretically, if I could plug the hard drive into a desktop computer, I could recover it easily enough with Linux tools -- I've used some of the HFS utilities in the past, and could probably extract the data from an image using BasiliskII once I've made an image in the first place.

My problem is that I'm not really all that familiar with working on hardware, although I've installed memory and internal hard drives in PCs before. Moreover, I doubt that I could easily plug the PowerBook's hard drive into my current laptop.

I'd be willing to buy a cheap desktop from, say, a thrift store, if it's cheaper than taking it to a data recovery service (likely). The question, though, is will my old PowerBook's hard drive plug into a desktop PC? Technical specs on the Internet (say, at [http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_250.html](http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_250.html)) say that the standard internal hard drive for this model is an EIDE drive -- does that mean that I can just drop it into any IDE port on the inside of a grey-box desktop?

Any help/suggestions are appreciated.

---

### Post by ajgreeny on 2010-04-10
I think the hard drive will be exactly the same as any other hard drive; although macs of that age were hardware specific, I believe they used the same hard drives as other machines.  If so I'm sure it must be possible to remove it quite easily and pop it into a USB attached cradle, and simply mount it in ubuntu and get the files off.

Apologies if I'm totally wrong about this, I admit I've never really used a mac at all.

---

### Post by sebastianabate on 2010-04-10
You cant connect a notebook disk to a desktop PC without an adapter (the connectors are different).
Your best option is to buy an IDE/SATA to USB adapter, its cheaper than any other option, and you dont need to open your actual pc to connect the disk.

[Check this link]("http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=ide+to+usb+adapter&oe=utf-8&um=1&ie=UTF-8&cid=9485045192101622072&ei=YQ3BS93xBIWNuAe35tDYBg&sa=X&oi=product_catalog_result&ct=image&resnum=5&ved=0CBsQ8gIwBA#")

---

### Post by pmooney78 on 2010-04-14
A much neater idea than what I was thinking. Thank you!

---

### Post by pmooney78 on 2010-05-02
Managed to borrow an appropriate IDE drive bay, plug it into an open USB port on my hub, and extract the data from the hard drive using 

```

dd if=/dev/sde of=~/macHD.dd

```

Note that the whole drive is being copied, not just a single partition.

The resulting image file can then be mounted under BasiliskII like any other drive image, and any file conversion (etc.) can be done using (68k) Mac programs from within the emulated environment. Converted files can then be copied to the Linux filesystem via the "Unix" virtual drive on the emulated Mac desktop.

Alternately, the resulting image file can be burned to a DVD (in my case, it was small enough, since this is a really old hard drive) as an image file, then mounted under BasiliskII by simply putting it into the DVD-ROM drive.

---

### Post by thankershow on 2013-01-11
> **pmooney78 said:**
> I have an old Mac G3-series PowerBook that won't boot, and hasn't for years. I've given up on solving the hardware problems and just want to recover the data off of the hard drive. I'm willing to destroy the computer to get the hard drive out, if that turns out to be necessary. 

Theoretically, if I could plug the hard drive into a desktop computer, I could recover it easily enough with Linux tools -- I've used some of the HFS utilities in the past, and could probably extract the data from an image using BasiliskII once I've made an image in the first place.

My problem is that I'm not really all that familiar with working on hardware, although I've installed memory and internal hard drives in PCs before. Moreover, I doubt that I could easily plug the PowerBook's hard drive into my current laptop.

I'd be willing to buy a cheap desktop from, say, a thrift store, if it's cheaper than taking it to a [mac data recovery]("http://www.transfer-iphone-recovery.com/data-recovery-for-mac.html") service (likely). The question, though, is will my old PowerBook's hard drive plug into a desktop PC? Technical specs on the Internet (say, at [http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_250.html](http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_250.html)) say that the standard internal hard drive for this model is an EIDE drive -- does that mean that I can just drop it into any IDE port on the inside of a grey-box desktop?

Any help/suggestions are appreciated.
If you want your Mac to be back in your native language go to System Preferences and the go to the international section (the flag) and then drag English to the top of the list.

As for your data, you hard drive could have simply died, which makes it very hard to actually get anything off it because it doesn't physically work anymore.

---

### Post by pmooney78 on 2013-01-11
Recovery was successful, thanks.

---

### Post by overdrank on 2013-01-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

