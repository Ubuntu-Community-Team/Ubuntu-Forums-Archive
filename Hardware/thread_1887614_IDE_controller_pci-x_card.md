---
title: "IDE controller pci-x card??"
date: 2011-11-27
forum: Hardware
---

### Post by Robertjm on 2011-11-27
Hello all,

My old computer crashed and so I am having to build a system from the ground up. However, I need to include my two internal IDE drives; at least for the forseeable future.

Have been looking at several cards online made my Masscool, Syba, Startech and Ultra. Hard to find any references to Ubuntu. For those that do (Masscool and Ultra) I seem to find just as many "it doesn't work" comments as I do "it works out of the box" comments.

Because of that I figured I would ask the collective wisdom of the ubuntuforums.org forums. :D

I will probably be using 64bit Natty because of sound driver issues in Oneric for Creative Labs Xfi cards. Also, it will probably be a duel boot sytem with W7 being the other O/S the card will need to be recognized by. However, my boot drive will be a SATA III SSD drive, so I don't need to boot off the IDE drives anymore. External USB cases are not an option.

Surely there's some other people that have had to tackle this issue? Which cards worked for you? Which cards didn't, or were more trouble than they were worth? An eSATA port would be cool, but not required.

Thanks!!

Robert

---

### Post by dandnsmith on 2011-11-27
In looking to 'solve' this problem, I bought a mobo which had an IDE slot as well as SATA, thus avoiding your apparent problem.

---

### Post by Robertjm on 2011-11-27
Easier said then done with a Socket 1155 z68 chipset motherboard!!

---

### Post by Robertjm on 2011-12-29
Just a quick followupn Tried using a Mascool pci-express card. However, its design sucks because the IDE port forces the ribbon to take up the adjacent pci-express slot too.

Ended up buying a couple IDE adapters to fit the back of the drive, and then connect by way of a standard SATA cable.

They're about $6 a piece at Monoprice. And they also have really innexpensive SATA cables too! Just make sure you get the correct adapter as they have SATA to IDE mobo adapters too.

[link to Monoprice adapter]("http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10407&cs_id=1040701&p_id=327&seq=1&format=2")

When I load my computer grub2 recognizes all the kernels from the 2 old IDE drives.

Robert

---

