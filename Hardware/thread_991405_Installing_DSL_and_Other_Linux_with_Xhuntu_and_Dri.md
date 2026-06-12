---
title: "Installing DSL and Other Linux with Xhuntu and Drivers PL HELP ME Thanks"
date: 2008-11-23
forum: Hardware
---

### Post by sieger007 on 2008-11-23
Hi 
All of a sudden I am getting linux mania with so many free models available :
I have chosen to install as follows :
 /dev/sda9 -- > DSL 1.2g 
 /dev/sda10 ---> Xbuntu  ( 2.5gigs) 
 /dev/sda7 - > Feather ( 900mb) 
 /dev/Sda8 --> Puppy ( 900mb)
 /dev/sda3 --> opensuse 11  ( 4.2g already installed ) 
 /dev/sda6 ---> 1g common swap for all . 
I used Yast2 to make the partitions . ALL OF THEM  in ext3  and ALL except for OpenSuse11 are Logical 

Partitions from an extended Windows Vista Partiton which I resized.

Now I made a bootable DSL Cd....
Booted fine.
I used Frugal - Grub option to start and install. 
it asked me what partition you want it to load image . 
I entered hda9 ../dev/hda9 no such partition...then 
sda9 same problem
I went to the terminal and typed 
sudo -u root dsl-hdinstall
and it gave an equivalent message ...I guess not the same words.

Questions ....: 
<> Dear Friends....NOW that my partitions are ready how can I install DSL to my already existing /ext3 

partition.
<> ALSO since SUSE11 in already installed, I would NOT like it do a grub install. I just want to 

install all these linux distros and have them indexed in the SUSE loader. How should I do that ?
Can some one help PLEASE.
<>Also I would like to know how can i install interpro wireless 495 abgn drivers for linux
<> I have an ASUS F3SV Laptop with Webcam . T7300  where can I download the webcam drivers for linux
Thanks galore
Happy thanksgiving.
Bye
San

---

