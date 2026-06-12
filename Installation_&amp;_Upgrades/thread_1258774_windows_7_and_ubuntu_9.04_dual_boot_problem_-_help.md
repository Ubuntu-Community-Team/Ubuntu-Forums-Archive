---
title: "windows 7 and ubuntu 9.04 dual boot problem - help needed"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by trojanworrier on 2009-09-05
Hello friend,

I'm new to ubuntu, so i was trying to dual boot windows 7 and ubuntu. i successfully dual booted, both windows 7 and ubuntu worked for me. I made 3 partitions:

1st partion for windows 7
2nd partition for linux
3rd partition for Data: must show up in both windows 7 and linux

but here is how i ended up:

/dev/sda1  - ntfs - 22.58 gb   <----windows

/dev/sda2  - linux-swap - 18.47 gb  , <---wanted to installed linux in this partition but                                                      i     couldnt, dont know why

/dev/sda3  - extended - 70.74 gb which has: 
      /dev/sda5  - ext3 - 67.81 gb
      /dev/sda6  - linux-swap - 2.93 gb

i wanted to use sda3 for data but linux got installed and cant see this partition in windows at it is "ext3".

:confused::confused::confused:

Please advice how do I do the following:

1st partion for windows 7
2nd partition for linux
3rd partition for Data: must show up in both windows 7 and linux

Thank You so much...

---

### Post by trinadhm on 2009-09-05
/dev/sda2 - linux-swap - 18.47 gb /dev/sda2 - linux-swap - 18.47 gb 
ubuntu could not be installed as u have made it as a linux swap partition, it is supposed to be ext3 or ext4 etc...
 
/dev/sda5 has got to be ntfs or fat to show up in both windows and ubuntu...

---

### Post by trojanworrier on 2009-09-06
Thanks a lot. Finally, Ubuntu 9.04 successfully installed. 
Thanks:popcorn:

---

