---
title: "using ipod as external bootable ubuntu main drive and still music player?"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by alienclone on 2009-08-31
my searches have lead me nowhere, i know it is possible to install Ubuntu onto an ipod and use it as a bootable drive but can it also be done so that the ipod still functions as a music player when not connected to the pc?

my goal is to plug the ipod into my pc, tell pc to boot from usb, then have everything i do on the pc be read and written to/from the ipod as if it is my main drive, then shutdown and remove ipod and use it as a normal ipod listening to music on the way to my friends house, then plug the ipod into their pc and tell it to boot from usb and have my desktop at my fingertips.

is this possible or am i just dreaming?

---

### Post by sideaway on 2009-08-31
The firmware is encrypted (assuming you iPod is classic or later?). You can't really touch it. Just install it as you would a normal USB disk. It won't be fast though...

EDIT: I read your post as opposed to just replying to the title lol.

There's two fundamental flaws. Grub. He will need grub installed. Or atleast you'll need to configure his boot priorities and configure the PC to boot from your ipod. The other is hardware configuration, this is a little harder to overcome, unles his PC uses the same chipsets, you're gonna run into issues. What you *could* do is just mount your iPod as your home drive, that way you have all your files, but none of the complications of an operating system.

---

### Post by alienclone on 2009-08-31
> **sideaway said:**
> The firmware is encrypted. You can't really touch it. Just install it as you would a normal USB disk. It won't be fast though...

EDIT: I read your post as opposed to just replying to the title lol.

There's two fundamental flaws. Grub. He will need grub installed. Or atleast you'll need to configure his boot priorities and configure the PC to boot from your ipod. The other is hardware configuration, this is a little harder to overcome, unles his PC uses the same chipsets, you're gonna run into issues. What you *could* do is just mount your iPod as your home drive, that way you have all your files, but none of the complications of an operating system.

yeah, it is my /home right now, i was just dreaming of making it more, but i have a lot of silly dreams so im used to disapointment.

---

