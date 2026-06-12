---
title: "OMG my Files are gone...."
date: 2008-08-30
forum: General Help
---

### Post by boom2k1 on 2008-08-30
In Ubuntu 7.10, I was transferring files from my mini-sd card to my usb drive in nautilus.

After it says the transfer is completed, I unmounted both drives.
(It took a bit of wait to unmount my usbdrive. But when it is done, I went on to reformat the mini-sd card.)

However, the next time I remount the usb drive, I figured that only a few directories were copied into my usb drive!!!! (And in those directories, all the files were 0 bytes!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!)

Another thing I found was that there is a new folder in my usb file system called FOUND0000, under which there is one single 600MB+ file called FILE0000.CHK
I strongly suspect that those files were all clustered into one file...

I tried to see the content of FILE0000.CHK by running more FILE0000.CHK, and found the first nonspace bytes to be:
```

CD001LINUX                           Ubuntu 7.10 i386                &#65533;oo&#65533;\\"k
5	                                                                        
                                                                                
                                                                                
                                                                                
                                                                        MKISOFS 
ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE
 (C) 1997 J.PEARSON/J.SCHILLING                                                 
                                                                       200710160
0531500200710160053150000000000000000002007101600531500                         
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
       

CD001EL TORITO SPECIFICATION

```

Is that an image file?!??!!


IS THERE ANY WAY FOR ME TO RETRIEVE BACK ALL THE FILES I LOST DUE TO SOME WEIRD CRAZY THINGS THAT HAPPENED JUST WITH SIMPLE FILE TRANSFER?!!?!!!

HELP !!!!!!!!!!!!!!!!!!!

---

### Post by iaculallad on 2008-08-30
Try using [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") on your mini SD Card.

---

### Post by boom2k1 on 2008-08-30
Thank you. I just downloaded testdisk to use photorec
following instruction from here:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)


THANK YOU SO MUCH!!!! I Hope it will work.. (at least partially retrieve back some of my files)

It is just done!!!! Although the recovery is probably not complete (because I have overwritten 350mb of my original 900mb stuff after the mini-sd has been formatted), I am seeing that a fair amount of the files had being recovered!
Thanks!!!!
You saved me a lot!!!!!!

---

