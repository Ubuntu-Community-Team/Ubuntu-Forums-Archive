---
title: "tty resolution to full HD?"
date: 2011-08-04
forum: Hardware
---

### Post by JoelMay on 2011-08-04
I'm trying to change my tty resolution in Ubuntu.  I have seen the framebuffer trick by setting the VGA boot flag.  My problem is I have a full HD monitor and none of the framebuffer resolutions look good.  I have a nVidia GeForce 9500 GT.

My question is if there's a way to set the tty resolution without using the framebuffer presets?

When I have to use them I don't like to use a 4:3 resolution on my 16:9 monitor; also low resolutions look ugly and don't show much.

---

### Post by Lampi on 2011-08-04
vga= is depreciated legacy-grub terminology

grub2 uses modelines of vbeinfo: gfxmode=<your vbemode> should switch  to the resolution you like. Make this permanent in /etc/default/grub, then run update-grub2

fontsize can be set using setupcon, you place those values in /etc/default/console-setup

for example [this]("http://forums.debian.net/viewtopic.php?p=376170#p376170") howto will setup a 80x25 console, you should use a higher res of your choice

---

### Post by JoelMay on 2011-08-04
Thank you for the reply.

Apparently Grub2 uses the VESA BIOS extensions.  The only 16:9 resolution I saw was 1280x720.  At least that will remove the stretching, but it still does not provide the resolution I want.

Is there an alternate way to change the resolution?

---

