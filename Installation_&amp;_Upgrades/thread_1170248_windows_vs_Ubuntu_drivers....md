---
title: "windows vs Ubuntu drivers..."
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-26
my motherboard is ASUS P4BP-MX 2.0..
they provide drivers for both windows and linux..
windows drivers often comes with .exe and linux with (.rpm or .tar)..
my doubt is 

does intalling drivers in Ubuntu 8.10(.rpm packagefor VGA) affect my hardware performance when i try to install Windows device drivers(.exe) in future after installing Windows XP SP2?

now i dont hav win XP due to installation prob..only Ubuntu 8.10

---

### Post by rob2uk on 2009-05-26
It'll have no effect on future performance under a different OS...

But .rpm files are for Red Hat/Fedora Core linux, not Ubuntu

It *is* possible to get them to work, but you'd be better off using the .tar files

---

### Post by vpnm_87 on 2009-05-26
is it advisable to use alien package to get .rpm work?
coz am kind of afraid to do compilation myself wit .tar especially for VGA drivers:-)

---

### Post by rob2uk on 2009-05-26
from the Alien site:

> Alien should not be used to replace important system packages

---

### Post by vpnm_87 on 2009-05-26
oops:-)
may be its time for me to learn lot by compiling driver files:-)
ll go with the .tar package then:-)

---

### Post by coffeecat on 2009-05-26
Why are you wanting to install the motherboard drivers that presumably came on a CD with the motherboard? Ubuntu comes complete with drivers for a vast range of hardware already compiled into the kernel. If everything on your motherboard (ethernet, sound, usb, etc) is working, then you don't have to install anything.

It's good to hear that Asus is providing Linux drivers, but for most up-to-date mainstream distros they are not necessary for the average end-user.

---

### Post by Mark Phelps on 2009-05-26
> **vpnm_87 said:**
> does intalling drivers in Ubuntu 8.10(.rpm packagefor VGA) affect my hardware performance when i try to install Windows device drivers(.exe) in future after installing Windows XP SP2?

Basically -- no.  Each OS uses its own drivers and neither one affects the other.  If you install using Wubi inside MS Windows, you're using the MS Windows drivers, not Linux drivers.  If you install Wine inside Ubuntu, you're using the Linux drivers, not MS Windows drivers.

---

### Post by albinootje on 2009-05-26
> **Mark Phelps said:**
> If you install using Wubi inside MS Windows, you're using the MS Windows drivers, not Linux drivers. 

If you have Wubi inside MS-Windows, and you boot Wubi, then you're using plain Ubuntu (except that it read and writes to the MS-Windows partition), and not using any MS-Windows drivers.

---

### Post by artsci2 on 2009-05-26
> **Mark Phelps said:**
> Basically -- no.  Each OS uses its own drivers and neither one affects the other.  If you install using Wubi inside MS Windows, you're using the MS Windows drivers, not Linux drivers.  If you install Wine inside Ubuntu, you're using the Linux drivers, not MS Windows drivers.

I have wondered why the need to make new drivers instead of just programming for the use of the windows drivers....

---

### Post by albinootje on 2009-05-26
> **artsci2 said:**
> I have wondered why the need to make new drivers instead of just programming for the use of the windows drivers....

That would, imho, be the same as asking : "Why write an open source OS (like Linux) when a closed source OS already exists?"

There's the Ndiswrapper project, with which you can use (closed-source) MS-Windows drivers for wireless cards, inside Linux. This can be handy because sometimes there are no native Linux drivers for certain wireless cards (Because the hardware vendor doesn't provide enough information e.g. or because the card is so new that Linux developers have no physical access to it to test it etc.)

Also, if you would use MS-Windows drivers exclusively for Linux you would become dependent on the supplier of those drivers, and therefore not being able to bug fix the driver yourself.

Let's make an effort to have more hardware vendors support Linux, 
so that we can have more and better native Linux drivers in the future.

---

### Post by artsci2 on 2009-05-26
> **albinootje said:**
> That would, imho, be the same as asking : "Why write an open source OS (like Linux) when a closed source OS already exists?"
...

Ah I guess I just didnt think of the drivers as being a closed or open source type of entity....duh!

---

### Post by 73ckn797 on 2009-05-26
> **albinootje said:**
> 
There's the Ndiswrapper project, with which you can use (closed-source) MS-Windows drivers for wireless cards, inside Linux. This can be handy because sometimes there are no native Linux drivers for certain wireless cards (Because the hardware vendor doesn't provide enough information e.g. or because the card is so new that Linux developers have no physical access to it to test it etc.)

Good point to mention.

To the OP:
If you are not ready to tackle command line install of a Windows wireless driver there is a GUI tool in Synaptic called "ndisgtk" that will do the job. You would need to copy the driver files from the provided CD to a folder on your computer then run ndisgtk which can be found under System/Administration and the bottom of the menu. Use the copied driver "inf" file and it ought to work.

---

