---
title: "Oh no i think i went wrong... very wrong"
date: 2008-11-26
forum: General Help
---

### Post by footynutdyl on 2008-11-26
Delete please

---

### Post by dje on 2008-11-26
in ubuntu open Applications >> Accessories >> Terminal and run (this command will list all partitions on your hard drive):
```
sudo fdisk -l
```
(that is a lower case L on the end, not a 1)
when it prompts for a password enter your normal logon password, no feedback will be shown on the screen just type it and hit enter ;)
then post the output here

dje

---

### Post by fooman on 2008-11-26
could you run the following command in a terminal (applications > accessories > terminal) and post the results back here:

```
sudo fdisk -l
```


edit: oops,  sorry i'm a bit slow today.

---

### Post by Titan8990 on 2008-11-26
> hey i got ubuntu onto my computer and i think its overwrited my vista what shud i do, im scared.


Be prepared to learn the hard way the value of backing up your system, especially before making changed to your hard drive (unless you made backups, then you shouldn't have much to worry about).

---

### Post by footynutdyl on 2008-11-26
i didnt make a backup:(

so has it gone then?

and also if i were to use ubuntu for the rest of my laptops days. i cant do the wireless or even the visual effects to work and the resolution

---

### Post by damis648 on 2008-11-26
Post the output of fdisk -l and we will know.

EDIT:
> i cant do the wireless or even the visual effects to work and the resolution
We will get to that when the time comes.

---

### Post by Titan8990 on 2008-11-26
It doesn't mean that your Windows is gone forever as it can always be reinstalled (pending you didn't pull of that label with your Window CD-KEY). But there is a good chance that your personal files are gone. We will not know until you post the output fdisk -l.

You may have to contact the manufacturer of your laptop to get a Windows installation CD. Regular Windows installation CDs will not work with a OEM key that is labelled on your laptop.

---

### Post by dje on 2008-11-26
please post the output of the command i posted earlier. we cannot help you until you do ;)

---

### Post by footynutdyl on 2008-11-26
that will bekinda hard coz i have to go on my dads comp to do this and g to my comp to do the terminal thingy

---

### Post by footynutdyl on 2008-11-26
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x2f795f59 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       18662   149902483+  83  Linux 
/dev/sda2           18663       19457     6385837+   5  Extended 
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris 
dylan@dylan-laptop:~$

---

### Post by dje on 2008-11-26
> **footynutdyl said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x2f795f59 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       18662   149902483+  83  Linux 
/dev/sda2           18663       19457     6385837+   5  Extended 
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris 
dylan@dylan-laptop:~$

unfortunately that shows that vista has been overwritten

testdisk is a free data recovery tool which may help you, for more info on how to use it see [here]("http://www.cgsecurity.org/wiki/TestDisk")

Next time make sure you make a full backup and know exactly what you are doing before proceeding ;)

---

### Post by footynutdyl on 2008-11-26
can u guide me how to get and how to use testdisk please

---

### Post by footynutdyl on 2008-11-26
ohh and the problem is i cant install testdisk coz the internet on ubuntu is connecting to my wireless

---

### Post by dje on 2008-11-26
Can you boot up the live cd and connect to the internet via ethernet? If so do so then open the terminal again and run:
```
sudo apt-get install testdisk
```
sorry but i wouldnt be able to guide you through using testdisk, have a look through the official documentation at the link i posted above


dje

---

### Post by footynutdyl on 2008-11-26
umm whats ethernet?

---

### Post by footynutdyl on 2008-11-26
and also can u link me the documentation (sorry i am askin for alot) but i have been stressed thinking i have lost vista

---

### Post by brokenreality on 2008-11-26
> **footynutdyl said:**
> umm whats ethernet?

[http://en.wikipedia.org/wiki/Ethernet]("http://en.wikipedia.org/wiki/Ethernet")

Can you connect to the internet through a wired connection from your modem/router to the ethernet port on your laptop. It should connect immediately to the internet.

---

### Post by dje on 2008-11-26
ethernet - ^^see above^^
documentation - [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

dje

---

### Post by footynutdyl on 2008-11-26
and exactly what will testdisk do?

---

### Post by dje on 2008-11-26
it may recover lost partitions, have a thorough read of the documentation ;)

---

### Post by footynutdyl on 2008-11-26
will that partition be my operating system?

and i dont really understand the doumentation

---

### Post by brokenreality on 2008-11-26
> **footynutdyl said:**
> and exactly what will testdisk do?

Well.... if you read the documentation from the link that dje provided, you above would find out. nYour going to have to read some documentation in order to be able learn how use testdisk.

Backing up is always important!! I learned that the first time I installed linux. From there on out I backed up everything I wanted to keep before making possible serious system changes. 

Be patient, people are trying to help you get past this, the up on test disk and go from their.

Also try this link.......  [http://www.users.bigpond.net.au/hermanzone/p21.html]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by dje on 2008-11-26
brokenreality's post above has some useful info
have a look at this [page]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Recover_deleted_files")
do **not** scan read it! have a thorough read of it

---

### Post by rhcm123 on 2008-11-26
> **footynutdyl said:**
> will that partition be my operating system?

and i dont really understand the doumentation

Ok, very long explanation of what you did. (Just guessing, but since you sound very new to the world, i'll assume you went with the ubuntu installer "we'll do it for you" mentality).


You had vista on a partition on your hard drive. I'm going to assume it came with your system.

You decided one day to come over to linux, or to atleast try it. You dloaded the live cd and decided you liked it, so you hit the handy install button on the desktop.

You answered the basic questions until you came to step 4. The partitoner.
Since you didn't even know what a parition was, you chose the defualt and installed ubuntu.

What the defualt did was format your entire hardrive into the following defualt configureation: entire drive minus 512 mb for your main partition in a filesystem known as ext3, and the 512 megabytes as somthing called swap. (don't worry about what that is.)

What you have essentially done is deleted your entire hard drive and placed a new os onto it.

About potential data recovery:
Now, for fun, on one my old pc's i tested the resilience of the files. If you reformat the drive then format it again as ext the (which the partitoner gparted or fdisk does when you delete old partitons and make new ones) you will most likely corrupt all the data.

I'm very sorry. Let it be a comfort that i did this. Twice. 
Don't let this ruin your linux experience.

---

### Post by footynutdyl on 2008-11-27
hey if testdisk wrent to work then how would i go about getting vista back?

---

### Post by roger_1960 on 2008-11-27
Hi

Unless you have Vista on disks, then Titan8990 has already mentioned that you will probably need install disks from the laptop manufacturer.

---

### Post by footynutdyl on 2008-11-27
will that be free?

---

### Post by brokenreality on 2008-11-27
> **footynutdyl said:**
> will that be free?

You should still have your vista install disk, unless you bought a computer with it preloaded and it did not come with it.

---

