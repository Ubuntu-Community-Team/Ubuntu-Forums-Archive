---
title: "OOPS! Created partition table and erased everything :("
date: 2008-11-24
forum: General Help
---

### Post by ...alex on 2008-11-24
So, i was using GParted, and as usual clicking around very quickly (what can i say, im a quicker 'mouser' heh). I accidentally clicked Device > Create Partition Table... > Create. :O!!!

Immediately regretting my decision and realising what i have done ;<

What is the best method to recover my Windows partition, Ubuntu partition and my Media partition?

Im working from the Ubuntu live CD at the moment.

gAH! I can't believe what i have just done!! :@

---

### Post by blazemore on 2008-11-24
Don't TOUCH your hard drive, and wait here while I look up something for you.

---

### Post by blazemore on 2008-11-24
Right. I'm sure you'd agree you have nothing to lose, and I hope you have a backup, so if all else fails you can reinstall and copy the files over.

If you don't, well, from now on maintain a backup regime and don't be such a careless imbecile =P

We're going to use a utility called testdisk to recover your data. If you can get Internet from the LiveCD, good. Otherwise, put your hard disk in a system that can get Internet from the LiveCD.

```
sudo -s
```
We're going to want to be root.

```
apt-get update
apt-get install testdisk
```

I don't know if it's in the default repos, maybe you have to enable some other ones.
Now run testdisk:
```
testdisk
``` (surprisingly)
Look for options to recover a partition table. I'm looking for something more specific. But don't do anything without writing here first or you might bugger it up even more.

---

### Post by ...alex on 2008-11-24
Believe me, i know!!!

It was litterally my mind telling my hand to click cancel and it some how clicked create.

EDIT: doing it now...

---

### Post by blazemore on 2008-11-24
Don't worry, I've done a similar thing before, and Testdisk got me out of it.

You know how Vista wont even let you open a file without moaning at you? Well guess what, it lets you delete a partition without even asking "are you sure?" go figure.

---

### Post by ...alex on 2008-11-24
I did a search and was going to try TestDisk before, but it cannot find the package. Which repos do i need to enable to get it? Couldn't find it when doing a search in the Package Manager either.

---

### Post by blazemore on 2008-11-24
run tesdisk, and select [ create ] ( a new log file ).

```
Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 32 GB / 29 GiB
``` (Yours will be slightly different)

Choose [ proceed ]
Choose [ Intel ]
Choose [ Analyse ]

```
TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 32 GB / 29 GiB - CHS 3916 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
No partition is bootable













*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

[Proceed ]
                            Try to locate partition
```

As you can see, no bootable partitions have been found.
Choose [ proceed ] to continue. On the next screen TestDisk will show you the partitions it has found:

```
TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 32 GB / 29 GiB - CHS 3916 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  3869 254 63   62171487
L Linux Swap            3870   1  1  3915 254 63     738927

```
Obviously, (hopefully) yours will show you your partitions!

[ Enter ]
Now we write our changes to the disk:
[ Write ]
Yes, you're sure: enter Y
[ OK ] you have to reboot...
Now you can [ Quit ] as many times as it takes to quit.
Reboot, and good luck!

---

### Post by blazemore on 2008-11-24
Oh wait, you can't find the repos?
```
sudo gedit /etc/apt/sources.list
```
Uncomment (remove the # ) in front of every repo (Not the actual comments though; use your common sense)

Then do a 
```
sudo apt-get update
```
And install testdisk.
or maybe find a deb on the Interweb.

---

### Post by ...alex on 2008-11-24
Ok,

So i have done all that, just rebooted and i got a Grub error 22. This is because (i just checked in GParted) It only recoverd my Windows partiton) Grub cannot find the linux partition...

I will have to download all the repos and teskdisk again to see whats happening as i am still on the live CD and for some reason its all only downloading at about 11kbs. So i will update you with what TestDisk says now.

---

### Post by blazemore on 2008-11-24
I have to go to a lesson now.
Copy any important files off your Windows partition onto a removable drive or something, at least you'll have salvaged some data.

TestDisk is definately the way to go

GRUB reinstallation;
```
sudo grub
find /boot/grub/stage1
```
It will give you hd(x,y)
then do
```
root hd(x,y)
setup hdx
```
That might not be the exact syntax, but it's along the right lines. That will fix an error 15 at any rate.
Good luck.

---

### Post by ...alex on 2008-11-24
I now post this off my Windows partition (i can't even remember the last time i used this ahha).

I ended up booting from the windows CD and using fixmbr through the recovery console however as i new my Linux partition wasn't there, so all i need to do was restore the MBR so it could boot to Windows i guess.

Thanks for the help!!!

It seems my Linux partition and my Media partition have been lost :( I will try some more data recovery programs to get them back, but tbh all my important files such as photos etc... were on my Windows partition, so its not all bad :)

Can you recommend some good back-up programs?

---

### Post by blazemore on 2008-11-24
Glad to have helped. Reinstall Ubuntu in the free space.
Backup programs for Windows or Ubuntu? I don't use a backup program, I just have an external hdd and copy all important files over every few days. If the system goes down for whatever reason, I can copy it back over.

As far as backup for Ubuntu is concerned, try here [http://www.letmegooglethatforyou.com/?q=ubuntu+backup](http://www.letmegooglethatforyou.com/?q=ubuntu+backup)

---

