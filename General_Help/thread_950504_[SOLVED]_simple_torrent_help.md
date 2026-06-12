---
title: "[SOLVED] simple torrent help"
date: 2008-10-17
forum: General Help
---

### Post by unknown25 on 2008-10-17
helo guys!!!!i hav been searching ubuntu forums for an easy way to share torrent downloading in ubuntu nd xp!!nd i couldnt understand anything!!!im new at ubuntu!!!i installed wine nd then installed utorrent!!i saw in many posts tat we shuld save in same location as in xp..!!but i cant do tat!!!wen i try to save it just gives option for C drive and Z drive!!!in my xp i hav downloaded the torrent abt 8%(100mb)i cant afford to do it again!!!so pls guys help me!!my D drive is NTFS nd c is Fat32!!!!so guys pls gimme out a very easy nd simple procedure to do it!!!!

---

### Post by Elfy on 2008-10-17
Is this a wubi install or did you install from the livecd to a seperate partition. Please open a terminal from accessories and run a terminal, use this command and paste the outputs you get

```
sudo fdisk -l
df -h
```

Please do not use exclamation marks like that in posts.

---

### Post by ajgreeny on 2008-10-17
I'm afraid I can't quite figure out what you want to do, but it sounds as if you want to save the downloaded torrent file (or part file if you stop it) to both your windows and ubuntu OSs.  I should have thought it was easier to just save it in one and then copy it across to the other.   you can do that in ubuntu without problem, in windows you will need to install a utility, eg explore2fs, to read the ext3 file system first, and then you can copy across.  Perhaps I didn't understand your question;  if so apologies for wasting your time.

---

### Post by Archmage on 2008-10-17
You could easy import the torrents or made a symbolic link on the same location.

---

### Post by unknown25 on 2008-10-17
> **Archmage said:**
> You could easy import the torrents or made a symbolic link on the same location.

how to do tat???explain a bit more!!nd thanx all guys for a quick response

---

### Post by unknown25 on 2008-10-17
> **forestpixie said:**
> Is this a wubi install or did you install from the livecd to a seperate partition. Please open a terminal from accessories and run a terminal, use this command and paste the outputs you get

```
sudo fdisk -l
df -h
```

Please do not use exclamation marks like that in posts.

here is the output```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x005d005d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        7684    41238855    f  W95 Ext'd (LBA)
/dev/sda3            7685        9729    16426462+  83  Linux
/dev/sda5            2551        5450    23294218+   7  HPFS/NTFS
/dev/sda6            5738        7589    14876158+   7  HPFS/NTFS
/dev/sda7            7590        7684      763056   82  Linux swap / Solaris
/dev/sda8   *        5451        5716     2136613+  83  Linux
/dev/sda9            5717        5737      168651   82  Linux swap / Solaris

Partition table entries are not in disk order

```

after tis i get lyk tis :akash@akash-desktop:~$ df -h
nd wen i click enter i get tis output
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              16G  2.7G   13G  18% /
varrun                188M   96K  188M   1% /var/run
varlock               188M     0  188M   0% /var/lock
udev                  188M   92K  188M   1% /dev
devshm                188M     0  188M   0% /dev/shm
lrm                   188M   34M  154M  19% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0              18M   18M     0 100% /media/cdrom0

```

---

### Post by Elfy on 2008-10-17
I would install ntfs-config and let it auto mount your ntfs partitions, after it's installed there will be a tool in system > tools menu, open that and choose which drives you want to have mounted at boot and then you should be able to use them after a reboot..

```
sudo apt-get install ntfs-config
```

---

### Post by unknown25 on 2008-10-17
> **forestpixie said:**
> I would install ntfs-config and let it auto mount your ntfs partitions, after it's installed there will be a tool in system > tools menu, open that and choose which drives you want to have mounted at boot and then you should be able to use them after a reboot..

```
sudo apt-get install ntfs-config
```

wat is the tools name:confused:i cant find anything:confused::(

---

### Post by Elfy on 2008-10-17
ntfs config I think, not sure but I doubt if you have many options available in the system tools menu

---

### Post by unknown25 on 2008-10-17
> **forestpixie said:**
> ntfs config I think, not sure but I doubt if you have many options available in the system tools menu
bro can u say the exact procedure to do it in full detail:confused:

i just want to do it:(.pls

---

### Post by Elfy on 2008-10-17
If you've done sudo apt-get install ntfs-config and found it in the menu then I don't really know what it is you expect me to be able to do?

---

### Post by unknown25 on 2008-10-17
> **forestpixie said:**
> If you've done sudo apt-get install ntfs-config and found it in the menu then I don't really know what it is you expect me to be able to do?


didnt get u bro.....nd ther are many options in in preferences nd administrator under system...bro as i already mentioned im a very new person to ubuntu..so i dont know even how to chnage background then how do u expect me to search an option like tis n mount nd etc.....Im Sorry For the Inconvenience Caused By Me [-o<

---

### Post by Elfy on 2008-10-17
Perhaps you should let me know exactly what options you have in the system tools menu :)

It isn't in the the system > preferences or system > admin menus - it should be on it's own in the applications menu.

From a terminal run ```
alacarte
```
That will open the menu editor - in the right hand pane, make sure that System Tools has a tick in the box.

---

### Post by unknown25 on 2008-10-17
> **forestpixie said:**
> Perhaps you should let me know exactly what options you have in the system tools menu :)

It isn't in the the system > preferences or system > admin menus - it should be on it's own in the applications menu.

From a terminal run ```
alacarte
```
That will open the menu editor - in the right hand pane, make sure that System Tools has a tick in the box.

ya i got a option under applications>systemtools>NTFS configuration tool

now wat should i do??i dont know how to use it:confused:

---

### Post by Elfy on 2008-10-18
OPen the tool - check the box for drives you want to mount [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#The](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#The) Automatic Way

---

### Post by loser28 on 2008-10-18
[http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)    hehe :lolflag:

---

### Post by stinger30au on 2008-10-18
if you still have xp running on your pc let it finish the torrent d/l

once it is done you are free to burn the data as you wish

---

### Post by unknown25 on 2008-10-18
> **stinger30au said:**
> if you still have xp running on your pc let it finish the torrent d/l

once it is done you are free to burn the data as you wish


my ubuntu internet speed is very speed than xp..nd if ther r viruses in tat torrent then i wont hav any problem is i download through ubuntu......

---

### Post by unknown25 on 2008-10-18
> **forestpixie said:**
> OPen the tool - check the box for drives you want to mount [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#The](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#The) Automatic Way

bro veryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryveryv thank you for the help!!!i wish i could give u 1000reps points!!!!

---

### Post by Elfy on 2008-10-18
Screenshot of what it's asking for please, I only used the tool once a long time ago, but I don't remember it being harder than ticking the box and rebooting

To attach screenshot look here [http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4)

---

### Post by Elfy on 2008-10-18
good :D

---

