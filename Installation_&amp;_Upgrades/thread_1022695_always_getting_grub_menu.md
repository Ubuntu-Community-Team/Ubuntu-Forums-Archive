---
title: "always getting grub menu"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by rbrcurtis on 2008-12-27
So lately my computer has started an odd issue where I get a grub prompt every time the computer boots.  I guess this wouldn't be too bad except that I don't know how to use grub at all, and its not the graphical menu where I can select a kernel, but a plan boring "grub>" prompt.

If I try to execute "boot" it tells me to load a kernel first, and the kernel command requires a filename as a parameter.  Can someone possibly tell me what filename I should be entering here?

Thanks!

---

### Post by Herman on 2008-12-27
[GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

Try the link above, it should help you I hope.

If you have a /boot/grub/menu.lst file, you should be getting your [GRUB's Main Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#gui"), I wonder why your computer doesn't have it or can't find it. Do you have a /boot/grub/menu.lst file?

Maybe you do but your file system is a bit tangled up and it can't be found easily. Perhaps try running a file system check? [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")**. **I'm only guessing.

---

### Post by didac on 2008-12-27
> **rbrcurtis said:**
> So lately my computer has started an odd issue where I get a grub prompt every time the computer boots.  I guess this wouldn't be too bad except that I don't know how to use grub at all, and its not the graphical menu where I can select a kernel, but a plan boring "grub>" prompt.

If I try to execute "boot" it tells me to load a kernel first, and the kernel command requires a filename as a parameter.  Can someone possibly tell me what filename I should be entering here?

Thanks!

The fast answer:

Type:
   root (hd0,0)
or whenever your grub files are (hd0,1) or whatever. Press Enter
   kernel vmli
and give it a tab to autocomplete the loooong name. Then add in the same line
   root=/dev/sda1 ro

or whatever is your root partition. Press Enter
Then:

   initrd initr

and give it a tab to autocomplete. Press Enter

   boot

and Press Enter

The slow solution:

you got a problem. Boot with the Live CD and type in a terminal:

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

Post the result and help will be forthcoming

---

### Post by rbrcurtis on 2008-12-27
Yes I do seem to have a problem.  I type
root (hd0,0)
configfile /boot/grub/menu.lst

and I get "Error 18: Selected cylinder exceeds maximum supported by BIOS".

I am sure that hd0,0 is correct, and I can't tab complete vmli..

its a 250gb sata drive and the mobo is a asus M2A-VM so there's no reason I should get such an error.

I can't find my live cd at the moment. I'll see if I can find it and post the results.

---

### Post by Herman on 2008-12-27
:) Hmmm, nice motherboard! 
**[ASUSTeK Computer Inc.]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.asus.com%2Fproducts.aspx%3Fmodelmenu%3D1%26model%3D1568%26l1%3D3%26l2%3D101%26l3%3D496&ei=mw9WScLkF4nOsAOtnOyJDQ&usg=AFQjCNHXVknLdu0gZ--ez2If3toWFG65nQ&sig2=hTrSBQE0xYmJO_hiETnV7Q")**


Looks like it's Linux freindly too, 
**[[LinuxBIOS] successfully flashed *Asus M2A-VM*]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=5&url=http%3A%2F%2Fwww.coreboot.org%2Fpipermail%2Fcoreboot%2F2007-September%2F025281.html&ei=mw9WScLkF4nOsAOtnOyJDQ&usg=AFQjCNElR-hV__8nCQFf-WfdwJXM4wLeMw&sig2=F3aJZLAwwTkGd4ybx50iNQ")**

Has One ATA-133 port and four SATA-300 ports controlled by the chipset supporting RAID0, RAID1 and RAID10; 
**[*ASUS M2A-VM* Motherboard Review | Hardware Secrets]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Fwww.hardwaresecrets.com%2Farticle%2F432&ei=mw9WScLkF4nOsAOtnOyJDQ&usg=AFQjCNEaUXqatLNKigTcgTMH6snCuDZwiA&sig2=Erlxe0KUusu8STkroey-IA")**

Are your using any kind of RAID at the moment? Or is that turned off?
(I know you only have one hard drive at the moment, but I'm just checking anyway).

Maybe you just need to play around with your BIOS settings a little, make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.
(If you have those settings in your BIOS, I haven't gone that far with my research yet actually, just shooting from the hip).

---

### Post by rbrcurtis on 2008-12-27
I actually have 3 hard drives plugged in, all sata.  the OS drive is the 250gb, and there are 2x 500gb.  None are raided as of yet.

I've been playing around with the BIOS settings and what I've discovered is that IDE channel 2 is detecting BAD via SMART.  Except that I don't have an IDE channel 2 on this mobo, from what I can tell, only a channel 1.  This was what prompted me to install ubuntu a few weeks ago, and when I did that I reset the BIOS settings to default, which had SMART off, which is why I didn't notice it was still happening until just now.  Maybe this has something to do with the grub issue?

I found by ubuntu cd, actually and 8.10 and a 6.06.  v8.10 now is saying that it can't find the cd when I choose any option on the startup menu (like install, check cd, etc), and 6.06 starts to load the OS but eventually hangs.  This is loading off an IDE dvd drive, so it seems like all my problems might be related to a bad IDE channel?

---

### Post by rbrcurtis on 2008-12-27
oh, IDE channel 2 refers to SATA channel 1, or something like that.  It was the 250gb SATA drive kicking that error, which is what grub is having problems reading.  So it looks like that's my problem right there.  Thanks for the help everyone.

---

### Post by Herman on 2008-12-27
It's fixed? :)

---

### Post by rbrcurtis on 2008-12-27
well, I just finished reinstalling Ubuntu on a different drive that doesn't fail SMART detect, and THAT boots fine, so yeah, I guess so.  ;)

---

