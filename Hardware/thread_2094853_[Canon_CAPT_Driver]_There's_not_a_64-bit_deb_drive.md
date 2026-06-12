---
title: "[Canon CAPT Driver] There's not a 64-bit deb driver in the recommended CAPT package??"
date: 2012-12-15
forum: Hardware
---

### Post by acronim on 2012-12-15
This is my printer: [http://www.canon.com.au/For-You/Printers/LaserShot-Laser-Printers/LBP3100B](http://www.canon.com.au/For-You/Printers/LaserShot-Laser-Printers/LBP3100B)
It's recommended a CAPT driver for Canon's printers LBP series on Ubuntu 12.04 here: [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)

Now I'm on Ubuntu 12.04 64bit
I unpacked the [Linux CAPT Printer Driver v2.40](http://gdlp01.c-wss.com/gds/4/0900007724/12/Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz) that I'v downloaded. the below picture shows its contents:

[img]http://i4.minus.com/jUF40SE1LVk12.png[/img]

As you see, there's not any 64-bit deb package for Debian/Ubuntu! What should I do?

(I try to convert 64-bit rpm packages to ded file using this command:
```
sudo alien -dc *.rpm
```
the convert process was successfully. I follow the "Doc" installation instruction:
```
sudo dpkg -i *.deb
sudo service cups restart
sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3150CAPTK.ppd -v ccp://localhost:59787 -E
sudo /usr/sbin/ccpdadmin -p LBP3100 -o /dev/usb/lp0
sudo service ccpd start
```
Done! except one thing:
Ubuntu help page says:
> Note: Ubuntu 12.04 has again blacklisted the usblp module which creates the /dev/usb/lp0 device link. To solve this problem do this```
sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf
```Then comment the file to look like this, canons driver does not talk to the printer through cups:
# cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
# blacklist usblp
But there's NOT the "blacklist-cups-usblp.conf" file in the"/etc/modprobe.d" directory!


However,  I get this error when I try to print a page:
/usr/lib/cups/filter/pstocapt3 failed

!!) I tried to install 32 bit deb files (refer to above image) on a 10.04  that was installed on a 32bit-machine and it worked!
Now I want to install it on my home pc (Ubuntu 64bit 12.04) to work??

---

### Post by pdc on 2012-12-16
> /usr/lib/cups/filter/pstocapt3 failed

I think if you use the SEARCH function from your MENU; 

and search on 

> pstocapt3 in your File System; 

........it may be in /usr/lib64/cups/filter

...if so .....if you copy it to /usr/lib/cups/filter

> [COLOR="Red"]sudo cp /usr/lib64 /cups/filter/pstocapt3 /usr/lib/cups/filter[/COLOR] 

[http://www.tuxfiles.org/linuxhelp/fileman.html](http://www.tuxfiles.org/linuxhelp/fileman.html)

......... I have an LBP3100 and it works well; I stick with 32 bit; it works

(my pstocapt3 is in /usr/lib/cups/filter)

---

### Post by acronim on 2012-12-18
tnx for the info.

> **pdc said:**
> 
........it may be in /usr/lib64/cups/filter

...if so .....if you copy it to /usr/lib/cups/filter

Done! It is NOT working yet!

Why there's not a 64-bit deb-binary package for CAPT driver?

> **pdc said:**
> 
......... I have an LBP3100 and it works well; I stick with 32 bit; it works
You're right. It work on 32-bit systems, but my OS is 64-bit!

---

### Post by grahammechanical on 2012-12-18
I may be completely wrong about this. Perhaps someone else will confirm my error. But I think that you need to create the file

> blacklist-cups-usblp.conf

We do that by running the command

```
sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf
```

If my understanding is correct, that command will open the text editor called Nano with a new file called blacklist-cups-usblp.conf.

You then put these lines in the file

> # cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
# blacklist usblp

and then save the file. Then there will be a blacklist-cups-usblp.conf file in /etc/modprobe.d folder.

I am guessing that the very existence of the file acts as the blacklist. The comments are there as information as to why the file was created.
Regards.

---

### Post by acronim on 2012-12-21
@[grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")
I done, nothing happend, Still not working :(

The below commands are those I done:
```
sudo alien -dc *.rpm
sudo dpkg -i *.deb
sudo /etc/init.d/cupsys restart
sudo /usr/sbin/lpadmin -p LBP3100 -m CNCUPSLBP3150CAPTK.ppd -v ccp://localhost:59787 -E
sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf
sudo /usr/sbin/ccpdadmin -p LBP3100 -o /dev/usb/lp0
sudo /etc/init.d/ccpd start
sudo rm /usr/lib/cups/filter/pstocapt /usr/lib/cups/filter/pstocapt2 /usr/lib/cups/filter/pstocapt3 /usr/lib/cups/backend/ccp
sudo cp /usr/lib64/cups/filter/pstocapt* /usr/lib/cups/filter/
sudo cp /usr/lib64/backend/ccp /usr/lib/cups/backend/
sudo cp /usr/lib64/cups/backend/ccp /usr/lib/cups/backend/
sudo apt-get install pixmap 
```

---

### Post by acronim on 2012-12-22
The below picture shows current status of my printer settings.  (Please click on the image to enlarge it)

[URL="http://img819.imageshack.us/img819/1197/lpb3100b.png"]
[IMG]http://imageshack.us/scaled/landing/819/lpb3100b.png[/IMG]
[/URL]

Please help me, I don't like to reinstall a 32-bit Ubuntu !!!

---

### Post by acronim on 2012-12-25
Up
:'(

---

### Post by acronim on 2012-12-28
nobody has LBP canon printer, here?

---

### Post by pdc on 2012-12-28
yes indeed they do; I have a 32bit Mint system; and an LBP 3100B and it works beautifully each time; I have answered posts about the LBP series; 

for those insisting on having a 64bit system, it falls to them to research; read the posts and try to tease out what are the issues: 

Confuxius say:

sometimes good is better than *better* ......

and sometimes okay is much better than *better* ............

---

### Post by acronim on 2013-01-01
> **pdc said:**
> I have answered posts about the LBP series
have you ever answered/saw any post about installing CAPT driver on 64-bit OS?

> **pdc said:**
> 
for those insisting on having a 64bit system, it falls to them to research; read the posts and try to tease out what are the issues
I'm confused why there is NOT a 64 bit deb file while there is a 64 bit rpm file in the [recommended CAPT package]("https://help.ubuntu.com/community/CanonCaptDrv190")?!!!!

---

### Post by pdc on 2013-01-02
it must be very frustrating and irritating and annoying to not get the CAPT driver running;

sivella has posted on how to get the LBP running on a 64bit system: see post #11 if you are not already familiar with it

[http://ubuntuforums.org/showthread.php?t=1982917&page=2](http://ubuntuforums.org/showthread.php?t=1982917&page=2)

sorry to hear you are confused

> I'm confused why there is NOT a 64 bit deb file while there is a 64 bit rpm file in the recommended CAPT package?!!!! 

.....one explanation would be that the LBP drivers are written by Canon ..so you get what they provide ..

..it should be a simple matter with alien to convert; and install an rpm package for a debian system

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

eg

> *[COLOR="SeaGreen"]Convert the package.rpm into a package.deb, and install the generated package[/COLOR]*.

 [COLOR="Red"]sudo alien -i package-name.rpm[/COLOR]

---

