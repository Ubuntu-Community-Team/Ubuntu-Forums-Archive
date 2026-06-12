---
title: "Printing on Epson AcuLaser C1100"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by brynk on 2006-10-16
I just installed Edgy on my desktop and can't get my printer to work again.
It's an Epson AcuLaser C1100 connected through usb.
I remember fiddling around with the drivers in Dapper, but I don't know what finally did the trick.
I used [these drivers]("http://www.avasys.jp/english/linux_e/dl_laser.html") for dapper.
Can anybody help me out?

---

### Post by brynk on 2006-10-23
Almost a week later and still no luck. I know for a fact I used the same drivers in Dapper so I'm really wondering what I'm doing wrong..
Anybody have any ideas?

---

### Post by brynk on 2006-10-23
Ok, I just threw my printer out the window out of frustration, so... problem solved.

---

### Post by _P_ on 2006-10-25
Hi Same here with a CX11FN. It worked well with breezy, almost well with dapper and no work with edgy. Epson has always the same old driver on his awasys site. 

 renderer command: pstoalcx11.sh  PageSize=a4 XY600=4720x6776 MediaType=normal TonerSave=false InputSlot=autoselection Collate=off Copies=1 Color=color Resolution=300
D [25/Oct/2006:11:00:09 +0200] [Job 19]
D [25/Oct/2006:11:00:09 +0200] [Job 19] Closing renderer
D [25/Oct/2006:11:00:09 +0200] [Job 19] /usr/bin/pstoalcx11.sh: 206: arith: syntax error: "Copies"
D [25/Oct/2006:11:00:09 +0200] [Job 19] renderer return value: 2
D [25/Oct/2006:11:00:09 +0200] [Job 19] renderer received signal: 2
D [25/Oct/2006:11:00:09 +0200] [Job 19] KID3 exited with status 1
D [25/Oct/2006:11:00:09 +0200] [Job 19] Process dying with "The renderer command line returned an unrecognized error code 2.", exit stat: 1


this is the error part of the log that ending with a foomatic-rip error exit.

I tryed with an old cups versione and the 1.3cvs but with no luck. 
..waiting ...
:-?

---

### Post by brynk on 2006-10-25
Ok, so I didn't actually throw it out :)
I thought I'd try installing it in dapper again the same way I did in edgy to see if I did something wrong. It worked like a charm, so it's definately an edgy problem. I don't know if it's got to do with cups or something else, maybe someone knows something for me to try?

---

### Post by _P_ on 2006-10-26
Confirm this bug here [https://launchpad.net/distros/ubuntu/+bug/68183]("https://launchpad.net/distros/ubuntu/+bug/68183")
if you can 
thanks

---

### Post by brynk on 2006-10-26
Ok, done. I hope someone'll find out what the problem is soon.

---

### Post by brynk on 2006-11-01
Meanwhile in noprint land...
It's been a while and the printer still doesn't work. Other people with the same printer are having the problem too, so it's not just that I'm stupid.
I think Ubuntu is great and I've been using it since it first got out. However, I'm now actually thinking about switching to another distro just to get my printer working. It's a printer so it should just work, I don't want to put any more time in it. I was told the printer works without any problems in fedora, so maybe I should just give up and use that...

---

### Post by brynk on 2006-11-05
Well, I'm still using Ubuntu and printing as well. Other people using tis printer [check this out]("https://launchpad.net/distros/ubuntu/+bug/68183").

---

### Post by plusmore on 2006-11-17
Carsten Busse added the following on the Avasys website:

> Since updating to ubuntu edgy i had a showstopper with the printer driver/filter for the aculaser cx11.

The foomatic filter seems to break the pipe, so the printing always stopped.

After a bit of log file debugging i found out that in the script /usr/bin/pstoalcx11.sh is making some problems (at least on ubuntu edgy amd64) and its the bash arithmetic syntax which had some change.

Lines using arithmetic like $((Copies+1)) need to be changed to $(($Copies+1)) etc to make it work again!

there are three occurences in line 202,228 and 229 which need to be changed. this will work on all bash's

This works for me using a SMB connected C1100 from Edgy, hope this helps.

---

### Post by lsilver on 2007-05-05
I had my CX11NF printer working in 6.06 thanks to the fix as described above but now that I have moved to 7.04 it doesn't work, even with the change as per above.

Anyone know how to get the CX11NF working with Fiesty?

---

### Post by jonst on 2007-05-06
Hi, I had a similar problem but recently I have found a great tech support site that help me deal with these problems. I am sure you will find some solutions there. If you need fast help they also have free live chat support. Here is the page for [Epson Aculaser C1100 Support]("http://www.fixya.com/support/p343354-epson_aculaser_c1100_printer")

Good luck

Jon

---

