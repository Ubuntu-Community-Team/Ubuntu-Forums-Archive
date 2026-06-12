---
title: "Pemastersys won't create ISO file."
date: 2008-08-25
forum: General Help
---

### Post by colobix on 2008-08-25
Hi. I am new with Remastersys so maybe I'm just doing it wrong, but I rad a place that Remastersys will also create an iso file for me after the backup process. Is that right? I took a look thru all the files remastersys made to see if I could find the iso file but nope. All I could find is some temp files, the backup file and a file called custom.iso.md5 on 0 bytes.

Is this right, and will the CD be perfect created if I Just burn that remastersys folder under as it is now under /home ?

Thanks in aedvance.

---

### Post by linux_tech on 2008-08-25
To create an iso image of your installation, try this-

To make a live cd backup and call the iso custom.iso
```
sudo remastersys backup custom.iso
```


This creates an distributable live cd of your system in a iso image called customdist.iso in the /home/remastersys directory. (with the dist option your personal folder is omitted)
```
sudo remastersys dist
```

---

### Post by colobix on 2008-08-25
Thanks alot :)

---

### Post by colobix on 2008-08-25
If I add some folders like /usr in that folder, will the usr folder be included in the iso file and the live Ubuntu and the installation program then?

---

### Post by linux_tech on 2008-08-26
If you use the dist option then anything in your personal folder will not be included, but everything else will. So if you want your personal folder and contents to be included then don't use the dist option.

---

### Post by colobix on 2008-08-26
OK thanks.
I tried both the methods but no .iso file saved in the remastersys folder.
So is there another program like remastersys I can try out that works the same way?

---

### Post by colobix on 2008-08-26
BuMp

---

### Post by linux_tech on 2008-08-28
2 other programs that allow you to create a customized Live CD/DVD of Ubuntu (a remaster) are; 
the Ubuntu Customization Kit- [http://uck.sourceforge.net/](http://uck.sourceforge.net/)
and Reconstructor-http://reconstructor.aperantis.com/

For creating a complete backup of the os, applications, data, in short everything to a bootable cd, you are looking for the equivalent of norton 
ghost.  For Linux I would check out 2 programs - clonezilla and g4l (ghost for linux)  These choices allow you to easily restore your system, applications and data easily if you have a hard drive go out, if ubuntu gets corrupted,  or a partition deleted.   This option will save you the time of having to install all your applications, drivers, etc. again. 

If you just want to backup data to a iso,then this can be done by opening up nautilus and enter


```
 burn:///  
```

move all the files that you want in there, click the Write to Disc button, it will open a prompt in the drop down box choose File - Image and it will create a .iso (non-bootable) file for you.  This method is useful if you just want to backup all your data to an iso.


[http://www.clonezilla.org/](http://www.clonezilla.org/)
see #7 advanced modes to create bootable iso image restore cd.
this is what I would do, I think that is the reason why you want a complete backup to iso.

---

