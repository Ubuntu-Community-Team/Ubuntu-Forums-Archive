---
title: "Cant read 1TB EXT3 HDD from NAS -- MDADM command error"
date: 2016-06-14
forum: Hardware
---

### Post by Stafa on 2016-06-14
Hello,

I am really struggling with this problem. i have been busy for week now..
I have a Freecom NAS with 2x 2TB HDD's in it.
Now the problem started with the freecom nas, it didnt reset and i could not connect. it didnt even shutdown..
i connected freecom support, they are helping me to get the nas working again. it doesnt react on anything, not even the reset button.

I asked the support how i can read the data from the HDD they said with linux and sended me a "guide".
I have some linux experience, so i runned it with a live usb and a external hdd docking station.
The docking station works, when i put a fat32 hdd in it and i write fdisk -l i can see it, but the nas hdd doesnt work that way.

I followed the guide i got from freecom(see below) but when i write the command mdadm -assemble --scan
it gives me a error: option -s not valid in manage mode

the same happends when i use the mdadm -assemble /dev/md0/dev/sdc5 command.

Can anybody help me? maybe its a stupid question, but i searched on the internet and i could not find and i dont wanna try other codes i dont now what they do.



The guide i received from freecom support:

[COLOR=#000000][FONT=&amp]Silver Store Linux Recovery

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]To mount RAID using Ubuntu Linux you have to install first this application "mdadm"
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]type **su** "to have a root access "[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Install mdadm[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**apt-get install mdadm**[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**fdisk -l** "This command will show a list of all HD drives connected" of RAID

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Example

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Device Start End Sectors Size Type 
/dev/sdc1 64320 4258623 4194304 2G Linux RAID 
/dev/sdc2 4258624 12647231 8388608 4G Linux RAID 
/dev/sdc3 12647232 13695807 1048576 512M Linux RAID 
/dev/sdc4 13695808 13695935 128 64K Linux RAID 
/dev/sdc5 13695936 1933659563 1919963628 915,5G Microsoft basic data

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]The data are stored on the /dev/sdc5 "Microsoft basic data"

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]with this command you will be able to read the raid[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**mdadm --assemble --scan**

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]if doesn’t show up or mount the drive, that means you have to do it manually[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]--------------------------------------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Check if the md0 is free by typing this command[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**mdadm --detail /dev/md0**

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]If it's free you will get this answer[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mdadm: cannot open /dev/md0: No such file or directory

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Now you can mount the device that contains the data[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**mdadm --assemble /dev/md0 /dev/sdc5**

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Answer 
mdadm: /dev/md0 assembled from 1 drive - need all 2 to start it (use --run to insist).

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**mdadm --assemble --run /dev/md0 /dev/sdc5**

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Answer 
mdadm: /dev/md0 has been started with 1 drive (out of 2).

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]After the last command you will be able to see the hard drive mounted with the data

[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Please note that the name of the device can be different like sdb5, sdc5, sdd5….[/FONT][/COLOR]

---

### Post by S.Haran on 2016-06-20
Hello Stafa, If your data partition is partition number 5. Then please post the output of ```
mdadm  --examine  /dev/sd?5
```

This will display the mdadm meta data on your RAID member drives and with that information additional advice can be provided.

---

