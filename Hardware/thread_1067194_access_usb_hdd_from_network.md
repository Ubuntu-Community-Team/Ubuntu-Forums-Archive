---
title: "access usb hdd from network"
date: 2009-02-11
forum: Hardware
---

### Post by M_JaGuar on 2009-02-11
hi ..

i have a wd hard disk and i want to be able to access the files and videos in it from other computer (both computers are ubuntu) and every time i try to watch a video i get a message say
 " you might not have permission to open the file "

and i tryd this in the terminal :
   ( sudo chmod 755 -R /media/"My Book" )
   ( sudo chmod a+rw -R /media/"My Book" )
   
   i dont know what to do :(

---

### Post by utnubuuser on 2009-02-11
Have you tried going through the right-click>>sharing options?  Select the disk icon, right-click on it, and check out "sharing".

---

### Post by M_JaGuar on 2009-02-11
yes i already shared it and i can access it and copy files from one computer to another but i cant watch the videos from 
the hard disk without copy it to my other computer

----

i forgot to tell you that the hard disk is fat format not ntfs




.

---

### Post by sr20ve on 2009-02-11
I would setup your USB drive mount point as an NFS share.

This site has a good walkthrough on NFS:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

### Post by sr20ve on 2009-02-11
> **utnubuuser said:**
> Have you tried going through the right-click>>sharing options?  Select the disk icon, right-click on it, and check out "sharing".

I believe this method only lets you share it as samba, which is not optimal for a linux to linux share.

---

### Post by M_JaGuar on 2009-02-12
thanks all for reply 

ok i give it a shoot in nfs

and it works fine for my home folder but for my usb hdd it dosnt work
i try to change the permission to 755 and it works until i restart both computers after that it didnt work for my usb hdd

----

and for the fstab file i dont know how to configure it 
so i still have to mount it manule my self from the terminal
every time 

----

any ideas

---

### Post by sr20ve on 2009-02-12
edit the /etc/fstab so you don't have to manually mount it from the terminal each time.

you should add a line that looks similar to this:

myfileserver:/media/disk  /data  nfs  defaults  0 0

You can also replace the hostname (myfileserver) with the ip address.

You can then test your fstab by running:

#sudo mount -a

---

### Post by M_JaGuar on 2009-02-12
this is my fstab file :

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6d9cc3dd-bba9-44f0-ad9c-cc3691721a37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a0b10799-8054-4470-8db2-ab640204cf43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

192.168.1.107:/media/"My Book" /home/bo7amny/ubuntu-pc/mybook nfs nfs defaults 0 0
192.168.1.107:/home/bo7amny /home/bo7amny/ubuntu-pc/home nfs defaults 0 0

my home folder works fine

but the "my book" not working and i think it about permission

---

### Post by sr20ve on 2009-02-12
> **M_JaGuar said:**
> this is my fstab file :
192.168.1.107:/media/"My Book" /home/bo7amny/ubuntu-pc/mybook nfs **nfs** defaults 0 0


Is that a typo? You have nfs listed twice.

Could you also post your /etc/exports, and the command you're running to mount it manually?

---

### Post by M_JaGuar on 2009-02-13
ok this is the exports file :

> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/media/"My Book" 192.168.1.0/24(rw,no_root_squash,async)
/home/bo7amny 192.168.1.0/24(rw,no_root_squash,async)

this is fstab file :

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6d9cc3dd-bba9-44f0-ad9c-cc3691721a37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a0b10799-8054-4470-8db2-ab640204cf43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


#192.168.1.107:/media/"My Book" /home/bo7amny/ubuntu-pc/mybook nfs defaults 0 0
192.168.1.107:/home/bo7amny /home/bo7amny/ubuntu-pc/home nfs defaults 0 0
192.168.1.107:/media/"My Book" /home/bo7amny/ubuntu-pc/mybook nfs defaults 0 0

the command to mount the hdd :

> sudo mount 192.168.1.107:/media/"My Book" ~/ubuntu-pc/mybook

and i must give the hdd the 755 permission every time before i run this command 

and the out but of ( sudo mount -a ) is :

> [mntent]: line 14 in /etc/fstab is bad

i dont know what wrong with this line i think it the name of the hdd ("My Book")
but i dont know how to change it

by the way thank you

---

### Post by M_JaGuar on 2009-02-14
some one help me please iam half the way over :(

---

### Post by ndale686738 on 2009-02-20
1) the fstab entry should be formatted as follows in the client
hostname:/hostdirectory /localmountpoint nfs rw,hard,intr 0 0

2) add the following to /etc/hosts on the client machine
IP_of_host	hostname

3) add the following to /etc/exports on the host machine
Folder_being_Shared hostname(rw,sync,no_subtree_check)

Thats it.

---

