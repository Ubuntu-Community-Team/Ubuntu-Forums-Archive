---
title: "Canon Pixma MP270"
date: 2011-05-18
forum: Hardware
---

### Post by VictorGF on 2011-05-18
I would love to be able to switch from Windows Xp but I have tried several attempts to install my printer. Can anyone help. explained simply please as I am accustomed to the easy method used by Windows.
My printer is:  Cannon Pixma MP270.

Many thanks.

---

### Post by aphatak on 2011-05-18
Canon Europe have a Linux driver for Pixma 270 - try this site - "http://software.canon-europe.com/products/0010753.asp".  They apparently have a .deb package which you should be able to install easily enough, usually by double-clicking the file name in Nautilus.

---

### Post by FriscoSoxFan on 2011-05-18
Its not your model, but after hours of frustration trying to install my ip3300 canon using foreign RPMs, I learned that the print head on my printer is the same as other models that there are out-of-the-box drivers for. 

Try googling from that angle. I wouldn't be surprised if a different model's driver works fine for you. Its just a matter of finding the right one.

---

### Post by VictorGF on 2011-05-18
> **aphatak said:**
> Canon Europe have a Linux driver for Pixma 270 - try this site - "http://software.canon-europe.com/products/0010753.asp".  They apparently have a .deb package which you should be able to install easily enough, usually by double-clicking the file name in Nautilus.

Thanks for that, downloaded but it doesn't show an"exe" anywhere, and I have no idea what Nautilus, cant see the name anywhere.  Any more clues?

As you can see I am a newbie at Linux, didn't start using a PC till I was 68, now am 79 and have only used Windows, but disapointed, so liked look of Ubunto etc.

---

### Post by aphatak on 2011-05-18
A Linux driver will not have an exe extension.  The driver comes as a 'package', not an executable.  When you download the package, it will most likely be in your Downloads directory (/home/<username>/Downloads).  It will have a '.deb' extension.

You have to install and start Linux to install the Linux driver.  You cannot do it from Windows.  If you haven't already done it, install Ubuntu in a dual-boot configuration - meaning retain Windows XP, and install Ubuntu in a small partition of the hard drive.  That way, you have both the operating systems, and you can boot into any one of them.  If you haven't installed Ubuntu yet, I'd recommend Ubuntu 10.04 LTS - LTS stands for Long Term Support.  This version has been around for a while for bugs to have been fixed, and it will be around (and supported) at least till the next LTS version comes out.  If you are feeling brave and adventurous, you can go for the latest and the sexiest version - 11.04.  However, understand that the birth of this version was accompanied by cries of pain, and you might end up adding your voice to the chorus!

Once you are comfortable with Linux, and have played around with it, download the driver package.  Nautilus in Ubuntu is the 'File Manager' in Windows.  It looks the same, feels the same, smells the same and behaves the same - or similar enough not to make a difference.  Open your home directory, then Downloads, and move the driver package files to another directory.  You should find a text file in the set with instructions on how to install.  Follow them and you should be printing happily.  If you don't, or need any help, give us a shout in this forum.

And if you are only 79 years young, you should look forward to a long and pleasant relationship with Ubuntu.

---

### Post by VictorGF on 2011-05-18
I have Ubuntu on a separate hard drive in the hope that I might clean the Windows HDD, eventually, for further use as a spare for back ups etc. I started with 8.04 and upgraded up to 10.4. Like the look and feel but would love to be able to use fully.  I also have Mandake on another HDD and also played around with Mint, Puppy and OpenSUSE, eventually settling on Ubuntu, I wonder if I chose the right one?

---

### Post by VictorGF on 2011-05-18
OK, got so far and come to some 'gobble d'gook'  thats double dutch to me, is there some way a simply click to install available? Make life easier.

This is what I found, what do I do now?

                       For Ubuntu 9.04
 1) Expanding the archived file and switching to the expanded directory
 [user@zzz /yyy]$ tar zxvf cnijfilter-mp270series-3.20-x-i386-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mp270series-3.20-x-i386-deb
 2) Installing the printer driver
 [user@zzz /yyy]$ sudo ./install.sh

---

### Post by StrayEddy on 2011-05-18
Yep good, that s the way to install your package.

---

### Post by VictorGF on 2011-05-18
May look good to some of you, but how do I do all that? Tis a mystery to me.

---

### Post by VictorGF on 2011-05-19
Looks as if I will have to keep Windows as I do not understand what the above was all about,unless someone can explain it to me in simple terms.  All I wanted to do was to be able to use my printer/scanner with Ubuntu but it seems a complicated procedure to set up.

---

### Post by VictorGF on 2011-05-19
Hi, is there anyone out there who can explain to me what the following means and how do I go about it? Otherwise I will have to give up Linux and keep Windows XP.

For Ubuntu 9.04
 1) Expanding the archived file and switching to the expanded directory
 [user@zzz /yyy]$ tar zxvf cnijfilter-mp270series-3.20-x-i386-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mp270series-3.20-x-i386-deb
 2) Installing the printer driver
 [user@zzz /yyy]$ sudo ./install.sh

---

### Post by Joelbruce on 2011-05-19
I[m having my own problems doing this, but I can tell you that commands are entered in a terminal window, or box. In the applications menu click on accessories and go down to Terminal. When you get the box you will see how the commands fit with the preprinted part. The word sudo at the begining is the administrators word, so you will be prompted for your password before the command will be executed. My problem is that when I type my password characters they don't show up on the screen!

---

### Post by VictorGF on 2011-06-17
Totally at a loss of how to enter this information to load to get my printer to work, anyone have simple instruction as to how I do this?
Thanks.:(

---

### Post by demonipuch on 2011-06-17
> **VictorGF said:**
> Totally at a loss of how to enter this information to load to get my printer to work, anyone have simple instruction as to how I do this?
Thanks.:(

Hi

Open a terminal and run these commands :

```
wget http://files.canon-europe.com/files/soft37268/Software/MP270_debian_driver_pack.tar
```This will download an archive containing your printer driver.

```
tar xvf MP270_debian_driver_pack.tar
```This will extract the content of the downloaded archive. You'll obtain a file called cnijfilter-mp270-3.20-i386-deb.tar.gz

```
tar zxvf cnijfilter-mp270-3.20-i386-deb.tar.gz
```This will extract files contained in  cnijfilter-mp270-3.20-i386-deb.tar.gz. You'll get a directory called cnijfilter-mp270series-3.20-1-i386-deb.

```
cd cnijfilter-mp270series-3.20-1-i386-deb
```To change the current path.

```
sudo ./install.sh
```This will run the installation script. Follow instructions to install your printer.

---

### Post by mainman44 on 2011-11-21
Hi Victor,

I too am a new user to Ubuntu and I am having the same problems in installing the driver for the same printer!

Did you ever manage to do it?  I find the Linux way of installing stuff difficult to understand as well - although I love using Ubuntu.  Just wish the software installing was more straight forward!

M.

---

### Post by demonipuch on 2011-11-21
Hello mainman44

All you need to do is running these commands in a terminal :

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp270series scangearmp-mp270series
```

---

### Post by mainman44 on 2011-11-23
Hi,

I followed advice on the forum from other newbies like me who had problems installing drivers/software on Ubuntu - completely different experience from Mac and Windows!

I have eventually installed the print and scanner drivers for my printer, but still can't use the printer/scanner.

I can bring up the print dialogue box OK and looks like I can print  etc., but then nothing happens.  I am also getting the following messag when I select the MP270 printer from the Applications-Accessories menu:

Could not launch 'MP270'

Failed to execute child process "/home/martind/Downloads/MP270_debian_driver_pack.tar" (Permission denied)

Any help to solve this would be greatly appreciated, as I have spent over a week trying to get a working printer.

Thanks!

---

### Post by mörgæs on 2011-11-23
Please don't double post. 
Threads merged.

---

