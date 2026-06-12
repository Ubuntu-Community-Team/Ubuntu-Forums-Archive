---
title: "Best hard-disk setup?"
date: 2008-11-21
forum: General Help
---

### Post by Edward850 on 2008-11-21
So I'm now doing a real Ubuntu install on my PC (not using wubi), and I need to know the best way to get it to work.

First off, I'll be using 8.04 (because 8.10 doesn't render correctly [see attachment]).

Now for problem. I have 2 hard-disks. One 80GB hard-disk divided into 2 NTFS partitions, and a 400MB hard-disk (also NTFS) as a 3rd. I was thinking of keeping the primary partition the same (as it is my windows partition), and the second partition would have 11GB taken from it for Ubuntu (10gb ext3 + 1gb swap).

Does 10gb sound about right for Linux? What happens if I want to install in add on and I don't have enough room for it (how would I install the add on to another partition)?.

I'm a little insecure about resizing my partitions because of what might happen if it fails. Anything I should know before hand?

---

### Post by caljohnsmith on 2008-11-21
Just curiouis, but is your second drive really just 400 MB, or did you mean 400 GB? But to answer your question, I think 10 GB for Ubuntu will work just fine unless you use a lot of that space for your personal files. Also, there shouldn't be any problem using Ubuntu's partition editor to make the partition changes, but it is always recommended to have everything important backed up just in case something goes wrong. It is possible to increase the size of Ubuntu's partition at some later time (assuming you have the drive space), but I would avoid it if you can; the "UUID" for the partition will change, and you'll have to modify some of your system files to get things working again. So it's better to try and give Ubuntu ample space to begin with. Also, in case you would like a little help with the installation process, I would recommend checking out this tutorial:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Let us know if you have any more questions. :)

---

### Post by qpieus on 2008-11-21
> **Edward850 said:**
> Does 10gb sound about right for Linux? 
Hello and welcome. I see caljohnsmith just said pretty much what I'm about to say...

10 GB is adequate for a linux installation. By that I mean it's enough room for the base OS installation plus plenty of room for extra applications you might want to install. The potential problem would be that over time, your personal data will grow such that you'll need more than 10 Gb total. This is easily addressed though - all you have to do is put your personal data (your /home directory, that is) on another partition.
Take my setup for example. I have a 6 GB partition that my OS resides on (the  root partition, it's called). Of that 6 GB, 3 Gb is used. I put my /home directory (personal data) on a separate partition that is much bigger so I have lots of room to save music, videos, whatever. Of course, you don't have to put your home directory on a separate partition. But if you stick with the 10 gb total for linux and your personal data, I think eventually you'll run out of room due to the growth of your personal data.

As far a resizing partitions, the usual advice is backup whatever data you don't want to lose in case the operation goes bad (although I've never had any problems when resizing).

---

### Post by Bucky Ball on 2008-11-21
> **qpieus said:**
> The potential problem would be that over time, your personal data will grow such that you'll need more than 10 Gb total. This is easily addressed though - all you have to do is put your personal data (your /home directory, that is) on another partition.

... And so say all of us! My personal rule of thumb? *Never *keep your personal data on the same partition as your OS and apps. A kind of Windoze hangover, but it has its advantages and most of them have to do with data security. When you want to reinstall the operating system (or have to after you've totally broken it by experimentation or intent!), you just kill the partition and start again, no need to fish out all the valuable bits. One other advantage is hardware related - if the drive crashes, it is usually one bad sector! Therefore, if you are lucky and that is on the OS partition, you can still access your other partitions with a bit of effort.

Speed of data access was another thing with Windoze as it would throw stuff everywhere and need to be defragged; in that instance, 6gb of OS and Apps on a 10Gb partition is going to be faster than 6gb of OS and apps on a 120Gb partition. Think about it. To retrieve a piece of data on the former you only have to reach into the cupboard, on the latter you have to go to the shop to get it! :)

Again, these things are mostly a safeguard against all eventualities with Windoze (ie virus, random crash, blue screen) but I have continued using the same concepts. Old habits die hard.

---

### Post by qpieus on 2008-11-21
Well said Bucky. I agree, I always have /home on a separate partition. It makes it so much easier to install a new version or another distro.

---

