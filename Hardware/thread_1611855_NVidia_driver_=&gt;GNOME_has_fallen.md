---
title: "NVidia driver =&gt;GNOME has fallen"
date: 2010-11-02
forum: Hardware
---

### Post by PulsUA on 2010-11-02
Hello, Ubuntu Community.
I have a problem on my Ubuntu 10.10 desktop. Today I have installed NVidia proprietary driver on my Asus K42JV. Model of GPU: NVidia GeForse GT335M. After system was rebooted I had seen black display with white letters. I think it is Terminal. :) I had entered my login and password successfully and saw the command line. 
1_.How can I delete this driver using Terminal commands?_
I have decided to reinstall Ubuntu and firstly I pressed "Try Ubuntu" to watch my memory. Some folders are closed for watching. [U]
2. How can I open this folders for copying them using the liveCD?[/U]
I was thinking a lot... And I deceided to copy this 'closed' folders on my flashdrive. But how can I do it? 
3._How to copy files from memory to flashdrive using Terminal?_
This is three questions. The best variant is answer on first question, because I won't have to reinstall all programs. But It would be good to get questions on any questions. Help me, please.
And sorry for my English. :)

---

### Post by Yellow Pasque on 2010-11-02
```
sudo apt-get remove --purge nvidia-current nvidia-kernel-common nvidia-settings
```

---

### Post by PulsUA on 2010-11-02
I have used this code. Boot is ended on purple screen with Ubuntu logo or black screen. Even Terminal does not run. System is down. 
How to get rights to copy closed folders from my hdd using liveCD? Advice please

---

### Post by Neds Moar Salt on 2010-11-02
> **PulsUA said:**
> I have used this code. Boot is ended on purple screen with Ubuntu logo or black screen. Even Terminal does not run. System is down. 
How to get rights to copy closed folders from my hdd using liveCD? Advice please

open up terminal on live cd and 
```
sudo nautilus
```

---

### Post by dabl on 2010-11-02
The partition on the hdd where your data is must be mounted.

If the hdd is /dev/sda, and the partition is /dev/sda3, and if it is a ext3 filesystem, then when you have the Live CD running, you open the terminal and make a new mount point:

```
sudo mkdir -p /mnt/HDD
```

Then you mount the partition:

```
sudo mount -t ext3 /dev/sda3 /mnt/HDD
```

Now, if you have inserted your flash drive, you can just copy the files to the flash drive, with nautilus or in the terminal with "cp", or however you wish.


But, I have also heard that Ubuntu has a graphical "device mounter" that we don't have in Kubuntu, so maybe you can use that from the Live CD.

---

### Post by PulsUA on 2010-11-03
> **dabl said:**
> 
if you have inserted your flash drive, you can just copy the files to the flash drive


You don't understand. I don't have permissions to watch some folders. I want to get this permissions and just to copy this files to my external HDD.

There is a risk that if I unmount this image I will not be able to watch this folders

---

### Post by PulsUA on 2010-11-03
I have copied all my hdd files successfully. After entered 
sudo nautilus
 and
first your code I entered and saw that all folders are open!!!
Thank you.
And there is a simple question. Can I get the programs on reinstall Ubuntu using older system files?
I want to get programs replacing system files by files of my previous system. What have I to do for it? Is it possible?

---

### Post by dabl on 2010-11-03
> **PulsUA said:**
> 

And there is a simple question. Can I get the programs on reinstall Ubuntu using older system files?
I want to get programs replacing system files by files of my previous system. What have I to do for it? Is it possible?

No.  Or, I should say "bad, bad idea!".

You could install a complete Ubuntu 10.04 system, or any earlier version if you have the ISO for installation.  But you cannot install 10.04 system files on a 10.10 system -- that will result in nothing working correctly.

---

