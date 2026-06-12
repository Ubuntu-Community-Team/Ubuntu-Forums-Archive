---
title: "IBM Thinkpad T43p Random Freezes (SATA Problem)"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by Titan3025 on 2005-08-15
Hi,

i have a T43p which gives me some probs. I have random freezes (no more input possible.. completly frozen).

It must be some kernel problem. I guess it is a SATA problem. I still have the original Ubunutu 2.6.10 kernel. 

I guess the following modules are the cause of the problem.
ata_piix, libata

I would gladly upgrade to 2.6.12 but on the other side I don't want to loose all these nice ubuntu convenience things (automounting of removable drives, etc).

Is there a save way to upgrade to 2.6.12.x. Any prebuild kernels for Hoary available somewhere?

Or is there another solution for my problem.

Cya
 Titan3025

---

### Post by Schlumpf on 2005-09-10
Dear Titan,

I've got exactly the same problems. I tried the breezy preview released yesterday with Kernel 2.6.12 but it freezes faster than hoary did.

Why do you guess it's a SATA problem?

Schlumpf

---

### Post by Titan3025 on 2005-09-10
Hi Schlumpf,

I also upgraded to Breezy PR1 yesterday. Funny coincident :-)

I also realized that it still freezes :-( I hope there will be a fix soon.

I guessed that it is a SATA problem with the dvd drive because when I searched Google I found a site that described this problem and stated that there is a race condition in the SATA kernel code.

Titan3025

---

### Post by Schlumpf on 2005-09-10
Hi Titan,

have u tried another distribution? I tried Suse 9.3 for a day and it didn't freeze. But I didn't like it so I removed it.

I will remove my dvd drive now and check if it works more stable. 
There's a problem with my display ( some black pixels) so I will call the support on monday. Perhaps they know s.th. about the problem.

I also noticed that the t43p freezes after some minutes when using eclipse.

Cu
Schlumpf

---

### Post by Lars A E on 2005-09-10
I've got the same problem with my dell 6000, and it is indeed caused by the sata kernel driver. 
Read more here:
[http://www.ubuntuforums.org/showthread.php?t=40723](http://www.ubuntuforums.org/showthread.php?t=40723)

A bug is posted in bugzilla and the fix i pending upload:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=13370](http://bugzilla.ubuntu.com/show_bug.cgi?id=13370) 

The quick fix is to always leave a disc in your optical drive, wich prevents the kernel from entering the buggy code.

---

### Post by Titan3025 on 2005-09-11
tnx for posting the bugzilla link. now i can keep tracking the bug directly :-)

---

