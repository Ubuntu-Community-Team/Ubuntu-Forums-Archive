---
title: "Wake up after hibernate on EeePC 1000HE"
date: 2011-04-23
forum: Hardware
---

### Post by LeXav on 2011-04-23
Hi !

I'm using natty on my eeepc. All is fine except hibernate. After wake up, my screen is 3/4 black and sparkles a lot.

Please have a look :

[[img]http://pix.toile-libre.org/upload/thumb/1303553969.jpg[/img]](http://pix.toile-libre.org/?img=1303553969.jpg)

Does anyone have a suggestion?
Thanks.
Xav'.

(Sorry for my english,  I'm typical french... ;-) )

---

### Post by LeXav on 2011-04-24
I've found this on dmesg :

[    0.959060] PM: Hibernation image not present or could not be loaded.

But, except the video problem all is reloaded (software, windows ... )
So, I think the system should have reloaded hibernation image.

Bizarre bizarre...

---

### Post by TheNacho on 2011-04-25
I have the exact same problem. A temporary fix for when the screen is garbled is to go into sleep mode and wake up again.

---

### Post by LeXav on 2011-04-25
> **TheNacho said:**
> I have the exact same problem. A temporary fix for when the screen is garbled is to go into sleep mode and wake up again.

I tried this and that's work fine. But, as you said, this is a temporary fix.

I've also tried to add some arguments at the pm-hibernate command.

But, none of them could help me.

Still looking form a solution.

---

### Post by wkcchampion on 2011-05-13
i have the same netbook, Ubunt u11 and i have the same problem. :confused:

---

### Post by Sgozz on 2011-05-16
Same on my EEE 1015PD, i'm on x64 version. Maybe i386 version fix the problem?

---

### Post by wkcchampion on 2011-05-16
> **Sgozz said:**
> Same on my EEE 1015PD, i'm on x64 version. Maybe i386 version fix the problem?

Nope, I have the 32 bit version. I'm not a computer tech but my suspicions go to the video drivers.

---

### Post by Sgozz on 2011-05-16
> **wkcchampion said:**
> Nope, I have the 32 bit version. I'm not a computer tech but my suspicions go to the video drivers.
Opensuse 11.4 works perfectly out of the box on my eee 1015pd, I'm afraid it's not driver's fault..

---

### Post by wkcchampion on 2011-05-17
Then, what may it be? An error loading the hibernation image / computer previous state?

---

### Post by wkcchampion on 2011-05-20
I downloaded a good 100 megs of updates yesterday and the issue still takes place. :(

---

### Post by Sgozz on 2011-05-25
FIXED!! Just enabled "Proposed" repository in Synaptic, downloaded new kernel and xorg upgrades and is working perfectly!

---

### Post by shakma on 2011-05-26
Sgozz, you rock!  I will confirm this solved the problem on my Asus 1005HA.  Had been working "out of the box" since 10.04, then this problem appeared with the Natty upgrade.  The "proposed" repository also seems to have cured the slooooow wake up from stand by.  I just hope I don't end up getting borked by some beta packages down the road ;).

I'll test it tomorrow, but hopefully this will also return full functionality of the VGA out.  It has serious issues under the unity shell, although "classic" still works as it should.  (But that's another topic for another thread.)

Thanks again, forum!

Peace.

---

### Post by wkcchampion on 2011-05-26
> **Sgozz said:**
> FIXED!! Just enabled "Proposed" repository in Synaptic, downloaded new kernel and xorg upgrades and is working perfectly!

Then, such updates should be moved to the "Recommended" or "critical" section!

---

### Post by shakma on 2011-05-26
> **wkcchampion said:**
> Then, such updates should be moved to the "Recommended" or "critical" section!
Damn straight!  Hasn't broken anything else yet, and compared to the "recommended" updates... it actually WORKS!

---

