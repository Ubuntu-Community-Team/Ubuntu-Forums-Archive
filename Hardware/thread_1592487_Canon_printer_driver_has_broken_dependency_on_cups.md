---
title: "Canon printer driver has broken dependency on cupsys"
date: 2010-10-10
forum: Hardware
---

### Post by AndyC_772 on 2010-10-10
Hi all,

Just upgraded to 10.10 and I can't get the official Canon driver for my printer to install. The printer is an i-SENSYS MF4690PL.

The driver comes as two .deb packages called cndrvcups-common_2.10-1_i386 and cndrvcups-ufr2-uk_2.10-1_i386.

This driver has had a history of dependency problems caused by the renaming of the libcupsys2 package a few releases back, and I've always worked around this using a transitional package called libcupsys2 (version 1.3.9-17ubuntu3.4 - I forget where I got it from, not the usual repositories) - but since the update to 10.10 this no longer helps.

Now instead I get:

```
sudo dpkg -i cndrvcups-common_2.10-1_i386.deb 
Selecting previously deselected package cndrvcups-common.
(Reading database ... 122224 files and directories currently installed.)
Unpacking cndrvcups-common (from cndrvcups-common_2.10-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on cupsys; however:
  Package cupsys is not installed.
dpkg: error processing cndrvcups-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-common

```

The other Canon package depends on this one, so it can't be installed either.

Any ideas please? I can print using a generic PCL6 driver, but I'd rather use the dedicated Canon one if possible.

---

### Post by sikander3786 on 2010-10-10
Did you try

```
sudo apt-get install cupsys
```

---

### Post by AndyC_772 on 2010-10-10
```
sudo apt-get install cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cupsys is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'cupsys' has no installation candidate
```

Nice idea... not that easy I'm afraid, though :(

---

### Post by sikander3786 on 2010-10-10
Here is what I got on Lucid.

```
malik@AMD:~$ sudo apt-get install cupsys
[sudo] password for malik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 42 not upgraded.
Need to get 73.4kB of archives.
After this operation, 115kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe cupsys 1.4.3-1ubuntu1.2 [73.4kB]
Fetched 73.4kB in 4s (16.3kB/s) 
Selecting previously deselected package cupsys.
(Reading database ... 155394 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.4.3-1ubuntu1.2_all.deb) ...
Setting up cupsys (1.4.3-1ubuntu1.2) ...
```

This problem seems to be Maverick specific. I couldn't find "cupsys" for Maverick here either.

[http://packages.ubuntu.com/search?keywords=cupsys](http://packages.ubuntu.com/search?keywords=cupsys)

I am not using Maverick right now, might be it has been discontinued, renamed or removed in Maverick. Let someone else jump in.

---

### Post by notlistening on 2010-10-11
Try looking here for your printer solution:

[http://help.ubuntu.com/community/CanonCaptDrv190](http://help.ubuntu.com/community/CanonCaptDrv190)

Just managed to get it running today after an hour or so. 

NL

---

### Post by yazid1 on 2010-10-11
Hi man,
try to install this transitional package [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb)

It works for me and it should work also for you ;)

Bye :)

---

### Post by bratliff on 2010-10-11
Thank you, Thank you, Thank you. I have been working on this for a while and this fixes the problem.

Bratliff



> **yazid1 said:**
> Hi man,
try to install this transitional package [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb)

It works for me and it should work also for you ;)

Bye :)

---

### Post by AndyC_772 on 2010-10-12
> **yazid1 said:**
> try to install this transitional package [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb)


Works a treat - thanks :)

---

### Post by yazid1 on 2010-10-12
Enjoy your new Maverick guys!!! ;)

---

### Post by ashish89_taurus on 2010-10-16
I have a Canon LBP2900.
My printer was working fine in 10.04
but not working after 10.10 upgrade.
The .deb you gave above is not working for me.
Help.

---

### Post by AndyC_772 on 2010-10-17
Can you describe the problem in a bit more detail?

Does it fail to install? Do you know which package appears to be missing?

If you can copy & paste the error message you're getting then maybe someone can help fix it. The more information the better :)

---

### Post by ashish89_taurus on 2010-10-17
Everything seems to be fine. But when I give command to print, the status in the Document print status shows  processing all the time.

Also when I went in the properties of the printer and clicked Print Self Test page it shows the error 

CUPS Server Error
There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I have tried everything I could find on Ubuntu forums regarding canon drivers and its installation in 10.10

Before I installed the .deb given here, i used to get the error message, 
Printer filter missing.

---

### Post by serdarhappy on 2010-10-21
> **yazid1 said:**
> Hi man,
try to install this transitional package [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb)

It works for me and it should work also for you ;)

Bye :)

Thanks this also solved my problem. I was almost going crazy and saw your post. That saved me. Thanks again.

---

### Post by onthenarrowpath on 2010-10-23
Great, great, great, yazid1! This dummy file did the job for me and saved my day!
Maverick is a real eyecandy, by the way ;-).

---

### Post by gcmelzi on 2010-10-25
I tried, but the dummy package didn't solve my problem, altough it looks very similar.
Printer is Pixma MP540 and it was working properly in 9.10.
I upgraded to 10.10, and since then haven't been able to get it working. 
I tried installing the dummy package and then the "common" driver downloaded from Canon site. 
See below what I'm getting with GDebi (basically, cache corrupted):
**Errore: impossibile soddisfare tutte le dipendenze (cache non integra)**
Anything you could suggest, please?

---

### Post by mnoyes on 2010-11-01
Nice work! -- I wish I had found this earlier, before hours lost on searching and trial and error. This kind of problem makes Ubuntu hard to recommend but this kind of collective troubleshooting/help makes it easy to recommend.

---

### Post by Doggo#86 on 2010-11-27
Hi

Thanks for all your help it worked great. My Canon MF4270 now works in Maverick.
I downloaded the printer driver from:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)

installed cupsys, except the link has changed to:
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb)

Then I installed the 2 .deb files that I downloaded above.

---

### Post by james a on 2010-12-02
Hi,

Thanks to  the team , i was struggling last  two days trying to install my Canon iR 3225 MFD printer driver
on Ubuntu 10.10,  since the old link was not working.

Finally i was able to print on my iR 3325 


Thanks a lot

---

### Post by Tavathlon on 2010-12-05
Yay, thank you! This also worked for my sister's old Pixma iP1300! (along with the guide in [http://ubuntuforums.org/showthread.php?p=3450617](http://ubuntuforums.org/showthread.php?p=3450617))

---

