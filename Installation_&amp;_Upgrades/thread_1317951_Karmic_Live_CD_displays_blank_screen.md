---
title: "Karmic Live CD displays blank screen"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by treesurf on 2009-11-07
Hi all.  When I run the Karmic Live CD it gets me as far as choosing a language and displaying the menu.  At that point, no matter which option I choose (except for boot from HDD) the screen goes blank.  However, the Live CD is still doing what I ask it to.  So, for example, if I choose "Boot Ubuntu without altering your computer" (or whatever it is), it will boot all the way to the desktop.  I know this because I hear it make the login sound.  However, the screen is totally blank the whole time.

I have checked the md5sum on my download, downloaded and checked it again, and even tried putting on a USB stick.  Same results.

Any suggestions?

thanks

---

### Post by treesurf on 2009-11-07
Sorry, forgot to mention my hardware:  Lenovo IdeaPad Y550 with integrated Intel graphics X4500.

---

### Post by mutrax on 2009-11-07
hehe... been there to.

Just add i915.modeset=0 to your kernel parameters. 

If you are using karmic, this is situated in /boot/grub/gru.cfg.

I changed mine like this....
```

linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=74befa82-a138-491d-9188-84b1888aed00 ro   quiet splash*** i915.modeset=0***
```

---

### Post by treesurf on 2009-11-07
How would I go about having the Live CD boot with that parameter?  I want to check out Karmic before installing it, but I can't even get the Live CD to display anything.

---

### Post by mutrax on 2009-11-07
If I remember correctly you can choose keymap, language with f2 and f3, and when you pick f6 other options, you can add the "i915.modeset=0"  

When editing grub parameters at first boot of your installed system, add the parrameters between "splash" and the "--" if present. At first boot this is modified by editing the menu entry by hitting "e". The rest is self explainatory.

You can serch the forum, since this is a problem that more users are experiencing.

Greets,

---

### Post by treesurf on 2009-11-07
Thanks!

---

### Post by KayakJim on 2009-11-08
I have the same problem only with an ATI 4650HD video card. Any idea on what I can do to fix that?

---

### Post by treesurf on 2009-11-10
Well, the i915.modeset=0 fix worked to boot into the LiveCD and do a fresh install of Karmic.  Unfortunately,  when I boot into Karmic I am back to the blank screen and I can't figure out how to configure Grub2 to use this fix.

Help please!

EDIT:  NEVER MIND, I figured it out.:biggrin:

---

### Post by KayakJim on 2009-11-10
> **wallaroo said:**
> I have this problem whenever clean installing ubuntu on my laptop (ATI video). My fix is to reduce the color-depth to 256 colors during the install phase.  This may work for you too.  When you are on the options screen and with 'Install' highlighted, press F6 to bring up the 'other' options, press ESC to close the pop-up screen and this will put you in edit mode for the boot options. Just type vga=771 (which will be appended to the end of the boot script). Then just press [Enter] to continue with the installation.  The addition of 'vga=771' sets video mode to 800x600 x 256 colors. If you prefer you can use 'vga=773' which sets it to 1024x768 x 256 colors.  This only sets the video mode for the installation phase.

This helped me out, although the screen is not very readable.

---

