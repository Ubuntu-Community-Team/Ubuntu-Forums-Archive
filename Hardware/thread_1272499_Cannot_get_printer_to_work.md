---
title: "Cannot get printer to work"
date: 2009-09-22
forum: Hardware
---

### Post by Rick Abraham on 2009-09-22
Hi guys I am using Ubuntu 9.04 and Im trying to get my Brother HL-2140 printer to work with Linux.
I plugged the printer in and switched it on, Ubuntu searched the database for a driver and came back with a HL-2170W driver.
I tried to install that but it didnt work, so I deleted that driver.
I then did a Google search and came across Brothers support page and found some drivers for Linux users.
So I downloaded the following files.

brhl2140lpr-2.0.2-1.i386.deb
cupswrapperHL2140-2.0.2-1.i386.deb
Im not sure whats the difference between a LPR driver and a Cupswrapper driver so I downloaded both.

but when I try and execute these files I get the following message.
Could not open
The package might be corrupted or you are not allowed to open the file.
Check the permissions of the file.

Im not sure what to do as I am a new user to Ubuntu
Please help !!

---

### Post by Rick Abraham on 2009-09-22
I followed these instructions but still no good.

[FONT=ms sans serif, helvetica][I]1) Plug in the printer to the computer. Ignore all the prompts, hit cancel, etc.
     2) Download the LPR and CUPS deb files from this link (or search     for them on the site): [http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140)
     3) sudo mkdir /usr/share/cups/model
     4) sudo dpkg -i --force-all --force-architecture [the two debs you     downloaded]
    **THE FORCE SWITCHES ARE VITAL FOR 64 BIT     MACHINES!**
      5)Profit. The printer should work and show up as "HL2140".[/I][/FONT]

---

### Post by Bucky Ball on 2009-09-22
brhl2140lpr-2.0.2-1.i386.deb

What happens when you just double click that file on the desktop or wherever you have saved it?

---

### Post by wojox on 2009-09-22
Try this:

[http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer)

---

### Post by ajackson on 2009-09-22
> **wojox said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=Brothers+printer)

Wojox when will you listen? A lot of the DEBs on the Brother Linux site do not currently exist, so all you get is redirected to another page (that is what you save if you right click).

In case you need it mentioning again **A lot of the DEBs on the Brother Linux site do not currently exist, so all you get is redirected to another page (that is what you save if you right click)**, so kindly stop blindly referring people to the how-to.

---

### Post by Rick Abraham on 2009-09-22
When I try and run the .deb packages in the terminal it gives me an error saying that they are not Debian format.
But the site that I downloaded them from said that they are Debian format.

I might have to download drivers from a different site and try them.
Does anyone know where I can find Linux Brother drivers ??

---

### Post by Rick Abraham on 2009-09-22
I wasnt able to find any other debian brother printer drivers to try, but I did find some more info regarding trying to install these .deb packages so below are some commands I tried to run but still had no luck.

ubuntu@Laptop:~$ sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
ubuntu@Laptop:~$ sudo mkdir /usr/share/cups/model
mkdir: cannot create directory `/usr/share/cups/model': File exists
ubuntu@Laptop:~$ sudo dpkg -i --force-all cupswrapper_hl_2140.deb
dpkg-deb: `cupswrapper_hl_2140.deb' is not a debian format archive
dpkg: error processing cupswrapper_hl_2140.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cupswrapper_hl_2140.deb
ubuntu@Laptop:~$ sudo dpkg -i --force-all lpr_hl_2140.deb
dpkg-deb: `lpr_hl_2140.deb' is not a debian format archive
dpkg: error processing lpr_hl_2140.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 lpr_hl_2140.deb
ubuntu@Laptop:~$

---

### Post by Rick Abraham on 2009-09-23
I noticed the .deb packages that I downloaded from Brothers webpage were only 1.4kb each.
The LPR deb is meant to be 40kb and the CUPS deb is meant to be 13kb.

So I contacted Brother support and told them this.
They said that there drivers are downloaded from a webpage maintained in Japan, so they have contacted them to see if they can fix the problem.
So I guess I just have to wait.

---

