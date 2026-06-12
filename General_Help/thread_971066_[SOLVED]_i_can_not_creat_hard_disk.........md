---
title: "[SOLVED] i can not creat hard disk........"
date: 2008-11-04
forum: General Help
---

### Post by miroooo on 2008-11-04
I can not create 3 partitions like C: D: and E: in Ubuntu

i was pro in MS Windows 

i am about to kill my self here  

some help please

	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)

---

### Post by Elfy on 2008-11-04
No-one can create partions like C D E in ubuntu it works differently

The first hdd is called sda, the second sdb

Partitions are numbered from 1, so 1st partion of 1st hdd is sda1, 1st on 2nd hdd would be sdb1

What are you trying to do?

---

### Post by ugm6hr on 2008-11-04
You can only create partitions on unmounted drives.

Therefore, you generally have to boot from the LiveCD (In Ubuntu LiveCD: System->Administration->Partition Editor),

If you understand partitions, it's easy.

They will be labelled something like: sda1, sda2, sda3 (rather tha C, D, E.

If you're an expert - try googling "GParted" for more detail (if necessary).

---

### Post by ugm6hr on 2008-11-04
You can only create partitions on unmounted drives.

Therefore, you generally have to boot from the LiveCD (In Ubuntu LiveCD: System->Administration->Partition Editor),

If you understand partitions, it's easy.

They will be labelled something like: sda1, sda2, sda3 (rather than C, D, E.

If you're an expert - try googling "GParted" for more detail (if necessary).

---

### Post by miroooo on 2008-11-04
i know that i can not get c,d and e drives here

and thanks for fast reply

the issue is i was giving you example of what i want to do..

i want to have  3 partitions for my hard disk without including the swap area ,and when i want to in stall new release of Ubuntu ,i format the old system and install a fresh one without touching my data like (programs ,movies ,.....etc)

in other words ,i want someone give me instructions for how to partition the hard disk using manual option  during the installation process ,and when i want to install a fresh copy of another Ubuntu release 

i hope i am clear to you ,sorry i am newbie for Ubuntu

and waiting for your reply

---

### Post by Elfy on 2008-11-05
I assume that you have an existing windows install with partition/s - make sure that it is defragged - I have also in the past turned off the pagefile prior to any resizing operations and then reset it afterwards.

I prefer to do the partitionin before I install - there is a partition editor in the System Admin menu of the livecd.

Resize the exisiting partition/s then once that has finished create an extended partition in the empty space.

In the extended partition create 3 logical partitions - 
1 for the system installation - I have found ~10Gb to be big enough to allow for growth
1 for swap - if you have a need to hibernate then swap=RAM or is greater. If you do not need to hibernate and RAM is gretaer than 1Gb then a smaller swap will suffice - mine is just less than 1Gb and rarely used at all. Less than 1Gb RAM swap = 1.5xRAM
1 for home - remaining space

When you start the install - choose manual, swap will be recognised and can safely be ignored

Pick the~10Gb partition - Edit partition, in the Use As dropdown pick ext3 , tick the format box, pick / from the Mountpoint menu. Close.

Pick the larger partition - Edit partition, in the Use As dropdown pick ext3 , tick the format box, pick /home from the Mountpoint menu. Close.

Proceed with installation

Makes sure before you start to do the resizing that you have good backups of data you can't afford to lose and bear in mind that resizing can take some time. Do not assume it has hung/crashed and turn it off.
> 
i hope i am clear to you ,sorry i am newbie for Ubuntuyou are now indeed more than clear enough, your first post though wasn't and to be honest you got the answer to the question - twice ;)

There's no need to apologise for being new - just make sure that you give people enough information to help you without making them read a novel :)

The same with thread titles - > i can not creat hard disk.I can't do that either.

Good luck - any other questions come back.

---

### Post by miroooo on 2008-11-05
o.k:p

i do that 

one more question

the mount points for the large partition that i created was /MEDIA001

it is displayed as a folder in the root directory and i can not create or put any thing in them.

i can not handle the mount points for the drive
>>this is screen shot for my hard disk MEDIA001,002 folders 

O.K >> My big question is :p

what is the mount points that give me 3 partitions i can put my data in ?!!!!

i hope i give you enough information

i will wait for your reply 
many thanks for your help


all the best 

miroooo

---

### Post by Elfy on 2008-11-05
Can you run a couple of commands from a terminal - Apps > Accessories. Any sudo command run from the terminal will require your password - it will be invisible.

```
sudo fdisk -l
ls /media
cat /etc/fstab
```

When you paste the command put [noparse]```
[/noparse] at the beginning and put [noparse]
```[/noparse] at the end.

---

### Post by miroooo on 2008-11-05
here is the result !!!!!!

can i understand ?

---

### Post by Elfy on 2008-11-05
Please don't paste thumbnails of output - just put it in the post and use code tags.

Open a terminal

Make 2 folders to mount the partitions into
```
sudo mkdir /media/MEDIA001 /media/MEDIA002
```

Now we'll backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.0511
gksudo gedit /etc/fstab
```

Make these changes to the file - I can't copy and paste as you used an image , so I'm not going to write the whole thing out.

change /MEDIA001 to /media/MEDIA001 and /MEDIA002 to /media/MEDIA002
Save and close then run these commands - post the outputs please :) - just copy from the terminal into a new reply - highlight the pasted stuff and hit the # button

```
cat /etc/fstab
df -h
```

---

### Post by miroooo on 2008-11-05
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3a862bf-9984-4db8-81a3-4642697bb68d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=08df8912-9b52-47c9-b893-604dedae474c /media/MEDIA001       ext3    relatime        0       2
# /dev/sda6
UUID=8fdb477d-f7a1-4687-a3a7-b7afcc84290c /media/MEDIA002       ext3    relatime        0       2
# /dev/sda7
UUID=63f84138-6487-4745-9a58-77fc15554b09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
miroooo@miroooo-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              42G  3.1G   37G   8% /
varrun                1.3G  104K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G   52K  1.3G   1% /dev
devshm                1.3G  160K  1.3G   1% /dev/shm
lrm                   1.3G   38M  1.2G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5              93G  188M   88G   1% /MEDIA001
/dev/sda6              93G  188M   88G   1% /MEDIA002
gvfs-fuse-daemon       42G  3.1G   37G   8% /home/miroooo/.gvfs
miroooo@miroooo-desktop:~$ 

```

this o/p  i am sorry):P

---

### Post by Elfy on 2008-11-05
hey that's better lol, if you ever need to post lots of diffrernt things it's best to use seperate code tags - there are more that you can do with bbcode - I'll put link at the end - because I tend to do quick reply I type the commands like I showed in #7

Anyway - run these commands - they should unmount from /MEDIA001 and into /media/MEDIA001 - if there's an error from either stop and post it here - in code tags lol

```
sudo umount /MEDIA001 /MEDIA002
sudo mount -a
```


You _might_ find that you don't have correct permissiosns - chmod and chown are your friend here, don't do it unless you need to.

```
sudo chown user.user /media/MEDIA001
sudo chmod 770 /media/MEDIA001
```

repeat for MEDIA002

> can i understand ?IF there's things you don't understand then do ask.

Finally the link for bbcode - 
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by miroooo on 2008-11-05
the unmount is o.k
but the permission is not o.k 

i tried the first code it gives me 
```
chown: invalid user: `user.user'

```

---

### Post by miroooo on 2008-11-05
i am sorry 
it takes too long 

i will re-install Ubuntu again  i packed up my data 

just give me the instructions that used in the partitioner from the step that check the radio button of Manual in the partitioner  to give me the partitions as i mentioned earlier

1 partition for the system
2 partitions for my data 
and swap space

P.S  my problem is in the Mounting points   as you know , so give a good clarification for it if is possible but the important thing is to give me the instruction 



 , and i will very grateful for you and your efforts
***waiting for you  and i have too much work i had to do ***

all the best 


miroooo

---

### Post by Elfy on 2008-11-05
I don't know your username - user is sort of genereic - change that to suit you

eg I would sudo chown kevin.kevin /media/MEDIA001

---

### Post by miroooo on 2008-11-05
please i want to install Ubuntu 8.1 
i want you to give the right instruction for mounting the hard disk partitions

and applied the last code and i become able to paste in the folder
but i still could not create folders in it 


all the best

miroooo

---

### Post by Elfy on 2008-11-05
The way to install is in post 5 - _do not do anything with your 2 data partitions when you are installing_ - do that later once you have started to use the system.

The information to mount your data partitions is in the last few posts

---

### Post by miroooo on 2008-11-05
you mean that when i give the mount point for the partitions

i enter /media/MEDIA001
    
and     /media/MEDIA002

just like that 

but i still can not create folders in the partitions

---

### Post by Elfy on 2008-11-05
> **miroooo said:**
> you mean that when i give the mount point for the partitions

i enter /media/MEDIA001
    
and     /media/MEDIA002

just like that 

but i still can not create folders in the partitions

When are you trying to do this - this thread is now talking about 2 completely different things.

I'm quite happy to help you but I cannot guess what errors you are seeing on your terminal/file manager - if you have errors then post them.

Have you actually edited fstab and run the mount -a command? 

If you run df -h in a terminal does it show that the folders have mounted at /media/MEDIA001 and /media/MEDIA002 ?

---

### Post by miroooo on 2008-11-05
i run it 

and now i can paste anything in them 

but i can not create folders in them

---

### Post by Elfy on 2008-11-05
Run this command from a terminal please - paste the command and the error here

```
mkdir /media/MEDIA001/test
```

I would also like you to run this command and paste it's output as well please - 

```
cat .bash_history |tail -30
```

---

### Post by miroooo on 2008-11-05
```
miroooo@miroooo-desktop:~$ mkdir /media/MEDIA001/test
miroooo@miroooo-desktop:~$ cat .bash_history |tail -30
compiz --replace
ccsm
sudo apt-get install subversion
svn ls https://svn.generation.no/emerald-themes
gtk-window-decorator --replace
emerald
kde-window-decorator
sudo aptitude install gcursor
/apps/compiz/plugins/state/screen0/options/widget
gnome-theme-manager
sudo mkdir /media/MEDIA001 /media/MEDIA002
sudo cp /etc/fstab /etc/fstab.0511
gksudo gedit /etc/fstab
cat /etc/fstab
df -h
gksudo gdmsetup
sudo apt-get install gdm-themes
sudo umount /MEDIA001 /MEDIA002
sudo mount -a
sudo chown user.user /media/MEDIA001
sudo chmod 770 /media/MEDIA001
sudo chmod 770 /media/MEDIA002
sudo chown miroooo.miroooo /media/MEDIA001
sudo chown miroooo.miroooo /media/MEDIA002
gnome-theme-manager
sudo gnome-theme-manager
sudo ln -s /home/<miroooo>/.themes /root/.themes
sudo apt-get install gdesklets
gnome-terminal --working-directory=%f --geometry=75x25+350+205
sudo apt-get install qt3-qtconfig qt4-qtconfig
miroooo@miroooo-desktop:~$ 


```

i think you have to belive me ,no reason for that ,the issue is that you are too helpful man 
i want you to give me the instruction for manual partitioning during insallation

---

### Post by Elfy on 2008-11-05
No error in terminal - the folder was created.

You say that you can't create folders - I'm assuming that you are using nautilus if not use whatever you do, open that in one of the 2 data partitions which are causing you a problem, try and make a folder. When you have the error message - move it to the left of the window so you can see both the message and the nautilus window. Take a screenshot and post that.

---

### Post by miroooo on 2008-11-05
as you see it is not active and the same for the second drive

and the same for the other partition

---

### Post by Elfy on 2008-11-05
Ok think I see it - open fstab again for editing ```
gksu gedit /etc/fstab
```
and remove relatime from the 2 /media/MEDIA lines. 

Then run ```
sudo umount /media/MEDIA001 /media/MEDIA002 &&sudo mount -a
```

Then run the commands again 

```
sudo chown miroooo.miroooo /media/MEDIA001
sudo chown miroooo.miroooo media/MEDIA002
sudo chmod 770 /media/MEDIA001
sudo chmod 770 /media/MEDIA002
```

---

### Post by miroooo on 2008-11-05
i think some thing wrong happen to MEDIA002

but it is o.k it works for MEDIA001


after all i will re-install Ubuntu 8.1

i want the instruction for partitioning my hard disk as i told you 

am i have to open new thread 

many thanks to you 

by the way is there is any source that include all the codes and its function
if there is any please give me a link

all the best 

******************
miroooo
*************

---

### Post by Elfy on 2008-11-05
Use partition editor in the livecd system admin menu to create partitions. 

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

If the command is a linux one then usually you can get the information in a terminal with it's man page

man cp for example.

There are a couple of fairly useful cheat sheets

[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)
[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

Generally searching for liux command will throw a whole load of pages up.

---

