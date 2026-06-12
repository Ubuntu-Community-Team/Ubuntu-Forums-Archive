---
title: "Does anyone have more the 2gigs of ram working?"
date: 2009-01-06
forum: Hardware
---

### Post by beastrace91 on 2009-01-06
Hey, so I just recently picked up a 1gig stick of ram to see if having 4gigs of ram or simply greater than two was the issue... apparently having more than 2 is the issue...

So my question is this does anyone have more than 2 gigs of ram in any distro of *buntu (If so did you have to do anything special to get it to work, if so what?)? Or if not can some suggested another distro with a semi low learning curve that will work with my 4 gigs of ram? I like Ubuntu alot, but I really do not want hardware I have purchased sitting unused due to the software I have and I would rather try a different distro instead of formatting back to Microsoft.

~Jeff

---

### Post by ShadowTek on 2009-01-06
I have 3gigs of DDR on Ubuntu 8.10 AMD64, and I haven't had any problems, nor did I have to "do anything" to get it to work.

---

### Post by beastrace91 on 2009-01-06
I guess Ubuntu just hates me then... I have tried both 32bit and 64bit with the same result on both.

~Jeff

---

### Post by damis648 on 2009-01-06
32-bit OS's can't use more than 4GB RAM (including video memory, that reserved for the kernel, etc.). In order to use >4GB, you need to install 64-bit Ubuntu or use a PAE compiled kernel.

---

### Post by ProfDecoy on 2009-01-06
It could also be a limitation of the motherboard for your system.  Some older boards, especially those in laptops, couldn't address more than a certain amount of ram.

I recently got a Dell 1705 replaced that "officially" only supported a max of 2GB, it recognized the 4GB I installed in it, but the BIOS would only make 3GB of it available, regardless of the OS.  The Studio 17 that Dell sent as a replacement does make the full 4GB of RAM I bought for it.

---

### Post by beastrace91 on 2009-01-07
(I have a 64bit OS) It appears to be an issue with my bios (even though it works fine in Vista/Solairis) WinXp/Linux will not boot properly with out a newer bios which they do not currently have available... I am contacting Asus to see if one is out there that is just not online.

~Jef

---

### Post by halovivek on 2009-01-07
hi
i use 64 bit ubuntu and i use to open lot of programs.
i do have three work space. one i use to open documents, spreadsheet the second work space for music and uploading of videos and datas to internet.
third one i use copy files from hard disk to back up.
till now i have crossed more than 10-15 times more than 4GB of ram and 2GB of swap partition. (10GB swap size)
but everything is really speed thats why i love ubuntu.

---

### Post by bixejo on 2009-01-09
I've got a TOSHIBA satellite laptop with 4Gb RAM and works fine with Ubuntu 8.04 x86_64 (it did also with 7.10, didn't try older releases).

I set also 4Gb of swap disk partition, but whenever I check it with "free -k" I found it completely unused.

Good luck,

---

### Post by gjoellee on 2009-01-09
I have 2gb RAM, work fine with all the distributions I have tried (it is a this moment 24 distributions).

---

### Post by nick09 on 2009-01-09
Hey beastrace91, your main problem is that your computer's motherboard won't accept more than 2GB of RAM. My computer can only accept 2GB of RAM(there is only two RAM slots for DDR400 RAM) and for the fact that the maximum size for each stick is 1GB.

---

### Post by markbuntu on 2009-01-10
I have 6GB ram on one machine and my Hardy and Intrepid 64 installs see it all but the 32 bit only sees 3.2GB. My other machine has 2GB. It used to have 3Gb, 2 1GB sticks and 2 500MB sticks but I took the 500s out because the machine kept freezing up. Mismatched ram can still cause problems even though practically everyone says otherwise.

---

### Post by beastrace91 on 2009-01-11
> **nick09 said:**
> Hey beastrace91, your main problem is that your computer's motherboard won't accept more than 2GB of RAM. My computer can only accept 2GB of RAM(there is only two RAM slots for DDR400 RAM) and for the fact that the maximum size for each stick is 1GB.

Wrong Nick. Windows Vista Reads more than 2 gigs just fine (as well as the bios)... I have 2 2gig sticks and 2 1gig sticks (extra laying around) when ever I try to boot with more than 2 gigs of ram I get "safe graphics mode" apparently this is a known issue (it is also said to happen on Xp from what I can find online) I saw someone some where recompiled a custom kernel to get it working... I might be looking into doing that if it is not too hard. I hate having my hardware sitting unused when it should be working. 

Here is [a thread](http://vip.asus.com/forum/view.aspx?board_id=3&model=G1Sn&id=20080702080446546&page=1&SLanguage=en-us) from the Asus forms of someone else with a similar issue. Apparently Asus refuses to release a bio update that will fix this issue, which is beyond annoying because 4gigs of ram worked fine before they sent me back my computer with a different mother board/gfx card (because the first one died while still under the year warranty)... Maybe I should sue haha

~Jeff

---

