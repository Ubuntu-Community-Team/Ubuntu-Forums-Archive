---
title: "How can I install Ubuntu on laptop with no cd drive?"
date: 2008-10-29
forum: General Help
---

### Post by randchamb on 2008-10-29
Hi all
This is my first post and I hope I can explain my problem correctly. I want to install Ubuntu on an old gateway laptop that has no OS installed on the hd and the CD Rom is not working. I have tried to boot from a portable usb Cd drive but the option in bios is not available. if I were to remove the existing hard drive from the laptop and connect it to another machine Is there a way to put an image of Ubuntu on the hd first then install it somehow from that? I am open to any suggestions.

Thanks in advance 
Randy

---

### Post by Coreigh on 2008-10-29
Your best bet is to borrow a USB cd-rom drive, but given you could not boot from the thumb drive that may not work either.

I have, with older versions, put the hard drive in to a working computer, installed linux and then put the hard drive back in the not-so-working computer. It *should* work but you may have trouble with hardware detection and updating (getting networking to work).

It kind of comes down to how bad do you need this to work? It will probably turn out to be a lot of work. So unless you really want to do it just to see if you can. It may not be worth the hassle.

---

### Post by bodhi.zazen on 2008-10-29
See [uhelp]community/Installation[/uhelp]

    There is a section on no CD ...

---

### Post by Helge on 2008-10-29
You can install on another computer, and then move the hard drive. You can clone the hard drive in a working computer to an USB-attached drive, and then move that drive to the CD-less computer. Unix command dd can be used for the cloning.

---

