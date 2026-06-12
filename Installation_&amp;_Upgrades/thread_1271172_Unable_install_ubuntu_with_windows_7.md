---
title: "Unable install ubuntu with windows 7"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by gigaforce1111 on 2009-09-20
Hi all,
I decided installing Ubuntu when Win 7 running on my machine, and I have some problems:
BTW I have Dell Studio 1555 with Intel graphic card.
my machine has 1 physical disk with 2 main partitions:
C: Windows 7 partition- 80GB
D: Storage partition- 220GB
While Installing Windows 7 a System Reserved Partition was made- 100MB
Another Partition, an OEM one- 40MB

I want to install Ubuntu on D.

I started installing after fragmentation under Manual Partitioning and New Partition was disabled (grey) when choosing the D partition. 
[IMG]http://img41.imageshack.us/img41/5384/20092009241.jpg[/IMG]
I decided creating partition dedicated to Ubuntu from the Win 7 Partitioning tool, and it all (C,D,System Reserved) turned from Primary Volume to Simple Volume. and from Basic to Dynamic.
[IMG]http://img17.imageshack.us/img17/5720/picture1tx.png[/IMG]
If you think that harm is done please tell me.

Now the D Partition is listed as unusable in the Ubuntu Install process.

Please help!
I want to install Ubuntu!

---

### Post by WatTwo on 2009-09-20
I was having almost the same problems, (windows 7 also)

So i just did a wubi install.

It's alot safer and more simple.

---

### Post by gigaforce1111 on 2009-09-20
> **WatTwo said:**
> I was having almost the same problems, (windows 7 also)

So i just did a wubi install.

It's alot safer and more simple.
Hi,
Thanks for the reply.

I used Wubi in the past and Ubuntu users used to say it runs slower in generally.
I want a real dual-boot machine and still looking for an answer.
Please help.

---

### Post by gigaforce1111 on 2009-09-21
Hi all,
Is it because of the 4 partitions limit on one hard drive?
Please reply!

---

### Post by presence1960 on 2009-09-21
> **gigaforce1111 said:**
> Hi all,
Is it because of the 4 partitions limit on one hard drive?
Please reply!

Bingo! You need to back up the D: partition and then in gparted delete that partition. Then create an extended partition with all that free space. Within that extended partition you can create as many logical partitions as space allows. Unlike Windows , Linux will boot from a logical partition with no acrobatics required.

---

### Post by presence1960 on 2009-09-21
> **WatTwo said:**
> I was having almost the same problems, (windows 7 also)

So i just did a wubi install.

It's alot safer and more simple.

Really no safer than a regular install, wubi installs mess up sometimes too, just search these forums. Wubi is not meant to be a permanent install- it is a temporary test drive for those who want to try Ubuntu without committing to partitioning their hard disk yet. See here:

[http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

The key word is **"try".** Wubi is meant to be used to try ubuntu before partitioning your disk in case you don't like Ubuntu. Since Ubuntu is a file in the Windows filesystem when using wubi it is subject to performance degradation due to windows filesystem fragmentation. To use Ubuntu with full speed and effects it is best to partition your disk and do a full install, whether that be from jumpstreet or after "trying" ubuntu with wubi.

---

### Post by NovoW5 on 2009-09-21
Since we're on the topic...does anyone know if I  will be able to dual boot Windows 7 using Gparted on Ubuntu 9.04 as my main OS? (Ubuntu is my main and only OS at the moment just for clarification)

---

### Post by NovoW5 on 2009-09-21
side note*, i would have partitioned the C: Drive after W7 was already on it since it was your only OS. C: should have had the bulk of your HDD space, and then partitioning that and installing ubuntu on the partitioned section would work, i don't know how you got D to be 200GB. is that an external drive? did you have another OS on there before W7 and partitioned 80GB for W7 install and cleaned off the other os leaving that extra 200GB?

---

