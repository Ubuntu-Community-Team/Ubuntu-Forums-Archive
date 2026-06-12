---
title: "Why not automount?"
date: 2009-04-20
forum: Hardware
---

### Post by Vock on 2009-04-20
I'm just wondering if there's a reason why most (all?) linux systems don't just auto-mount HDD? I know it's an option to do so, but is there some sort of advantage to not automatically mounting your HDD that i'm unaware of? Is it bad to always have all partitions mounted?

---

### Post by jerrrys on 2009-04-21
in a nutshell, auto mount will allow you to go to an os of choice...
your not really loading all partitions...theres a ton of info on it...

[http://www.google.com/search?q=auto+mount+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=auto+mount+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by lisati on 2009-04-21
With some of my partitions and HDDs, I'd rather that it doesn't automount when I start Ubuntu, as a precaution against accidentally borking backups or Windows (where I have it on my system)

---

### Post by RealG187 on 2009-04-21
> **lisati said:**
> With some of my partitions and HDDs, I'd rather that it doesn't automount when I start Ubuntu, as a precaution against accidentally borking backups or Windows (where I have it on my system)

ya sometimes I only mount partitions when I need them and not have them in the way when I don't.

---

### Post by Vock on 2009-04-22
So having extra partitions mounted won't affect performance? It's mainly so you don't have access to it if you don't want to mess around with it or something else to?

---

### Post by Lux Aurumque on 2009-04-22
Whatever you do, try to avoid pysdm 

it's supposed to auto-mount all drives, and it does... except that i cannot write to them once i use it... and it's a pain to fix.

---

### Post by RealG187 on 2009-04-23
I wouldn't wanna mount all drives, I have a recovery partition!

---

### Post by zero7404 on 2009-04-27
in my case, i have an HDD that i'd like to automount upon startup in ubuntu...it doesn't have to automount right away, but within a min or 2 of login would be nice.

it is an ntfs hdd and it's only purpose in life is to store files like docs, pics, music, etc....my ubuntu installation resides on the same physical hdd as my vista installation, and the disk i'd like to mount doesn't contain any OS's...

the commands and howto seems to elude my searches on here.
i also went and created a fat32 partition on the same hdd, but since i don't know how to make it automount, i don't really have a use for it. also, since ubuntu has no problem mounting an ntfs disk, i probably wouldn't need the fat32 partition anyway.

---

