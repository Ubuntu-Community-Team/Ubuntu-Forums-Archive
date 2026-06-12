---
title: "All in one printers"
date: 2014-03-26
forum: Hardware
---

### Post by christon74 on 2014-03-26
Good evening fellow-Ubunters:)

Today my question is: 'how can you scan documents (Xsane, simplescan, Skanlite...) with an all in one printer when you log on to Ubuntu? 
Mine is a Canon Pixma MG 3150.
Ubuntu version: 12.04 LTS (Precise pangolin)
Neither Xsane or simplescan can find the device..... (no devices available) and yet the Canon MG 3150 is connected and it is on.

Thanks for time and trouble.
Chris.

---

### Post by gifford on 2014-03-26
Have you installed the scanner drivers? Here is one link that has it:[https://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3150.aspx](https://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3150.aspx)
Here is another link with info: [http://askubuntu.com/questions/123638/canon-multifunctional-mg3150-printer-ok-but-scanning-is-not](http://askubuntu.com/questions/123638/canon-multifunctional-mg3150-printer-ok-but-scanning-is-not)

---

### Post by christon74 on 2014-03-26
Hello gifford and thank you for this quick reply. 
Yes, I have already downloaded the driver but I do not know how to install them. 
/home/christophe/Downloads/scangearmp-mg3100series-1.80-1-rpm.tar.gz is there in my 'downloads' file but what should I do next? Open with archive manager? Naaah. It does not install it. I  am feeling like I'm  a prat, really. :oops:

---

### Post by pdc on 2014-03-26
Hi Christophe; (bonjour?)

first you would be best with a debian package for ubuntu;

so go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100394102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100394102.html) and download the package they offer: [COLOR="#008000"]scangearmp-mg3100series-1.80-1-deb.tar.gz[/COLOR]

Download; save it as it comes down to your Downloads directory

if you open a terminal: and paste in the commands below and hit the ENTER key after each paste: I suggest you use the menu of the terminal; and the mouse: ie go along to EDIT and down to PASTE

the commands should be 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mg3100series-1.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mg3100series-1.80-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

................that should install [COLOR="#0000FF"]ScanGearMP[/COLOR] and to run it, 

> [COLOR="#FF0000"]scangearmp[/COLOR]

........it should then load;

__________________________

thereafter a launcher would help you so if you use the commands

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR] ........

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR] .............after that command, you will get a dialogue box: (picture hopefully with this post)

the **Command** needs to be > scangearmp and the rest is what you want to call it  yourself: you should end up then with a button on your desktop to click; to launch your [COLOR="#0000FF"]ScanGearMP[/COLOR]

---

### Post by christon74 on 2014-03-27
Hello /bonjour pdc:)
Yes, I am French. What has given me away? LOL
Thank you for all the instructions_ I have just tried copying them to a terminal window but it says it still cannot find any scanner or that the scanner is disconnected.:confused:

I am really glad I am on a dual boot and can choose vista when I need scan documents or print anything in color.

Anyway, a thousand thanks again for your help.;)

---

### Post by pdc on 2014-03-27
bonjour Christophe; eh bien, peut-etre nous essayons .............

well let's try the command

> [COLOR="#FF0000"]lsusb[/COLOR]

to  see if the printer is recognised;

and 

> [COLOR="#FF0000"]dpkg -l | grep scangear[/COLOR]

can you copy and paste those; and paste the results back here

---

### Post by christon74 on 2014-03-27
Re-Bonjour pdc :D 
voilà le résultat:
christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 006 Device 002: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 002 Device 004: ID 04a9:1752 Canon, Inc. 
root@hp1:/home/christophe# dpkg -l | grep scangear
ii  scangearmp-common                        1.80-1                                              ScanGear MP for Linux.
ii  scangearmp-mg3100series                  1.80-1                                              ScanGear MP for Linux.
root@hp1:/home/christophe# 

I also need say that I have just connected an old flat scanner Canon Lide 25. it works!
no need to search for any driver. Xsane has found it immediately! :D

---

### Post by christon74 on 2014-03-27
..... Now if I plug out the Canon LIDE 25, here is the result:
christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 005 Device 002: ID 0461:4d20 Primax Electronics, Ltd HP Optical Mouse
Bus 002 Device 004: ID 04a9:1752 Canon, Inc. 
root@hp1:/home/christophe# dpkg -l | grep scangear
ii  scangearmp-common                        1.80-1                                              ScanGear MP for Linux.
ii  scangearmp-mg3100series                  1.80-1                                              ScanGear MP for Linux.
root@hp1:/home/christophe# 

NOTE: the two last lines on the terminal read a bit different in that both 'scangears' are in the lower case and they are red.
:|

---

### Post by pdc on 2014-03-27
thanks; I note you using the su before you issue the commands: I would be just using the straight commands on my computer; so I am functioning as a user; (not administrator):

......... so I don't know why you have this issue with scangear; .........it works for me .........if you have your own flatbed scanner: sounds like a good solution

(there should be no need to use sudo su commands for things like lsusb command and the list command I gave you: dpkg -l | grep scangear

---

### Post by christon74 on 2014-03-31
Thanks a lot for all help pdc. Apologies for not coming back sooner:redface:

---

### Post by pdc on 2014-03-31
tout marche bien?

---

