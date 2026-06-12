---
title: "Dualboot sharing program settings between Ubuntu and WinXP"
date: 2008-12-02
forum: General Help
---

### Post by Hansje on 2008-12-02
Hi,

I have a dual boot system Windows XP SP3 / Ubuntu 8.04 LTS. So far I like Ubuntu very much. There are some things I want to improve.
For Thunderbrid and Firefox I can share my profile folder, which is great! Now I like to do the same for programs like Filezilla, PHP5 server, mysql server and bluefish. I looked around but can not find any info on how to do this. The PHP5 server should be easy, just point to the same 'www' directory I guess. I tried it by editing php.ini, but with no result, I am missing something.
Can anyone point me in the right direction?

Thanks in advance:)

---

### Post by Hansje on 2008-12-03
For FileZilla I managed to edit the fzdefaults.xml file so both FileZilla installations use the same config dir.
There are still some problems:
- In Ubuntu the file permission is read only... It runs perfectly if I run filezilla as root (sudo filezilla) If I run Nautilus as root (sudo nautilus) I'm not able to change anything to the permissions of the xml files in the configdir.
- For all my websites I configured (in Windows) a local directory. the local directory in Ubuntu is not the same, so it won't work.
Maybe this info is usefull:
I started configuring FileZilla on my XP installation, copied the config-dir to the new location on a NTFS partition, edited fzdefaults.xml for both Ubuntu and Windows. In windows everything is fine.

---

