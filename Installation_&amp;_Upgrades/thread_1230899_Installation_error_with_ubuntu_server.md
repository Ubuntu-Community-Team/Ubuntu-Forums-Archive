---
title: "Installation error with ubuntu server"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by smcbryde on 2009-08-03
Installing on an older Compaq Presario with Windows 2000 installed. (Looking to make it into a dedicated web server with LAMP for software development and testing)

Downloaded the server 32bit ISO burned it onto a dvd, placed it into the dvd drive and started the computer. Got language selection screen (pressed enter), then main Ubuntu install screen (pressed enter) and got a blinking cursor and the following:

BUG: Int 14: CR2 c1000000 (followed by a bunch of hex)

Stack: (and a bunch more hex)

Repeated the process by downloading from a different computer, burning onto a cd-rw, with different burning software, and got the same result.

I've searched dozens of pages before and after this attempted install and nothing has spoken to anything like this.

I don't speak Linux, so...Any "not too technical" ideas?

---

### Post by Sef on 2009-08-04
Instead of installing, go down the menu to 'Check Disk for Errors' (or something similar) to make sure the disk is good.

---

### Post by Baladan on 2009-08-08
I am experiencing the exact same problem. I purchased an Ubuntu 9.04 Disc 1 - Install/Live CD. So I suspect the disc is OK.
 
I have tried install, install in graphics safe mode, checked the disc and always get the same error:
 
Bug: Int 14 CR2 c100000 etc.
Stack: ff78f000 fffffff etc.
 
The machine is a Compaq Presario 5900Z.
 
Processor: 1 Ghz AMD Athlon
RAM: 384 MB
Virtual Memory: 32 bit
File System: 32 bit
BIOS: Phoenix Version EPP Rev. 9.00 09/27/99
OS: Windows 98 2nd Edition
 
 
I did the memory test. It took 52 minutes and gave me 118% pass (whatever that means.) Passed "1" then continued to test, and I pressed Esc. to stop the test. 
 
I checked the HP (formerly Compaq) website, but no BIOS updates exist.
 
Any ideas?

---

