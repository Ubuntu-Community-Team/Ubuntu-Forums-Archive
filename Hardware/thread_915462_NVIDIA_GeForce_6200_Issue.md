---
title: "NVIDIA GeForce 6200 Issue"
date: 2008-09-09
forum: Hardware
---

### Post by Mapasano on 2008-09-09
I'm a newbie to Linux and have a Dell Poweredge 1600 server I'm running as a desktop machine with Ubuntu (Hardy) loaded.  The machine has embedded video with not much in the way of resolution.  I purchased a NVIDIA GeForce 6200 PCI to get better performance and resolution.  When I put the card in and boot, I get two beeps after a few minutes and no video from either video port (the new card or the embedded port).  

Anyone know how to get it recognized?

---

### Post by DirtDawg on 2008-09-10
I installed exactly the same card just a couple months ago and it worked fine. I simply installed the card, then booted up and it worked. I can't remember if I was prompted to install new drivers or not, but I remember the process was fairly simple, so know that the card *does* work.

It's possible you need to disable your onboard card. I think this is done (cautiously) through BIOS. I've never had to do this, so unfortunately I can't tell you how it's done.

---

### Post by DirtDawg on 2008-09-10
I should say, you can enter BIOS on most computers by hitting F12 (sometimes ESC or some other key) when you see the manufactures' logo (the "Dell" screen in your case) after you start the computer.

Once in BIOS, there might be an option something along the lines of "primary video controller = onboard" that you'll want to change to PCI. Now, your computer will probably have a similar option, but not exactly the same. And I must warn you to **please be careful when tinkering with BIOS**. If you change the wrong option because you're not 100% sure of what you're setting, **there is a chance you will render your computer unusable.**

Take your time and make sure you get it right.

If there is no obvious option for changing video card input, your motherboard is probably supposed to disable the onboard card automatically when you install a PCI card (as mine does). If this is the case, then something else is wrong.

---

