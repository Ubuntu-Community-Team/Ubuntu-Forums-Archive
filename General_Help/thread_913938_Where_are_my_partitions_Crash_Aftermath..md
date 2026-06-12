---
title: "Where are my partitions? Crash Aftermath."
date: 2008-09-08
forum: General Help
---

### Post by lyznx on 2008-09-08
Alright. I have been searching and reading threads for hours now, but none of this makes any sense to me.
 Maybe somebody can just point me in the right direction.

I had an Ubuntu/Vista dual boot.
My computer crashed about 7 hours ago.
I finally got the computer to work again, but got that grub error 17 or W/E.
So i did a fresh install of Ubuntu. It created a new partition from unused space. and it is working great.
 Here is the problem;
Where are my other partitions?
Where is my other physical drive?
Where is the data on those partitions?


 I have been reading through these threads, and I am completely dumbfounded by the whole thing. Mounting/unmounting something, Reinstalling Grub/MBR, lines of code im trying to put through the terminal, which is probably causing more of a problem.
 I cant even ATTEMPT to custumize any of the codes, because i have no idea what i have anymore. dev/sda5 hd0  Root  These things arent making anysense to me.
 
 can somebody please help me?



Edit: I didnt want to bump.
 Also, Seeing as how this is more trouble than its worth, and i could probably download the data faster than trying to retrieve it from these partitions.
 Since vista cant see ubuntu partitions and Ubuntu cant see vista,
What is the best way to completely reformat both of my internal hard drives??? So I can do a complete Fresh start.



And one more question. If and when i do that.
 SHould I install Vista first or Ubuntu First?

---

### Post by Sycron on 2008-09-08
Post the output of ```
sudo fdisk -l
```

---

### Post by manishtech on 2008-09-08
> Where are my other partitions?They are still available on your system, just you need to mount them (will explain what is mounting)

> Where is my other physical drive?Its also present, if its detected by BIOS, then it will be available in ubuntu too

> Where is the data on those partitions?The data on those partitions is on the partitions itself :P


>  I have been reading through these threads, and I am completely dumbfounded by the whole thing. Mounting/unmounting something, Reinstalling Grub/MBR, lines of code im trying to put through the terminal, which is probably causing more of a problem.Its looking geeky due to the fact that you never heard about it. Chill! Its not so tough. We are here to guide you through each and every step. Just have patience.

>  I cant even ATTEMPT to custumize any of the codes, because i have no idea what i have anymore. dev/sda5 hd0 Root These things arent making anysense to me./dev/sda5 is the first extended partition. hd0 means the first hard disk, hd1 is second and so on.
 
>   can somebody please help me?
We are here for helping itself

---

### Post by manishtech on 2008-09-08
Hope you know how to run the command!

Goto Applications> Accessories> Terminal

now copy this command, goto terminal. Goto Edit>Paste and press enter. You will get some output. Now select them and then Edit>Copy and then paste it here. I cant be more simpler.

---

### Post by Sycron on 2008-09-08
> **manishtech said:**
> They are still available on your system, just you need to mount them (will explain what is mounting)


Its also present, if its detected by BIOS, then it will be available in ubuntu too


The data on those partitions is on the partitions itself :P



Its looking geeky due to the fact that you never heard about it. Chill! Its not so tough. We are here to guide you through each and every step. Just have patience.



/dev/sda5 is the first extended partition. hd0 means the first hard disk, hd1 is second and so on.
 
 **[SIZE="4"][COLOR="SandyBrown"]can somebody please help me?[/COLOR][/SIZE]**

How can I help you ?

---

### Post by lyznx on 2008-09-08
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4174f33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14409   115740261   83  Linux
/dev/sda2           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

---

### Post by manishtech on 2008-09-08
> **Sycron said:**
> How can I help you ?
I missed to quote the last line asked by the OP :)

---

### Post by manishtech on 2008-09-08
> Since vista cant see ubuntu partitions and Ubuntu cant see vista,
Ubuntu can see vista partitions, you can modify it only after mounting it

> And one more question. If and when i do that.
 SHould I install Vista first or Ubuntu First?
First Vista then Ubuntu, but no need to format all. Just mount information can be stored and it will be fixed!

---

### Post by lyznx on 2008-09-08
> **lyznx said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4174f33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14409   115740261   83  Linux
/dev/sda2           14410       14593     1477980    5  Extended
/dev/sda5           14410       14593     1477948+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f3ba0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

I have no idea what all this means.
 I know the 500 gb is an external. I have never put an O/S on that.
 I thought I had Ubuntu on the 120, and windows on another(which I forgot the size)
 Im not seeing the third drive.

---

### Post by Sycron on 2008-09-08
I can't see where's the windows. You have a 500GB HDD that should have Windows...

---

### Post by lyznx on 2008-09-08
> **Sycron said:**
> I can't see where's the windows. You have a 500GB HDD that should have Windows...

No. The 500GB is RAW storage.

---

### Post by Sycron on 2008-09-08
> **lyznx said:**
> No. The 500GB is RAW storage.

You don't have windows installed on your HDD's then.

---

### Post by lyznx on 2008-09-08
> **Sycron said:**
> You don't have windows installed on your HDD's then.

Why is it not showing my other internal Harddrive? Windows may be on there.

---

### Post by Sycron on 2008-09-08
Your other internal HDD is that with 120GB ?

---

### Post by lyznx on 2008-09-08
Figured it out.
 The whole reason for the crash was that the hard drive  got fried.
 And that missing hard drive was the one with the O/S's. grr. 200gb hard drive down the drain.
 I opened it up, and the pins were all black and plastic melted.
 Thanks for the help guys.

Edit: just a note: I was able to connect it with a diff power connector temporarily, ang got my data. So, Its cool.

---

