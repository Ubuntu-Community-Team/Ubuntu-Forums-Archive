---
title: "What file system for shared drive (Vista 64 bit and Ubuntu)"
date: 2008-11-12
forum: General Help
---

### Post by meuge on 2008-11-12
I am going to be setting up a dual-boot system, with Windows Vista 64 bit as well as Ubuntu 8.10. I've purchased a 500GB drive for my media files, and I'd like to be able to share it between the two operating systems. I was wondering which file system to use in order to be able to read, write, open and modify the files from either OS. 

My options are basically to use Ext2/3 and use the Ex2 file system driver in Windows, or to use NTFS and use the Ntfs3g driver in Linux. 

Currently I am leaning towards the latter, but I would appreciate any comments or experiences one way or the other. 

Thanks in advance.

---

### Post by Archmage on 2008-11-12
Are you sure that the ext2/3-driver is working in Vista?

I personal would give NTFS a try.

---

### Post by saffagirl on 2008-11-12
I'm still fairly new at this, but I have got a shared partition in NTFS, I'm using Vista 32bit and Ubuntu Hardy. ..

no problems using the file structure in either OS read/write enable in both. Only thing to bear in mind is if Vista isn't shut down properly then you cant access the ntfs structure....

---

### Post by meuge on 2008-11-12
> **saffagirl said:**
> I'm still fairly new at this, but I have got a shared partition in NTFS, I'm using Vista 32bit and Ubuntu Hardy. ..

no problems using the file structure in either OS read/write enable in both. Only thing to bear in mind is if Vista isn't shut down properly then you cant access the ntfs structure....
Thanks. 

I guess that means that in order to boot Ubuntu, I'll have to suffer through the 10 minutes needed to shut down Vista, and another 10 minutes to start it again. Oh well. I guess that's the price I pay for still playing games at the age of 27.

---

### Post by iKonaK on 2008-11-12
I can't imagine why you would want Vista on your pc but if the Ex2 file system driver works in Vista 64 then there are no doubts, go with ext3.

---

### Post by meuge on 2008-11-12
> **iKonaK said:**
> I can't imagine why you would want Vista on your pc but if the Ex2 file system driver works in Vista 64 then there are no doubts, go with ext3.

I still play games, which unfortunately means that I need to use Windows. Since Vista is the only OS that supports DirectX 10, then I am pretty much stuck using Vista. I never used it on my own computer, but my experience with using it on other people's machines was pretty poor. I just hope that SP1 has improved it enough to be usable. 

Certainly, I do not intend to use it for much besides games, which is why I am installing Ubuntu as well.

---

### Post by saffagirl on 2008-11-12
I bought a new laptop and got stuck with Vista....so I feel your pain. That was part of the reason I'm trying to move to Ubuntu.

There are still issues which mean I'm forced to use Vista for me- I communicate on skype and my webcam still ain't working which means I use that other OS.

And yes, it does seem like Vista takes ages to shut down.(read make a cup of coffee/ tea at this point)....but like I said it won't mount otherwise. But otherwise can read/ write happily to NTFS on both OS:) ....try Parted Magic I managed to do everything from there.

---

### Post by Vadi on 2008-11-12
I'd say NTFS. Vista comes with zero support for ext3, while Ubuntu reads and writes to ntfs just fine - so you should be safe on both sides.

---

### Post by Archmage on 2008-11-13
> **meuge said:**
> I still play games, which unfortunately means that I need to use Windows. Since Vista is the only OS that supports DirectX 10, then I am pretty much stuck using Vista.

Why are you forced to stick with Vista, because of DirectX 10? Till now there are three games on the market that needs DirectX 10 and around 5 million that don't.

And three of this three games suxs. Therefore you still could go with Windows XP or even Wine.

If the gaming companise someday choose to trash the game-buyers that still have XP (at the moment this are two thirds of the Windows-Gamers) than this might change. But not now.

---

