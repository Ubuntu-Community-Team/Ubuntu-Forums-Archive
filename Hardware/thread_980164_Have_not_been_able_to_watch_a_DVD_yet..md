---
title: "Have not been able to watch a DVD yet."
date: 2008-11-12
forum: Hardware
---

### Post by rlonnborg on 2008-11-12
This is a first install of Ubuntu on my laptop.  I have followed several steps and install all the codex to play DVD.  I have tried Kaffine, MPlayer and gxine.  I put the DVD in and it will spin up, but never plays.  The player will usually fade out and I get tired of waiting.  I will then force close it.

Also has any had the problem of Firefox opening too large for the window.  I have to F11 twice to get it back to the size of the window.

---

### Post by m_duck on 2008-11-12
Did you add the medibuntu repository when you were trying to get playback before? If not, check [here]("https://help.ubuntu.com/community/Medibuntu") for instructions to add the repo.

Once you have it added, the main package you need is **libdvdcss2**. You can either install it in synaptic package manager or via the terminal:
```
sudo apt-get install libdvdcss2
```Other useful packages for playing various media formats are:

[LIST]
[*]   **ubuntu-restricted-extras** (this also includes a flash plugin, some more fonts etc)
[/LIST]

[LIST]
[*]   **w32codecs** (or w64codecs if you are running a 64 bit OS)
[/LIST]
 
Another thread worth reading regarding multimedia is: [Comprehensive Multimedia and Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

EDIT: Regarding firefox, is it that the firefox window is taking up a larger area than is available on your screen? If so you can press and hold alt, then left click and drag the window to a position where you can grab the window borders to resize it. Close firefox and reopen it and it *should* have remembered the dimensions.

---

### Post by Totenglocke on 2008-11-13
I had the same problem with Firefox.  The problem is Compiz Fusion.  I installed the "compiz fusion icon" from synaptic and used that to turn off Compiz and use Metacity instead (after compiz fusion icon is running just right click, go to "select window manager", and select Metacity).  After that, no more problems with Firefox starting too big.

---

### Post by Rovdjur on 2008-11-13
Well, I hate to say it, but don't get your hopes up too much. Looking at your sig, you have a T42, and those all came with ATI video cards, and ATI hates linux, so even if you get the DVD to play, don't expect a very good framerate :-/

---

