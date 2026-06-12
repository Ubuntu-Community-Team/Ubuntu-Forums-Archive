---
title: "Multi-boot system"
date: 2008-07-30
forum: Hardware
---

### Post by ajfisherman on 2008-07-30
Hi all I wanted to partition my 40 Harddrive in my laptop.  THrer will be a variety of operating systems running and I have a few questions.
1.  How can I partition my harddrive like this (Im using Damn small Linux):
[Minix-5gig                       ]
[Ubuntu*-7gig                     ]
[TinyXP-10gig                     ]
[MicroXP-5gig                     ]
[Windows98-3gig                   ]
[DSL-3gig                         ]
[Fat partition to swap files-5gig ]
[Linux swap-1gig                  ] 
*Ubuntu will use openbox
2. How to set up grub to haldle all of them
3. Is it possible to put all the windows together on a partition and safly boot them?  Could I do the same with dsl & ubuntu?
ANY help would be appreciated.

---

### Post by ElephantGun on 2008-07-30
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

These guys make a bootloader called EasyBSD. It's based on the Vista bootloader, but you can run it on XP. Just run it on one of your XP installs and it should work okay.

Since each OS is seperate, unless you're going to be using a virtual machine to run some of them, you'll need a partition for each and every one of them (to the extent of my knowledge). 

The main problem I see is that since there's more than one version of windows that isn't vista, you'll have to do some BOOT.INI configuring. (EasyBSD boots based on OS type, there's a few articles in their wiki about this.)

I don't know if GRUB works any differently from EasyBSD, so really, I know almost nothing about it at all. 

I think the best solution here is definitely using virtual machines. Since you have so many OS's, you'd be wasting more time booting them up than configuring VMware.

(I'll bet that didn't help much. :()

---

### Post by markbuntu on 2008-07-30
You can avoid a lot of problems by using the chainload option in grub. It will switch entirely to whatever boot scheme you have on another partition or drive. Read here:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ajfisherman on 2008-07-31
> **ElephantGun said:**
> 

I think the best solution here is definitely using virtual machines. Since you have so many OS's, you'd be wasting more time booting them up than configuring VMware.

(I'll bet that didn't help much. :()

The laptop is a Dell Latitude CP M166ST(i think) 96 MB of ram and a 144 MHZ MMX Proc.  It has a 40gb had to offset the rest.  When I bought it it came with a 3gig hd.
So VMs are out of the question.

---

### Post by ElephantGun on 2008-07-31
Based on that laptop's specs, I'm not sure it can run all of those OS's. I thought XP needed 233 MHz to run? Could be wrong, though.

---

### Post by ajfisherman on 2008-07-31
Using tiny & micro xp wich require less specs than the full editions.

---

### Post by ajfisherman on 2008-08-04
Ok i got it figured out i used slax to partition it.  and used dd to move oses after they were installed.

---

