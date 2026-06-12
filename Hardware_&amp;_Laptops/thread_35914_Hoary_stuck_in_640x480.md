---
title: "Hoary stuck in 640x480"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by TestDummy! on 2005-05-20
Hello. I tried to install Hoary on my laptop (Toshiba Tecra 8000, P2-300, 128MB, 6GB HDD). The install goes smoothly, but when X starts, all I get is 640x480. 

I've tried messing around with xorg.conf, to check what's up, but 1024x768 is already in there at the default bitdepth. But I go to change the resoultion in Gnome, and the only option I get is 640x480. With Warty, everything worked rather well, it defaulted to 1024x768 and just worked, but with Hoary it doesn't. 

I've tried asking on #ubuntu but I didn't get very far (Thanks for trying :) ) 

Any ideas?

---

### Post by Klojum on 2005-05-20
Having the same problems here with a Toshiba 300CDT (yes, a prehistoric laptop now with 80MB internal and 40GB external memory). Perhaps that the C&T videochips in Toshiba are not fully supported?

---

### Post by TestDummy! on 2005-05-21
[QUOTE=Klojum]Perhaps that the C&T videochips in Toshiba are not fully supported?[/QUOTE]

Hm, last I checked, both Linux and Windows said my Toshiba had a NeoMagic chip for the video. 256AV if I recall the chipset correctly.

I'm just guessing, but I wonder if the switch of X server that was in Warty to the other one that is in Hoary makes any difference here.

(I remember Warty using XFree86 and Hoary X.Org)  ](*,)

---

### Post by Xian on 2005-05-21
[QUOTE=TestDummy!]I'm just guessing, but I wonder if the switch of X server that was in Warty to the other one that is in Hoary makes any difference here.[/QUOTE]
If your X was working in Warty then the first thing I would check is to make sure your "Monitor" section in /etc/X11/xorg.conf is configured properly. Specifically, check to see if sync rates are needed and what their values should be. Are you able to load a LiveCD that uses Xorg? If so then do that and if the screen appears properly, compare its X config with the one you have presently in Ubuntu.

Or you could run the command below and choose 'Advanced' when it is time to set up your screen parameters. Afterwards, go back and verify that those were actually written to the xorg.conf file. I've seen it often where some of those values get left out and have to be added manually.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by TestDummy! on 2005-05-21
[QUOTE=Xian]Are you able to load a LiveCD that uses Xorg?[/QUOTE]

Uh huh, I have Slax too, which used Xorg last I checked, and it boots into 1024x768 without any extra input. Same with Kanotix, and basically every other LiveCD I have.

---

### Post by Xian on 2005-05-21
[QUOTE=TestDummy!]Uh huh, I have Slax too, which used Xorg last I checked, and it boots into 1024x768 without any extra input. Same with Kanotix, and basically every other LiveCD I have.[/QUOTE]
Okay, great. Have you been able to compare its X config with the one you are presently using on Ubuntu?

---

### Post by TestDummy! on 2005-05-21
Not really but I guess I could try that

---

### Post by Xian on 2005-05-21
It would be my next step. The idea being to compare the two and note any differences in the "Monitor" and and _possibly_ "Device" sections. If you find that the LiveCD X config has some additional lines, then rename your current xorg.conf, append those changes and save it as a new xorg.conf. I suspect that the sync rates are the source of this issue.

---

### Post by TestDummy! on 2005-05-22
Odd, this is really messed up. I boot up Slax to open up xorg.conf and compare it to the one for Hoary, but..

This is a config file for XFree86... I should have sworn it used XOrg. They say one thing and the file says another. I'm a little lost.  :?: I thought most distros switched over to XOrg after that whole license deal with XFree86

---

### Post by shof2k on 2005-05-23
I've noticed that a few reports of the screen resolution stuck at 640x480 during a hoary installation.  Warty seems ok though.  Is this common, if so should a bug report be filed?

over to you guys

---

### Post by andlinux21 on 2005-05-24
Yeah i tried to change my display but its stuck also. Its at 800x600 but it will go one notch higher in winblows.  If I can just get my display to adjust to 1024x780 it would be a perfect lappy for me even without the sound. \\:D/

---

