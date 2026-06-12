---
title: "Accidentally removed a partition while installing. Help?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by joosto on 2009-07-10
Hello ,

I'm new to Ubuntu, but I wanted to try it out. So I made a booting USB disk with Unetbootin (The live disk didn't work for me).

During the installation progress I accidentally removed the partition of my D: drive. Luckily Windows is installed on my C: drive, but my question is, how do I recreate this partition so that windows recognizes it as my D: drive?

Some information that might be helpfull:
Where the free space is now, /dev/sda3 used to be, type ntfs.

[IMG]http://i788.photobucket.com/albums/yy165/joosto/Screenshot.png?t=1247221143[/IMG]

Can someone please help me?

Thanks :)

---

### Post by Sub101 on 2009-07-10
Im unclear if you have successfully installed Ubuntu. If you have then you can use GParted to format the free space.

If you are yet to install then I believe you can format the space using the partitioner during the installation process.

It is also possible in Windows, but I forget how.

---

### Post by joosto on 2009-07-10
No I haven't installed it successfully yet. But will windows recoginize it as my D: drive after formatting the free space?

I'm sorry if I don't understand everything quick enough but I'm new to this.

---

### Post by joosto on 2009-07-10
Fixed :D. I thought the changes were made already, but I found out the changes would be made in a later phase of the installation. My D: drive still exists, and Ubuntu is now installing! :D.

I'm sorry for the inconvenience.

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Just for information - I was looking at a slightly different problem, some one suggested TestDisk (get it via your Synaptic Package Manager) as a solution.

Having had a look at it, it's been down-loaded & will be wending it's way onto a boot CD once I figure out how !!!

Phill.
[/FONT][/SIZE]

---

