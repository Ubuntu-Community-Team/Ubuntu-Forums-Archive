---
title: "Pioneer optical drive not communicating with/ recognized by programs"
date: 2022-01-15
forum: Hardware
---

### Post by drumone on 2022-01-15
I have a brand new custom built system with a Pioneer BDR-2212 internal blu-ray writer installed. For reasons I can't determine, the drive will not communicate with/be recognized by the programs (VLC and MakeMKV)  on my OS. I have tried every command I can find on the net to fix this. MakeMKV gives this error: "The program can't find any usable optical drives." VLC keeps giving this error:    
[COLOR=#ff0000]
Playback failure:[/COLOR]

 [COLOR=#000000]DVDRead could not open the disc "/dev/cdrom".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/cdrom'. Check the log for details.

I know for a fact that the system recognizes the drive as being there. At this point, I'm ready to leave Ubuntu behind after many years of using the OS. This is just a frustrating experience. I just need it to work. Any suggestions on how I can fix this will be greatly appreciated. I'm comfortable using a terminal at a basic level, but specific line commands will need to be provided. Thanks in advance.
[/COLOR]

---

### Post by Bashing-om on 2022-01-16
Neil_Harbel; Hello -

I do not use either MakeMKV or VLC so all I can do just get this ball rolling for you.

> 
I know for a fact that the system recognizes the drive as being there.


Show us what the kernel is aware of:
post back the result of terminal command:
```

sudo lshw -C Disk

```

see where we go from here

---

### Post by Holger_Gehrke on 2022-01-16
First use 'lsblk' to find the actual device name for your optical drive. It's probably (/dev/)'sr0'. In vlc open Tools->Preferences, Input/Codecs and change 'Default optical device' from '/dev/cdrom' to '/dev/' + the name you found. '/dev/cdrom' (and /dev/dvd and probably some other name for BlueRay) is just a symbolic link created by udev if this kind of device is found; if this link wasn't created for some reason but the device is there and you can use it then using the real name instead of the link should work.

Holger

---

### Post by drumone on 2022-01-16
This is what I got back from that command:

  ```
*-namespace               
       description: NVMe namespace
       physical id: 1
       logical name: /dev/nvme0n1
       size: 931GiB (1TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: guid=135f7fb9-aea4-4478-af9e-b6df4bc29081 logicalsectorsize=512 sectorsize=512
  *-namespace
       description: NVMe namespace
       physical id: 1
       logical name: /dev/nvme1n1
       size: 931GiB (1TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: guid=c529149c-f134-4337-8276-487ee41aadf0 logicalsectorsize=512 sectorsize=512
  *-disk:0
       description: SCSI Disk
       product: SD/MMC
       vendor: Generic-
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 1.00
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sda
  *-disk:1
       description: SCSI Disk
       product: Compact Flash
       vendor: Generic-
       physical id: 0.0.1
       bus info: scsi@3:0.0.1
       logical name: /dev/sdb
       version: 1.01
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:2
       description: SCSI Disk
       product: SM/xD-Picture
       vendor: Generic-
       physical id: 0.0.2
       bus info: scsi@3:0.0.2
       logical name: /dev/sdc
       version: 1.02
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:3
       description: SCSI Disk
       product: MS/MS-Pro
       vendor: Generic-
       physical id: 0.0.3
       bus info: scsi@3:0.0.3
       logical name: /dev/sdd
       version: 1.03
       serial: 3
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open
```

---

### Post by drumone on 2022-01-16
Holger, this is what your command provided:

NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0     9M  1 loop /snap/canonical-livepatch/126
loop2         7:2    0  55.5M  1 loop /snap/core18/2253
loop3         7:3    0  61.9M  1 loop /snap/core20/1270
loop4         7:4    0   219M  1 loop /snap/gnome-3-34-1804/77
loop5         7:5    0 255.6M  1 loop /snap/gnome-3-34-1804/36
loop6         7:6    0  43.3M  1 loop /snap/snapd/14295
loop7         7:7    0  55.5M  1 loop /snap/core18/2284
loop8         7:8    0  99.4M  1 loop /snap/core/11993
loop9         7:9    0 295.7M  1 loop /snap/vlc/2344
loop10        7:10   0  65.2M  1 loop /snap/gtk-common-themes/1519
loop11        7:11   0  54.2M  1 loop /snap/snap-store/558
loop12        7:12   0  62.1M  1 loop /snap/gtk-common-themes/1506
loop13        7:13   0  49.8M  1 loop /snap/snap-store/467
loop14        7:14   0 247.9M  1 loop /snap/gnome-3-38-2004/87
loop15        7:15   0  29.9M  1 loop /snap/snapd/8542
sr0          11:0    1  1024M  0 rom  
nvme1n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme1n1p1 259:2    0  47.7G  0 part /
&#9500;&#9472;nvme1n1p2 259:3    0    61G  0 part [SWAP]
&#9492;&#9472;nvme1n1p3 259:4    0 822.8G  0 part /home
nvme0n1     259:1    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1 259:5    0   100M  0 part /boot/efi
&#9500;&#9472;nvme0n1p2 259:6    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:7    0 930.8G  0 part 
&#9492;&#9472;nvme0n1p4 259:8    0   593M  0 part

---

### Post by drumone on 2022-01-16
Holger, the default optical drive was already "/dev/sr0". Could you be more specific as to the changes I need to make? My apologies, but I'm still learning how to do this. I start my degree in software development (at the age of 43!) in March. Boy do I have a lot to learn! Thanks to Holger and Bashing for your help!!!

---

### Post by Yellow Pasque on 2022-01-18
> configuration: status=open 

Was the drive physically open when you ran the command? If not, that seems suspicious. It should have been status=nodisc or status=ready depending on whether a disc was in the drive.

EDIT: Another trick would be to take a known good bootable DVD and try to boot with it (assuming mobo is capable of that). If that doesn't work, then your problem runs deeper than the OS level.

---

### Post by drumone on 2022-01-19
I don't think it was open when I ran the command. I'm also running into issues with the drive on the Windows side of my machine too. I'm checking into it being a hardware problem. Pioneer hasn't responded to me yet. If I don't get anything back from them soon, I'm going to return the drive and try another one if I have too. My Amazon return window is coming up quick. I'll post more when I know something more.

---

### Post by drumone on 2022-01-26
It looks like this is a hardware issue. I'm sending back the drive. The seller on Amazon wasn't willing to work with me. Pioneer requires me to ship it to them at my cost. I can buy another drive for less than the price of shipping this one back for warranty coverage. I'm thinking of looking at LG now. Thanks to those of you that offered trouble shooting suggestions.

---

### Post by drumone on 2022-02-08
Well...I feel a little foolish, but it wasn't the hardware. Out of desperation, I took my optical drives and the whole tower to a local computer repair shop with the intention of having them test the optical drives. They diagnosed the problem and corrected it for free!! Strangely enough, it turned out to be the fact that I had over clocked my system. I used the utilities that came with the motherboard to do the overclocking. Once everything was reset to factory norms it all worked properly again. I verified this by running the one of the overclocking programs that's a part of the BIOS. BAM! Everything went sideways again. I reset it back to factory defaults and all worked correctly. Considering I don't really have a need for overclocking the system, it's staying the way it is. Lesson learned!

---

