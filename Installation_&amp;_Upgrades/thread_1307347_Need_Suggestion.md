---
title: "Need Suggestion"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Krishnan.V on 2009-10-31
Hi, I have a 500 GB of HDD, with 2.74GB of RAM. I am using Windows xp on one side. I want to install Ubuntu 9.10 on other. I just wanted to know how much space should i allot to SWAP and EXT partition. I am going to use Ubuntu more frequently and will use WinXp for games and all.

Please provide your inputs.

---

### Post by Sensiva on 2009-10-31
Short answer is : swap min <1.5xRAM>  swap max <3xRAM>

Please read this SWAP FAQ , its really helpful[ https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Krishnan.V on 2009-10-31
What about EXT?

---

### Post by Sensiva on 2009-10-31
> **Krishnan.V said:**
> What about EXT?
huh? 8-[

---

### Post by JBAlaska on 2009-10-31
Honestly I think the swap "formula" needs to be updated for users with >3GB RAM, I have always used the 2x RAM swap size when I had = < 2GB of RAM and even then very little of the swap partition was ever actually used. Now that I have 4GB RAM, I decided to use a 4GB swap partition and I have never seen more than 2% being used, with mostly 0% being used on a day to day basis.

Actually I guess it does not matter in these days of 500GB-2TB+ HD's, to allocate 4-8GB on a swap file...So now that I think about it, I guess I have no point LOL

Krishnan.V, 1.5 X RAM is a safe bet, and you might seriously think about making a /home partition as well, as in:

/ (root-mountpoint) EXT4 or EXT3 if your want, EXT4 works fine for me and is noticeably faster.
/swap
/home EXT4 or EXT3 as above.

---

### Post by florus on 2009-10-31
ext is not a partition. ext3 and ext4 are different file systems. ext4 is the default for new 9.10 installations and faster than ext3.

---

### Post by JBAlaska on 2009-10-31
Damn sorry...I did not think I needed to specify that (as he or she is going to finger that out in gparted), as the OP was asking about EXT (Filesystem not a partition lol)

---

