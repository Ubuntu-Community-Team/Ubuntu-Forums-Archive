---
title: "HELP- Ubuntu 8.10 Live CD installation removed my XP partition"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by onzki on 2009-04-20
HELPme guys! 
Hi, i'm a newbie in this forum and ubuntu OS=)
here's my case:

i got my ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Using my hpdv6670ee laptop-I was able to install ubuntu 8.1 last night using live CD..  and honestly, it looks nice and feels really light..i can hear the OS breathin' well hehe=). 
HOWEVER, the bad thing is- it formatted my XP partition! I didn't expect it to happen because during the partitioning stage-i precisely assigned Ubuntu to use 25 GB out of my 145GB drive.. its very clear- i used the partitioning "slider" (i dont  know what's the term).. and then i continued.. 
but in the end, it made my xp drive its page file or simply an empty file drive!

what did i missed? my goal is to have a dual boot.. xp and ubuntu 8.10. Im really interested in installing Ubuntu..but i need to keep my XP because of my work related programs such as autocad, 3d max and adobe photoshop, illustrator etc.

I appreciate your help. thanks!

---

### Post by upchucky on 2009-04-20
Don't panic,

Assuming that the Ubuntu live cd you used to do the install does actually boot up to a graphical desktop, (this means booted using the cd only, not an actual install) Then boot the machine using the Ubuntu live cd, then download this,

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

Open a terminal, "on the desktop title bar" click Applications > Accessories > Terminal then type this in the terminal,

```
sudo bash ~/Desktop/boot_info_script*.sh
```

It will create a file on the desktop that shows everything on the drive and will provide the information to get the dual boot working.

Post the results of the file here, (copy/paste),  so we can see what is actually on the drive and then advise how to set it up.

If you did indeed do as you posted then your original windows will still be there, and a file called menu.lst that the grub bootloader uses to load either OS needs to be edited to be able to boot either OS

---

### Post by onzki on 2009-04-20
Im sorry- it's not "live cd". what i have is the desktop installation i downloaded from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


ill revise my title.

Thanks!!

---

### Post by lisati on 2009-04-20
> **onzki said:**
> Im sorry- it's not "live cd". what i have is the desktop installation i downloaded from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


ill revise my title.

Thanks!!

There are two main kinds of CD you can download for the Desktop edition: the "Live CD" which boots to a graphical desktop, and an "alternate" installation CD which uses a text-based installation process. Just to be clear: which exactly did you download?

---

### Post by upchucky on 2009-04-20
Ok, assuming that you can still boot into your installed Ubuntu, open a terminal, click Applications > Accessories > Terminal then type this in the terminal,

```
sudo fdisk -l
```


post the results here we should be able to see the drive info and if windows is still intact and be able to advise the next step.

---

### Post by onzki on 2009-04-20
Thanks so much guys! i don't know what happened to my pc but its workin now, i can use my xp again. its weird- really the last 3 times i choosed to load xp- it didn't load but rather started with ubuntu instead. Im up and runnning now.. Thanks again..
should i delete this post, coz it seems to be a false alarm?:o

---

