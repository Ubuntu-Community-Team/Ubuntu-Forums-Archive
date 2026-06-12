---
title: "Sata II HDD in 8.04"
date: 2008-10-01
forum: Hardware
---

### Post by B1scu1T on 2008-10-01
I bought a computer the other day which i would like to use as a Media Server/HTPC but instead of buying another windows licence i thought i would be brave and give Linux a go. This is the dedicated attemp i have with linux having used very little command line in either windows or mac osx but im eager to learn so i jumped in and gave it a go. 

I put the computer together (Nforce 610i ,E1200, 1gb 667 ram, 6200tc, 80Gb PATA drive + 750GB SATA II Drive)

I installed Linux using the alternative method on my 80GB PATA drive then installed the 6200tc using 'hardware drivers' in the administrative menu. 
So far so good and everything is fine.

I plug in the new 750GB drive and use partition editor to format the drive in ext3. and then i mount in by right clicking in computer. Thing is i cant do _anything_ with the drive as i dont have permissions, can anyone tell me what i have missed/where i have gone wrong/what i need to do :confused:?

Thanks in advance and sorry im such a noob

---

### Post by haydnc on 2008-10-01
Hi B1scu1T.

There are probably several ways to fix this, and some of those are bound to be shorter than what I'm about to put down here... sadly I only know the long (long long) way around for fixing this and I don't have my Ubuntu machine here with me so please forgive me if some of the steps are slightly off - they're all from memory.

First the easy stuff - you need a place to mount the 750Gb drive to once we get the rest sorted out.
Easiest way to sort that out is to start up a gnome-terminal (Programs - Accessories - Terminal) and type in:
```
cd /mnt
sudo mkdir data

```
It should ask you to put in your sudo password - that's your regular login password in this case.

Next fire up the partition editor and make a note of what /dev relates to the 750Gb drive. It'll probably be /dev/sda, but we need to know for sure.

Then you need to set things up so the system will mount the drive every time you start up your computer. To do that you need to edit the fstab file. In your terminal window type the following:
```
sudo cp /etc/fstab /etc/fstab_backup

gksu gedit /etc/fstab
```
and type in your password when asked. It **should** fire up gedit with the fstab file open. If it doesn't try Alt-F2 to bring up a run window and type gksu gedit then manually browse to /etc and open fstab.

Add the following line to the bottom of the fstab file:
```
/dev/***sda1*** /mnt/data ext3 defaults 0 0
```
**Make sure you replace the sda1 bit with whatever the partition was as per the partition editor!**

Reload your partition tables by typing the following into your Terminal window:
```
sudo mount -a
```

Then, finally to set the permissions so that you can write to the newly mounted partition type the following in the Terminal window:
```
sudo chown username:username /mnt/data -R
sudo chmod 755 /mnt/data -R
```
**You need to replace "username" with your Ubuntu login name**

The only other thing I tend to do is set up a link to the mounted drive directly in my home directory:
```
ln -s /mnt/data /home/username/data
```
**Once again replace "username" with your Ubuntu login name.**

Also, after I started writing this I found this link:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
which has a very similar procedure and includes pictures, in case you need them.

Good luck, and again sorry if anything is slightly inaccurate since it's all coming from memory.

---

### Post by B1scu1T on 2008-10-01
I tried to follow through those steps but i keep getting the same reply from terminal

```
sudo: unable to resolve host Server
```

so im guessing its not working. Should i post up what happens?

---

### Post by haydnc on 2008-10-01
How far through did you get before it gave the error?

---

### Post by B1scu1T on 2008-10-01
any step with sudo in it gives me that error

---

### Post by haydnc on 2008-10-01
Apparently some other people out there in internet land have run into that problem. I found this for fixing it:

Click:
System > Administration > Network 
Change to the Hosts tab. 

At the top of the list you should see 'local host' and the computer's name - check that the computer name (Alias) is correct. 

Apparently if the computer name has anything added on the end of it.. eg compname.mynetwork (the .mynetwork part) it has problems.

Let me know if that sorts out your sudo problem... actually... if it does sort out your sudo problem let me know if everything else works. :D

---

### Post by B1scu1T on 2008-10-01
Ok il check back in tomorrow after some much needed rest & another attempt, thanks a lot for the help :D

---

### Post by B1scu1T on 2008-10-02
all seems to have worked now thats fantastic cheers! Just to be sure though, now anything i store in the /storage folder (which is  the one i used opposed to the one you suggested) will go onto that hard drive and work on that hard drive independently. So if the operating system messed up and i had to reinstall ubuntu, i wouldsimply remount the drive.

---

### Post by haydnc on 2008-10-02
Thats right. As long as you don't delete, format or otherwise overwrite the contents of the SATA drive it'll act as independent storage and can just be remounted whenever you re-install your OS.

Sadly I have in the past experienced accidental deletions, formattings and overwritings - and there's no way I've discovered to recover if you make that mistake. :(

---

### Post by B1scu1T on 2008-10-03
Isnt there harddrive recovery software similar to the stuff that can recover ntfs or fat32 hard drives.

Something strange is happening with the hard drive. Every time i boot up it seems to appear under a different identifier. One time it will boot up as SDA1 next time it will be SDB1 so it mounts as a seperate hard drive rather than part of the exsisting filesystem. Feel free to correct me if i have used any of the wrong lingo,

---

### Post by haydnc on 2008-10-06
I've done some reading and I see that the way we added your new drive to the fstab file is outdated and, as you've noted, can be messed up a bit by the drive mounting under different identifiers.

The fix looks pretty simple though.

First open a terminal and type:
```
sudo blkid
```

That should list all your hard drives and their Universally Unique Identifier - something like this:

>  /dev/sda1: TYPE="ntfs" UUID="72C0DE8EC0DE57C5" LABEL="windows" 
 /dev/sda2: UUID="30fcb748-ad1e-4228-af2f-951e8e7b56df" SEC_TYPE="ext2" TYPE="ext3" 
 /dev/sda5: TYPE="swap" UUID="8c4e69f8-5074-42c0-8134-0b2429c4c02c" 
 /dev/sdb1: SEC_TYPE="msdos" UUID="4848-E35A" TYPE="vfat" 

Make a note of the UUID for your SATA drive. You'll be using it in a moment.

Next re-open fstab for editing as you did before:
```
gksudo gedit /etc/fstab
```

Find the line where you had: 
> /dev/sda1 /storage ext3 defaults 0 0 

and edit it so that it looks like this:

> # /dev/sda1
UUID=<whatever the UUID you noted down was> /storage ext3 defaults  0 0


~~~ 

Using the UUID should solve the problem of having it change device ID's on you.

To test it out type you should be able to type these commands in your terminal:
```
sudo umount /dev/sda1
sudo mount -a
```

Again, forgive me if I've got any commands slightly off as I'm doing this from memory (no Ubuntu at work... yet). In theory that should unmount your SATA drive then remount it as per your updated fstab entry.

I'm sure if anyone knows of a better way to do it they'll probably post it here.
:)

---

