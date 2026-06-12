---
title: "What sizes should my partitions be?"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by jimmyboy09 on 2009-02-03
Hi there.  

I am about to set up a dual boot with XP and was wondering if any experienced ubuntu users could give me a "quote" on how big I should make each of my partitions (swap, /home, /, etc).

My hard drive capacity is 149 gb.  Does it make a difference if I want to leave about half of it for XP and my files?  I have 2 gb of RAM.

Thanks in advance.

---

### Post by Powerman2442 on 2009-02-03
> **jimmyboy09 said:**
> Hi there.  

I am about to set up a dual boot with XP and was wondering if any experienced ubuntu users could give me a "quote" on how big I should make each of my partitions (swap, /home, /, etc).

My hard drive capacity is 149 gb.  Does it make a difference if I want to leave about half of it for XP and my files?  I have 2 gb of RAM.

Thanks in advance.

In my opinion it is up to you to reserve how much space you want for Ubuntu. When I dual booted Vista/Ubuntu on my laptop I had a 120 GB hard drive that had about 100 GB free. I resized the 100 GB partition to about 69, giving me 31 GB to work with for Ubuntu. Since Vista was my main OS I used it to store music, documents, videos, games etc. I wanted it to have a fairly large partition, compared to Ubuntu.

With the 31 GB left I used a LiveCD to insall Ubuntu and designated 1 GB for swap and let the installer determine how large my /, and /home should be. 

They say you should reserve double your physical memory for swap. So if you have 2 GB of RAM aka. 2048 MB you should reserve 4096 MB for swap. Personally I think this rule of thumb should really only stand for computers with low memory or people who know they are going to use RAM intensive programs. I had 2 GB of RAM in my laptop and Ubuntu never came close to touchy it. I decided to reserve 2048 MB for the swap though. It was pretty much a waste of my hard drive in my opinion.

I also had my Vista partition set to automount on start-up so I could access all my music and videos from Ubuntu without needing to save it twice, which saves a ton of room on your Ubuntu partition for other things. I also had a file on my Windows partition named "Ubuntu" that I used to save files from Ubuntu onto my HDD without touching my space on my Ubuntu partition.

Guess it depends on what you plan on doing with it. Are you going to play solitare, send e-mails, instant messages, and browse with Firefox? If so your swap definitely doesn't need to be over 2048 MB of RAM, unless something has changed in Ibex (I haven't got a chance to use Ibex yet). Maybe if you pan to use more RAM intensive apps you would need more. I'm pretty sure you can always resize your Ubuntu partition and swap using gparted. Like I tell everyone I am a Ubuntu/linux newbie myself. Most of the info I give comes from what I have done and had work for me.

Good luck,

---

### Post by jimmyboy09 on 2009-02-03
Great great info.  Thanks powerman.  I guess it's not that I plan on running memory intensive apps.  I just thought that if I were to ever do this, I might as well do it at install and "get it over with".

---

### Post by Powerman2442 on 2009-02-03
> **jimmyboy09 said:**
> Great great info.  Thanks powerman.  I guess it's not that I plan on running memory intensive apps.  I just thought that if I were to ever do this, I might as well do it at install and "get it over with".

I've heard people say running OpenOffice can push you over and into swap, but I ran it on my laptop and I had 2 GB of RAM and I never had a problem. In fact I went through and opened every program that came with Ubuntu 7.04 when I first got it running and my RAM usage never did max out, according to the Hardware Monitor built into Ubuntu.

---

