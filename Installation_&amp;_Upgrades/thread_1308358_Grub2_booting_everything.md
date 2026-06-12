---
title: "Grub2 booting everything?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Abble on 2009-10-31
[B]Got a few question about grub2.

  With Grub2 you can boot various operating systems on different devices. Is it is possible to make an entry so grub can scan for bootfiles on an cd-rom, floppy or usb-stick?

Grub can only display a few resolutions. In my case resolutions in 4 by 3 ratio (1024x768 ). The thing is my monitor is a 16 by 10 ratio monitor. The monitor will strech the image so it will fit on the whole monitor (1280x800). The bad thing is that the image will loose its correct ratio. The picture gets deformed. Is it possible that grub can display an image 'deformed'? So when the bootmenu is displayed, the picture will be correct.
Can grub display images in a way so it will be displayed correctly on widescreens?

See 'Reply #36' on this forumthreat [http://kubuntuforums.net/forums/index.php?topic=3106368.30](http://kubuntuforums.net/forums/index.php?topic=3106368.30)
[/B]     


---------------ignore the old comment-------------------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Got a few question about grub2.

About booting:
 First of all is it possible to boot a usb-stick? Actually booting files from the stick.
 
 Second is it possible to boot a bootable cd-rom?
 
 You may think why would this fellow want this. Well thats becoz I would like to have 1 environment 'Grub2' who will handel every boot sequence I want. I want to boot ubuntu, fedora, windows xp, mac, cd-rom boot disk, bootable usb-stick and yes also a bootable floppy disk. So the startup sequence does not have to swap my cdrom drive or floppy drive when it starts up, its a bit faster and no noise. So it will be there in Grub when I need it. Further more for the usb-stick booting option will give me an extra boot possibility. That is the bios can't do it and it would be wonderfull if it could be done with grub2. Maybe it's to much to ask for the last 1, but you will never know if you don't shoot.
 
 
 About the graphic:
 Is it possible to auto adjust images to fit a widescreen monitor if the vbe only come up with 4 by 3 screenresolution ratios?
 
 You can do this manually with a graphic tool like gimp. Deforming the image, so when its deformed again by the monitor its shown correct.
 
 For example the highest output resolution the system got is 1024x768 (4:3). The system will send a 1024x768 images to the monitor. The monitor will deform the image, stretch it, to a 1280x800 (16:10) or whatever ratio to make it fit to the screen. (Don't think the resolution will change but the actual image will strech to fit the monitor, but I am no geek, just guessing). The system gives a 4:3 image and the monitor makes it a 16:10 images.
 Now iff you do this manually you will have to:
 (open image with 1280x800 resolution or crop it)
 - resize the image to 1024 higth and 768 wide.  (1,25 x higth and wide 1,04 x wide) 
 
 The result is that the image is slightly squeezed horizontally. But when the bootmenu shows the images will be stretched (by the monitor) and shown correct.
 
 My third question is, is it possible to let grub2 do this automatically? 
 And to let it work with an easy gui setup like startupmanager. 
 Selecting 1024x768* in stead of the regualar 1024x768.



O Ooo I almost forget. If any of the three question can be confirmed with a yes.
Please list the commands.

I thank you,
Abblr

---

### Post by Abble on 2009-10-31
16 views in 1 hour. Come on ppl give me something :)

---

### Post by karlo on 2009-10-31
> **Abble said:**
> 16 views in 1 hour. Come on ppl give me something :)
Actually your thread is kinda confusing. Can you rephrase it, like make it user-friendly?;)

---

### Post by Abble on 2009-10-31
Man I did my best, will try again.

Well you have Grub2. With it you can boot various operating systems on different devices. Is it is possible to make an entry so grub can scan for bootfiles on an cd-rom, floppy or usb-stick?

Grub can only display a few resolutions. In my case resolutions in 4 by 3 ratio (1024x768 ). The thing is my monitor is a 16 by 10 ratio monitor. The monitor will strech the image so it will fit on the whole monitor (1280x800). The bad thing is that the image will loose its correct ratio. The picture gets deformed. Is it possible that grub can display an image 'deformed'? So when the bootmenu is displayed, the picture will be correct.
Can grub display images in a way so it will be displayed correctly on widescreens?

---

### Post by Abble on 2009-10-31
Is it understandable now?

---

### Post by karlo on 2009-10-31
> **Abble said:**
> Man I did my best, will try again.

Well you have Grub2. With it you can boot various operating systems on different devices. Is it is possible to make an entry so grub can scan for bootfiles on an cd-rom, floppy or usb-stick?

Grub can only display a few resolutions. In my case resolutions in 4 by 3 ratio (1024x768 ). The thing is my monitor is a 16 by 10 ratio monitor. The monitor will strech the image so it will fit on the whole monitor (1280x800). The bad thing is that the image will loose its correct ratio. The picture gets deformed. Is it possible that grub can display an image 'deformed'? So when the bootmenu is displayed, the picture will be correct.
Can grub display images in a way so it will be displayed correctly on widescreens?
It's totally complicated ...

---

### Post by drs305 on 2009-10-31
> **Abble said:**
> Well you have Grub2. With it you can boot various operating systems on different devices. Is it is possible to make an entry so grub can scan for bootfiles on an cd-rom, floppy or usb-stick?

Grub can only display a few resolutions. In my case resolutions in 4 by 3 ratio (1024x768 ). The thing is my monitor is a 16 by 10 ratio monitor. The monitor will strech the image so it will fit on the whole monitor (1280x800). The bad thing is that the image will loose its correct ratio. The picture gets deformed. Is it possible that grub can display an image 'deformed'? So when the bootmenu is displayed, the picture will be correct.
Can grub display images in a way so it will be displayed correctly on widescreens?

From the GRUB 2 menu, you can press "c" to get into the command line and then type "vbeinfo" to show you the resolutions available to GRUB 2. Don't know if you have already done that, but if not perhaps there are more resolutions available than you think. 

There is a line in /etc/default/grub to set the resolution. Note this resolution and the vbeinfo command are for resolutions of GRUB 2 only, not after the system boots.

If you were unaware of these things, there is more information in the GRUB2 link in my signature line. Look at the /etc/default/grub entry.

---

### Post by Abble on 2009-11-01
This is the whole point about the graphic. I already did the "vbeinfo" and the only resolution I got is in the 4 by 3 format. And yes I know the resolution from "vbeinfo" is only for grub2. Anyway will check out your links.

---

### Post by Abble on 2009-11-01
What if I change the 

'GRUB_CMDLINE_LINUX=vga=792 splash' 

line to 

'GRUB_CMDLINE_LINUX=vga=355 (0163h) splash' 

in the /etc/default/grub

Will it change the bootmenu or the stuff that come after?



source info: [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by drs305 on 2009-11-01
> **Abble said:**
> 
Will it change the bootmenu or the stuff that come after?


That should effect your system resolution after the boot. The GFXMODE is the setting that effects the GRUB display.

---

### Post by Abble on 2009-11-01
Than I guess I am stuck.

---

