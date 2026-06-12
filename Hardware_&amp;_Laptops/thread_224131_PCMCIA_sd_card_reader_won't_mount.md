---
title: "PCMCIA sd card reader won't mount"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by fastly on 2006-07-27
Hello

I have a PCMCIA 6 in 1 card reader to transfer files from my digital camera to laptop. This used to work perfectly (e.g. pop the PCMCIA with sdcard in and it automounts, places icon on desktop and asks if i want to import new pictures).

Right now nothing happens when I insert the card, not even an icon under Places->Computer. I've tried restarting with the drive installed and now at least I can see an icon "488.4MB Volume" under Places->Computer, however when I click in this I get the following error:  

error: device /dev/hde1 is not removable

error: could not execute pmount

I have installed and running: 
hal 0.5.7-1ubuntu18 
dbus 0.60-6ubuntu8

I've tested the same card reader and card on a windows laptop and it works fine there...

Any suggestions are very much appreciated.

Thanks

Alex :p

---

### Post by Z(L)o on 2006-08-02
> **fastly said:**
> Hello

I have a PCMCIA 6 in 1 card reader to transfer files from my digital camera to laptop. This used to work perfectly (e.g. pop the PCMCIA with sdcard in and it automounts, places icon on desktop and asks if i want to import new pictures).

Right now nothing happens when I insert the card, not even an icon under Places->Computer. I've tried restarting with the drive installed and now at least I can see an icon "488.4MB Volume" under Places->Computer, however when I click in this I get the following error:  

error: device /dev/hde1 is not removable

error: could not execute pmount

I have installed and running: 
hal 0.5.7-1ubuntu18 
dbus 0.60-6ubuntu8

I've tested the same card reader and card on a windows laptop and it works fine there...

Any suggestions are very much appreciated.

Thanks

Alex :p
 
I am having the same issue here.

---

### Post by Z(L)o on 2006-08-04
After performing some research I've succeeded. 

*Please, don't hesitate to correct me if I am wrong within the "instructions" - I am a newbie trying to help:)

Here is what you need to do:
0) run 
sudo fdisk -l 
to figure out how your sd card is defined

Mine looks like that:

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1         976      249805+   6  FAT16

1) create the mount point 
mnt/cf
2)modify fstab 
add the following line

/dev/hde1 /mnt/cf auto noauto,rw,user,exec, 0 0

(this includes read/write access)
3) mount the card by running
mount mnt/cf

4) goto mnt/cf in order to access the card 

Hope it works.

URLs to check out:
[http://www.debian-administration.org/articles/405](http://www.debian-administration.org/articles/405)
[http://linuxweblog.com/node/195](http://linuxweblog.com/node/195)

---

### Post by Tripmonkey_uk on 2006-08-05
Just what I needed thanks :D 
Not the neatest of fixes, but it works even better than it used to in some ways. 

[[IMG]http://img85.imageshack.us/img85/3441/cfcz0.th.png[/IMG]](http://img85.imageshack.us/my.php?image=cfcz0.png)

As u can see by the screen shot.. it now gives me a drive called cf & the drive with the mount point. 
To access the card, I need to insert it, click on the cf drive to mount it & access it once, then click on the drive with the mount point to access it every other time after that, aswell as to unmount it with.

This is a bit of a pain, but it does let me mount & unmount the card as many times as I like. Before I could only mount it once & then I'd have to remove the PCMCIA card completely to mount it again after that.

Good stuff :cool:

---

### Post by takakia on 2006-08-16
Thanks for the explanation, I had exactly the same problem and your tutorial helped me a lot.

thanks for the excellent how-to

---

### Post by pmanski on 2006-08-19
Hi

I saw this issue yesterday after upgrade kernel to linux-image-2.6.15-26-686. Version 2.6.15-23 doesn't have problems with mounting pcmcia and usb memory disks. I didn't tried 2.6.15.25 cause I read about problems with that version arleady.

Greetings from Poland
paff

---

### Post by pmanski on 2006-08-20
I tried 2.6.15-25, both the 386 and 686 - have the same problem with mounting my PCMCIA with CF-card.

2.6.15-23-386 & 2.6.15-23-686 are for now the best choice in Ubuntu Dapper.

Greetings
paff

---

### Post by strebormj on 2006-09-04
> **Z(L)o said:**
> After performing some research I've succeeded. 

*Please, don't hesitate to correct me if I am wrong within the "instructions" - I am a newbie trying to help:)

Here is what you need to do:
0) run 
sudo fdisk -l 
to figure out how your sd card is defined

Mine looks like that:

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1         976      249805+   6  FAT16

1) create the mount point 
mnt/cf
2)modify fstab 
add the following line

/dev/hde1 /mnt/cf auto noauto,rw,user,exec, 0 0

(this includes read/write access)
3) mount the card by running
mount mnt/cf

4) goto mnt/cf in order to access the card 

Hope it works.

URLs to check out:
[http://www.debian-administration.org/articles/405](http://www.debian-administration.org/articles/405)
[http://linuxweblog.com/node/195](http://linuxweblog.com/node/195)



Thanks for the informative post. For the benefit of anyone else who stumbles across this thread:  This also works for mounting cards in the multi-card reader in the Acer Travelmate 8204 under Dapper Drake (6.06.01 / 2-6-15-26-386) and for mounting the internal drive, and SD card, in the Palm Tungsten T5 (Drive Mode).

---

### Post by lutra on 2006-10-03
> **pmanski said:**
> Hi

I saw this issue yesterday after upgrade kernel to linux-image-2.6.15-26-686. Version 2.6.15-23 doesn't have problems with mounting pcmcia and usb memory disks. I didn't tried 2.6.15.25 cause I read about problems with that version arleady.

Greetings from Poland
paff

I downgraded kernel to 2.6.15-23 and it works for me with a 5in1 pcmcia card reader.

---

### Post by boakes on 2006-10-31
This command ```
0) run
``` gets me ```
bash: syntax error near unexpected token `)'

```

---

### Post by Z(L)o on 2006-10-31
> **boakes said:**
> This command ```
0) run
``` gets me ```
bash: syntax error near unexpected token `)'

```

the command to run is:

[COLOR="Lime"]sudo fdisk -l [/COLOR]

---

### Post by boakes on 2006-11-01
I guess I'm SOL because it doesn't show up under there.

---

### Post by laosboyme on 2006-11-14
It says permision denied?!:)

---

### Post by soundsystem00 on 2007-03-15
> **Z(L)o said:**
> After performing some research I've succeeded. 

*Please, don't hesitate to correct me if I am wrong within the "instructions" - I am a newbie trying to help:)

Here is what you need to do:
0) run 
sudo fdisk -l 
to figure out how your sd card is defined

Mine looks like that:

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1         976      249805+   6  FAT16

1) create the mount point 
mnt/cf
2)modify fstab 
add the following line

/dev/hde1 /mnt/cf auto noauto,rw,user,exec, 0 0

(this includes read/write access)
3) mount the card by running
mount mnt/cf

4) goto mnt/cf in order to access the card 

Hope it works.

URLs to check out:
[http://www.debian-administration.org/articles/405](http://www.debian-administration.org/articles/405)
[http://linuxweblog.com/node/195](http://linuxweblog.com/node/195)


I saw that this worked for someone but all it detected for me was a C drive. Any suggestions? I have a laptop

---

