---
title: "Help! wifi wont work on Acer Aspire 4530"
date: 2011-03-25
forum: Hardware
---

### Post by ripperd on 2011-03-25
hello guys
im a newbie in ubuntu, im using maverick meerkat, but the problem is my wifi wont work!
i already look the other thread with the same 4530 but the wifi hardware is different
can someone help me :(

---

### Post by smuthavarapu on 2011-03-25
Hi Ripperd, 

Did you try Additional Drivers ? Go to global menu bar at the top.

System --> Administration --> Additional Drivers.

See if you get the Proprietary drivers, if so, activate them and restart the machine.

---

### Post by ripperd on 2011-03-25
it only show a nvidia driver

---

### Post by ripperd on 2011-03-25
problem solved. all i have to do is installing wicd so i can manage the wifi to turn on and off

thankies

---

### Post by steven8 on 2011-05-17
I'm glad you got it fixed, and it sounds like the same problem we're having, but how did you get it installed without access to the internet?  I found it listed, along with other programs which might help, but we can't get them without access to the network.  I even put in the livecd to see if we could find it there, but I do not know how to navigate the .gz package files.

Any help would be greatly appreciated.

---

### Post by glomerulus on 2011-05-17
Hey steven8,

You can download the packages you need from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Get the **.deb** files and install using :

```
sudo dpkg -i pkgName.deb
```

---

### Post by steven8 on 2011-05-20
> **glomerulus said:**
> Hey steven8,

You can download the packages you need from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Get the **.deb** files and install using :

```
sudo dpkg -i pkgName.deb
```

I downloaded:

wicd_1.7.0+ds1.6_all.deb
wicd_daemon_1.7.0+ds1.6_all.deb
wicd_cli_1.7.0+ds1.6_all.deb
wicd_gtk_1.7.0+ds1.6_all.deb

which seem to be only the tip of the iceberg, as every time I try to install any of these by the terminal I get an error saying package doesn't exist, even when I supply a path, and the software manager just yells at me because there is no internet connection to download the packages.  Which I know means there are other packages needed, but when you go into these things, there are like oodles of things that say 'depends'.  Does that mean we need all those packages that say depends, and how do I get the system to know where they all are even if I can get the terminal to recognize a package at all?

My true frustration lies in the fact that the live CD seemed to have no trouble seeing a wireless connection. Yet, having installed from that same CD, whatever it used to see the connection was not installed.  How the heck can that happen???

---

### Post by steven8 on 2011-05-20
Could the required packages possibly be on the installation disk, and could they be retrieved from there?

If so, how?

---

### Post by steven8 on 2011-05-20
Terrific. :rolleyes:  I found that we need to activate the proprietary Broadcom driver but guess what???  You guessed it, it can't be downloaded!!  I love Ubuntu, but this is ridiculous.

---

### Post by steven8 on 2011-05-20
> **steven8 said:**
> Terrific. :rolleyes:  I found that we need to activate the proprietary Broadcom driver but guess what???  You guessed it, it can't be downloaded!!  I love Ubuntu, but this is ridiculous.

WoW!  Even though it said there was an error in downloading, when I restarted the system, it worked!!  I&#7743; posting this from within Ubuntu!!  My son will be thrilled when he gets home!!

---

### Post by coffeecat on 2011-05-20
> **steven8 said:**
> Could the required packages possibly be on the installation disk, and could they be retrieved from there?

If so, how?

> **steven8 said:**
> Terrific. :rolleyes:  I found that we need to activate the proprietary Broadcom driver but guess what???  You guessed it, it can't be downloaded!!  I love Ubuntu, but this is ridiculous.

Couldn't get a word in edgewise :wink:, but rather belatedly, and too late I see! :)

Community documentation (which includes how to get the drivers off the CD):

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

And - yes, you can download it, but you have to use an ethernet connection. The reason the proprietary drivers are not in a  default installation is because of restrictive licensing issues. The good news is that Broadcom have started to work with the Linux community and a new open source driver is now available in Natty. It only supports a handful of cards so far but, hopefully, in future releases this fiddling about to get Broadcom to work will be a thing of the past.

---

### Post by steven8 on 2011-05-25
> **coffeecat said:**
> Couldn't get a word in edgewise :wink:, but rather belatedly, and too late I see! :)

Community documentation (which includes how to get the drivers off the CD):

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

And - yes, you can download it, but you have to use an ethernet connection. The reason the proprietary drivers are not in a  default installation is because of restrictive licensing issues. The good news is that Broadcom have started to work with the Linux community and a new open source driver is now available in Natty. It only supports a handful of cards so far but, hopefully, in future releases this fiddling about to get Broadcom to work will be a thing of the past.

Sorry about that, but I was trying really hard to have it done before my son got home.  I wanted to surprise him.  The sad thing is, although he was happy and surprised, he had had the idea of bringing his laptop upstairs to hook to the ethernet.  I am sad to say I'd not thought of that most obvious solution, since we run a wireless router off of our cable modem.  Doh!!  Thanks for the link to the docs.  That is really good information.  Yet, it's even more exciting about Broadcom working with the Linux community!!  :popcorn:

---

