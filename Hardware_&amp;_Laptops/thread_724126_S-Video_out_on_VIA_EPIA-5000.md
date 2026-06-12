---
title: "S-Video out on VIA EPIA-5000"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by Lolibuntu on 2008-03-14
Hi all,

I have a VIA EPIA-5000 board which has an S-Video output that I'm trying to use with a server-installation of Ubuntu 6.06. The S-Video output is connected with a german 50Hz PAL plasma TV.

After power on the BIOS screen and grub are displayed fine. But as soon as the kernel image has been loaded and linux is booting it seems that the S-Video output switches to 60Hz NTSC (?). The display is running through from the top to the bottom of the screen.

Because so far there is no X involved I have no clue where I can handle this. Is this a framebuffer issue? I already tried to pass the following kernel parameter:

```
-video=tridentfb:800x640@50
```

With no success. Nothing changes...

The TV-Out option in BIOS is set to PAL. Graphic chipset is trident. The normal VGA-Output works fine.

Lolibuntu

---

