---
title: "Windows No Disk Error"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by rcoop on 2009-08-23
Hi,

Can someone help me out.  I'm trying to run wubi on my windows xp desktop, but I get a message ' Windows - No disk processing exception ...' error.  I can't seem to figure why I'm getting the error. 

thx,

rudy

---

### Post by running_rabbit07 on 2009-08-23
When and where do your get this error? At restart?

---

### Post by rcoop on 2009-08-23
Hi,

Thx for replying.

I get the error as soon as I click on the wubi app.

When I initially ran wubi it came up fine, but then I realized I wanted to install ubuntu on a separate partitiion, so I created one using the linux system rescue cd and formated as fat32.  Rebooted, went back into wubi and that's when I started to get the error.  I reformatted the partition again in windows xp making it ntfs, thinking that might resolve my problem. Rebooted, but still get the same error when I tried to use wubi.
Thinking wubi might have gotten corrupted, I downloaded wubi again and tried running, but get the same error.

rudy

---

### Post by mike3point2 on 2009-08-29
I too am having the same problem, however i am trying on a dual boot xp32 and vista64 system and wubi give the same error for both. :confused:

---

### Post by theozzlives on 2009-08-29
> **rcoop said:**
> Hi,

Thx for replying.

I get the error as soon as I click on the wubi app.

When I initially ran wubi it came up fine, but then I realized I wanted to install ubuntu on a separate partitiion, so I created one using the linux system rescue cd and formated as fat32.  Rebooted, went back into wubi and that's when I started to get the error.  I reformatted the partition again in windows xp making it ntfs, thinking that might resolve my problem. Rebooted, but still get the same error when I tried to use wubi.
Thinking wubi might have gotten corrupted, I downloaded wubi again and tried running, but get the same error.

rudy

WUBI app??? When you boot (since you setup dual boot) you should get GRUB. it'll give you a choice between Ubuntu and Windows. Since you installed WUBI, you should get the Windows boot menu that'll give you a choice between Windows or Ubuntu. Choose Ubuntu and you'll go to WUBI.

If you want to use real Ubuntu, just remove WUBI through add/remove programs.

---

### Post by presence1960 on 2009-08-29
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

