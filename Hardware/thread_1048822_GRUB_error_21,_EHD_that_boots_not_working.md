---
title: "GRUB error 21, EHD that boots not working"
date: 2009-01-23
forum: Hardware
---

### Post by lukedmor on 2009-01-23
Hi, i installed Ubuntu on my Vista computer, and kept vista because windows is useful sometimes. Then, after being on Windows for a while, i restart my comp. to go into ubuntu. i get grub error 21 before the grub menu comes up. the external hard drive (WD MyBook essential external)is where i installed Ubuntu/grub. It appears the external hdd is not working. when i turn on the computer, i hear it starting up, then failing. starting up, and failing. agian and again and again.

I would like to know either how to get rid of the grub boot loader link on my internal drive, so it will automatically boot Vista like it did before i installed Ubuntu; OR, how to fix the external hard drive so it will work.

i bought the WD5000 at COMPusa before it closed, before i knew i would be taking such risks. now, i cannot return it without paying a BUNCH of money to another store, which is definetely not preferred.

Lukedmor

---

### Post by caljohnsmith on 2009-01-23
How about trying this:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
And replace "sda" with whichever is your Vista drive (most likely sda), and that should allow you to boot straight into Vista again. Then to install Grub to the MBR (Master Boot Record) of your Ubuntu drive, how about doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should install Grub to the MBR of your Ubuntu drive. Then when you reboot, if you set your BIOS to boot the Ubuntu drive, you should get the Grub menu at least (if that drive is working). Let me know how it goes or if you run into problems.

---

### Post by lukedmor on 2009-01-24
thanks, but where am i supposed to type this. i know the terminal, of course; but i basically dont have linux, my hdd failed. i found out that it is irrepairable.

So, pretty much, my computer is an external with openSUSE and Vista (Vista internal, openSUSE another external). So there is a link to grub in my destroyed ehd. i understand what ur saying, but i get error 21 every time i turn on my computer. i am running a live CD of ubuntu right now

---

### Post by lukedmor on 2009-01-24
oh haha. looks like you can do that on the live CD as well. Kudos to caljohnsmith. but i didnt do the last part, because i dont remember what was what when it came to those hd0,1 things and stuff.

---

