---
title: "Which is my bottleneck? Ubuntu runs, but slowly"
date: 2013-03-28
forum: Hardware
---

### Post by kyalami321 on 2013-03-28
Hi all, 

first post on the forums. Just installed Ubuntu 12.04 and loving it. I used an older HP small form factor PC as the target system, and I know one of the following is causing Ubuntu to run quite slowly. Which should I upgrade?

RAM: 512MB DDR PC2700 (333MHz) running in Dual-Channel, installed as four 128MB sticks
GRAPHICS: nVidia Geforce 6200 PCI (256MB RAM, 64-bit) (computer also has an empty low-profile 1.5V AGP slot)
HDD: 80GB IDE Hitachi Deskstar (ATA100), computer can take SATA (dunno if SATA-I or SATA-II).

Ubuntu was installed as the single operating system (using entire drive). Using Ubuntu 2D during my session.

Thanks!

---

### Post by carl4926 on 2013-03-28
If you can upgrade the RAM - do
And I suggest using Xubuntu

---

### Post by kyalami321 on 2013-03-28
figured, gonna buy some 1GB sticks, hopefully get it up to the max (4GB). what about the hard drive? is it too slow?

---

### Post by carl4926 on 2013-03-28
> **kyalami321 said:**
> figured, gonna buy some 1GB sticks, hopefully get it up to the max (4GB). what about the hard drive? is it too slow?

Really it's not going to matter about the HD

---

### Post by kcc12 on 2013-03-28
If your hard drive is close to full, that could be slowing it down. If you're only using a fraction of the space, though, then it's not the bottleneck, your RAM is. And like car4926 suggested, Xubuntu or Lubuntu would be good options - I had an old laptop with similar specs that was slow and clunky with Ubuntu/Unity desktop but now runs like new using Lubuntu.

---

### Post by sanderj on 2013-03-28
> **kyalami321 said:**
> Hi all, 

first post on the forums. Just installed Ubuntu 12.04 and loving it. I used an older HP small form factor PC as the target system, and I know one of the following is causing Ubuntu to run quite slowly. Which should I upgrade?

RAM: 512MB DDR PC2700 (333MHz) running in Dual-Channel, installed as four 128MB sticks
GRAPHICS: nVidia Geforce 6200 PCI (256MB RAM, 64-bit) (computer also has an empty low-profile 1.5V AGP slot)
HDD: 80GB IDE Hitachi Deskstar (ATA100), computer can take SATA (dunno if SATA-I or SATA-II).

Ubuntu was installed as the single operating system (using entire drive). Using Ubuntu 2D during my session.

Thanks!

... what's the CPU?

---

### Post by sudodus on 2013-03-28
> **sanderj said:**
> ... what's the CPU?
+1

I agree with *carl*'s suggestion about RAM and desktop environment (Lubuntu or Xubuntu). But to give more accurate advice we need information about the CPU too.

With at least 1 GB of RAM, you can try the flavour of Ubuntu and install afterwards from a live desktop iso file (via CD/DVD/USB). This way you know before installation. You can also install the corresponding desktops into your existing Ubuntu, and select which one to run at the login screen (as you probably selected Ubuntu 2D).

```
sudo apt-get install lubuntu-desktop
```
```
sudo apt-get install xubuntu-desktop
```

You can keep all desktop environments, but if you want to settle with one of the desktop environments you can delete the others according to this link

[[COLOR=#ff0000]http://www.psychocats.net/ubuntu/[/COLOR]]("http://www.psychocats.net/ubuntu/")

---

### Post by mörgæs on 2013-03-28
Normally the CPU does not matter much. If you manage to find a spare that fits into the socket it will only speed up the system a little bit, as memory is still the main constraint. 

Lubuntu 12.10 and/or more memory is the way to go.

---

### Post by sanderj on 2013-03-28
> **mörgæs said:**
> Normally the CPU does not matter much.

So a 10-year old Pentium versus a current quad core i5 does not matter much? :confused:

---

### Post by carl4926 on 2013-03-28
It the realms of what possible upgrade could me made, probably not. And I'm sure that's what @[COLOR=#000000]mörgæs would be thinking[/COLOR]

---

### Post by mörgæs on 2013-03-28
@sanderj:

Correct, as the user can not change them (to anything significantly different). 

Operative system and memory can be changed, and it gives a massive improvement.

---

### Post by sudodus on 2013-03-28
> **carl4926 said:**
> It the realms of what possible upgrade could me made, probably not. And I'm sure that's what @[COLOR=#000000]mörgæs would be thinking[/COLOR]

This is correct, but the advice concerning flavour of Ubuntu might differ depending of the CPU.

---

### Post by mörgæs on 2013-03-28
No. We already know that the computer is from the age where memory came in 128 MB sticks. Lubuntu 12.10 FTW.

The CPU is likely to be a Pentium 4 or something in that neighbourhood.

---

### Post by Enoch247 on 2013-05-03
I have an older single core desktop machine that is maxed out at 2GB of memory. the thing ran great with ubuntu 11.10. I upgraded to 12.04 and it ran painfully slow. I noticed that starting with 12.04 it was making use of swap space for the first time that I had ever noticed. since I couldn't upgrade the memory any more I tried throwing in a cheap SSD I found on newegg. as far as everday usage (browsing the web and checking email) I can't percive any deffernce between this junker and the quad core 8GB modern machine I have at work (also running ubuntu 12.04)

edit: I should also add that I use Unity 2D on both machines, and it is just as responsive on both machines. so you don't have to give up Unity if you like it just because you machine is not the latest/greatest (in my opinion).

---

### Post by kyalami321 on 2013-05-04
@enoch247 so hdd could be a big factor? my ubuntu currently accesses the HDD like crazy, but less so than when it had a pentium 4 with a 533MHz FSB. now it has one with an 800MHz FSB, about 3GHz

---

### Post by Yellow Pasque on 2013-05-04
> my ubuntu currently accesses the HDD like crazy
Did you ever add more RAM or still stuck on 512MB? So you upgraded the CPU? Your thread's kind of hard to follow with these information gaps...

---

