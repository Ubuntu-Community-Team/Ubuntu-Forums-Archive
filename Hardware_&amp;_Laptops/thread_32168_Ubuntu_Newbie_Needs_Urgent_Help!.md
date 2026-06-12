---
title: "Ubuntu Newbie Needs Urgent Help!"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by bhanja_Trinanjan on 2005-05-06
The latest Ubuntu is up and running.

Here is my list of problems:

1. No tool to configure my pppoe-adsl connection.  
The package at [www.ubuntuguide.com](www.ubuntuguide.com) doesn't work. I followed all the instructions. I even got a link to launch this package. When I click it, nothing happens. 

2. So decided to go back to my crappy dialup connection (Rockwell ext modem). Modem dials, isp modem replies and then NOTHING happens... No pages open in any browser.
   

3. My Canon i255 USB printer is detected and configured automatically. However, when I print a test page, nothing happens.

4. I haven't yet tried to install the ati fglrx driver for x.org. Can anticipate that it will be a great fiasco.

I feel frustrated.... Feel like banging my head on a brick wall 

It's time that we had distros that work out of the box... Will move to Suse 9.3 pro installable version when it is released for downloading (the live version is of no use to me)

Please help! It seems that Ubuntu linux follows the mantra:

If it's detected, then it's broke! ](*,)

---

### Post by ifrflyer on 2005-05-06
First, welcome to Ubuntu. Thanks for trying it. Second, when you're starting a new OS, whatever new OS, there are bound to be things which are unfamiliar. These are not necessarily bugs, but rather that they are behaving in a manner that is, to you, unexpected. The best way to go about getting help is to - as you have begun to do here - list the issues and ask for help.

One important thing to do is to take this one thing at a time and post each question to the appropriate message board. For example, the question about PPOE is probably best addressed to ->Networking and the printer to installation help, etc. Please take a few minutes and check the various sub categories then post in the appropriate place.

> 1. No tool to configure my pppoe-adsl connection.
The package at [www.ubuntuguide.com](www.ubuntuguide.com) doesn't work. I followed all the instructions. I even got a link to launch this package. When I click it, nothing happens. 

Please tell us what kind of network card you are using - wired ethernet? Wireless? USB to the ADSL modem? Through a router and network or direct to the modem? 

Please give us as much information specifically about your hardware setup. 

If it's ethernet or wireless, please show us the results of this command rrun from a terminal window:

ifconfig

iwconfig

Thanks, stick with it and you'll get help. It's a great distro. I have learned that there are reasons for the most sublimely frustrating aspects of running Linux; the more frustrating the problem, the more you'll learn about how it all works, the more confidence you'll have adderssing new problems and issues as they come up.

---

### Post by bhanja_Trinanjan on 2005-05-06
Got the adsl connection to work using 'pppoeconfig'

How can I find and install the ATI driver? I want 3d acceleration! Please help!

---

### Post by lorap on 2005-05-06
hi friend!
first of all discussing your printer,i'm sorry but it's a bug :-)
you'll need to add your printer via cups printing services (native unix services).
yup you'll need open a terminal window and make some work.
all the things you have to do are explained here:

[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

and speaking your ati video card driver read this manual:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Vaughn on 2005-05-07
When it came to getting 3D acceleration with my Radeon AIW 9600 working I found the following pages helpful:

[http://www.ubuntuforums.org/showthread.php?t=24763](http://www.ubuntuforums.org/showthread.php?t=24763)
[http://www.ubuntuforums.org/showthread.php?p=119518#post119518](http://www.ubuntuforums.org/showthread.php?p=119518#post119518)
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

My notes show that I did the following:
_Install xorg-driver-fglrx_
Add universe to your repositories
$ sudo apt-get install xorg-driver-fglrx
$ echo fglrx | sudo tee -a /et/modules

_Modify xorg.conf_
Optionally back up xorg.cong with...
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
$ sudo gedit /etc/X11/xorg.conf
Change ati to fglrx in the line
        Driver          "ati"
to get
        Driver          "fglrx"
Add the line **bold** line below
>>>>
        Driver          "fglrx"
        BusID           "PCI:3:0:0"
**        Option          "UseInternalAGPGART"    "no"**
EndSection
<<<<
Save and exit

_Reboot_ (I had to anyway)

Goodluck :-)

---

