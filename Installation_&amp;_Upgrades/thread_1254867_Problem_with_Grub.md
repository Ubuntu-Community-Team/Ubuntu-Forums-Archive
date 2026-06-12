---
title: "Problem with Grub"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Stirfry on 2009-08-31
I just got back into the Linux world. I have a 320 gig hard drive with Windows xp on it..and i have a 160 gig hd with Ubuntu installed. Ubuntu was installed after xp. The problem is that my computer boots directly to Ubuntu without asking me if i want to boot to xp. Grub isnt even coming up. Any help with this would be great..thanks.

---

### Post by DFlame on 2009-08-31
Watch the boot procedure closely onscreen. Do you see "GRUB loading stage 1.5" or anything like that, even for a splitsecond before it boots?

Regardless whether you do or not, let it boot into Ubuntu. Open a Terminal window and enter this:

```
sudo gedit /boot/grub/menu.lst
```

In the text editor that appears, copy all of the text and place it on a service like [Pastebin](http://ubuntu.pastebin.com). You can then place a link to it here for us to take a look. Needless to say, don't make any changes to that file yet.

If you can't get it on there, just paste it in a post here. Pastebin links tend to keep everything tidy though :)

---

### Post by presence1960 on 2009-08-31
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

This will give us much more detailed info about your setup & boot process including the info requested by previous poster.

---

