---
title: "how to install Vista back"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by ychakarov on 2009-03-24
HI there. 
The problem I have is that i did erase my Vista by mistake when I was instaling Linux and I do want it back because of my wife. She cant work with Ubuntu. I cant install it back cause can not make the hard disk NTFS
when I go to partition editor in Ubuntu does not work

---

### Post by KCG102282 on 2009-03-24
All you have to do is make sure your bios is to to boot your dvd/cd drive first and incert your ista disk and install over it.

---

### Post by oozehead on 2009-03-24
yup

just boot from the dvd/cd  and follow the installation process and ull have vista back :)

---

### Post by ychakarov on 2009-03-24
i do want to keep ubuntu as well for me

---

### Post by ychakarov on 2009-03-24
it says can not install windows because only installs it on NTFS and can not recognize the file sistem

---

### Post by Mark Phelps on 2009-03-24
You're asking for different things each time ...

If you want to "keep" Ubuntu, then you're talking about a dual-boot installation.  In that case, download and burn a GParted Live CD (you can find a link at distrowatch.com), boot from that CD, shrink the Ubuntu partition and move it to the right -- creating unpartitioned space to install Vista.  When you install Vista, it will overwrite the MBR, and you will then need to reinstall GRUB to boot back into Ubuntu.

If you only want to be able to "use" Ubuntu, do the same with a GParted LiveCD but erase your whole drive, install Vista on part of it, and then install Ubuntu on the remainder.  Ubuntu will find Vista and automatically add it to its boot menu.

---

### Post by bruno9779 on 2009-03-24
It is kind of shameless to ask on Ubuntu forums how to re-install Fista

---

### Post by mhgsys on 2009-03-24
> 
bruno9779  	
Re: how to install Vista back
It is kind of shameless to ask on Ubuntu forums how to re-install Fista 


I agree. 

But still, 

You can use the live cd of Ubuntu to delete your partitions, and make it all free space again, 
that way vista can read it again, 

for a dual boot follow the post from Mark. 

Personally I think your wife should learn to work with linux, 
like mine had to.

lol

---

### Post by Muhammad Ahmed on 2009-03-24
> **mhgsys said:**
> I agree. 

But still, 

You can use the live cd of Ubuntu to delete your partitions, and make it all free space again, 
that way vista can read it again, 

for a dual boot follow the post from Mark. 

Personally I think your wife should learn to work with linux, 
like mine had to.

lol



IN any case you will have to install vista first to have dual boot for ubuntu and vista.!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by 73ckn797 on 2009-03-24
> **Muhammad Ahmed said:**
> IN any case you will have to install vista first to have dual boot for ubuntu and vista.!!!!!!!!!!!!!!!!!!!!!!!

Windows does not play nice with another OS installed prior to itself.

---

### Post by mhgsys on 2009-03-24
> **Muhammad Ahmed said:**
> IN any case you will have to install vista first to have dual boot for ubuntu and vista.!!!!!!!!!!!!!!!!!!!!!!!

Not totally, 

I agree it's the easiest way though, 


but you could map drives and or partitions in grub to let windows think it's on primary disk first partition

with
```

map (hd0) (hd1)
map (hd1) (hd0)


```

f.e if the windows is slave disk.

or 
```

map (hd0,0) (hd0,1)
map (hd0,1) (dh0,0)


```

f.e if windows is on the primary disk, second partition,

---

