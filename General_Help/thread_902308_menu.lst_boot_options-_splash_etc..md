---
title: "menu.lst boot options- splash etc."
date: 2008-08-27
forum: General Help
---

### Post by Garratt on 2008-08-27
hello,

I killed grub the other day when i reformatted, couldn't load either OS, on a dual boot system so i finally fixed that, but before i fixed it i had installed QgrubEditor, I ended up fixing it by, swapping the hdd numbers over in menu.lst(which did not work and prevented grub from loading), Qgrubeditor had removed any other data inside menu.lst so it just read the 2 hdd's, and safemode, ram-test...
I then used Super Grub disk to "live swap" and this fixed things.

so a few minutes ago i un-installed Qgrub, and loaded up Startup manager. This rewrote menu.lst and auto saved the incorrect old values(well actually saved my 80g ubuntu os as (hd1,0) safemode etc(hd1,0) and the 600g vista hdd as (hd1,0).
so i loaded up menu.lst and changed the ubuntu values back to (hd0,0), then restarted the system, luckily i did not need to use the super grub cd, my changes worked.

I had also used a splash which upon restarting said it could not load, when ubuntu booted up i checked menu.lst and it has put it on (1,0) as well.

```

#A splash image for the menu
splashimage=(hd1,0)/boot/grub/splashimages/hit.xpm.gz

```

so changed this to (hd0,0) .... this worked i get no error anymore and the image shows, but it's very pixelated like an old atari. 

down further on the file it says:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795
```

I have seen many people say to use this option, is this to change the reso?? and if so should i just uncomment the last line? (im on 21/22inch widescreen im not sure lol... and i normally use 1400x900 resolution)

also I'm curious about other options such as:
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

```

would this make sure in future grub would not get confused about exactly where it is? not that I really need this because i now know how to edit the file, but who knows...3 years from now i may completely forget.

also:
```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

```
seem to suggest similar things, i'm not sure what any of these options actually do.
I tried reading through as much as i could in /usr/share/doc/grub but there was not much info on it...

---

### Post by mcduck on 2008-08-27
Anything in #defoptions will be added to end of kernel lines when grub-update adds new kernels into Gmenu.lst (during a kernel update).
So the effective options are the ones at the ends of kernel boot lines, this here is just to set the defaults.

#groot is, like you sufggested, to configure the grub root location.

# updatedefaultentry=false, when togled to true, will change he default boot option number according to what happens in the menu.lst durin kernel updates. For example if your windows entry is the 6th entry, and set to be the default, kenrel update would add 2 more entries making windows the 8th entry. This setting would tell grub-update to update the default value to correct one.

# savedefault=false This, when true, adds "savedefault" to the end of every boot option. Combine this with the defautlt=saved to make Grub always boot to the last used OS by default.

---

### Post by Garratt on 2008-08-27
cool so you think i should add the groot option and change it to (hd0,0) so in future it knows where the heck it is and knows what to do?

what about the vga splash options?

---

### Post by mcduck on 2008-08-27
> **Garratt said:**
> cool so you think i should add the groot option and change it to (hd0,0) so in future it knows where the heck it is and knows what to do?

what about the vga splash options?

yes, definitley change the #groot to correct one.

The splash, quiet, vga and others are kernel boot options, and the ones at kernel boot entries are the ones that do anything. The setting under default options is, like the name suggests, the default setting. So every time grubupdtae adds new kernels to menu.list it takes the options in #defoptions and adds them to the kernel's boot options. So to change these you need to add them to the kernel options, and then also into the #defoptions to make your changes stay after kernel updates.

"splash" enables/disables the graphical boot. "quiet" reduces the amount of messages outputted to screen during boot. If the splash is enabled but you remove "quiet" you'll get the graphical boot _with_ scrolling boot messages. :o . Remove "splash" and you get the traditional Linux boot-up with loads of scrolling text.

"vga" enables kernel frame buffer, allowing you to configure diplay resolution & colors outside the graphical desktop. I haven't got a list of possible values for this, but I use "vga=792" for 1024x768 with 24-bit colors.

---

### Post by digitalpbk on 2009-11-08
from ubuntu 9.1 the menu.lst is at /etc/default/grub and you have edit and  update grub it with update-grub command. 


[http://digitalpbk.com/2009/11/changing-default-boot-os-grub-ubuntu-910](http://digitalpbk.com/2009/11/changing-default-boot-os-grub-ubuntu-910)

---

