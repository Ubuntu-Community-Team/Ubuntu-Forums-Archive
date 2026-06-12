---
title: "How do I get a third monitor working?"
date: 2014-01-21
forum: Hardware
---

### Post by Maheriano on 2014-01-21
I've got a cheap GeForce 210 video card and it has VGA, DVI and HDMI outputs on it. I can only have 2 outputs running simultaneously, even if I plug in 3, only 2 will work. I looked online and it looks like this card only supports 2 consecutive outputs. That's fine but I tried putting in another PCI video card I had laying around, hooked up the third VGA monitor to it and it still didn't work. I confirmed the VGA monitor does work as I tried it with only this card by removing the GeForce 210 and it worked fine. I do not have onboard video on my motherboard, how can I get this third monitor working alongside the other 2? Should it be as simple as plugging in another video card?

---

### Post by QIII on 2014-01-21
Hello!

Is the other card made by the same OEM?  Is it supported by the same driver?

---

### Post by Maheriano on 2014-01-22
> **QIII said:**
> Hello!

Is the other card made by the same OEM?  Is it supported by the same driver?

No, one is the Asus 210 card powered by Nvidia: [http://www.memoryexpress.com/Products/MX33912](http://www.memoryexpress.com/Products/MX33912)
The second is a generic ATI card.

---

### Post by QIII on 2014-01-22
Ah.  Therein lies the difficulty.

The OEMs are not as kind to Linux users as to Windows users.  This sort of arrangement is not likely to work due to conflicting drivers.  With only one or the other proprietary driver installed, one of the cards will not work.

I'm not sure how well this would work if you were to uninstall the Nvidia driver(if you have it installed) and use the default open source driver installed when you installed Ubuntu.  I can't say how well even the two open source drivers would play together.

If it is worth your time, you might try uninstalling the proprietary driver and rebooting to see if both cards will respond, but I have my doubts.  If it does work, then you will likely have to stick with the open source drivers, which, as I am sure you understand, do not support all the features of either card.  For most users, however, the open source drivers are sufficient.

Let us know if just removing the proprietary driver at least gets you use of both cards, but I have my doubts.

Cheers.

---

### Post by jp734 on 2014-01-22
@QIII - Just a thought, before uninstalling anything, can't he try to activate the card and screen by creating a configuration file and use the vesa driver for the ati card?

@Maheriano - When you installed the driver for you NVidia, did it create a xorg.conf file that you can edit and add another card, monitor and screen section for your ati?

I would think that's possible but you might not get the performance you want.

---

### Post by Maheriano on 2014-01-23
I'm not that well experienced with video drivers so my preferred option would be to pick up another cheap Asus 210 card when I get a chance and see if that works better. I'll let everyone know, might take a week or more.

---

### Post by mystyc1 on 2014-01-24
Have you checked your BIOS/EFI?  When booting up, but before any OS begins loading, all three monitors should output the standard pre-boot POST info.  If this does not occur, and your bios is not set to some default speed-booting sequence, then bios does not see it and so hence no OS will.  It is possible that with older/cheaper systems the motherboard itself will not support more than one video card at a time.  Are both cards PCI-express?  

In any case, if bios recognizes all three monitors then it might be possible to do a triple monitor system.  
I am not quite sure about the situation with 2 separate cards, other than that separate OEM drivers don't play well with others, but I do know of hybrid "dual graphics" videocards that have more than one GPU on the same card.  They are more commonly seen in laptops, but desktop versions do exist.  The point is that the techniques used there might help you.  
Look up "[Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")" for more information there.

---

