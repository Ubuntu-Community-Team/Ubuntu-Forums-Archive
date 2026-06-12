---
title: "What happened when I installed Ubuntu + Vista?"
date: 2008-11-01
forum: General Help
---

### Post by Roasted on 2008-11-01
I have 4 drives in my computer. Drive A, B, C, D.

A = 500gb
B = 500gb
C = 250gb
D = 250gb

I like my installs to be on drive A, as far as OS's go. I had Ubuntu Intrepid Beta + XP on it. I recently obtained a copy of Vista Ultimate so I decided to go with Vista Ultimate + Ubuntu Intrepid (Final Release). 

So I unplugged all of my hard drives except my top SATA drive to do my installs. I prefer this because in the past, Grub used to get messed up easily and would often install itself on my backup drives which was kind of stupid. But anyway, I just like to install with 1 drive.

So, drive A is plugged in, B C D are not. I install Vista + Ubuntu.

Hours later, thanks to the painfully long process of installing my drivers in Vista, I'm ready to boot. I boot up, and my old desktop is back. Everything is there. Programs, settings, everything. It's then I realize I'm on Intrepid Beta, which all of my previous settings.

Here, I somehow installed Vista + Ubuntu on my other 500gb drive. But I don't understand, because my other hard drive was the only one plugged in for my XP + Intrepid beta install weeks earlier + the only one plugged in when I installed Vista + Intrepid.

So basically, this is what I'm facing.

Drive A - 500gb - XP + Ubuntu Beta
Drive B - 500gb - Vista + Ubuntu Final Release
Drive C - 250gb - Backup
Drive C - 250gb - Backup

The only thing I can think of, is when I had only my 1 500gb drive plugged in, that due to the lack of presence of other drives, Ubuntu assigned it /dev/sda, even though it was originally /dev/sdb. Because XP + Ubuntu hard drive is indeed /dev/sda when everything is plugged in, which Vista + Ubuntu hard drive is assigned to /dev/sdb when everything is plugged in. However, with only my top 500gb hard drive plugged in when I installed Vista and Ubuntu Final Release, it did indeed say /dev/sda.

So that's the only thing I can think of, is that my hard drive took on a different device tag when it was the only one present.

I guess in the future I should just work with all of my hard drives plugged in?

---

