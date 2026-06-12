---
title: "Brother DCP-110C - I'm so close that its frustrating"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by wanger123 on 2005-11-21
Hi all, I have been trying to get the brother DCP-110C multifunction printer working in Kubuntu 5.10. I have downloaded both the lpr and cupswrapper from the brother website and tried to install them. I managed to install the dcp-110c lpr but I cant install the cupswrapper. I get the following:
wayne@ubuntu:~$ cd /brother
wayne@ubuntu:/brother$ sudo dpkg -i --force-all cupswrap.0
(Reading database ... 59438 files and directories currently installed.)
Preparing to replace cupswrapperdcp110c 1.0.0-1 (using cupswrap.0) ...
/etc/init.d/cups: Command not found.
Unpacking replacement cupswrapperdcp110c ...
Setting up cupswrapperdcp110c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperDCP110C
/etc/init.d/cups: Command not found.

I dont seem to have the cups file that its looking for in /etc/init.d.

This is so frustrating because when I try to add a new printer, the driver shows up in the list, and the printer is detected in the setup wizard, and if I try to print a test page after setup the job just sits in the print manager window saying processing (but nothing ever happens). Sometimes the printer gets the red cross (stopped) as soon as you send the test page.
Please help. Suggestions??
Many thanks
wayne**[B]**[/B]

---

### Post by Teroedni on 2005-11-21
Here is one who managed to get it work
He had to use another driver.
Hope you can get something out of this

> I am using LPRng version of lpd, without cups


```
This is a great printer. Their own driver works in Linux.

It even works in kernels 2.6.x even though they
caution about them and have tested only 2.4.x

I am using LPRng version of lpd, without cups.

Here is my solution:

My rpm installation does not work well on my system.

I discovered that I had to run their command manually
to make it edit my /etc/printcap properly:

/usr/local/Brother/inf/setupPrintcapij DCP110C -i USB

They should offer non-RPM non-DEB installation.
It really is simple:

(As super user ):

cd /
rpm2cpio DCP110Clpr-1.0.2-1.i386.rpm |cpio -idumv
find /usr/local/Brother -exec chown lp {} \;
/usr/local/Brother/inf/setupPrintcapij DCP110C -i USB
```

---

### Post by wanger123 on 2005-11-24
Thanks Teroedni, however this didnt apply to my situation. 
Finally found a few things in the archives that worked.

[http://www.ubuntuforums.org/showthread.php?t=30262&highlight=chmod+o%3Drw+%2Fdev%2Fusb%2Flp0](http://www.ubuntuforums.org/showthread.php?t=30262&highlight=chmod+o%3Drw+%2Fdev%2Fusb%2Flp0)
[http://www.ubuntuforums.org/showthread.php?t=30262&highlight=sudo+chmod+o%3Drw](http://www.ubuntuforums.org/showthread.php?t=30262&highlight=sudo+chmod+o%3Drw)

sudo chmod o=rw /dev/usb/lp0
basically, I think this is the key, and is in the bugzilla

Many thanks to eddy42 and petertc for the tips
Hope this helps

Wayne

---

### Post by wanger123 on 2005-11-24
Just a quick update. Could not get chmod to stick after reboot (using 777, nor could I get chown 777 etc..... to stick).

Eventually used kate to edit /etc/udev/rules.d/020permissions.rules and changed the section: usb lp 0-9 **GROUP="lp"** so that it now reads usb lp 0-9 **MODE="0666"**.

Rebooted and it is now happy days :D 

thanks to all

wayne

---

### Post by Teroedni on 2005-11-24
Great to hear
The usb permision was new to me :rolleyes: 

Could you make a quick description on what you did to install this driver , and could i get permission to submit it to this wiki?[http://doc.gwos.org/index.php/Print/Brother](http://doc.gwos.org/index.php/Print/Brother)

Hopes to get a positive answer:)

Could you also mark this thread as [Solved)

Thank You:)
And have a nice day
Regards Teroedni

---

### Post by wanger123 on 2005-11-24
Hi Teroedni, yep I would be happy to write a quick guide (now where did I put all those scraps of paper I used to write bits of code over the last few days - lol) :rolleyes:

Now I really hate to ask this for fear of ridicule, but how do I mark the thread as solved?

Many thanks
wayne

---

### Post by Teroedni on 2005-11-24
Great:)
THanks:KS 


To marks a solved preedd edit on your first post and write [solved] at the end of your tiitel line:)

---

### Post by wanger123 on 2005-11-24
Ahhhh! I have to select the "Go advanced tab when editing" :-k 

ciao

wayne

---

