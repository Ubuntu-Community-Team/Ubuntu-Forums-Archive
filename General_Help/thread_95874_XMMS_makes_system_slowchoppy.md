---
title: "XMMS makes system slow/choppy"
date: 2005-11-27
forum: General Help
---

### Post by etlatino on 2005-11-27
Hello, Happy Thanksgiving

  I am new to ubuntu and linux, I just installed XMS to play my mp3s.  While playing my mp3s my mouse movements get choppy and overall desktop performance slows down.

I am running a 2.6 p4, with 1gig ram, raptor harddrive is where the mp3s are stored but the format is ntfs.

any suggestions or better programs?

---

### Post by Perfect Storm on 2005-11-27
Could it be that you havn't setup the 3D acceleration for your grapgic card? Just a shot...

---

### Post by angrykeyboarder on 2005-11-27
[quote=etlatino]Hello, Happy Thanksgiving

 I am new to ubuntu and linux, I just installed XMS to play my mp3s. While playing my mp3s my mouse movements get choppy and overall desktop performance slows down.

I am running a 2.6 p4, with 1gig ram, raptor harddrive is where the mp3s are stored but the format is ntfs.

any suggestions or better programs?[/quote]

XMMS is dated anyway.  Use BMP instead.

Better yet, a media player you can acutally see. ;-)

---

### Post by etlatino on 2005-11-27
how do i set up my graphics card 3d acceleration?

---

### Post by Perfect Storm on 2005-11-27
Which card do you have?

This might help: [http://doc.gwos.org/index.php/3D_Graphic_Cards](http://doc.gwos.org/index.php/3D_Graphic_Cards)

---

### Post by o_fortuna on 2005-11-27
> I am new to ubuntu and linux, I just installed XMS to play my mp3s. While playing my mp3s my mouse movements get choppy and overall desktop performance slows down.

Actually, I had a similar problem with XMMS. After playing several files fo a while, I noticed that my computer slowed down a lot. I checked the system monitor (Applications --> System Tools --> System Monitor, look for XMMS), and it turned out that XMMS was using tons of memory. I restarted the program, and I noticed that every time I started playing a new file, the memory usage increased :mad:! You might want to see if you're having the same problem.

If you are, then I'd say, unless you want to restart XMMS every time you want to play a new file, try installing beep-media-player from synaptic. I've never had any problems with it.

---

### Post by etlatino on 2005-11-27
Thanks a lot, I installed the 3D driver you suggested and I see an overall system performance increase.  Thanks

---

### Post by Perfect Storm on 2005-11-29
You might also install the right kernel for your Pentium.

```

sudo apt-get install linux-686

```

reboot.

---

