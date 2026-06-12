---
title: "DVD burning problem: SYNCHRONOUS FLUSH CACHE"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by jofre on 2006-10-01
Hi lads, I was wondering if anybody around here could help me. 

The problem is my new DVD burner: "PIONEER DVD-RW DVR-110D" (As detected by Dapper).

I have already waste 4 dvds.I try first with gnome-baker, I got a "sucseful" burn, that I could not manage to open/mount. I tried to use mkisofs to do a iso image, and then use growisofs to burn the dvd. 
The result is here:

growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=cd_image.iso
Executing 'builtin_dd if=cd_image.iso of=/dev/dvdrw obs=32k seek=0'
/dev/dvdrw: "Current Write Speed" is 2.0x1385KBps.
   7471104/4012644352 ( 0.2%) @1.2x, remaining 35:44

.....

4003725312/4012644352 (99.8%) @2.0x, remaining 0:03
builtin_dd: 1959312*2KB out @ average 1.9x1385KBps
/dev/dvdrw: flushing cache
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=11h/ACQ=05h]: Input/output error


I have been searching the web, but I found very little help. The few posts I found were to cryptic for my programming/linux knowledge.  I just have Ubuntu on my machine, so I don't knwo if it would work on WindowsXP, but I would like to keep with a clean linux machine.

Thanks a million,
Jofre.

---

### Post by andlinux21 on 2006-10-01
:) Have you tried K3B to burn your DVD's?  Its pretty straight forward and its in the repos.

---

### Post by jofre on 2006-10-01
I thought that K3b was just a GUI to mkisofs and grwoisofs. So I am not sure to see the advantage of using K3b.

---

### Post by bigken on 2006-10-01
dont know if this will help ? to copy a disc you can right click and save as iso and to burn just right click the iso and burn and k3b is a great peice of software ;)

---

### Post by jofre on 2006-10-01
I have nothing against K3b!!! But K3b is just a frontend application. The program that actually does the "burning" is growisofs.

---

### Post by jofre on 2006-10-01
After all morning trying to find a solution, the status is this:

I found that in the changelog of growisofs-5.2 had some problems with Pioneer dvd writers. So I donwloaded the edgy package which is version 6.0. And still got the same error message.

---

### Post by dieresys on 2006-10-29
Hi Jofre,
I'm having exactly the same problem, and I think It gets worst on Edgy.
Could you tell me witch firmware version does your recorder has?

I'm going to update my recorder to 1.39 version [1].
I let you know when I have some news.

Manuel

[1]http://www.pioneer.es/es/download.jsp?dir=/files/support/dvrup&filename=DVR110D_FW139EU.EXE

---

