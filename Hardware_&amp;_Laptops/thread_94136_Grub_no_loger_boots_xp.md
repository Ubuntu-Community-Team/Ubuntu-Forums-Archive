---
title: "Grub no loger boots xp"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by 50invalids on 2005-11-23
i have a dual boot system, ubuntu 5.10 / win xp pro 
it has been working quite well untill suddenly grub won't let me boot into xp 

xp pro is on hda1 (ntfs)
ubuntu is installed on my second hardrive

ubuntu is on hdb3 ext3
and on hdb6 linux swap
hdb1 is fat32

my grub menu.ls file reads as follows 
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

when trying to boot it loadfs up as follows:
(hd0,0)
'unknow file system' code x07
savedefault
makeactive
chainloader	+1

and the machine just hangs

please, please, how can i resolve this?

---

### Post by 50invalids on 2005-11-23
correction: 
when it tries to load it gives the following :
root (hd0,0)
 file system type unknown partition type 0x7
savedefault
makeactive
chainloader +1

and the machine just hangs

please help

---

### Post by lisje on 2005-11-23
oh you need to map since your linux and your windows are on different drives (eurhm I don't know any other way to say it... I'll just dig up the code)

map (hd0) (hd1)
map (hd1) (hd0)

I don't really remember where exactly to put it in your grub-file... but I think you'll get a step further this way.

greets,
Lisje

---

### Post by 50invalids on 2005-11-24
thanks for the suggestion
... this still doesnt work.. i also tried replacing root with root noverify , that gets rid of the error message, but still xp doesnt boot, i'm just left with the grub commands on screen and nothing else...
could this mean there's a problem with my xp hd? or mbr? i tried to reinstall grub and still i get the same problem .... this is driving me mad

---

### Post by x__dark on 2005-11-24
Is the drive Ubuntu is on recognized first or second by your bios?

If it isn't get rid of everything under "makeactive"

Map over to the other drive

so it should look like:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd1) (hd0)
map (hd0) (hd1)

I think that should work. That's how I used to boot into windows xp.

---

### Post by 50invalids on 2005-11-24
well the oder in the bios is correct , hd0 (hda win xp) is first) and hd1 is second ...

still won't boot... not grub doesn't hang on boot comands but returns back to grub menu when i try to boot xp.... this is just joke now 

any other suggestions?

---

### Post by fatcity on 2005-11-25
I've had a similar problem before.  The following works for me.  From the grub command prompt, GRUB>, enter the following four commands (You will still get the error msg after the 1st command):

root (hd0,0)
makeactive
chainloader +1
boot

---

### Post by spanella47 on 2005-11-30
had the same problem when i installed ubuntu a week ago.  I'm pretty new here, but i set up a 2 step process that seems to work so far.  I added 2 seperate entries into grub:

1)
title Microsoft Windows XP Professional step 1
root (hd1,0)
makeactive
map (hd1) (hd0)
map (hd0) (hd1)

2)
title Microsoft Windows XP Professional step 2
root (hd1,0)
makeactive
chainloader +1

when in the grub menu i select the first entry and it just returns me to the grub menu for whatever reason with no error.  Then choosing the 2nd entry (same as your initial post and the one causing me troubles) works with no errors.

again, I'm new and have no reason why this would work, but it has so far.

good luck

---

