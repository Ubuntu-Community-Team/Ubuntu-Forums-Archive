---
title: "Symbolic link to second harddisk/shortcut desktop on Ubuntu 21-10"
date: 2022-07-22
forum: Hardware
---

### Post by robertj2022 on 2022-07-22
Hi,
I want on my desktop a shortcut to a map on a 2e disk on my Ubuntu 21-10 machine, I made a symbolic link with the ¨ln -command" in the terminal. It was succesfull so far, I have an icon on my desktop, but with a little red cross. I can´t open the map to see the content. I see that root is the owner, maybe that is the problem.I tried to change the ownership with the ¨chown" command, but that didn´t work.
I want to see the content of the map by dubble clicking the icon, of course. How can I fix this?

Gr,
RobertJ

---

### Post by guiverc on 2022-07-22
Ubuntu 21.10 or the 2021-October release is EOL (*end of life*) so I'd plan your *release-upgrade* **asap** to Ubuntu 22.04 LTS.

Notice can be found here [https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/](https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/)  and it contains [an upgrade link]("https://help.ubuntu.com/community/JammyUpgrades") too that maybe helpful.

If your command was

```
ln -command
```

I'd not expect anything but an error, or at least something unhelpful.   Sorry I don't understand what you were trying to do though, so I maybe missing something & someone else maybe more helpful.

---

### Post by ajgreeny on 2022-07-22
Ubuntu 21.10 is now EOL so you really must install a fully supported version; I suggest either 20.04 or 22.04.

There is not enough detail to help you at present with the problem you have so please show us the output of commands ```
sudo fdisk -l
``` followed by ```
sudo blkid -c /dev/null
```

Assuming the disk on which the map is sitting is formatted to a Linux filesystem such as ext4, it will by default be owned by root, as you have found.
It should, however, be easy to change the ownership to your user, which you say you tried but did not tell us what command you used.
Those command should give us enough information to be able to help you more.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by robertj2022 on 2022-07-22
Thanks for the replies!

I made the link with the command:
```
sudo ln -s /mnt/2eschijf/rob /home/robertj/Bureaublad
```

I tried to change the ownership with:
```
sudo chown robertj  /mnt/2eSchijf/rob
```

Output sudo fdisk -l :

```
Schijf /dev/sda: 931,51 GiB, 1000204886016 bytes, 1953525168 sectoren
Disk model: TOSHIBA DT01ACA1
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 4096 bytes
In-/uitvoergrootte (minimaal/optimaal): 4096 bytes / 4096 bytes
Schijflabeltype: dos
Schijf-ID: 0x000148e7

Apparaat   Op. Begin      Einde   Sectoren Grootte ID Type
/dev/sda1  *    2048 1953523711 1953521664  931,5G 83 Linux


Schijf /dev/sdb: 931,51 GiB, 1000204886016 bytes, 1953525168 sectoren
Disk model: ST1000DM010-2EP1
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 4096 bytes
In-/uitvoergrootte (minimaal/optimaal): 4096 bytes / 4096 bytes
Schijflabeltype: gpt
Schijf-ID: CBB2E762-0BF1-45F7-A7DE-1FD68D57287A

Apparaat     Begin      Einde   Sectoren Grootte Type
/dev/sdb1     2048    1050623    1048576    512M EFI-systeem
/dev/sdb2  1050624 1953525134 1952474511    931G Linux bestandssysteem

```

Output -->sudo blkid -c /dev/null
```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="64b85838-cf10-49ab-a46f-c655ea89cf58" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="000148e7-01"
/dev/sdb1: UUID="4927-F06A" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="b0696adc-405f-4a52-8f78-05bd866a9152"
/dev/sdb2: UUID="6a0f2c44-e9fa-4303-9a08-ad6f6cbb7e8e" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="cb8f8120-69a4-4046-a1db-b4cc4ff9ddd7"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"


```

After the command:
```
sudo chown robertj /mnt/2eSchijf/rob 
```
there was no error message:P

thanks in advance

---

### Post by oldfred on 2022-07-22
I mount a data partition and then link folders inside that partition.
For a new install, I have script that creates mount point, changes permissions & ownership & links folders.
First few times I did it manually and then said why am I redoing the same thing over & over. I have multiple test installs where I want same data. 

These are all essentially the same:
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

