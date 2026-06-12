---
title: "data rescue with PhotoRec"
date: 2013-05-27
forum: Hardware
---

### Post by leevio on 2013-05-27
Hello everyone,


I want to try to retrieve data from my dysfunctional external 640GB hard drive with PhotoRec.


Right now I have two external HDDs connected via USB to my Ubuntu-Netbook: 
on the one string the malfunctioning 640GB hard drive,
on the other a 1TB back-up HDD onto which I want to copy files, assuming PhotoRec can find any.


My only concern now is:

how do I even select the FUNCTIONING 1TB hard drive from the PhotoRec menu (see Screensots attached)?
I don't want to accidently select the broken 640GB hard disk as the directory onto which found data shall be saved
(as otherwise retrieveable data might be overwritten).


Anyone who can quickly advise under which heading / identification 
the functioning hard disk can be found in Ubuntu/PhotoRec ?


A quick reply is very much appreciated.



[IMG]https://imageshack.us/scaled/medium/607/kopiertam27mai2013029.jpg[/IMG]







[IMG]https://imageshack.us/scaled/medium/43/photorec2.jpg[/IMG]





[IMG]https://imageshack.us/scaled/medium/221/photorec3.jpg[/IMG]

---

### Post by dargaud on 2013-05-27
Where did you mount your 1Tb backup ? Once mounted normally, simply select any directory on it and Photorec will place the files it finds in it. It won't otherwise touch the files already present on it (it's not like copying partitions with Filezilla if that was the sense of your question).
The defective disk must be connected but not mounted. You can find which device it is by looking for /dev/sd... in the last lines returned by dmesg after you plug it in.

---

### Post by leevio on 2013-05-28
> **dargaud said:**
> Where did you mount your 1Tb backup ? Once mounted normally, simply select any directory on it


Dargaud,


thanks for the reply.

What exactly is the difference between "mounted" and "connected" ?  :confused:  
As mentioned above, I have them connected to my Netbook via USB-cable ---- not sure whether the 1TB is mounted though?

And my question is precisely: where do I find the directory / directories of the 1TB hard drive in Ubuntu / through the terminal? 
The layout is not Windows-conform (obviously), hence my difficulties with finding the needed drive(s) 
(as opposed to simply opening the Explorer in Windows and seeing any external hard drives listed as D: , F: , etc.
                                                        - then browsing the hard drive and open any contained folders---
                                                       ------- I can't tell by the designation "drwxr + numbers" which hard drive / hard disk it is) .

---

### Post by dargaud on 2013-05-28
Ha, OK, so basically it's not a question about Photorec but about mounting an external drive. When you connect it, you should see an icon that tells you "there's a new USB drive, do you want to connect/mount it"? Then you normally find it in /media/something

---

