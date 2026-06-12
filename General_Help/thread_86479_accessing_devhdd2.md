---
title: "accessing /dev/hdd2"
date: 2005-11-05
forum: General Help
---

### Post by wadesmart on 2005-11-05
11052005 0828 GMT-5

I backed up my data to a second hard drive. I put all my /home in hdd3 and data from /tempdir in hdd2. I was able to acces hdd3 and copy all of that data back to my new /home after installing 5.10 but when I go to hdd2 it says empty. I mounted it at media/HD/hdd2. 

I used the command df -h and I see that /dev/hdd2 was 981M, I used 558M, leaving 374M. I just do not understand why I cant gain access to it. 

Wade

---

### Post by Remmelas on 2005-11-05
sounds like you may not have permissions on it?  try using ```
sudo ls /media/HD/hdd2
```

---

### Post by glantucan on 2005-11-09
Hi, I have more or less the same problem. I added 

```
/dev/hdb3 /media/hdb3 ext3 defaults 0 3 
```

to my fstab.
I can browse the partition after mounting it (There's nothing there thought) but I can't copy anything inside. It says I haven't permissions.

I tried several things, even mounting it at my home dir. No results.
Please help me

Thanx

---

### Post by Who on 2005-11-09
As has already been said in terminal-talk, you could try browsing the disk as superuser. In a terminal:
sudo nautilus --no-dektop --browser
(though --browser is up to your personal preference :))
That ought to determine whether the files are there...

---

### Post by BoyOfDestiny on 2005-11-09
System->Administration->Disk Management

You can mount/unmount/reformat etc there. (I mount mine to a folder, saving gnome session makes it remember).

If you see no files still, go Application->System Tools->Run as a different user, and type nautilus (will launch it as root).

Good luck!

---

### Post by glantucan on 2005-11-09
>  you could try browsing the disk as superuser. In a terminal:
sudo nautilus --no-dektop --browser
Yup, but my problem is not to access any files in this partition. What I want is to enable permanent access to it as a user. I don't think using this partition as root forever is a solution.
Thank you, anyhow

---

### Post by glantucan on 2005-11-09
[QUOTE=BoyOfDestiny]System->Administration->Disk Management
You can mount/unmount/reformat etc there. (I mount mine to a folder, saving gnome session makes it remember).
Good luck![/QUOTE]

Thanks again but, still this is not a solution for me (despite it's a good hint for usual users :) ). I need to share the (future) contents of this partition in a local network, so I need to have **rw** permissions no matter the user is logged in.

---

### Post by glantucan on 2005-11-09
](*,)  Stupid of me! 
i did this before on other linux distros (long time ago) because I had the same problem and I didn't remember it.
I did modify /etc/fstab to enable the OS to mount the partition on boot. 
Then used chmod to allow other users to write, because by default only the owner (that is: root) has this permission. Bellow is the entry in /etc/fstab I just added  (Use, for instance,  [FONT="Courier New"]sudo gedit /etc/fstab[/FONT] )
```
  ...
/dev/hdb3     /media/hdb3      ext3     defaults     0     3
...
```
Ctrl-s, go back to the terminal:
Don't forget to create this folder on /media/
```
sudo mount /media/hdb3
```
Then, once I check the mounted partition is on /media/hdb3, do:
```
sudo chmod -R a+w /media/hdb3
```
Which enables write access to everybody on that directory and corresponding subfolders

If you want to do the same you'll have to change **hdb3** for you particular device **ext3 **for your particular filesystem and the last number **3** in the fstab entry to the one indicating the place in which the system must check this partition on boot.

Hope this help to others

---

### Post by wadesmart on 2005-11-09
My problem was, even after I mounted it I couldnt see the files. 

Turns out they were hidden. There were in a file .Trash-root. After selecting show Hidden files I could see everything. 

Wade

---

