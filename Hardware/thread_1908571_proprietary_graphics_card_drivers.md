---
title: "proprietary graphics card drivers"
date: 2012-01-13
forum: Hardware
---

### Post by yar0n on 2012-01-13
hi, i have problem with ubuntu :S
i tried to install my graphic card with ubuntu drivers update,
but noting happend! i dont know why is doesn't recognize my graphic card at all ! 
i am using VMWARE 
after i imaged the ubuntu file i go to the driver updater 
and that what he show me....
[IMG]http://img11.imageshack.us/img11/9285/captureatl.png[/IMG]
my driver card is intel 965 express chipset family
please help !!! :confused:

---

### Post by MoreOrLess on 2012-01-13
vmware doesn't do vga passthrough the last time i checked, so you have to use the vmware video driver regardless of what GPU you have. intel doesn't have proprietary drivers anyway...

---

### Post by yar0n on 2012-01-13
> **MoreOrLess said:**
> vmware doesn't do vga passthrough the last time i checked, so you have to use the vmware video driver regardless of what GPU you have. intel doesn't have proprietary drivers anyway...
and why is that ? why intel doesnt have  proprietary drivers?
and why when i go to  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) i cant see flash update?

---

### Post by yar0n on 2012-01-14
please help! up!

---

### Post by madvinegar on 2012-01-14
Have you tried downloading the driver from here?

[http://www.intel.com/p/en_US/embedded/hwsw/software/iegd#download](http://www.intel.com/p/en_US/embedded/hwsw/software/iegd#download)

---

### Post by MoreOrLess on 2012-01-14
> **madvinegar said:**
> Have you tried downloading the driver from here?

[http://www.intel.com/p/en_US/embedded/hwsw/software/iegd#download](http://www.intel.com/p/en_US/embedded/hwsw/software/iegd#download)
It's not going to work in a virtual machine.. 

You may be able to get better graphics with spice (search vmware spice).
> why intel doesnt have proprietary drivers?
You say that like it's a bad thing for the driver to be open-source..

---

### Post by mörgæs on 2012-01-14
> **MoreOrLess said:**
> 
You say that like it's a bad thing for the driver to be open-source.

Yes, why are you (=original poster) searching for proprietary drivers anyway?

---

### Post by Mark Phelps on 2012-01-16
From what I can tell ...

> i dont know why is doesn't recognize my graphic card at all ! 

this is yet another person who doesn't understand that graphics drivers are installed by default -- and thinks they have to install them manually.

---

### Post by yar0n on 2012-01-16
> **Mark Phelps said:**
> From what I can tell ...



this is yet another person who doesn't understand that graphics drivers are installed by default -- and thinks they have to install them manually.
its not recognize my graphic card with or without vmware...

---

### Post by Mark Phelps on 2012-01-16
> **yar0n said:**
> its not recognize my graphic card with or without vmware...


OK, then let me back up a bit ...

The screenshot you provided CLEARLY shows an Ubuntu desktop. It also shows that no Restricted Drivers are available.

This is your desktop, right?  Not a screenshot you grabbed from somewhere else?

If this is your desktop and, as you say, it did NOT recognize your graphics card, there would be NO graphics drivers installed, and instead of that Ubuntu client area in the virtual machine window, it would just be black.

So ... the presence of the Ubuntu desktop proves it DID install drivers for your graphics card.

OK?

---

### Post by MoreOrLess on 2012-01-16
Unsubscribing from this one.. ;)

---

### Post by mörgæs on 2012-01-16
Mark Phelps, though it is correct what you write a less aggressive tone would be nice.

---

