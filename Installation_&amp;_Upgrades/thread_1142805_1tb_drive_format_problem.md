---
title: "1tb drive format problem"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by marbour on 2009-04-29
Hi.

I am experiencing my 1st problem with Ubuntu 8.10 that I have not been able to fix with the help of this forum: formatting my new 1TB WD caviar green drive.

I have a media center that is working just fine to which I want to add my new 1TB drive. With the help of this forum I tried console tools, live CDs, GUI tools and nothing does it. I also followed instructions on using mkfs and its "friends" to the same result: I can't create a large partition on my drive.

All the time I am being told there is an error creating ext3 partition on /sdxx/ (tried pluggin it elsewhere on the board as well)

I unplugged my "old" drive to install fresh on my 1TB drive with no success either. The only way this drive works under Ubuntu is if I create a small partition and install (100G for example). But booting to Ubuntu later does not let me create a big partition.

I tried ext2, ext3, fat (to mount with my old drive), and every other journalized fs I could try.

I pop in Mandriva PWP 2008 and it installs flawlessly in a 1TB "/" mounted partition.

Ubuntu Gurus: Any "theological" answers to this? Please! I don't want to be stuck with Mandriva in the living room while all the other computers in my life run Ubuntu (8.10 LTS at the office and 8.10 at home, sorry, my wife's is WinXP)

Best regards

Marc

---

### Post by magearwig on 2009-08-13
In the same boat with my new Buffalo drive.  Any progress?  I'll be back when I learn something post worthy.

---

### Post by Mark Phelps on 2009-08-13
Both GParted and Parted Magic were recently updated (last few days, I believe).  Have you tried the most recent version of their LiveCDs?  You can get both of these from the distrowatch.com web page.

---

