---
title: "Can't change default OS to ubuntu"
date: 2008-10-01
forum: General Help
---

### Post by zslastman on 2008-10-01
I'me dual booting ubuntu and windows xp on a dell "Latitude D520" laptop. When i turn it on, i first get a menu with just two entries - Windows xp or Ubuntu. If i choose ubuntu i then get the grub menu with the options for standard boot, recovery mode, memtest etc. My problem is this. I want it to boot ubuntu by default since windows is in the habit of messing things up. But every solution to this problem i've found involves editing the grub/menu.lst file in ubuntu, but this is pointless because that menu doesn't come up until i choose ubuntu on the first one, which defaults to windows after a few seconds. How can i change the default on this menu? Is it something specific to my dell or to windows? Sorry if this is a repost.

---

### Post by Aero-Z on 2008-10-01
> **zslastman said:**
> I'me dual booting ubuntu and windows xp on a dell inspiron laptop. When i turn it on, i first get a menu with just two entries - Windows xp or Ubuntu. If i choose ubuntu i then get the grub menu with the options for standard boot, recovery mode, memtest etc. My problem is this. I want it to boot ubuntu by default since windows is in the habit of messing things up. But every solution to this problem i've found involves editing the grub/menu.lst file in ubuntu, but this is pointless because that menu doesn't come up until i choose ubuntu on the first one, which defaults to windows after a few seconds. How can i change the default on this menu? Is it something specific to my dell or to windows? Sorry if this is a repost.
What does this give you:
```
cat /boot/grub/menu.lst
```

---

### Post by zslastman on 2008-10-01
I get  this

#this is a divider added to seperate the menu items below from the Debian
#ones.
title other operating systems
root

#This entry automatically added by the debian installer for a non-linux OS
#on /dev/sdal
title           Dell utility Partition
root            (hd0,0
savedefault
chainloader     +1


#This entry automatically added by the debian installer for a non-linux OS
#on /dev/sdal
title            Microsoft windows XP professional
root             (hd0,1)
savedefault
chainloader +1





Thanks for the quick reply by the way

---

### Post by Aero-Z on 2008-10-01
> **zslastman said:**
> I get  this

#this is a divider added to seperate the menu items below from the Debian
#ones.
title other operating systems
root

#This entry automatically added by the debian installer for a non-linux OS
#on /dev/sdal
title           Dell utility Partition
root            (hd0,0
savedefault
chainloader     +1


#This entry automatically added by the debian installer for a non-linux OS
#on /dev/sdal
title            Microsoft windows XP professional
root             (hd0,1)
savedefault
chainloader +1





Thanks for the quick reply by the way
Your menu.lst is too short. There's something missing. You could also try to use GUI to change the default OS. It's called Startup Manager. I don't remember if you can get it with apt by default. But try:
```
sudo apt-get install startup-manager
```
You can find it under System->Administration menu. From there you should be able to select which OS is the default one.
You can also get the deb from [HERE.]("http://web.telia.com/~u88005282/sum/downloads.html")

---

### Post by louieb on 2008-10-01
Looks like you described haveing a WUBI (inside windows) install.  Is that right?

If so the 1st boot menu is controlled by a file in your window install c:\boot.ini.  Haven't done a wubi install but heres a thread on ntldr and dual booting a regular in its own partition install. Some of it doesn't apply to you but the part about the boot.ini file could get you in the right direction.

[Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")

---

