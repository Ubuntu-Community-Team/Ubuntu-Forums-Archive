---
title: "[SOLVED] df reports root partition is 100% in use"
date: 2008-09-15
forum: General Help
---

### Post by wjp.reg on 2008-09-15
Can someone tell me how to investigate the reasons why my /dev/sda1 filesystem is reported to be 100% in use??



```
wolf@ubuntu-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   14G     0 100% /
varrun                506M  224K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6              38G  2.3G   34G   7% /home
/dev/sda5              24G  2.6G   21G  12% /mnt/shared
overflow              1.0M   80K  944K   8% /tmp
gvfs-fuse-daemon       14G   14G     0 100% /home/wolf/.gvfs
/dev/sdd1             299G   46G  253G  16% /media/Elements_

```

Not sure how to proceed. Only discovered the "problem" after the latest update and the update manager reporting that it could not write some files because of a lack of space. Suggested I run **dpkg --configure -a**, but this failed also.

I checked **fstab** and noticed a second /swap partition on a different drive (sdc) I have installed, and commented it out (worth a try, no? :-)).  After rebooting I again tried **dpkg --configure -a** and this time it was suggested I reinstall **smbfs**, which was part of the failed upgrade. This worked, but I still don't know why my filesystem on /dev/sda1 is reported to be full.

My **fstab** reads as follows:
```
wolf@ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=20645c10-948e-4871-9de9-693f2b39e545 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b1c03e77-af4d-41c5-a5f1-317815cf0fde /home           ext3    relatime        0       2
# /dev/sda5
UUID=608E-25F6  /mnt/shared     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=b065a9fc-463b-43a5-9a19-a1031f4357f1 none            swap    sw              0       0
# /dev/sdc3
# UUID=ac6180c2-a0c1-42ee-9b3e-9f9442bdf3e1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks in advance,

P.S. FWIW, this is _not_ my laptop config as listed in my signature below, but my main desktop config.

---

### Post by iaculallad on 2008-09-15
You could try using the Disk Usage Analyser to check your / directory if it helps.
Applications—>Accessories—>Disk Usage Analyser

---

### Post by wjp.reg on 2008-09-15
Thanks for your reply iaculallad;

I have run the disk usage gui and it looks great, but I didn't get any clues as to the cause for my filesystem showing no available free space.

I can't imagine having used 14Gs for /.

Any idea how I might proceed?

Thanks

---

### Post by liyanricaoqiyue1314 on 2008-09-15
To the married-Niu.      If that is not a Jiangsu-door furniture carpenter, Mei Niu doomed to marry a village of pottery Bozi wife. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Bozi home village of Tao Tao willing to spend with her sister-Niu for the pro-Gege Mei-yun.      Peach blossom in full bloom one day. - Niu made a home in Jiangsu's Wang is said to be a carpenter, he is to help fight-Niu furniture for the dowry. [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Wang linked to 20, a carpenter, keep-the first, Meiqingmuxiu, Douren favorite. [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)     Niu Mei Mei Nanzi never seen this, just Piaoyi Yan echocardiography have the feeling, but also face slightly Fatang.      Fortunately, not being the King is busy working carpenter found. [Runescape quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)     At this time, coincides with Nongmang season. Meiyun to Lane busy farm work, cooking at home-Niu hospitality Wang carpenter.      Wang carpenter while living doing carpentry, with the side-Niu chat.      Wang Mei Niu carpenter asked a lot of problems. [AOC Power Leveling](http://www.aoc-power-leveling.org)     Wang Mei Niu was a carpenter asked Mianhongerchi,. Thanks to Wang carpenter only pay attention to work and do not pay attention to observe.      Niu and Wang Mei carpenter contact Shijianyichang, bolder gradually larger. One day, she assured Wang carpenter questions:      "You have mountains there?? "      "We are the Great Plains there," says Wang carpenter replied, "do not see Hill. Tianba are all big."      "You have Baogu family, Yang Yu eat?? "Wang Mei Niu asked carpenter.      "We have Baogu home, not Yang Yu, but we do not eat Baogu." Wang-work carpenter Bianyue, "that is used to feed the finishing pigs."      "That is what you eat? "Mei Niu continue to ask.      "We eat rice," Wang carpenter said, "so throughout the year."      "Rice Gouchi?? "Mei Niu asked.      "Gouchi year of 2003 miles." Wang carpenter said, "every year sold several tons of surplus grain."       - Niu did not know "several tons of surplus grain" is the span mean, it inconvenient to ask for fear their Mochu Xi Wang carpenter laugh. [Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Day night, thinking about the day-Niu Wang carpenter, then a sleepless night.       Three days later, Wang Mei Niu carpenter Datan to the marriage, on the sorry for her, advised her out of the poor mountain valley, the mountains to. [Buy Aoc Power Leveling](http://www.aoc-power-leveling.org)      "To the mountains, to Gansha? "Niu-inexplicably asked.       "When my daughter-in-law ah? "Wang Xiaoxiao carpenter surreptitious manner.       Niu Mei Zhang De Crimson's face, quickly turned back to thatched houses, heart kept jumping. [Buy Age Of Conan Power Leveling](http://www.aoc-power-leveling.org)      Wang left carpenter tools, catch up with the entrance of housing.       "Really." Wang carpenter Mangshuo, "You beautiful, I love you, really like you!"       "You Bieluan said." Mei Wu Zhuolian Niu said, "I would not agree to the Columbia." [Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      "He did not take advantage of the home," Wang said Niu carpenter-advised, "Do you think escape."       "Does not work." Mei Niu shaking his head said, "I have miles to the brother-for-daughter-in-law, brother can not be left regardless." [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)      "My hands of the rich." Wang carpenter serious, "your brother to stay 5,000 yuan, he casually enough to marry the daughter-in-law." [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)      Niu Dian Ledian-head. [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)      Wang entered the house carpenter, cling-Niu, a while Kuangwen. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      - Niu homeopathy fell on the bed&#21398; [Runescape GP](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      The next day at dusk. Meiyunganwan farm work at home, no-Niu and Wang carpenter, Quejian table with red Buguo the 5000 money. Meiyun mind is the span that matter. [Rs quest](http://www.runescape-shop.com/runescape-quest/runescape-quest.php)      Six months later, Mei Yun from the hands of traffickers to buy a woman a wife. [rs money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)      Has just completed marriage. Mei Mei Yun Niu suddenly received from Jiangsu to the distress of the letter: I was fooled by Wang carpenter, a carpenter at home with his wife Wang, the children, he will I money to sell 15,000 to a local 30-year-old Bozi Wife&#21398; Come help me. [runescape shop](http://www.runescape-shop.com)      Meiyun read the letter, a sigh out: "Oh, I Yousha to be? on when the pro-change! "

---

### Post by tuxxy on 2008-09-15
Just a thought but have you checked your trash, i know the root trash can be a problem on occasions

Open a terminal and type

```
sudo find / -type d -iname *Trash* | grep Trash

```

You should now have a list of trash folders, you can use nautilus now if you want to check the contents, for example to view the roots trash you could type this

```
gksu nautilus /root/.local/share/Trash

```

---

### Post by drs305 on 2008-09-15
You can check your trash situation. Refer to the tutorial in my signature line to find all your system trash. If you haven't emptied it in a while that could be the reason your disk is full.

---

### Post by wjp.reg on 2008-09-15
Thanks to all who replied.

**drs305's** link helped me identify the root trash being the cause of my disk usage.

NOTE:  Funny thing is Disk Analyser gui still reports 100% usage even after a refresh, while **df -h** reports only 22% usage, which is what I might have expected - I prefer to believe the change reported by the **df command** ;-)

> wolf@ubuntu-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  2.9G   11G  22% /
varrun                506M  228K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  108K  506M   1% /dev
devshm                506M   72K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6              38G  2.3G   34G   7% /home
/dev/sda5              24G  2.6G   21G  12% /mnt/shared
overflow              1.0M   80K  944K   8% /tmp
gvfs-fuse-daemon       14G  2.9G   11G  22% /home/wolf/.gvfs
wolf@ubuntu-desktop:~$ 


---

### Post by tuxxy on 2008-09-15
Yes, you are best to stick with df for drive information

---

### Post by drs305 on 2008-09-15
> **wjp.reg said:**
> 
NOTE:  Funny thing is Disk Analyser gui still reports 100% usage even after a refresh, while **df -h** reports only 22% usage, which is what I might have expected - I prefer to believe the change reported by the **df command** ;-)

The top folder of Disk Usage Analyser can be pretty confusing in that it will always show 100% usage after a 'Scan Filesystem'. Like tuxxy, I rely on the CLI for getting my disk usage information in a format which is accurate and understandable. For gui-based information, the gnome-system-monitor 'File System' tab is generally fairly good (System, Administration, System Monitor).

---

