---
title: "Can't boot any Ubuntu Live CD! Modern PC, tried everything I can think of..."
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by mindry on 2009-05-10
Hi all,

I'm fairly new to Linux, and started checking it out after my brother ordered an Ubuntu CD from Shipit. Since I'd just had to reinstall Windows after a nasty virus that got through my AV somehow, and since I already use FOSS wherever possible, I decided to switch to Linux, and decided that Ubuntu would be the best choice, but I've had no end of problems trying to use the Live CD.

My problem is thus. Every time I boot from a Live CD of Intrepid, Jaunty or anything based off one of those, I get past the loading bar, and then everything freezes. Sometimes I get to move the mouse for a few seconds, sometimes I get the statrup sound, sometimes I see a black X in the middle of the screen, sometimes I even get a few seconds on the desktop, but it **always** freezes eventually. The screen locks up, the CD drive goes quiet and won't eject, and the Num Lock and Scroll Lock lights on my keyboard start flashing. Then I have to hard-reset. I've tried numerous Ubuntu based distributions, including Mint, and all have the same problem, except the Mint XFCE edition (which eventually worked, although Xubuntu Jaunty doesn't), and Kubuntu Hardy (which works fine, although I haven't tried any other Hardy distributions and don't really want an old version anyway).

What's bizzare is this is NOT an old or obscure computer. It is a HP Pavilion a6220.uk bought in December 2007, with Intel Core 2 Duo E4400 2GHZ, ATI Radeon graphics and 2GB of RAM. Yet every recent Ubuntu distribution I try gives the same flashing keyboard freeze. What in the world could be the problem? I've tried doing all this:


[LIST]
[*]Graphical safe mode/compatibility mode (made NO difference)
[*]Verifying disc integrity (says the disc is OK but still won't boot)
[*]Wubi (exactly the same happens when booting into my new Wubi install)
[*]Burning onto a DVD-RW instead of a CD-R
[*]Haven't tried burning at a lower speed yet, but the official Canonical Intrepid disc, which is presumably a higher quality than my home-made ones, suffer the same problem, so I can't see how this would help
[*]Using a Live CD instead of a USB
[*]Using an SD card
[*]Using a different IDE CD drive
[*]I've even tried using my brother's graphics card (a higher end Radeon, from his newer Pavilion with an AMD Athlon which is able to boot these discs) and it STILL didn't work
[*]Tested my RAM with Memtest86+, no errors found
[/LIST]
All to no avail. The only thing I haven't tried is the alternate install disc, purely because I don't want to go through all the partitioning rigmarole only to find I still can't boot into the finished install. Can anyone tell me what the problem is? Presumably it's hardware related, but if it's not the RAM, CD drive or graphics card, what is it? And is the alternate disc worth trying or not, considering I'd rather not wipe Windows at this stage? Or should I just stick to old distributions, or go elsewhere (PCLinuxOS works, but I don't really like it compared to Ubuntu and Mint)? Please help, this is driving me mad!

---

### Post by mindry on 2009-05-12
OK, I have tried Hardy-based distributions and they seem to work OK, but there are still graphical problems when using "switch user" (with fglrx this freezes the system, without fglrx the screen goes all green and fuzzy when I log back in). I then tried dual-booting with an alternate CD install of Jaunty, which installed OK, and I get to the lovely login screen, and then the exact same problem happens again! Please help me, this is infuriating!

---

### Post by docdraino on 2009-06-23
i have the same problem, yet it still has gone on unsolved. my diagnosis is that relatively new graphics cards might be the problem. i have a nivida geforce 9800 GT 512mb and i can't even get past the loading screen. that goes for the livecd and on a fresh install. i have no idea how to fix this problem what so ever :(

---

### Post by merlinus on 2009-06-23
ATI and Radeon are probably the problem.  Try the text-based alternate install cd.

FWIW, I have an nvidia geforce 9400 gt, and it works splendidly!

---

### Post by Therion on 2009-06-23
Okay, talk about a stab in the dark, but here goes (and I suggest this because it actually saved my sanity a couple years ago)...

Pull the ribbon cable from your optical drive.  I'll bet you dollars to donuts it's a standard 40-wire/40-connector ribbon cable.  What I'm going to suggest you try is an **80-wire**/40-connector cable.  See attached pic.

The additional 40 wires don't connect to anything, they insulate the connector wires against electromagnetic interference.  I know it sounds nutty the science is sound on this one.  As we continue to push more and more data across the same cable, the more sensitive it becomes to getting borked.  The 80-wire connector solves this problem for cheap.  Mine set me back around $8.

---

### Post by mindry on 2009-06-23
I found my problem eventually, after extensive Googling suggested the culprit might be the one thing I hadn't bothered changing, the TNET1130 Wireless PCI card. Booting without the card, and then installing the drivers with Ndiswrapper solves the problem. This is annoying because the ebay listing for the card specifically said Ubuntu-compatible - in fact it works on most other distros but not Intrepid or Jaunty. Linux Mint XFCE Edition works fine though, even though the Xubuntu Intrepid it is based on doesn't, leading me to suspect a new Network manager since Intrepid is the problem, since Mint XFCE uses Wicd instead. But it doesn't matter if you boot without the card first. Hope this helps someone as this issue was a real pain and almost put me off Linux completely, let alone Ubuntu.

---

