---
title: "Errors writing to a SD card from ubuntu"
date: 2008-05-19
forum: Hardware
---

### Post by adonet on 2008-05-19
When in Ubuntu 7.10 or 8.04 I can write to a SD card that's connected to my cardreader, but the files that are written contain many errors, the file system in the directory I'm writing to on the SDcard gets corrupted (FAT32) and the SD card gets spontaneously disconnected. When booted in Windows Vista, everything works just fine.
It's the case on two different computers with different card readers.

I did copy several jpg files (250 Mb) to the SD card. All seemed to copy fine, but the test directory seems empty when unmounted in ubuntu and then hotplugged into the pocket pc device.

When replugged into the ubuntu machine, all files in the test directory got unreadable filenames.

jeroen@adonet:~$ ls /media/disk/test
ls: kan geen toegang krijgen tot /media/disk/test/b<)äysci.sze: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/cZecRUZ&#9564;.Ü&#9566;&#9569;: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/8)98)98).14!: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/¡¬&#9569;£ü£&#9569;&#9563;.&#9569;  : Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/éñ{éñsuö.îè¡: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/&#9555;ä&#9619;&#9564;&#8745;ü&#9616;&#964;.æ&#9555; : Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/&#9569;öªÑ&#9569;&#9619;&#9569;¡.¬¡&#9555;: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/&#9580;&#9575;&#9555;£&#8359;ñ  .&#8776;&#9566;&#9563;: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/a1je1re9.JE1: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/ &#8730; &#964;&#964;&#964;&#8776;&#8776;.&#8776; &#8804;: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/ykZ}sJqc.BiZ: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/&#948;&#9616;&#9616;&#8745;&#964;&#9616;&#8745;&#964;.&#9555;&#8745;&#8745;: Invoer-/uitvoerfout
ls: kan geen toegang krijgen tot /media/disk/test/¡ä¬£kÄäc.èkö: Invoer-/uitvoerfout

meaning: cant access /media/disk/test/xxxxxx: Input-/output error

My conclusion is that I cant write to this (or any) SD card from Ubuntu, while I can from windows.

Is there any driver needed in ubuntu that's not installed out of the box to write without these errors to a SD card?

Jeroen

---

