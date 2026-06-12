---
title: "Can not run Microsoft Office Install CD"
date: 2010-09-16
forum: Hardware
---

### Post by Jonners59 on 2010-09-16
I have upgraded my wife's Sony Viao laptop from 9.10 to 10.4.  We found that her Microsoft Office applications would not save, so I have tried reinstalling them from the CD.  I found the CD would not 'play'/install so I am unable to load the applications.

The drive works if I put a DVD in.

Any advise, what info do you need......

Please help before I get it in the neck!

---

### Post by efflandt on 2010-09-16
Just curious what Ubuntu would have to do with MS Office problems in Windows?  Are you trying to do this on a virtual Windows system, under Wine, or is Ubuntu a Wubi install (within Windows instead of separate partition)?

---

### Post by Jonners59 on 2010-09-17
> **efflandt said:**
> Just curious what Ubuntu would have to do with MS Office problems in Windows?  Are you trying to do this on a virtual Windows system, under Wine, or is Ubuntu a Wubi install (within Windows instead of separate partition)?

Sorry for the delay....  Wife went in to labour!!!!  Still waiting for the little un to arrive.

I have set all the machines up with 10.4 and then use both WINE and Crossover.  Crossover is a better/improved WINE.

The problem is whether WINE or Crossover I can not run the CD.  It does not spin or show up as a directory, yet I know it works as I can play DVDs perfectly.....

---

### Post by Jonners59 on 2010-09-17
> **jonusb3 said:**
> Weighing these two arguments, I [ny asian escort]("http://www.escortasianny.com") prefer to the latter one. In my eyes,  [ny asian escorts]("http://www.escortasianny.com") though “the moonlight clan” may acquire temporary satisfaction from their consumption, in [ny escorts]("http://www.escortasianny.com") the long term, it is unfavorable to their family and career. Just as a proverb says, one should [ny escort]("http://www.escortasianny.com") always prepare for a rainy day.

What planet are u on???

---

### Post by IcarusR on 2010-09-17
Why not just use OpenOffice, which runs on ubuntu natively & is compatible with MS office.

---

### Post by sikander3786 on 2010-09-17
> **Jonners59 said:**
> The problem is whether WINE or Crossover I can not run the CD.  It does not spin or show up as a directory, yet I know it works as I can play DVDs perfectly.....

Are you sure the disc is in proper working condition. Scratches... Does is mount under Windows, if you can somehow check the disc itself?

---

### Post by Jonners59 on 2010-09-19
> **sikander3786 said:**
> Are you sure the disc is in proper working condition. Scratches... Does is mount under Windows, if you can somehow check the disc itself?
I've used it several times, and only the day before on another machine, and tried it just now on the machine I am on now...  Works fine.

Could it be a driver, or something of that type?

---

### Post by Jonners59 on 2010-09-19
> **IcarusR said:**
> Why not just use OpenOffice, which runs on ubuntu natively & is compatible with MS office.
It is not that compatible, and completely changes all the formatting especially if you use fully, if it can even open...  Open Office is like MS O 2003, but 2007 and 2010 are a step change and far more advanced.  I do use Open Office for my basics and manipulating docs where I think it does well, but in general, there is so much more to 2007 and 2010.

My issue is not the ap it is the CD.  I have had it running, but had an error after the last kernal.  To be honest since starting this thread the kernal has now completly failed, and the machine will not boot beyond Grub2

---

### Post by Jonners59 on 2010-11-23
Can anyone help please????
 
This ONLY happens on ONE machine, my wife's pink (yes, it really is pink) Sony viao.
 
The drive plays other media fine, and the CD works on other machines fine.
 
When the CD is installed on THIS machine, the drive does not even mount.  It does not craete an icon on the desk top and it is not listed in places.

---

### Post by cariboo on 2010-11-23
Can you manually mount the CD?

```
sudo mkdir /media/cdrom
```

then

```
sudo mount /dev/sr0 /media/cdrom
```

---

### Post by Jonners59 on 2010-11-23
> **cariboo907 said:**
> Can you manually mount the CD?

```
sudo mkdir /media/cdrom
```then

```
sudo mount /dev/sr0 /media/cdrom
```

Hi Cariboo
Long time no see.  Trust you are well...

Ran the above, but it did not work..

```
chiara@chiara-Pinkviao:~$ sudo mkdir /media/cdrom
[sudo] password for chiara: 
chiara@chiara-Pinkviao:~$ sudo mount /dev/sr0 /media/cdrom
mount: /dev/sr0: unknown device
chiara@chiara-Pinkviao:~$
```

---

### Post by cariboo on 2010-11-24
The cdrom may be aliased to something else other than /dev/sr0, to check open a terminal and type:

```
ls -l /dev/cdrom
```

in my case it echos back:

```
ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2010-11-24 09:00 /dev/cdrom -> sr0
```

Use whatever it tells you, and try again.

I'm doing well, but it's been awful cold the last couple of days.

---

### Post by Jonners59 on 2010-11-24
Same here...

I am not sure I am following correctly.

This is what I got.

[HTML]chiara@chiara-Pinkviao:~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 2010-11-24 20:41 /dev/cdrom -> sr0
chiara@chiara-Pinkviao:~$ sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists
chiara@chiara-Pinkviao:~$ sudo mount /dev/sr0 /media/cdrom
mount: /dev/sr0: unknown device
chiara@chiara-Pinkviao:~$[/HTML]

---

### Post by CharlesA on 2010-12-02
I usually mount cds like this:

```
sudo mount /dev/cdrom /cdrom/
```

See it that'll work.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> I usually mount cds like this:

```
sudo mount /dev/cdrom /cdrom/
```See it that'll work.

Didn't work....

[HTML]chiara@chiara-Pinkviao:~$ sudo mount /dev/cdrom /cdrom/
mount: /dev/sr0: unknown device
chiara@chiara-Pinkviao:~$ [/HTML]

---

### Post by CharlesA on 2010-12-02
Can you post the output of this please:

```
ls -la /dev/cdrom
```
```
ls -la /dev/dvd
```

---

### Post by pricetech on 2010-12-02
As a workaround, you could put the disk in the other computer's drive and share that drive across the network and install that way.

---

### Post by Jonners59 on 2010-12-03
> **CharlesA said:**
> Can you post the output of this please:

```
ls -la /dev/cdrom
``````
ls -la /dev/dvd
```

They seem the same.  COuld it be blocked in some way or a driver missing?  There has abeen a lot of talk about the excessive security on the new releases, stopping the use of *.exe installs.

[HTML]chiara@chiara-Pinkviao:~$ ls -la /dev/cdrom
lrwxrwxrwx 1 root root 3 2010-12-03 07:11 /dev/cdrom -> sr0
chiara@chiara-Pinkviao:~$ ls -la /dev/dvd
lrwxrwxrwx 1 root root 3 2010-12-03 07:11 /dev/dvd -> sr0
chiara@chiara-Pinkviao:~$ [/HTML]

PS:  Our share solution does not work completely.  DNLA (Tv access) has stopped working as a result.  Done a full circle.

---

### Post by Jonners59 on 2010-12-03
> **pricetech said:**
> As a workaround, you could put the disk in the other computer's drive and share that drive across the network and install that way.

Could, but that's not the point.  Thanks anyway.

---

### Post by owiknowi on 2010-12-03
My first thought was: what kind of CD do you use? Is it an original MS Office CD or one provided by Sony (shipped with the laptop)?  If you have a registration code you should be able to obtain an original (OEM) CD from MS (download and burn at minimal speed).

---

### Post by Jonners59 on 2010-12-03
> **owiknowi said:**
> My first thought was: what kind of CD do you use? Is it an original MS Office CD or one provided by Sony (shipped with the laptop)?  If you have a registration code you should be able to obtain an original (OEM) CD from MS (download and burn at minimal speed).

It is a genuine, fully working Microsoft Windows Office 2007 install CD bought directly from Microsoft.  No pirate or other.

It works fine on all other machines, Windows and Ubuntu 9.10, 10.4 and 10.10, but not this one.

This machine does run DVDs perfectly well so the player is fine.

---

### Post by CharlesA on 2010-12-03
If the drive still won't read the disc, you could always copy the files to a thumb drive and do it that way.

If it's the only machine having problems, I would suggest making a copy of the cd and trying to see if the copy will read or not. I'd blame a flaky drive tbh.

---

### Post by Jonners59 on 2010-12-03
> **CharlesA said:**
> If the drive still won't read the disc, you could always copy the files to a thumb drive and do it that way.

If it's the only machine having problems, I would suggest making a copy of the cd and trying to see if the copy will read or not. I'd blame a flaky drive tbh.

" thumb drive"?

The problem I have is that on this machine i can not open the CD as it does not appear or mount in any way.  Would be nice to understand why and get it going too.

---

### Post by CharlesA on 2010-12-03
> **Jonners59 said:**
> " thumb drive"?

[USB drive/pen drive/whatever you want to call it]("http://www.google.com/products/catalog?hl=en&expIds=17259,27213,27753,27868&sugexp=ldymls&xhr=t&q=thumb+drive&cp=6&um=1&ie=UTF-8&cid=16433823676753255760&ei=5SH5TMrIC4G78gbazMXpCQ&sa=X&oi=product_catalog_result&ct=image&resnum=10&sqi=2&ved=0CHAQ8gIwCQ#").

> The problem I have is that on this machine i can not open the CD as it does not appear or mount in any way.  Would be nice to understand why and get it going too.

I don't know what the problem is, since other media mount properly.

---

### Post by Jonners59 on 2010-12-03
Ah, with you...  USB stick or memory stick over here.

---

### Post by CharlesA on 2010-12-03
Yep. :)

---

### Post by Jonners59 on 2010-12-03
> **CharlesA said:**
> Yep. :)
I know, I am slow...  Just go easy with the slap

---

### Post by CharlesA on 2010-12-03
Lol. Different words mean different things in different areas. :P

---

### Post by owiknowi on 2010-12-04
Maybe this is to obvious:  Copy the files from the USB drive to the local HDD. This way you don't need any external media in order to use the software.  In order to do so you could create a small FAT32 or NTFS partition.

---

### Post by Jonners59 on 2010-12-04
I think we are going off plot here.  The issue is that the DVD player was used to install Microsoft Office. and play DVDs.  The MS Office stopped working for some reason, so we want to re-install it.  The DVD still plays DVDs, BUT it will not mount for MS Office CD...  In fact the device does not even appear, in any form and so can not be mounted.  This is what we want to fix, not just copy the CD on to a storage device of another CD via another machine.  But fix this one.

---

### Post by CharlesA on 2010-12-04
The only thing I can really suggest is to burn a copy of the cd and try the copy.

That would rule out the disc.

I know I've had drives that get picky about which discs they will read.

---

### Post by Jonners59 on 2010-12-04
> **CharlesA said:**
> The only thing I can really suggest is to burn a copy of the cd and try the copy.

That would rule out the disc.

I know I've had drives that get picky about which discs they will read.
That sounds a good idea

---

### Post by Jonners59 on 2011-01-03
Still no joy with this, though closer.

I copied the CD to a memory stick and tried that.  It would not boot, so I copied the contents of the memory stick to the Desktop of the machine

I then realized why it may not have worked off the stick, as the *.exe files were not set to "executable", which I changed on  the desktop version...

I then ran the desktop version, and it started to load.  It installed all of the extra bits and bobs and then came to the MS Office bit.  It started to install, including adding the key, but then got stuck in finding the uinstall files.  No matter what I tried it would not accept the location of the files it wanted, and so it cancels the install.

Any ideas folks?????):P

---

### Post by Jonners59 on 2011-01-07
Besides the below steps taken, I have completely rebuilt the machines and still it will not work.  I am certain it is just a tick in the box or driver that is missing.  Please, can anyone help?????

---

### Post by CharlesA on 2011-01-07
Don't really have any other steps for you to try, outside of just using OpenOffice, which isn't what you want to do.

---

