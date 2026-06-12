---
title: "Internal Notebook keyboard not recognized"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by Das Auge on 2008-03-21
I installed Ubuntu 7.10 on a friends notebook: Asus L3000D

All seems to work fine, with one ecception: The internal notebook keyboard ist not recognized. In BIOS the keyboard ist working, so it is not broken. But as soon as Ubuntu starts, the internal keyoard does not work anymore. An external PS/2 keyboard works fine. I had to do the installation with the external one. 

Also with feisty (live) and INSERT 1.3.9b (based on Knoppix) I ran into the same problem. I already tried to start with the boot parameter acpi=off, without bettering. The only effect was that the battery was not found, too. 

I could not find a similar problem on the forum and the wiki about the notebook does not even mention the keyboard. I hope, you can help me.

---

### Post by teaker1s on 2008-03-23
have you tried xev to see if you have keycodes when a key is pressed? if you get codes but no output then it my be a simple mapping issue

---

### Post by Das Auge on 2008-03-24
I tried now. I dont have keycodes from the internal keyboard, but only from the external one and the mouse.

---

### Post by teaker1s on 2008-03-24
just a thought, have you legacy usb turned on in bios?
Also have you tried ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Das Auge on 2008-03-26
> just a thought, have you legacy usb turned on in bios?
Also have you tried
Code:

sudo dpkg-reconfigure xserver-xorg
 Yes, I alreday tried dpkg-reconfigure xserver-xorg. But it didn't change anything. 

And I am afraid I dont have a bios entry like turn legacy usb on. It is a Bios with very few options. Don't know why.

---

