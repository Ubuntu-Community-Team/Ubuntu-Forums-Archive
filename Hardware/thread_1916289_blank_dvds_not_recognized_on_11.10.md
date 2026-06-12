---
title: "blank dvds not recognized on 11.10"
date: 2012-01-27
forum: Hardware
---

### Post by noworldorder on 2012-01-27
Ubuntu 11.10

It is not recognizing blank dvds in the drive - not showing up in nautelis and brazario cannot see it.  However, if there is a dvd with a file on it it is recognized.  

No luck with k3b... When I run it it says:

> No CD/DVD/BD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs.

Any ideas?

---

### Post by noworldorder on 2012-02-10
Bump...  please help - I cannot find a solution to this anywhere... :confused:

---

### Post by winh8r on 2012-02-10
have you got cdrdao installed?

---

### Post by noworldorder on 2012-02-10
> have you got cdrdao installed?

Thanks for the reply...  Yes I do have that installed

---

### Post by winh8r on 2012-02-10
what is the *-cdrom part of the output from the command:


sudo lshw

---

### Post by noworldorder on 2012-02-10
*-cdrom
                description: DVD reader
                product: DVD-ROM DS-8D3SH
                vendor: PLDS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HD13
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc

---

### Post by winh8r on 2012-02-11
> **noworldorder said:**
> *-cdrom
                description: DVD reader
                product: DVD-ROM DS-8D3SH
                vendor: PLDS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HD13
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc

Looks like that is your problem then. Your drive is a DVD reader only.
DVD-ROM = READ ONLY MEMORY.

You will need to acquire a DVD RW (READ+WRITE) drive in order to record to DVD.
The ooutput you should see is like this for a DVD writer drive:
*-cdrom
                description: DVD writer
                product: CD/DVDW TS-H552D
                vendor: TSSTcorp
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP06
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc





Hope this helps you.


Please mark the thread as solved using the thread tools at the top right of the page

Thanks.

---

