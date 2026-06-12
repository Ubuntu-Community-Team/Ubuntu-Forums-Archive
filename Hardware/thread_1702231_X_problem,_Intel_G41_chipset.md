---
title: "X problem, Intel G41 chipset"
date: 2011-03-07
forum: Hardware
---

### Post by gstilma on 2011-03-07
I've got a weird problem with my display:

I'm dual-booting Win7 and Ubuntu 10.10, both 64-bit. My GPU is integrated on my Intel board, which uses the G41 chipset. My Westinghouse 19" monitor supports 1440x900 resolution and has been running fine for a few weeks on this new build.

A few days ago, booting into Ubuntu threw an error message that was too quick to read, but said something like 'Cannot load device/display configuration,' after which it kicked down to 800x600. In System-->Preferences-->Monitor I am now unable to detect my monitor. The tty console shows ```
*ERROR* EDID checksum is invalid, remainder is 157
``` Weird part is: after this first happened, I rebooted into Win7 and got the same 800x600 ugliness, but my display was still detected accurately and I was able to reset it to 1440x900. Looks fine in Windows now.

At the time of the initial error, I was playing around with GRUB, but nothing serious, just /etc/default/grub timeouts and the like.

I've already created an xorg.conf to force the 'intel' driver, but no difference.

I'm interested in fixing this, but also in understanding why it happened so as to prevent it from reoccuring, if possible. Thanks for any advice.

UPDATE: I'm getting into the habit of solving my own problems that I post here. I got back to 1440x900 using [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically setup with xrandr") and learned something new in the process. Oddly, my POST Intel splash screen and Ubuntu splash now look odd, but I can live with that. I haven't marked this post 'SOLVED' because it's not really -- just kind of a hack. Does anyone have a more elegant solution or at least know what caused this?

---

