---
title: "Laptop hardware issue"
date: 2009-04-28
forum: Hardware
---

### Post by Jameshardy88 on 2009-04-28
Hi, first up i would like to say that this problem is a little off topic as i believe that it is not related to ubuntu or linux in any way, however i am having computer issues and felt this was the best place to ask.

I am currently dual booting ubuntu Jaunty and windows xp which is how i have determined that this is not an OS problem. Basically at least once every 24 hours approx sometimes under 60 minutes my computer will have a complete system freeze (caps and num lock etc do nothing), requiring me to re-boot. Does anyone know what could be causing this. I suspect it could be a RAM problem as the issue began at approximately the same time that i had my ram replaced due to the old 1 being fried. What actions will i need to take to rectify this problem?

---

### Post by Danial on 2009-04-28
> **Jameshardy88 said:**
> I suspect it could be a RAM problem as the issue began at approximately the same time that i had my ram replaced due to the old 1 being fried. What actions will i need to take to rectify this problem?

James, 
Just an idea if you want to give it a shot. Try to run Memtest on your system. Best option would be to download and copy to CD/floppy and boot from there.  Run the test and this may take a while but if there is a problem with memory, you sure will find it.

You can find some info here: "http://www.memtest.org/" and download link is here: [http://www.memtest86.com/]("http://www.memtest86.com/").

I hope this may help to locate and isolate the problem.

Danial

---

### Post by coffeecat on 2009-04-28
Complete system freezes in both Linux and Ubuntu are certainly a hardware issue, and I would have put bad RAM near the top of the list even if you hadn't said you had recently replaced it. With the trouble starting when you changed the RAM, it becomes an almost certainty.

I agree with trying a memtest, but you should be able to start memtest from the grub menu when you first boot up. No need to download anything.

Sometimes you need to run memtest for several hours to detect a fault. Even a few pass cycles don't mean there isn't a problem.

---

### Post by Jameshardy88 on 2009-04-28
If it turns out that the ram is the problem will i need to replace it? if so how do i know which ram will be compatible?

---

### Post by coffeecat on 2009-04-28
> **Jameshardy88 said:**
> if so how do i know which ram will be compatible?

I've used Crucial several times to replace/upgrade RAM. If you go to this page:

[http://www.crucial.com/uk/?click=true](http://www.crucial.com/uk/?click=true)

...you'll see that you can put your Manufacturer, Produce Line and Model in and they advise you which modules are compatible. All fairly easy. Crucial is a reliable make, and they do a good postal service.

Another good make is Kingston with a similar system here:

[http://www.kingston.com/UKROOT/](http://www.kingston.com/UKROOT/)

Just don't go to PCWorld or Maplins. You'll pay much more.

---

