---
title: "Can't burn or mount using dvd writer???"
date: 2009-03-11
forum: Hardware
---

### Post by BFDFF on 2009-03-11
I was attempting to burn a Data DVD with Brasero. It never gave me the option to burn the disk. I looked in Places>Computer and the CD-RW/DVD-RW is listed. If I click on properties all info is unknown. If Search in the terminal it shows up as :
  *-cdrom
                description: DVD writer
                product: CD/DVDW TS-L532A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TI51
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

I have tried searching for help mounting the device. Nothing seems to work. any ideas??

---

### Post by abhishek.malhotra35 on 2009-03-11
The configuration looks good. Does your Burn button gets enabled when you add a file to burn. For me, when I click on it, it asks me to either burn the DVD or make an image. Normally I don't use Brasero. I had bad experience with it. Instead I use K3B. Good software to burn DVDs.

---

### Post by BFDFF on 2009-03-11
The burn button doesn't even become enabled. The only "location" to burn to is file image.

---

### Post by utnubuuser on 2009-03-11
hi -> [http://forums.cnet.com/5208-6617_102-0.html?forumID=11&threadID=284097&messageID=2705370](http://forums.cnet.com/5208-6617_102-0.html?forumID=11&threadID=284097&messageID=2705370)

---

### Post by BFDFF on 2009-03-11
Thank you all. I discovered that Brasero has been having some issues and under the advice tried K3b which worked wonderfully. Thank you for the time and research to help me in my quest.

---

