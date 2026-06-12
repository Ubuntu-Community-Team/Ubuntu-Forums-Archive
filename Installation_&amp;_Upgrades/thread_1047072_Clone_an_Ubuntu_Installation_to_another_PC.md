---
title: "Clone an Ubuntu Installation to another PC"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by pinguino99 on 2009-01-22
Hello all,
I have an ubuntu installation on a PC, let's call it PC1, and its hard disk DISK1 250 GB, partitioned by ubuntu installer. Only 20GB are used.
I have PC2, with DISK2 smaller  (160GB) and i would like to "clone" PC1 to PC2.
Is it possibile ?  How ?
I tried clonezilla ... but no success.
My aim will be have PC2 with ubuntu in a similar way PC1 is. 
I work in IT on a company and I would like to easily prepare PC without installing and configuring everything.
Any suggestion ?
Thanks to all !!
Pinguino99

---

### Post by Partyboi2 on 2009-01-22
Have a look at [COLOR=Blue][partimage]("http://www.psychocats.net/ubuntu/partimage")[/COLOR]

---

### Post by pinguino99 on 2009-01-22
> **Partyboi2 said:**
> Have a look at [COLOR=Blue][partimage]("http://www.psychocats.net/ubuntu/partimage")[/COLOR]

Thanks for the reply...
Partimage seems more to be a backup/restore tool for partitions.
My request is a bit different : backup an ubuntu installation, and restore it to a different pc / hard disk...

---

### Post by Kevbert on 2009-01-22
If the PC hardware is exactly the same cloning should be fine, but if you want to just make sure you have all the same packages installed on each computer you could try this in terminal on computer one:
```
sudo dpkg --get-selections > filelist.txt

```
This makes a package list (filelist.txt) which you want to copy to the new PC (which you've already installed Ubuntu). Now to install all packages:
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < filelist.txt
sudo aptitude install dselect-upgrade

```
The other method would be to produce your own [[COLOR="Red"]installation CD.[/COLOR]]("https://help.ubuntu.com/community/InstallCDCustomization")
This may be of [[COLOR="Red"]use[/COLOR]]("http://www.justlinux.com/forum/showthread.php?threadid=149328%27") - you'll need to recreate the mbr and grub via the live-CD.
Hope this is of use.

---

### Post by pinguino99 on 2009-01-22
> **Kevbert said:**
> If the PC hardware is exactly the same cloning should be fine, but if you want to just make sure you have all the same packages installed on each computer you could try this in terminal on computer one:
```
sudo dpkg --get-selections > filelist.txt

```
This makes a package list (filelist.txt) which you want to copy to the new PC (which you've already installed Ubuntu). Now to install all packages:
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < filelist.txt
sudo aptitude install dselect-upgrade

```
The other method would be to produce your own [[COLOR="Red"]installation CD.[/COLOR]]("https://help.ubuntu.com/community/InstallCDCustomization")
Hope this is of use.

Ok, but your solutions requires that i install and configure ubuntu, update it, and then download/install (and in some cases configure) packages. Moreover i uses some non free software (Lotus Notes, for example) that needs to be installed and there is no repo.
I thought there was a solution that i can backup the whole disk/partitions content, and restore it in another computer if with smaller disk.
If PC is the same i could use clonezilla or some "ghost-image" tool. But i would deploy a high number of ubuntu installations on different computers. So a tool for quickly "clone" a working ubuntu pc would be great.
Anyway, thanks a lot for the interest and the reply.

---

### Post by Kevbert on 2009-01-22
See last link that I've just added in previous post, it may be a better solution.

---

### Post by pinguino99 on 2009-01-22
> **Kevbert said:**
> See last link that I've just added in previous post, it may be a better solution.

Thanks again...
But the link you gave me maybe is not very helpful.
It says :
How to migrate XP, Vista, Linux, BSD and Solaris to a bigger hard disk

but if i have smaller hard disks ?!?

---

### Post by boof1988 on 2009-01-22
> **pinguino99 said:**
> Hello all,
I have an ubuntu installation on a PC, let's call it PC1, and its hard disk DISK1 250 GB, partitioned by ubuntu installer. Only 20GB are used.
I have PC2, with DISK2 smaller  (160GB) and i would like to "clone" PC1 to PC2.
Is it possibile ?  How ?
I tried clonezilla ... but no success.
My aim will be have PC2 with ubuntu in a similar way PC1 is. 
I work in IT on a company and I would like to easily prepare PC without installing and configuring everything.
Any suggestion ?
Thanks to all !!
Pinguino99

How about [Remastersys](http://www.remastersys.klikit-linux.com/)?  Would it do what you need?

---

### Post by Kevbert on 2009-01-22
> **pinguino99 said:**
> Thanks again...
But the link you gave me maybe is not very helpful.
It says :
How to migrate XP, Vista, Linux, BSD and Solaris to a bigger hard disk

but if i have smaller hard disks ?!?

It's the method that you want, the size of the hard disk is pretty irrelevant as you want to copy all information from one disk to another.

---

### Post by pinguino99 on 2009-01-23
> **Kevbert said:**
> It's the method that you want, the size of the hard disk is pretty irrelevant as you want to copy all information from one disk to another.

Ok, i will take a look and try to follow your suggestion and also the remastersys option.
Honestly i thought it would be easier.
I'll write down the results.
Thanks again to all.

---

### Post by jamesande on 2009-01-23
> **Kevbert said:**
> 
This may be of [[COLOR="Red"]use[/COLOR]]("http://www.justlinux.com/forum/showthread.php?threadid=149328%27") 


thanks heaps that was really helpful

---

### Post by rzrgenesys187 on 2009-01-23
I read about this page a while ago.  May not be exactly what you are looking for but may be useful [http://codepoets.co.uk/docs/system_imaging](http://codepoets.co.uk/docs/system_imaging).

Basically it involves using dd to to a bitwise copy of whatever you want.  You can then restore this image to a different partition

---

### Post by macvr on 2009-03-10
i used to use the dselect package as was given above...

but i found this in the #ubuntu irc... just type " [COLOR="Blue"]!clone[/COLOR] " in the irc

i think that this is better since there is no need to install the dselect package , and it just uses the aptitude... :D

 To replicate your packages selection on another machine (or restore it if re-installing), you can type 
```
$aptitude  --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```
 move the file "my-packages" to the other machine, and there type 
```
$sudo xargs aptitude --schedule-only install < my-packages ; sudo aptitude install 
```



also this is an easy option> [http://ubuntuforums.org/showpost.php?p=6660813&postcount=1]("http://ubuntuforums.org/showpost.php?p=6660813&postcount=1")

---

### Post by pinguino99 on 2009-05-13
>  To replicate your packages selection on another machine (or restore it if re-installing), you can type 
```
$aptitude  --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```
 move the file "my-packages" to the other machine, and there type 
```
$sudo xargs aptitude --schedule-only install < my-packages ; sudo aptitude install 
```



Thanks but... remember that not all applications installed comes from repos. SAP Gui (and all java apps) for example, or Lotus Notes. 
Or MS Office 2003, through wine.

I tried remastersys and ... i am impressed because it really works.
Creating the .ISO, burn it, and then install it to another different pc.
Really seems to work flawlessly.

Thanks to all, very helpful.

---

### Post by black_shadow on 2009-05-13
Hi

Even Easier if you have the second hard drive in your PC is 

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

Mike

---

### Post by theozzlives on 2009-05-13
Use remastersys, I don't remember the link but do a google, it's the klikit one.

---

