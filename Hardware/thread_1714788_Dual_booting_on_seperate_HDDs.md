---
title: "Dual booting on seperate HDDs"
date: 2011-03-25
forum: Hardware
---

### Post by xbobby_bobx on 2011-03-25
Hey guys here is my problem: I'm trying to install Ubuntu 10.10 on my desktop on a separate hard disk my computer is currently operating Windows XP on 80 GB Hard Disk and I want to install Ubuntu on 14 GB Hard Disk without touching my Windows Hard Disk. I tried to install it on another computer then swap it to the other computer but it didn't even let me boot my XP so what should I do and please explain briefly.

Thank you :)

---

### Post by oldfred on 2011-03-25
I assume these are IDE/PATA drives. You have one set as master & the other as slave. Is you BIOS newer and lets you choose which drive to boot? Older BIOS only follow the IDE standard of booting the primary master.

With both drives plugged in:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by xbobby_bobx on 2011-03-26
Oh I can't install it because I have no Linux on my hard drives, I can boot from the live disk but due my memory capacity I won't do it, any other ideas? I really want do it in a simple way, Linux is awesome I have been working with it for a long time. By the way can I install it via WUBI on a slave drive? Is it possible? Or it won't boot?

---

### Post by oldfred on 2011-03-26
I am not very knowledgeable on wubi.

You should be able to run the script from any liveCD that boots. It is just a script that runs Linux commands and saves output to a file results.txt that you then can post.

---

### Post by xbobby_bobx on 2011-03-26
OK I will try to do it tonight and I will post it tomorrow or something, is that OK with you? :)

---

