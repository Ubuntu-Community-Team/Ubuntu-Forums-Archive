---
title: "New gfx card problems"
date: 2010-07-14
forum: Hardware
---

### Post by Rocky1980 on 2010-07-14
Hi all,

I am some real issues with my new gfx card. My old nvidia 6600 was on its last legs so I puted up a gt220. I installed it in the machine however now ubuntu boots in low gfx mode :(

I have tried removing and installing X server but that did not help, now all that happens when I load it is an error saying I am now using any nvidia drivers. Also hardware drives says I have nothing installed. Next I tried downloading the driver from the nivida website 

NVIDIA-LINUX-X86-256.35.run

however when I try to run this in terminal using 

sh NVIDIA-LINUX-X86-256.35.run
or 
sudo sh NVIDIA-LINUX-X86-256.35.run
or
sudo sh ./NVIDIA-LINUX-X86-256.35.run

all I get is message saying cant open.

I have also tried fix x server in recovery mode but with no luck

I am using 8.10.

Help please

---

### Post by overdrank on 2010-07-14
> **Rocky1980 said:**
> Hi all,

I am some real issues with my new gfx card. My old nvidia 6600 was on its last legs so I puted up a gt220. I installed it in the machine however now ubuntu boots in low gfx mode :(

I have tried removing and installing X server but that did not help, now all that happens when I load it is an error saying I am now using any nvidia drivers. Also hardware drives says I have nothing installed. Next I tried downloading the driver from the nivida website 

NVIDIA-LINUX-X86-256.35.run

however when I try to run this in terminal using 

sh NVIDIA-LINUX-X86-256.35.run
or 
sudo sh NVIDIA-LINUX-X86-256.35.run
or
sudo sh ./NVIDIA-LINUX-X86-256.35.run

all I get is message saying cant open.

I have also tried fix x server in recovery mode but with no luck

I am using 8.10.

Help please

Hi and it may just be a typo but the file name would be NVIDIA-Linux-x86_64-256.35.run
Note that I named the 64bit file name.:)

 Also you will need to cd ( changed directory) to the directory where the file is located.

Also on a side note 8.10 has reached end of life support. It may be time for a upgrade. :)

---

