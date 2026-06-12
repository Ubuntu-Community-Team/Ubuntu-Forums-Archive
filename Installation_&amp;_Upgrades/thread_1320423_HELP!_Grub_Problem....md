---
title: "HELP! Grub Problem..."
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by damastax68 on 2009-11-09
Help, I upgraded windows lost grub, tried to restore then i got error 2 now i used grub super disk and now i can boot windows but when i set it to the hdd that ubuntu is on it goes to the grub prompt.

---

### Post by presence1960 on 2009-11-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by damastax68 on 2009-11-09
```
derek@derek-desktop:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for derek: 
bash: /home/derek/Desktop/boot_info_script*.sh: No such file or directory

```
This is all I get... plz help me...

---

### Post by skyiscrying on 2009-11-09
You have to download the Boot Info Script from SourceForge.net ......click on the link in his reply to you.

---

### Post by presence1960 on 2009-11-09
> **skyiscrying said:**
> You have to download the Boot Info Script from SourceForge.net ......click on the link in his reply to you.

**and place the file on the desktop prior to running the terminal command**

---

