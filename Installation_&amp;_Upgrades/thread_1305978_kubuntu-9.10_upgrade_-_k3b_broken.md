---
title: "kubuntu-9.10 upgrade - k3b broken?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by zapporius on 2009-10-30
I used k3b to rip my cd's to either mp3 or flac in 9.04, and I thought I'd upgrade to 9.10 this morning.

After the upgrade, k3b couldn't rip anymore. At first it spewed errors about lame, so I first reinstalled lame, and then I reinstalled k3b. It didn't help.

Then I tried ripping to flac, and it appeared to be working, until I tried to play those flac files. All I got was static noise. So for some reason the "flac" files were complete bogus, their size did vary, but the content was garbage. The flac files that I ripped in 9.04 worked perfectly in amarok, so its no error in playback chain.

---

### Post by snuffyo on 2009-11-03
I had the same problem with ripping mp3s after upgrading to jaunty. In my googling, I fixed it through this:

In the k3b preferences, plugins > external audio encoder > edit

check both boxes:
Swap Byte Order
Write Wave Header

This will allow the CD to be ripped without an error. To fix the static on the mp3s:

add -x to the command options

Hope it works for you!

---

### Post by tqft on 2010-01-17
> **snuffyo said:**
> I had the same problem with ripping mp3s after upgrading to jaunty. In my googling, I fixed it through this:

In the k3b preferences, plugins > external audio encoder > edit

check both boxes:
Swap Byte Order
Write Wave Header

This will allow the CD to be ripped without an error. To fix the static on the mp3s:

add -x to the command options

Hope it works for you!

Your -x fix worked for me - was just getting static on mp3 rips with k3b.

Interesting;y the default settings for k3b have the byte order swapped, but the -x reverses something again from 
man lame
"
-x     Swap bytes in the input file or output file when using --decode.
              For sorting out little endian/big endian type problems.  If your encodings sounds like static, try this first.
              Without using -x, LAME will treat input file as native endian.
"

I actually tried putting the other settings off and that failed as well.   So no idea but works now,

---

