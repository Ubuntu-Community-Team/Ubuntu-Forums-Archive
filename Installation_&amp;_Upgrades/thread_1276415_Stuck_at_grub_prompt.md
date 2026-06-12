---
title: "Stuck at grub prompt"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by xxhopingtearsxx on 2009-09-27
I'm not really new to Ubuntu seeing how I've been using it for some time, but all I do is chat and watch videos, so I'm still pretty much a newbie, so please try to be as simple as possible.

I was installing Ubuntu 8.04 on Ubuntu (I deleted Ubuntu 9.04 because of some wifi problems and wanted to see if 8.04 would help).. I tried installing it on wubi. It wouldn't show up in Windows Boot Manager. I went to EasyBCD and added Ubuntu manually, and I get stuck a a black and white MS-Dos like screen that says "Grub". I really don't know what to do.

I tried it with 9.04, too, and it did the same thing. I can't boot from the CD because when I do, I get some green lines as if I was playing a broken cartridge on an old school Nintendo. It did that with other successful installs I've had, so I don't think that's really an issue. Please help. I really want to use Ubuntu again and not be stuck on Windows.

---

### Post by kranny on 2009-09-27
Did you try the Alternate Cd...
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by renkinjutsu on 2009-09-27
at grub, try entering these commands
(ignore everything with a # when you're typing your commands)
```
find /boot/grub/stage1

#Then, it should give you something looking like (hd0,3) or whatever
#then take that value and enter

root (hd0,3) #or whatever it was

chainloader +1

#and lastly...

boot
```


This is not a fix, it's just so you can boot up into Ubuntu (hopefully) so you can be more at ease while looking for help.

---

### Post by kranny on 2009-09-27
> **renkinjutsu said:**
> at grub, try entering these commands
(ignore everything with a # when you're typing your commands)
```
find /boot/grub/stage1

#Then, it should give you something looking like (hd0,3) or whatever
#then take that value and enter

root (hd0,3) #or whatever it was

chainloader +1

#and lastly...

boot
```


This is not a fix, it's just so you can boot up into Ubuntu (hopefully) so you can be more at ease while looking for help.

He said he couldnt get to the shell..

---

### Post by xxhopingtearsxx on 2009-09-27
When I type those codes, it takes me back to the Windows Boot Manager.

---

### Post by xxhopingtearsxx on 2009-09-27
bump.

---

### Post by xxhopingtearsxx on 2009-09-27
Bump. |: Ugh, my thread keeps going down to the next page and I really need help.

---

