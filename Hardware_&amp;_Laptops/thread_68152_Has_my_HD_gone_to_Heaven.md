---
title: "Has my HD gone to Heaven?"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by oVerCaffeinated on 2005-09-22
Here's the deal. I've got a 120Gb IDE Seagate drive and a fresh install of Ubuntu 5.04 on it. I've got about 40Gb of data I need to copy from an NTFS drive to my Ubuntu ext3 drive. First time I tried to copy it locked up a little way through. My USB Mouse stopped functioning. I pressed CTRL+ALT+F1 and what was on the other side was:

```
[color=navy][b]EXT3-fs error (device hda1) in start-transaction: Journal has aborted

uhci 0000:00:10.0:host system error, PCI problems?
uhci 0000:00:10.0:host controller halted, very bad![/b][/color]
```

It would have this message constantly scrolling down the console. I could do nothing but reboot. When Ubuntu was booting up again it had:

```
[color=navy]**/ contains a file system with errors, check forced.**[/color]
```

So I let it do it's scan and a whole heap of errors came up. All the errors were about "inodes" and it kept telling me to press "Y" to fix the problems. It did this about 500 or so times before it told me to reboot. I reboot and Ubuntu now seems fine. So I start were I left off from copying the files. It happens again. Only this time when I go through fixing the errors and rebooting Ubuntu, Xorg seems to be totally stuffed. Just a black screen with the loading circle/dots cursor. Also when I turn the computer off the HD makes a big clicking sound which I think is the horrid "Click of Death".

So is my drive totally stuffed or what?

---

### Post by fordfan753 on 2005-09-22
I'm not an expert with hardware (or anything) but it's possible. Is the drive under warrany?

---

### Post by oVerCaffeinated on 2005-09-22
If it did have a warranty I think it's too late, I've had it for more than a year. I traded it for a faulty modem I received at a computer market and there are no records of purchase so I doubt I'm going to get anything from this. I don't really care about the dead HD just all the files I'm going to loose.

Also now the BIOS refuses to recognise the drive saying the "S.M.A.R.T. Controller" has failed or something. I think that's the final nail in the coffin for this drive. I think it's time to get my protective glasses and smash it with an axe.

---

### Post by skoal on 2005-09-22
[QUOTE=oVerCaffeinated]I think that's the final nail in the coffin for this drive. I think it's time to get my protective glasses and smash it with an axe.[/QUOTE]
D'oh! Hold that axe, homer. I bet we can at least salvage your data off the drive first. If (and when) you do eventually get a second drive, just haller back here and we'll try something...

\\//_

---

### Post by KingBahamut on 2005-09-22
Skoal that would be entirely based on if its not the Logic thats bad on the HD. If it is, then he's in trouble. 

I just hope to God that if the Logic isnt bad, that the Maint. Parition is still intact. If so, then we can help you, no problem.

---

