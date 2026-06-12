---
title: "Duel Boot TROUBLE.  XP Pro with Ubuntu 5.10."
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by ubuntuforums on 2006-02-06
Hey guys. I just downloaded the i386 ISO for Ubuntu 5.10 and I want to make it duel boot on my XP Professional system. Anyway I figured it would be easy, so I opened up Partition Magic, resized my XP partition and put aside 10gb for Ubuntu. I poped in my burnt cd with the iso of ubuntu 5.10 and restarted my computer. Then the computer automatically booted to CD and I chose my language, keyboard setup, and I let it automatically partition the free space. Then I let it install, after a minute or two the screen turned red and I got an error, so I clicked continue to try again, this time the screen turned read again and gave me the selection of three kernals, something like,, ubuntu i386, ubuntu image i386, and ubuntu image 2.1 something... So I chose the first kernal and it gave me an error after just a little bit, so then I did it over again,, and so on till I tried all three kernals, still got an error.

So I said whatever, restarted my computer and removed the cd. Then it checks for boot record from CD drive, then the the IDE hardrive, after the hard drive it says "...OK" then nothing, so I started to set up windows on the partition I made for Ubuntu, but when it restarted it showed BOTH OSes so I selected my old one and i booted right in. So its fine now I guess, but I dont know why Ubuntu wouldn't installl... Please help, thank you...

Specs for the sysytem im installing ubuntu on...
Intel Celeron 1.7GHz
768MBs of ram
Radeon 9600XT 256DDR
SoundBlaster Live! 24-bit 7.1
300W PSU...
40GB Maxtor hard disk driver...
LG 12x 8x 32x Recordable/Rewritable disk drive...

i think thats it for that system,,,

All help/comments are appreciated,, THANKS... I want to install Ubuntu asap.

---

### Post by Robgould on 2006-02-06
You need to check your .iso....sounds corrupted.  Bott from windows install cd.  Got to rescue panel or resotre panel..can't remembe now.  Run fixmbr to repaig your master boot record.  Delete your Ubuntu partition with partition magic.  Re-download the .iso and try again.  Make sure you are downloading the right .iso for your system (386).  Hope this helps.

---

