---
title: "Minolta Page Pro 1300 drivers"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by zupermanz on 2005-05-27
I have a Minolta Page Pro 1300 laser printer.... Is it possible to make it work on linux?
(It has no support for windows and is connected with a usb)

---

### Post by jrobcet on 2005-05-28
I have a Konica Minolta 1350 that works fine with Ubuntu after compiling the drivers and grabbing the PPD file from here: [http://linuxprinting.org/show_driver.cgi?driver=min12xxw&fromprinter=Minolta-PagePro_1300W](http://linuxprinting.org/show_driver.cgi?driver=min12xxw&fromprinter=Minolta-PagePro_1300W)

If you need further instuctions to get everything compiled and installed just let me know.

---

### Post by zupermanz on 2005-05-28
[QUOTE=jrobcet]I have a Konica Minolta 1350 that works fine with Ubuntu after compiling the drivers and grabbing the PPD file from here: [http://linuxprinting.org/show_driver.cgi?driver=min12xxw&fromprinter=Minolta-PagePro_1300W](http://linuxprinting.org/show_driver.cgi?driver=min12xxw&fromprinter=Minolta-PagePro_1300W)

If you need further instuctions to get everything compiled and installed just let me know.[/QUOTE]

Ive downloaded the ppd file .
How do i compile the driver?

---

### Post by zupermanz on 2005-05-28
Ive compilled the drivers...it works...almost
Prints one page (the first page) then stops.The printer (after the 1st page is printed)
behaves like is not connected(it blinks).To print another page i have to turn it off and on again...
Any ideas? 
BTW i have exectly the same problem when i use madrake.

---

### Post by jrobcet on 2005-05-28
Did you copy the PPD file to /usr/share/cups/model?

---

### Post by zupermanz on 2005-05-29
[QUOTE=jrobcet]Did you copy the PPD file to /usr/share/cups/model?[/QUOTE]
Yes...but it still stamps only the first page....
Any ideas?

---

### Post by Inv on 2006-02-16
I've also got the pagepro 1350w, and am also having problems getting it to do anything. I'm fairly to mostly new at Linux, and I'd like to be able to continue using it, but my printer is something I use on a daily basis. Can anyone help me out?

---

### Post by zupermanz on 2006-02-17
i 've got it working. it was simple ...just change from letter to A4 (paper size)

---

### Post by Inv on 2006-02-21
You really got it to work just by changing the paper settings? You didn't do anything else? 

That's not doing it for me :( 

I've got the 1350w though, which model is yours?

---

### Post by zupermanz on 2006-02-22
Only paper size....
Compiled the drivers as siad before and copied the ppd file.

---

### Post by Loco_gr on 2006-02-26
I have Konica Minolta Page Pro 1300W and I also can't print. Ubuntu automatically recognizes the Printer but I can't print. The page size is in A4.
I have downloaded the ppd file but I can't understand how to compile the drivers.

Can you please explain to me how did you compile the drivers because I can't see anywhere on this topic any reply on how to compile the drivers.

Thanks in advance for your help.

---

### Post by zupermanz on 2006-02-26
download the drivers from [http://www.hinterbergen.de/mala/min12xxw/](http://www.hinterbergen.de/mala/min12xxw/)
extract
./configure
sudo make
sudo make install
sudo make clean
copy ppd file to /usr/share/cups/model
setup printer

---

### Post by Inv on 2006-02-26
Zupermanz is right on, folks. His advice worked very well on my system.

I humbly thank you, Zupermanz.

---

### Post by Loco_gr on 2006-03-25
Yes it really worked!

Thanks for your help zupermanz !!!

---

### Post by bigbirdsam_malaysia on 2006-04-28
Tried it, still can not print :( The Job seems stay in the queue all the time...

---

### Post by Grymling on 2006-06-01
Did you solve the problem with your Konica-Minolta Pagepro 1300 ?
I've tried all the above, and still, nothing happens.
My printer is by default A4 and I changed that in the ppd-file.
But it just put the printing in queue.

I have Kubuntu Dapper Drake.

---

### Post by paralija on 2006-06-10
You need to replace line

DeviceURI usb://KONICA/MINOLTA%20PP1300W

with line

DeviceURI file:///dev/usblp0

in file /etc/cups/printers.conf

---

### Post by Trenchbroom on 2006-06-14
I've been using Ubuntu (well, Kubuntu until Dapper anyway) since Hoary, regular vistor to the site.  But I officially joined this forum this evening just to say:

**THANK YOU PARALIJA!!**

I've been struggling with my Minolta 1250W for over a year now.  Had to keep Windows around strictly as a printer driver.  One little line change, a reboot...and VIOLA!  It works!

Thanks again!

---

### Post by zupermanz on 2006-07-02
I have just installed  1300w to dapper- Kubuntu . You dont need to download any drivers.Just go to system setttings---)printer----)add choose (i have chosen minolta 1300w m1250), then choose where is connected and everything works fine (remember to set page size to a4 if you use a4). Much simpler than hoary....

---

### Post by lonetree on 2006-07-06
[QUOTE=paralija]You need to replace line

DeviceURI usb://KONICA/MINOLTA%20PP1300W

with line

DeviceURI file:///dev/usblp0

in file /etc/cups/printers.conf[/QUOTE]

You are great paralija. Seems like dapper has different way of installing printer compared to hoary. Sigh, why do they have to always change the way it works.

thanks again

But now, I am facing a serious problem with printer sharing which was working perfectly in hoary.

I have been using ubuntu 5.04 since it was released until last few days where I decided to upgrade to 6.06, I did a clean install and configures my new machine to act as a file server, PDC, and as well as printer server.

In 5.04, I shared the printer to my windows machines using cups, by mean od ipp. Got it work from a guide by occy.

However, now, I am facing a problem with 6.06. When I first install my Minolta PagePro-1300W, 6.06 detected the printer and I install the driver successfully, but when I try to print, it didn't print until I do a search from the forum that I need to change some settings in /etc/cups/printers.conf. After which, printing start with no error.

Next, I have enable smb printing and also cups. I tried installing the networked printer in windows, at first, I tried using cups by mean of ipp, [http://servername:631/printers/printername](http://servername:631/printers/printername), that didn't work for me, nothing was printed out. Then i tried to add printer using smb printing, again, printer is reflected in windows, I connected the printer and installed the driver, this time, after the printer is added, it shows there, "access denied, unable to connect", tried test print, but it still doesn't print.

However, one strnage thing I notice when I check the print job via cups web interface, it shows that all these test prints were completed.

What could I have done wrong here?

Last thing I did to make sure that print share is working, I tried printing from another ubuntu machine, and it printed out without fail.

Hope someone can help me on this, now all my windows machines cannot print at all.

regards,

---

### Post by damiafix on 2007-03-01
HI, 
very thanks for this post, I've installed my Konica Minolta PagePro1300W with success. The problem is only the velocity...from when I start 'print' at  the effective print I wait also for 1, 2 minutes. It's normal? Ther's a way for change this latency?

Regards, Damiano P.

---

### Post by sam0t on 2007-03-20
I could install automaticly Pagepro 1300 drivers without any extra fuss about couple months ago with Egdy 6.10. But now as I did reinstall of Ubuntu I cannot find PagePro 1300 drivers from the list. What has happened? :(

I have a hunch that might be the cause, I followed couple guides before I tried to install the pagepro 1300 with my earlier install of Ubuntu. Maybe I have not enabled some repository thingy or something? I checked out that I atleast have restricted repositories enabled in synaptick packet manager.

ps. Ok I have been checking out the guide awhile now, lets see if I got it right. I must copy the PPD file to correct location and then convert the .rpm -> .deb and the install the .deb package? After that the PagePro 1300 should appear on my Printers list under Konica Minolta?

edit:

Args nicely done. Ofcourse there is a list for KonicaMinolta and just Minolta. The default drivers were in Minolta folder, man Iam blind :D

---

