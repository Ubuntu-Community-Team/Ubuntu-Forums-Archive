---
title: "Gparted"
date: 2010-11-10
forum: Hardware
---

### Post by Dark Shinobi on 2010-11-10
Hello everyone! I am a complete newbie when it comes to all things linux, having just installed ubuntu 10.04 on my laptop from wubi. Having loved it so much, I gave it its own partition and moved it over to a ext4 extended partition with a swap drive. So now Im thinking about completely removing windows and running linux exlusively on my laptop. The problem I am having is moving my data. I am low on space here, so I moved some data then used gparted to change my windows drive size and gave unallocated space to resize my ubuntu partition. Now, Gparted wont let me resize my ubuntu drive, probably because either the linux had to go on an extended partition and the unallocated space is on the primary, or because it is before my linux partition. I have included a screenshot of my partition as reported by Gparted. Any suggestions to be able to resize my Ubuntu partition would be most appreciated :)

---

### Post by Elfy on 2010-11-10
Do you get the same issue if you are using a livecd - you need to have the ubuntu partition unmounted to work on it.

Try with a livecd - also you will likely need to right click and swap off /dev/sda6.

---

### Post by Dark Shinobi on 2010-11-10
Yes I'm using the live cd, only booted back up to post this and to take the screenshot, but I didnt try to swapoff sda6, Ill reboot and give it a try.

---

### Post by Dark Shinobi on 2010-11-10
Well swap was already off in the live cd, it only gave me the option for swapon. Any other suggestions? Still wouldn't let me resize it :(

---

### Post by Yellow Pasque on 2010-11-10
It's not going to let you resize it because it's extended. You may be able to do it if you first resize the extended part (sda4), but I'm not sure if it's possible.

---

### Post by garvinrick4 on 2010-11-10
I got a question here, I know Dell calls its Utility partition a Hidden partition in Windows but being sda1 would that not be a primary? If so I count 4 primarys, if not being sda1 in a partition why is it not a primary?

---

### Post by Yellow Pasque on 2010-11-10
sda1 is a primary partition (as are sda2 and sda3). That's three primaries and an extended (which is valid).

---

### Post by garvinrick4 on 2010-11-10
> **Temüjin said:**
> sda1 is a primary partition (as are sda2 and sda3). That's three primaries and an extended (which is valid). Oh, I see what he is trying to do, increase and extended which you cannot do and he has got 4 primarys so he ended up with dead space for linux just able to increase size of sda3. DUHH, takes me a while sometimes.

---

### Post by Dark Shinobi on 2010-11-10
Yeah unfortulately with that damn dell utilities, the recovery partition, and windows, I had no choice but to create an extended partition to put a real OS in. And actually, it did let me do it. I had to right click on the /dev/sda4 itself and click on move/resize instead of the partition linux was on itself. So problem is solved for now, at least until I decide to do away with windows all together. Thank you for helping me sip a little bit more from my first cup of ubuntu :)

---

### Post by Elfy on 2010-11-11
> **garvinrick4 said:**
> ... increase and extended which you cannot do ...You can resize extended partitions 

> **Dark Shinobi said:**
> Yeah unfortulately with that damn dell utilities, the recovery partition, and windows, I had no choice but to create an extended partition to put a real OS in. And actually, it did let me do it. I had to right click on the /dev/sda4 itself and click on move/resize instead of the partition linux was on itself. So problem is solved for now, at least until I decide to do away with windows all together. Thank you for helping me sip a little bit more from my first cup of ubuntu :)Yep - for anyone else turning up here - before you can resize logicals inside an extended - resize the extended so the unallocated space is inside then it will be available for the logicals

---

### Post by garvinrick4 on 2010-11-12
That is nice to know, I thought I was stuck with what my partition scheme I had.
Now moving my Extended to left will it have to move everyone of my partitions left
to make  space on right end of Extended partiition or will it just give me
space on the left of Extended? Will be worth it if get unallocated on left
of my extended, to much info to move if it has to move everything to the left
do not want to risk moving all the partitions in one command. 
This as a given I make room by resizing sda2 to make unallocated space.

---

### Post by garvinrick4 on 2010-11-12
Thank you forestpiskie for repairing thread.

---

### Post by Dark Shinobi on 2010-11-17
Unfortunately for me it was stuck on the left and the whole file system had to be moved to the left to extend it. But overall it was maybe an hour and Gparted handled it just fine.

---

