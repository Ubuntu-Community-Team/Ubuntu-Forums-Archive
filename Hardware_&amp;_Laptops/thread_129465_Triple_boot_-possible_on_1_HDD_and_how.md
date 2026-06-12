---
title: "Triple boot -possible on 1 HDD? and how?"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by Strev_123 on 2006-02-13
I've found a tutorial for getting my MP3 player running under linux but it's writen for Debian and some of the commands are unrecognised in Ubuntu (is this right?). As I'm kind of ditching windows that partition is getting smaller by the day. At the moment I have around 2GB of free space in my windows partition that I don't want in there still leaving enough for windows swap. I want to resize my windows partition to get at the 2GB of space to make a rather small 4GB partition to install Debian as all I'm gonna use it for at the moment is to access my player. My main problems are;

1. Ubuntu automatically mounts my windows partition upon booting, when I launch GParted and unmount the partition I'm unable to resize it. Will stopping it being mounted at startup enable me to resize the partition??

2. All of the above will be useless if I can't solve this... GParted informs me that I cannot have more than 4 primary partitions, which I assume I already have, otherwise why am I getting this message. Will I still be able to install Debian?

Partitions are: 

/dev/hda1 8mb
unallocated 1986mb
/dev/hda2 7021mb <-- Windows
/dev/hda3 10574mb <-- Ubuntu
/dev/hda4 extended
^^^^/dev/hda5 361mb <-- swap

Also can Debian use the existing linux swap partition as this will save space. (Need new Drive!! :mrgreen: )

---

### Post by curtis on 2006-02-13
I believe it can happily use the same swap partition.
Not sure about the other questions though, I'm half a asleep sorry.

---

### Post by lha on 2006-02-14
1. It's not a good idea to partition a drive in use. You should use a live-cd to partition.

2. You can make more logical partitions, but they have to be inside that extended partition hda4. Your troubles will be caused by the fact that you cannot move ext3 partitions. (Atleast the partition tools I know cannot.) As your root probably is ext3, you cannot move it to get more space for hda4.

I wonder what is that 8mb hda1? It looks too small to be /boot, and way too small to be anything else.

Finally, I believe you don't need Debian. Ubuntu is very similar to Debian, being derived from it, so if it works with Debian, it has very good chances to work with Ubuntu. If you'd post link to that how-to, maybe someone could tell how to translate it to Ubuntu. Also, telling what exactly doesn't work in that how-to would be useful.

---

### Post by lha on 2006-02-14
Forgot to mention that if you use hibernation, you can't share swap. Other than that, there is no reason why you couldn't use the same swap partition for both os'.

---

### Post by Strev_123 on 2006-02-14
@ Iha... The link for the HOWTO is [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article) . I believe that I could get it working but it's not very clear, phrases like > As root go in this directory and do:

      ./configure && make && make install && ldconfig  really don't make sense to me... do it where??? and what are the &&'s for? Do I have to put something in there?? A Ubuntu HOWTO for this would be really helpful as for all I know they are popular players and people new to Linux would probably ditch it 'coz their hardware doesn't work 'out of the box' or with a simple driver install. (edit: found a script on the [forums]("http://www.ubuntuforums.org/showthread.php?t=33040&") but it's written for Hoary and the line > wget "http://download.ubuntuforums.org/ubuntusetup/sources.list" in the script on page 2 doesn't work :()

Also the 8mb /dev/hda1/ partition was there when I bought the comp along with another hidden /dev/hda3/ partition which contained backups for the preloaded software which I got rid of on day one and have never ever used. I assumed it was the boot partition where GRUB was :confused:  If I can get the player to work without having to install debian, how would I go about making another partition with the spare space to store stuff but in the hda4 extended bit?

PS. Have both Ubuntu CD's burned (live and install), will live affect the configuration of my hard install?

---

### Post by lha on 2006-02-14
[QUOTE=Strev_123]@ Iha... The link for the HOWTO is [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article) . I believe that I could get it working but it's not very clear, phrases like  really don't make sense to me... do it where??? and what are the &&'s for? Do I have to put something in there?? A Ubuntu HOWTO for this would be really helpful as for all I know they are popular players and people new to Linux would probably ditch it 'coz their hardware doesn't work 'out of the box' or with a simple driver install. (edit: found a script on the [forums]("http://www.ubuntuforums.org/showthread.php?t=33040&") but it's written for Hoary and the line  in the script on page 2 doesn't work :()

Also the 8mb /dev/hda1/ partition was there when I bought the comp along with another hidden /dev/hda3/ partition which contained backups for the preloaded software which I got rid of on day one and have never ever used. I assumed it was the boot partition where GRUB was :confused:  If I can get the player to work without having to install debian, how would I go about making another partition with the spare space to store stuff but in the hda4 extended bit?

PS. Have both Ubuntu CD's burned (live and install), will live affect the configuration of my hard install?[/QUOTE]

I took a quick glimpse on both that how-to and thread, and here are some things for you:

First, you need a few packages. Use Synaptic or apt-get to install following packages:
build-essential
gcc
g++
libgtk2.0-dev
libgnomeui-dev
libxml-perl
libusb-dev
libid3tag0-dev
(I'm not sure if they suffice or if all of them are needed, just took 'em from that script you tried.)

Also, you need to install cvs.

I'll assume you start working in your home directory. When you have done
cvs -z3 co libnjb,
you'll have a directory called libnjb. Cd into it,
cd libnjb

Those &&s and ;s are just used to chain commands. You can do
sudo ./configure
sudo make
sudo make install
sudo ldconfig
instead of doing
./configure && make && make install && ldconfig
as root. I'm in a bit hurry now, but I hope this will help you forward a bit.

---

### Post by Strev_123 on 2006-02-14
OK, just working through the original HOWTO (first post in above thread). It works fine, (ie. downloaded and unpackaged the libnjb files) up until ```
./configure && make && make install && ldconfig
``` then I get the message ```
bash: ./configure: No such file or directory
```. It says that I may need to install dev libraries for libusb so I have installed the following from synaptic: 

libhid0, libusb-0.1-4, libusb++-0.1-4c2, libusb-dev, libusb++-dev

I didn't know which one it was refering to so I installed them all :-?

Thanks to anyone who has an answer.

---

### Post by Strev_123 on 2006-02-14
YAY... it works, big BIG thankyou to Iha, still be banging it if you hadn't pointed me in the right direction \\:D/ \\:D/ \\:D/

---

### Post by lha on 2006-02-14
[QUOTE=Strev_123]OK, just working through the original HOWTO (first post in above thread). It works fine, (ie. downloaded and unpackaged the libnjb files) up until ```
./configure && make && make install && ldconfig
``` then I get the message ```
bash: ./configure: No such file or directory
```.[/QUOTE]

Did you do ./configure in the directory that was created during download? That configure-file should have been downloaded with other libnjb files. You can do
ls -l
and look for a file named configure.

---

### Post by lha on 2006-02-14
[QUOTE=Strev_123]YAY... it works, big BIG thankyou to Iha, still be banging it if you hadn't pointed me in the right direction \\:D/ \\:D/ \\:D/[/QUOTE]

Hmm, strange... How come this message was visible to me only after I posted my previous message, even though timestamp says it was posted earlier? Well, nice to hear it sorted out. :)

---

