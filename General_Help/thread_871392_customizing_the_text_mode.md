---
title: "customizing the text mode"
date: 2008-07-26
forum: General Help
---

### Post by toylas on 2008-07-26
Dear All,

I am not aware of the jargon that goes with this stuff so I'm posting it in the general issues forum. Here's what I want to do:

I want to customize the text mode (the ones you get by pressing ctrl+alt+F1 etc. I'm not sure what exactly is the term for them but I guess these are called vt1, vt2 etc.). I once installed Gentoo on one of my machines and the text mode had a nice image as the background and the text was very nice small font resembling courier with size ~12pts. I once tried to look for available fonts but did not find a way to get really nice smooth ones. 

Could someone please shed some light on the jargon involved and the way to go about configuring for all this? All I know is that I need to have framebuffer enabled for this. But how to do all this is something that I have no idea about. Any help and pointers would be greatly appreciated.

Thanks,
Toylas

---

### Post by toylas on 2008-07-26
Hi,

I just read a little bit about customizing the text mode resolution and tried to use the vga=*** switch but at bootup I got a message that the resolution is not supported. I did a scan but the max I could get was vga 80x60. When I chose that option, my text mode was not usable at all. It kept flickring. I have a Dell Inspiron 6400 laptop. I use X at 1200x800 resolution. Is there a way to configure my laptop for a higher resolution text mode?

---

### Post by CatKiller on 2008-07-26
> **toylas said:**
> I use X at 1200x800 resolution. Is there a way to configure my laptop for a higher resolution text mode?

It's certainly possible to get a higher resolution. Whether it's possible to get your native resolution is a different matter.

For example, my menu.lst has **vga=0x31B**, which gives me a 1280x1024, 24-bit colour mode. The numbers to pass to set the vga mode are the numbers of the VESA modes plus 200 (hexadecimal). Unfortunately, the combination of the proliferation of new resolutions with the move away from framebuffer stuff meant that "starting in VBE/Core 2.0, VESA no longer defines new VESA mode numbers and no longer require support of existing numbers" according to Wikipedia. That page also suggests that 0x360 **might** give you a 1200x800 8-bit mode.

It is probably possible to find out what the mode numbers your particular graphics adaptor uses for different resolutions, and pass that number appropriately with the vga= line in GRUB, but I don't personally know of a way to do that.

---

### Post by toylas on 2008-07-27
Thanks for the reply CatKiller. I tried the 0x31B and 0x360 both but it does not work for me. I get error for both and an option to scan before booting. I get 6 options like: 80x30, 80x35, 80x50 etc. Out of those 6 options, 80x60 does not seem to work either though I have not tried all of them. Anyone any other ideas??
Thanks,
Toylas

---

### Post by CatKiller on 2008-07-27
Well, I was reading the modes from [this Wikipedia page]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VBE_mode_numbers"). Don't forget to add the 200 on. The table underneath that lists Linux video mode numbers is out of date, I think. I had the decimal number some time ago, and at some point had to change it to the hexadecimal equivalent.

Otherwise, hopefully someone can chime in with a way to get the mode you want from your graphics adaptor.

---

### Post by CatKiller on 2008-07-28
Actually, I just found myself reading [this page]("http://www.savvyadmin.com/console-framebuffer-in-ubuntu/") for other reasons. It's possible that I fiddled with these files some time ago, and simply forgot about it. Perhaps this might help you get the resolution that you want?

---

