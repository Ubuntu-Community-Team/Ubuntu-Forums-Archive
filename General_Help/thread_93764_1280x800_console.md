---
title: "1280x800 console?"
date: 2005-11-22
forum: General Help
---

### Post by shidai.liu on 2005-11-22
Anybody know how to get a 1280x800 console?

Thank you.

---

### Post by hw-tph on 2005-11-23
Depends on what kind of graphics chip you have. With ATI Radeon-based graphics you can - according to what I have heard - use the radeonfb framebuffer driver to get 1280x800. However, if you use this driver you cannot use ATI's own binary drivers (if that is an issue to you).

If you use nvidia graphics you're pretty much shot. With the vesa framebuffer driver, or the new vesa-tng it doesn't work. rivafb (which would make the use of nvidia's binary drivers impossible) doesn't support 1280x800 and it seems the nvidia-fb driver doesn't either. I settle for using 1024x768 with the ordinary vesa or vesa-tng drivers on my laptop, but then again I don't use the console much in Ubuntu.


H&#229;kan

---

### Post by shidai.liu on 2005-11-23
What about other graphics card? I'm using Intel 850GME in my Dell 700m. Thanks for your reply.

---

### Post by seldenthuis on 2005-11-23
1280x800 is impossible if you want to keep the nice graphical bootsplash theme. That's because Usplash only works with vga16fb or vesafb. You can get 1280x1024 though. Just put 'vga=0x31B' in the kernel options in /boot/grub/menu.lst.

Other resolutions and color depths are also possible.
/usr/share/doc/linux-doc-2.6.12/Documentation/fb/vesafb.txt.gz gives you this table:
```

    | 640x480  800x600  1024x768 1280x1024
----+-------------------------------------
256 |  0x301    0x303    0x305    0x307
32k |  0x310    0x313    0x316    0x319
64k |  0x311    0x314    0x317    0x31A
16M |  0x312    0x315    0x318    0x31B

```

---

### Post by shidai.liu on 2005-11-23
Thanks.

---

