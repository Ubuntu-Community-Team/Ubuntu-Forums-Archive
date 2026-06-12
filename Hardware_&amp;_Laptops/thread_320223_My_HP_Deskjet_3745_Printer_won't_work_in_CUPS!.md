---
title: "My HP Deskjet 3745 Printer won't work in CUPS!"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by novice_geek on 2006-12-16
Hello everyone in the Ubuntu Community! :) 

I just installed CUPS on my Ubuntu LAMP server (I believe it's either Dapper Drake 6.06 or 6.10), and I can't get my HP Deskjet 3745 inkjet printer to work.  I was going to try the .ppd file option, but I can't find one.  I know that this printer worked with openSUSE 10.1, so I figure it should be able to work with Ubuntu.  I believe the drivers were something like HPLIP or HPIJS.

I have tryed multiple configurations, and I still can't get it too work.

By the way, I have NO GUI.  I am using tty over my LAN to configure everything.  This may sound pointless, but most of the stuff I have found online needs GNOME for something.

Also, I am a Ubuntu 'noob,' and I am an intermediate Linux 'noob.'  So please spell out everything.  All of the code needed and ext.

Thanks in advance for the help!

---

### Post by randomnumber on 2006-12-17
This is what i would do in your situation.

Try the drivers for the Deskjet 3740 and hope they work for your Deskjet 3745. It seems to me that they are going to be the same. 

GOOD LUCK

I make no guarantees and I am still learning.

---

### Post by novice_geek on 2006-12-17
Thank-you for the suggestion, randomnumber

Unfortunately, I don't have this driver.  The driver that Ubuntu keeps picking is HP Deskjet 340, which is definately not it.

On my Windows XP box, I use the Windows version of the 3740 Series drivers, and those work great.  If anyone can tell me where to get that and how to install it, I would greatly appreciate it :)

Thanks,
novice_geek

---

### Post by baza41 on 2006-12-18
I'm having the same problem, with the 3745. It's detected as a 3740, but I just can't get it to print. The printer status wotsit keeps reporting, 'job stopped'

---

### Post by randomnumber on 2006-12-18
This may not help but my configuration is that I have a hp Deskjet 5550 connected to a windows XP machine while I run Ubuntu 6.10 on my desktop. The 5550 is shared and all I had to do to get it printing was add printer, select SMB and find the driver. The printer setup worked really well for me, especially considering the work originally involved.

I looked for the driver under CUPS for Deskjet 3745 and only found Deskjet 3740. It said hpijs is recommened.

i have added extra repositories and this may have added more printers, I do not know.

Again, good luck.

If you have trouble getting a good answer try adding more details about your network.

---

### Post by novice_geek on 2006-12-18
[SIZE=2]I finally got it to work.  When I installed CUPS, it didn't install properly (I couldn't even use the web-based config... outside of lynx on the local machine!)  Once I reinstalled, I found some more drivers, and that fixed it... sort-of.  I installed the .ppd, and it prints.  The only problem now is that a 15ppm printer took LITERALLY 28 minutes to print the test page!  I'm not kidding.  I started a job and it started printing at 7:49.  It wasn't finished until 8 something.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]If anyone has an idea on how to fix this problem, please don't hesitate to mention it.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Finally, thanks to everyone who kindly posted a reply.  This is why the Ubuntu community is so great! :)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thanks![/SIZE]

---

### Post by novice_geek on 2006-12-18
Oh sorry, I forgot to add this to my reply from a few minutes ago...
Baza41... Go here [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740) and click on "download .ppd"
 
This is the file I used.  I'm not sure if you will get the extreme slowness problem that I did, but it might help you.
 
Hope it helps :)

---

### Post by randomnumber on 2006-12-18
> **novice_geek said:**
> [SIZE=2]I finally got it to work.  When I installed CUPS, it didn't install properly (I couldn't even use the web-based config... outside of lynx on the local machine!)  Once I reinstalled, I found some more drivers, and that fixed it... sort-of.  I installed the .ppd, and it prints.  The only problem now is that a 15ppm printer took LITERALLY 28 minutes to print the test page!  I'm not kidding.  I started a job and it started printing at 7:49.  It wasn't finished until 8 something.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]If anyone has an idea on how to fix this problem, please don't hesitate to mention it.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Finally, thanks to everyone who kindly posted a reply.  This is why the Ubuntu community is so great! :)[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Thanks![/SIZE]

Just a guess.
Sounds like a spooling issue. I think that can be changed on the setting of the computer with the printer. Set to something like print after first page spooled. 
Maybe a network speed issue.

---

### Post by baza41 on 2006-12-19
> **novice_geek said:**
> Oh sorry, I forgot to add this to my reply from a few minutes ago...
Baza41... Go here [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740) and click on "download .ppd"
 
This is the file I used.  I'm not sure if you will get the extreme slowness problem that I did, but it might help you.
 
Hope it helps :)

Outstanding! it's working now, thanks :D

---

### Post by novice_geek on 2006-12-19
>  
Just a guess.
 
Sounds like a spooling issue. I think that can be changed on the setting of the computer with the printer. Set to something like print after first page spooled. 
Maybe a network speed issue.

 
Randomnumber:
Unfortunately, I can't find an option that will allow me to change any spooling options. By the way, this printer is connected directly to the machine's only USB port, so the network shouldn't be causing problems. I want to use this machine as a print-server (using this printer). I'm too much of a geek to settle with one of those little $50 boxes, or else I would just do that...
 
This just came to me a minute ago...
I'm not sure what the minimum specs are CUPS... but here is my systems specs and some software that's running. If anyone sees a problem with this, please tell me
Intel Celeron (Socket A... OLDSCHOOL!) @ 500MHz
1 stick of SDRAM @ 64MB
1 20GB primary HDD
1 250GB secondary HDD for file storage (/home)
1 10/100/1000 PCI NIC running @ 100Mbps
I am also running Apache, SSH, SFTP, and some other server-software.
 
Thanks for all of the help :)

---

