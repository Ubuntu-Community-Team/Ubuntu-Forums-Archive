---
title: "Unrecoverable External HDD"
date: 2019-05-19
forum: Hardware
---

### Post by shane_faulkinbury2 on 2019-05-19
I have this WD 2 TB HDD and I've tried everything from GParted to Disk to format it.  I had LUKS using FAT of course, but needed to recover some files, but couldn't so I wanted to reformat it and move files over from my other HDD, but couldn't complete the task!

Is there any terminal commands I could try before trying a DBanning it in a last ditch effort and then trashing it if that doesn't work?  :confused:

---

### Post by carl4926 on 2019-05-19
Have you tried fdisk from the terminal?
I often find it works in difficult situations
Be sure to identify your device and change sdX to whatever it is eg; sdb

[COLOR=#000000][FONT=&amp]Typically, you would simply start fdisk:[/FONT][/COLOR]
  ```
# fdisk /dev/sdX
```
[COLOR=#000000][FONT=&amp]and select:[/FONT][/COLOR]
  o   create a new empty DOS partition table
[COLOR=#000000][FONT=&amp]and then:[/FONT][/COLOR]
  n   add a new partition
[COLOR=#000000][FONT=&amp](primary, number 1, default size to use the entire device)[/FONT][/COLOR]
  t   change a partition's system id
[COLOR=#000000][FONT=&amp]Use type 7, NTFS or select as you require
[/FONT][/COLOR]w   write table to disk and exit
[COLOR=#000000][FONT=&amp]Finally:[/FONT][/COLOR]
  # mkfs.msdos -n SOME_NAME /dev/sdX1

---

### Post by shane_faulkinbury2 on 2019-05-19
?
```
fdisk /dev/sda5

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


fdisk: cannot open /dev/sda5: Permission denied
sup@sup-HP-Compaq-8200-Elite-SFF-PC:~$ sudo su
root@sup-HP-Compaq-8200-Elite-SFF-PC:/home/sup# fdisk /dev/sda5


Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


The old crypto_LUKS signature will be removed by a write command.


Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0xcfdfed47.


Command (m for help):
```

---

### Post by crip720 on 2019-05-19
Make absolutely sure that is the right partition.  Usually sda refers to an internal drive.

---

### Post by shane_faulkinbury2 on 2019-05-19
I get it now, but if my primary is sda5 that I want to format how do I set it to that?  I don't want to format my computers HDD!

---

### Post by shane_faulkinbury2 on 2019-05-19
Sorry I didn't see your post [COLOR=#000000]crip720, I see only one LUKS sda, so that means the external is gone since my computers HDD is also LUKS?[/COLOR]

---

### Post by crip720 on 2019-05-19
Will disks or gparted see the external, one of them should let you know the 'sd?' of external?

---

### Post by shane_faulkinbury2 on 2019-05-19
I don't see it!

```
NAME                 MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTloop0                  7:0    0 225.1M  1 loop  /snap/webstorm/90
loop1                  7:1    0 150.2M  1 loop  /snap/opera/36
loop2                  7:2    0   174M  1 loop  /snap/spotify/34
loop3                  7:3    0  93.7M  1 loop  /snap/telegram-desktop/715
loop4                  7:4    0 150.2M  1 loop  /snap/opera/37
loop5                  7:5    0    16K  1 loop  /snap/software-boutique/39
loop6                  7:6    0  91.9M  1 loop  /snap/amparerandompassword/1
loop7                  7:7    0  34.8M  1 loop  /snap/gtk-common-themes/1122
loop8                  7:8    0  52.9M  1 loop  /snap/john-the-ripper/290
loop9                  7:9    0    95M  1 loop  /snap/darktable/32
loop10                 7:10   0  34.6M  1 loop  /snap/gtk-common-themes/818
loop11                 7:11   0  89.3M  1 loop  /snap/core/6673
loop12                 7:12   0 173.9M  1 loop  /snap/signal-desktop/108
loop13                 7:13   0   168M  1 loop  /snap/netbeans/5
loop14                 7:14   0  24.8M  1 loop  /snap/hugo/4735
loop15                 7:15   0  19.6M  1 loop  /snap/skrooge/14
loop16                 7:16   0 546.2M  1 loop  /snap/rider/8
loop17                 7:17   0 106.7M  1 loop  /snap/monento/5
loop18                 7:18   0  21.1M  1 loop  /snap/python36-jamesh/20
loop19                 7:19   0  52.7M  1 loop  /snap/john-the-ripper/297
loop20                 7:20   0  89.4M  1 loop  /snap/core/6818
loop21                 7:21   0  14.9M  1 loop  /snap/chromium-ffmpeg/11
loop22                 7:22   0  86.3M  1 loop  /snap/ubuntu-mate-welcome/335
loop23                 7:23   0  87.9M  1 loop  /snap/go/3540
loop24                 7:24   0   6.4M  1 loop  /snap/syncthing/361
loop25                 7:25   0 101.9M  1 loop  /snap/darktable/38
loop26                 7:26   0 101.9M  1 loop  /snap/darktable/35
loop27                 7:27   0 140.7M  1 loop  /snap/gnome-3-26-1604/82
loop28                 7:28   0  35.3M  1 loop  /snap/gtk-common-themes/1198
loop29                 7:29   0  86.7M  1 loop  /snap/ubuntu-mate-welcome/319
loop30                 7:30   0 140.7M  1 loop  /snap/gnome-3-26-1604/78
loop31                 7:31   0  87.9M  1 loop  /snap/go/3584
loop32                 7:32   0  93.7M  1 loop  /snap/telegram-desktop/737
loop33                 7:33   0 456.4M  1 loop  /snap/wine-platform/125
loop34                 7:34   0  21.4M  1 loop  /snap/chromium-ffmpeg/13
loop35                 7:35   0  24.8M  1 loop  /snap/hugo/4624
loop36                 7:36   0 225.2M  1 loop  /snap/webstorm/92
loop37                 7:37   0   6.4M  1 loop  /snap/syncthing/358
loop38                 7:38   0 173.7M  1 loop  /snap/signal-desktop/107
loop39                 7:39   0 140.7M  1 loop  /snap/gnome-3-26-1604/74
loop40                 7:40   0 150.2M  1 loop  /snap/opera/35
loop41                 7:41   0  53.7M  1 loop  /snap/core18/731
loop42                 7:42   0  98.6M  1 loop  /snap/brackets/99
loop43                 7:43   0 104.1M  1 loop  /snap/brackets/107
loop44                 7:44   0 456.4M  1 loop  /snap/wine-platform/128
loop45                 7:45   0 174.5M  1 loop  /snap/spotify/32
loop46                 7:46   0    88M  1 loop  /snap/go/3739
loop47                 7:47   0 503.3M  1 loop  /snap/rider/17
loop48                 7:48   0 222.2M  1 loop  /snap/webstorm/86
loop49                 7:49   0 100.7M  1 loop  /snap/brackets/104
loop50                 7:50   0 546.1M  1 loop  /snap/rider/7
loop51                 7:51   0  12.9M  1 loop  /snap/tor-middle-relay/269
loop52                 7:52   0     4M  1 loop  /snap/gnome-calculator/352
loop53                 7:53   0 173.9M  1 loop  /snap/signal-desktop/109
loop54                 7:54   0  91.1M  1 loop  /snap/core/6531
loop55                 7:55   0   744K  1 loop  /snap/pass-hash/7
loop56                 7:56   0   6.4M  1 loop  /snap/syncthing/352
loop57                 7:57   0  24.8M  1 loop  /snap/hugo/4529
loop58                 7:58   0  53.7M  1 loop  /snap/core18/941
loop59                 7:59   0   2.3M  1 loop  /snap/gnome-calculator/260
loop60                 7:60   0  53.7M  1 loop  /snap/core18/782
loop61                 7:61   0  17.6M  1 loop  /snap/chromium-ffmpeg/9
loop62                 7:62   0 456.4M  1 loop  /snap/wine-platform/122
loop63                 7:63   0   151M  1 loop  /snap/gnome-3-28-1804/31
loop64                 7:64   0     4M  1 loop  /snap/gnome-calculator/406
loop65                 7:65   0 265.4M  1 loop  /snap/kde-frameworks-5-core18/29
loop66                 7:66   0  52.9M  1 loop  /snap/john-the-ripper/283
loop67                 7:67   0   151M  1 loop  /snap/gnome-3-28-1804/40
loop68                 7:68   0  93.6M  1 loop  /snap/telegram-desktop/663
loop69                 7:69   0  71.7M  1 loop  /snap/software-boutique/31
loop70                 7:70   0 381.1M  1 loop  /snap/netbeans/6
loop71                 7:71   0 180.2M  1 loop  /snap/spotify/35
loop72                 7:72   0  71.6M  1 loop  /snap/simplekey/1
loop73                 7:73   0 113.6M  1 loop  /snap/moneydance/2
loop74                 7:74   0  86.7M  1 loop  /snap/ubuntu-mate-welcome/324
loop75                 7:75   0  88.8M  1 loop  /snap/nextcloud-client/10
loop76                 7:76   0   151M  1 loop  /snap/gnome-3-28-1804/36
sda                    8:0    0 931.5G  0 disk  
&#9500;&#9472;sda1                 8:1    0   731M  0 part  /boot
&#9500;&#9472;sda2                 8:2    0     1K  0 part  
&#9492;&#9472;sda5                 8:5    0 930.8G  0 part  
  &#9492;&#9472;sda5_crypt       253:0    0 930.8G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root
    &#9474;                253:1    0 929.8G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1
                     253:2    0   976M  0 lvm   [SWAP]
sdb                    8:16   0   1.8T  0 disk  
sr0                   11:0    1  1024M  0 rom 
```

---

### Post by shane_faulkinbury2 on 2019-05-19
Unless sda is my main and sda5 is the external!

---

### Post by crip720 on 2019-05-19
sdb is external.  sda is a 1TB drive, anything with sda is on that drive.  sdb is a 2TB drive, the one you want to fix.  Go back to carl's post #2, and change the sdX to sdb and you should be good to go.  This is only good if you only have the internal and external drive connected, if you have any other drives(USB, hard drives) connected, don't do anything.  Unfortunately this about as much as I know.  Good luck.

---

### Post by shane_faulkinbury2 on 2019-05-20
Thanks guys, fdisk worked to create a new 2 TB NTFS partition.  Now I'm trying Disk to reformat to FAT, but it's going to take 14 hours 35 minutes! I'll report back tomorrow!  :D

---

### Post by crip720 on 2019-05-20
Here is a nice simple instruction for fdisk for future use.  [https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](https://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

---

### Post by shane_faulkinbury2 on 2019-05-27
Sorry guys, I was so happy I totally forgot about this! Your idea worked perfect and I recovered the drive then rewrote it to FAT and loaded it back up!  Now I can hold of on buying a new one.  Thanks for saving me the cash!  :P:popcorn:

---

