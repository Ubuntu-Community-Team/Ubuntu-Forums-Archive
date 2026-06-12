---
title: "grub2 problem"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by geum on 2009-11-02
ubuntu-9.10 on SDA
FreeBSD-7.1 on SDB
Did a clean install of Karmic,after rebooting there was no boot menu,it booted straight into ubuntu.Grub failed to find my second hd(sdb).So I thought no problem I'll just edit /boot/grub/menu.lst,that's when I found out there is no menu.lst anymore.It's now grub2 and for the life of me I do not know what and where to edit anything.

---

### Post by darco on 2009-11-02
try this command,should find your OS

```
sudo update-grub
```


darco

---

### Post by geum on 2009-11-02
Thanks darco but it still only finds ubuntu.
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by darco on 2009-11-02
Grub2 is a different beast.
I too have two seperate hdd and I installed Karmic on sdb and after a few updates, it actually sees my sda drive...are you fully updated? 
Try this link and/or search the forums for grub2

[HTML]http://ubuntuforums.org/showthread.php?t=1195275[/HTML]

darco

---

### Post by geum on 2009-11-02
Yes I am fully updated darco and and I have read the link you supplied,but I still cant see which way to go,most of it talks about upgrading to grub2.
I do not like grub2 I was quite happy with grub legacy and menu.lst.
Why did'nt grub2 detect my second hd,I suppose there is no way I can go back to grub legacy without downgrading ubuntu.

---

### Post by geum on 2009-11-02
Any help would be greatly appreciated.

---

### Post by FrodeA on 2009-11-02
Have you seen this page?

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

It even has a section on how to revert to grub legacy... ;)

---

### Post by geum on 2009-11-04
What I have done so far.
Reverted back to grub legacy,edited menu.lst to boot my other hd,but it still boots straight into ubuntu (no boot menu).But if I select ESC at boot prompt I do get a boot menu where Ubuntu and FreeBSD are listed and I can boot either one and everything is fine.How can I get the boot menu to show without pressing ESC everytime.

---

### Post by kansasnoob on 2009-11-05
> **geum said:**
> What I have done so far.
Reverted back to grub legacy,edited menu.lst to boot my other hd,but it still boots straight into ubuntu (no boot menu).But if I select ESC at boot prompt I do get a boot menu where Ubuntu and FreeBSD are listed and I can boot either one and everything is fine.How can I get the boot menu to show without pressing ESC everytime.

Run the command:

```
gksudo gedit /boot/grub/menu.lst
```

And look for these lines:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**[COLOR="Red"]#[/COLOR]**timeout		**[COLOR="Red"]10[/COLOR]**

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu

The # (aka: comment) in front of hiddenmenu makes the menu show.

The # in front of timeout makes grub just sit there until I've made a decision. If I remove that # then grub will boot the default in the specified 10 seconds. That 10 seconds can be changed to any value you wish if you choose to have grub boot the default.

I prefer mine to just wait for me to decide, nothing more annoying than to be rebooting to get into another OS and just then having to answer the doorbell and having the wrong OS boot.

Remember to click on Save after editing the menu.lst. Then just file > quit.

---

