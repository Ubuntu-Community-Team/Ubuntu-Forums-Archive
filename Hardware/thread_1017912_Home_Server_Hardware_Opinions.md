---
title: "Home Server Hardware Opinions"
date: 2008-12-21
forum: Hardware
---

### Post by Stant0n on 2008-12-21
I've tasked myself with building a home server that will perform many various functions,  including: MythTV, Bittorrent tracker, backup system, FTP server, etc. I'm looking for hardware recommendations from some experienced linux users.

I've decided on using the Xen Hypervisor with Ubuntu Dom0 to host multiple OS instances so that I can keep a maximum level of segregation between my personal data and remotely accessible data.

I already have a Zalman case (pretty), 
Highpoint Rocketraid 1740 (RAID5 and open source drivers), 
Seagate 1TB Drives x4 (3TB of storage in RAID5 )

I'm looking to purchase: 
processor, 
motherboard, 
video card, 
powersupply, 
RAM,
video capture card

According to Intel's marketing documentation,  there's around a 30% performance increase on using server virtualization on a platform that supports IOMMU, (vPro). Which is defacto standard in the new i7 chipsets as far as I know.  
I also haven't checked in a while, but last I recall ATI/AMD video cards have very limited linux support compared to nVidia. Is this still the case? What about overscan resizing for my HDTV?
And as for video capture cards,  I'm really at a loss to which would be best to use.  There's decent support for the Hauppauge cards isnt there?

Currently I'm thinking of these specifics:
Intel Core i7 920 (quad core, affordable)
Intel BOXDX58SO  (IOMMU support, PCI for raid controller)
2GB DDR3 1600 x3 (triple channel support)
Enermax PSU (high quality and quiet)
GeForce 9500 (passive cooling, DVI out)
Hauppauge WinTV-HVR-2250 (inexpenssive)


Notes:
I will not buy an MSI product ever again, please don't recommend them to me.
I'm located in the USA so I need an NTSC compliant video capture card.
If you think I'm approaching this all wrong, please let me know how you'd do it and why.

Thanks for your time.

---

### Post by Stant0n on 2008-12-23
Is there perhaps a different forum I should post this in?

---

### Post by iggykoopa on 2008-12-23
Honestly your going way overkill with that hardware, I have an amd phenom 2.2 ghz and I'm running Mythtv, Squid, Bind, LTSP(hardly ever use it), virtualbox with an xp instance in it, and various other things. The only time my cpu usage goes over 20-30% is if I'm encoding videos and the system is still quick even then.

---

### Post by Stant0n on 2008-12-23
So I shouldn't ignore Core 2 Duo options because they should be just as viable? 
Thanks for the reply.

What video capture card are you using?

---

### Post by iggykoopa on 2008-12-23
I was initially using a pinnacle dvb-tuner to get ota broadcasts, then was using firewire from my comcast digital box. I didn't end up really liking either option because the channel listings weren't vary accurate. Now I just rip my movies from dvd and watch tv series on hulu.

---

### Post by Stant0n on 2008-12-23
I've also got a Comcast box with a firewire out.  You think I could forgo the tuner card and use the box for capture?

---

### Post by iggykoopa on 2008-12-23
you can but there are definate problems with doing it that way. Comcast encrypts some channels all the time and some channels for certain shows. There's no way of knowing beforehand which shows will be encrypted except trial and error. If you tune into an encrypted channel it will lock the connection (you just get a black screen) and can't unlock it until you reset the connection. So say you schedule 5 shows to record, the second is encrypted, the rest will just show up as black. So it's probably worth the investment in the tuner card, you just wont be able to tune in HD channels(you need to connect to the digital box for the HD channels).

---

### Post by Stant0n on 2008-12-23
I don't yet have any experience with MythTv,  but wouldn't it be possible to program in connection resets after each program to ensure that an encrypted channel not ruin the rest of your recording?

Also, I'm assuming that a video capture card wouldn't be able to decrypt encrypted channels either.  Is this the case?  Is there any way to DVR the encrypted broadcasts?

---

### Post by iggykoopa on 2008-12-23
The encrypted channels arent a problem with the tv tuner card because the box decrypts them and puts them back out over the cable, you only need one digital box and you can watch the standard channels with a tv hooked up to the regular cable outlet, it works the same way with the tuner card.
There is a script to reset the connection, but I was never able to figure out a way to detect automatically when you've tuned into an encrypted channel, maybe someone has figured out a workaround by now. I tried it about 7 months ago.

---

### Post by Stant0n on 2008-12-23
Thanks for your replies so far, I really appreciate it.

Do you use an LCD TV?  I've had problems with overscanning on mine from my windows PC and the nVidia drivers had a hack to resize the desktop.  Do you know if there's similar support for nVidia or ATI/AMD cards for overscan?

---

### Post by iggykoopa on 2008-12-23
I was having similar problems at first, at the time nvidia didn't have an overscan option but they were working on it. I went through my tv's options more and set the stretch setting to pixel for pixel or something like that(maybe direct can't remember, it's an aquos) and that fixed the problem. If you absolutely can't find a fix you can actually adjust it in mythtv so the mythtv window displays in your viewable area.

---

