---
title: "External HDD Ownership - Formatting Help"
date: 2015-02-23
forum: Hardware
---

### Post by ryan131 on 2015-02-23
So I have an interesting situation: I am a digital design student at a college using Macs, meanwhile I use a PC with Windows and Ubuntu. My external HDD for school is Mac-formatted and I use Mac Drive on Windows to read/write on the drive. Unfortunately, Ubuntu doesn't see me as the owner of the drive. In a quick Google search, I've found the solution is to format it from my Ubuntu PC. If I didn't need it formatted any particular way, that would be fine, but it appears I need it formatted for Macs. I've been procrastinating on reformatting it, but here are my questions:

1. Can Ubuntu format for Macs?
2. Does Mac formatting actually help maintain the integrity of the files when I'm opening them in three different OSes?
3. Any suggestions for formatting? I might be over-complicating things with the Mac formatting, so I figured I should ask while I'm here.

Misc. info:

* looking at the device properties, the exact formatting isn't shown while in Ubuntu, but I will check in Windows shortly and edit this post
* the drive is an OWC 1TB HDD
* I already have a backup of the drive, and I will update it right before I reformat too.

---

### Post by ajgreeny on 2015-02-23
The easiest format or filesystem type to be available in all three OSs will be fat32, as all others are limited on one or other of the OSs;


[LIST]
[*]NTFS is fine for Linux and Windows but not read/write for Macs.
[*]HFS+ is limited to read only in Linux, as far as I'm aware; no idea about its use in Windows.
[*]EXT# filesystems are not usable (or not safely according to many who have tried) in Windows, nor in Macs I think.
[*]FAT32 is read/write by all so should be the most flexible for you.
[/LIST]

---

