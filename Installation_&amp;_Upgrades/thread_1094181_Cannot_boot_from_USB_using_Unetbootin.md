---
title: "Cannot boot from USB using Unetbootin"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by runekruse on 2009-03-12
Hi - I have tried to install Kubuntu and Ubuntu from USB-pen using Unetbooting. 
Everything seems to work fine, it transfers the files as it is supposed to and the option "reboot now" appears, but when booting there is no USB boot option, it just continues to win-XP. 
I have tried pressing F8 but still no USB-boot option. 
I'm using a Toshiba Portege m205 if that's of any significance.

Thanks Rune

---

### Post by Therion on 2009-03-12
You probably need to configure your system's BIOS to boot from USB.  Not sure how, exactly, to get into your particular system's BIOS settings, but common keys to do so are "Del", F2 or F12.  

You should get a brief screen before your Windows splash that says something about a key to press to enter setup, or something along those lines.  That would be the key you're looking for.  

Once you're in the BIOS setup menus you'll want to configure your boot chain to include booting from USB.  If it's not available, you may simply not be able to use Unetbootin.

---

### Post by demonarundo on 2009-11-11
I've done all that and nothing
 think this application is useless

---

### Post by Mighty_Joe on 2009-11-11
> **demonarundo said:**
> I've done all that and nothing
 think this application is useless

Those of us who have used it successfully would disagree. ;)
You would probably get more help if you told us what you did (i.e. how your drive is formatted, what iso you used) and exactly what went wrong.  
If you just registered to complain, well, I guess your done then.

---

### Post by darkod on 2009-11-11
Unetbootin just creates the USB stick for you. You don't have to click on Reboot Now, in fact it is better that you don't.

Instead just close unetbootin, your stick is created. Then do this:
1. Open the usb stick and in the root rename syslinux.cfg to syslinux.old
2. In the folder isolinux fiand and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

The above procedure will allow to see the ubuntu menu when you boot from the stick, instead of unetbootin menu which is slightly confusing.

It's a different question whether the computer can boot from usb at all.

---

