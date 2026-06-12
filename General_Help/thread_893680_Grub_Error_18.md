---
title: "Grub Error 18"
date: 2008-08-18
forum: General Help
---

### Post by Twizzle on 2008-08-18
I have been paying with Ubuntu 8.04 server edition for a while and have been setting up Zoneminder. Yesterday I had just finished getting everything set up as I wanted it, and powered down the server.

Today, I booted it up and everything was fine. I powered it back down and left it for around an hour.

When I came back to it, I powered it up but got as far as:

```
Searching for Boot Record from IDE-0..OK
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18
```

Having looked on the web, I am aware that Error 18 is:

> Error 18: Selected cylinder exceeds maximum supported by BIOS

The thing is, I have changed nothing on my system. 

Can I assume from this that my HDD has died / is dying?

Is there any way I can recover my system.

Luckily, there is nothing valuable on the drive. It was an unused (not too old) Seagate 160Gb that I was using to get to grips with the server edition.

The ultimate plan is to get a RAID card and mirror everything...

But back to my GRUB problem... Any suggestions?

---

### Post by fjgaude on 2008-08-18
If you have booted several times with the same result, you might try making sure the menu.lst file points to the correct drive to boot.

---

### Post by caljohnsmith on 2008-08-18
Definitely sounds suspicously like a hardware problem, but you can try the following to fix grub:
[LIST]
[*]First boot up a Live CD
[*]Open a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][this should return your Ubuntu partition in the form (hdX,Y)][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
[/LIST]

---

### Post by Twizzle on 2008-08-19
Hmmm. Im guessing:

```
Error 15: File not found
```

Is not a good sign after running:

```
find /boot/grub/stage1
```

Is there any way I could have accidentally deleted something or is my hdd buggered!

It was chundering away for some time when looking for stage1.

---

### Post by caljohnsmith on 2008-08-19
Definitely sounds like a hardware problem to me based on what you've said so far, Twizzle. Can you check your HDD cables and make sure they are secure? Also, try booting up a Live CD and doing the following in a terminal:
```
sudo fdisk -lu
```
Please post the output. Can you mount your Ubuntu partition and look at files? Also, you could try running "testdisk" from the Live CD to check how it sees your partitioning structure as compared to fdisk. You might have to install it first:
```
sudo apt-get install testdisk
```
And then run it with
```
sudo testdisk
```

---

### Post by Twizzle on 2008-08-19
Thanks for he suggestions. I am currently running a full scan using the Seagate SeaTools disk and so far it is onlt 41% done and has taken about two hours!

So far I have seen error code 40h and error code 10h (not sure what they mean really - in the middle of googling lots!)

There are also a whole load of:

```
Found bad sector: <number>
```

errors.

Its not looking good for my disk!

I get the gist of the Seatools errors, so I will reboot into Live CD and try as you suggested.


*Edit* - Oh and the cables are fine. I have removed and re plugged and tried a new cable. I only have the one HDD attached and have only just added a CDRom to do all the tests. It is very basic no frills server.

---

### Post by Twizzle on 2008-08-19
OK, I had split the drive into three 60Gb, 60Gb, and 39Gb (1Gb Swap). If I remember rightly it was 39Gb for '/' , 60Gb for '/home' and 60Gb for '/var'

So far I can browse my two 60Gb partition but not the 39Gb partition.

```
sudo fdisk -lu
```

shows me my partition table as above and has a star in the /dev/sda1 boot bit (my 39Gb partition). There are no errors  or apparent problems I can see. (I can't cut and paste - different machine!)

Testdisk starts and gives me a load of options. It seems to show my partition table and says structure ok.

Two of the partitions (when you select them) say:

```
EXT3 Lage file Sparse superblock Recover, 60 GB / 55 GiB (or 38GB / 36GiB
```

and the other says nothing about 'Recover'.

---

### Post by caljohnsmith on 2008-08-19
> **Twizzle said:**
> There are also a whole load of:

```
Found bad sector: <number>
```

I think that about says it all--if your HDD has a whole bunch of bad sectors, I would invest in a new one at this point if I were you. ;)

---

### Post by Twizzle on 2008-08-20
Thanks for your help and suggestions - off to the shop now I guess!

Before I do though, I have read about zeroing the drive if the bad sectors were caused by a software problem - As there are so many bad sectors, is it worth me doing this? How can I tell (without reinstalling and waiting for it to crash again) if zeroing is going to work for me?

---

### Post by caljohnsmith on 2008-08-20
> **Twizzle said:**
> Thanks for your help and suggestions - off to the shop now I guess!

Before I do though, I have read about zeroing the drive if the bad sectors were caused by a software problem - As there are so many bad sectors, is it worth me doing this? How can I tell (without reinstalling and waiting for it to crash again) if zeroing is going to work for me?
How about posting the output of the following command:
```
sudo smartctl -a /dev/sda
```
That will report info about your HDD's health, and also what capabilities it has. How old is your HDD? At this point, since that HDD is not usable anyway, I suppose you don't have anything to lose by doing a "low-level format" on it to zero the HDD, and running your HDD's diagnostic tests on it again; but I'm not sure it will help. But do you have a backup somewhere of your important files? If not you can probably still mount your Ubuntu partition from a Live CD and copy files off of it.

---

### Post by Twizzle on 2008-08-20
I tried to do a low-level format and it sat at 0% for about two hours. I guess that says it all.

Thanks again for the help and suggestions though.

---

