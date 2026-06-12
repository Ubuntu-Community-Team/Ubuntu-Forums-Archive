---
title: "Grub Bootloader"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by blud on 2006-02-02
Is it possible to make my computer wait at the Grub bootloader instead of loading up Linux straight away. I would like to make it stop at the bootloader and wait for me to choose which operating system I would like to use can this be done.

---

### Post by psboy1987 on 2006-02-02
grub bootloader should give you about 30 seconds to choose which os you are going to use. Are you sure you have 2 operating systems loaded? does it pause when your computer starts?

---

### Post by Sutekh on 2006-02-02
You should make a backup of your GRUB menu first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

Then look for this section in your GRUB menu.lst (this is a clip from mine)

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		5**
```

Your entry may be so low that you don't have time to choose the OS to boot.  You could try making the value higher.

It may also be that your GRUB menu is hidden from view.

Look for this section
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**#hiddenmenu**
```
and make sure its commented (#) out.  Otherwise you have to press ESC to see the menu.


You should have at least the options of booting Ubuntu and Ubuntu Recovery Mode as well as a memory test even if you only have Ubuntu on your PC.

---

### Post by blud on 2006-02-02
It pauses for about 10 seconds then loads up Ubuntu however I would prefer for it to wait at the bootloader screen until I choose which system I want to load as I have a habit of turning on my computer as I come home then I go get changed and then when I come back to my computer Ubuntu has loaded most of the time this isn't an issue but sometimes I require windows to do stuff as I haven't worked out how to do them properly in Linux.

---

### Post by Sutekh on 2006-02-02
[QUOTE=blud]It pauses for about 10 seconds then loads up Ubuntu however I would prefer for it to wait at the bootloader screen until I choose which system I want to load as I have a habit of turning on my computer as I come home then I go get changed and then when I come back to my computer Ubuntu has loaded most of the time this isn't an issue but sometimes I require windows to do stuff as I haven't worked out how to do them properly in Linux.[/QUOTE]
I dont know if you can get it to wait *indefinately*, but you can get it to wait a looong time if you want.  Just give it several hundred seconds to wait!

---

### Post by louca on 2006-04-23
what if you comment out the timeout?
will that MAKE it pause? or will it just not wait at all?

---

### Post by R3linquish3r on 2006-04-23
Commenting the timeout sounds like a good idea....

---

### Post by Sutekh on 2006-04-23
I'm sure you've found out by now.

A timeout of 0 will not wait at all.

Commenting out the line will wait indefinitely.

Appararently using text causes the menu to wait aswell.

[http://ubuntuforums.org/showpost.php?p=711661&postcount=8](http://ubuntuforums.org/showpost.php?p=711661&postcount=8)

---

