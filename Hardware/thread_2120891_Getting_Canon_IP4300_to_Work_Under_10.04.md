---
title: "Getting Canon IP4300 to Work Under 10.04"
date: 2013-02-27
forum: Hardware
---

### Post by oldefoxx on 2013-02-27
I am using Ubuntu 10.04 now, and decided to get my printer working so that I can print out a UPS shipping label.  Normally I would send this to my wife, have her print it, and that would be it.  But her hard drive failed, and I am waiting for a new one to arrive.  So time to get my Canon IP4300 working with my laptop.

Trouble is, I don't have a Printers option under Administrator, just Printing, and when I bring that up, it just lists Other/Network Printer and asks for a URL.  It does not show any printers or brand names in the left column, so nothing to choose from.

I've searched these forums and got 50 returns, but nothing to help.  I've used Google to search elsewhere, but again no help.  One post did relate to a link to a site in Australia, but the link goes nowhere now.

I just don't have it in my head as to what has to be done here to get it working.  While I wait for some help, I'm going to track down the USB cable and make sure it is routed correctly.

And some help would be appreciated.

Oh, I got broke in on a couple of months back, heard a noise and called out from a different room, and they paniced and left.  Had to be a couple of teenagers.  But with the way things are going, I expect more of the same in the future, and next time hope to be better prepared.

Trouble is, stupid government politicians want to take arms away from honest citizens and leave them in the hands of criminals. They can't seem to learn from experience of use their noggins to see the obvious for themselves.

---

### Post by Tiomun on 2013-02-27
> **oldefoxx said:**
> I am using Ubuntu 10.04 now, and decided to get my printer working so that I can print out a UPS shipping label.  Normally I would send this to my wife, have her print it, and that would be it.  But her hard drive failed, and I am waiting for a new one to arrive.  So time to get my Canon IP4300 working with my laptop.

Trouble is, I don't have a Printers option under Administrator, just Printing, and when I bring that up, it just lists Other/Network Printer and asks for a URL.  It does not show any printers or brand names in the left column, so nothing to choose from.

I've searched these forums and got 50 returns, but nothing to help.  I've used Google to search elsewhere, but again no help.  One post did relate to a link to a site in Australia, but the link goes nowhere now.

I just don't have it in my head as to what has to be done here to get it working.  While I wait for some help, I'm going to track down the USB cable and make sure it is routed correctly.

And some help would be appreciated.

Oh, I got broke in on a couple of months back, heard a noise and called out from a different room, and they paniced and left.  Had to be a couple of teenagers.  But with the way things are going, I expect more of the same in the future, and next time hope to be better prepared.

Trouble is, stupid government politicians want to take arms away from honest citizens and leave them in the hands of criminals. They can't seem to learn from experience of use their noggins to see the obvious for themselves.

I have been playing with cups and a canon printer lately. But that's on ubuntu 12.04 or 12.10. I am in no way a expert on this subject but here's my thoughts anyways

If your not having much luck you may want to try installing cups
$ sudo apt-get -y install cups

after installing cups you should be able to configure the printer through your web browser. there should be many tutorials on installing this on the google.

There's also a package of additional drivers if cups doesn't install with the one you need.

$ sudo apt-get install printer-driver-gutenprint

heres a tutorial i found for installing cups
[https://help.ubuntu.com/10.04/serverguide/cups.html](https://help.ubuntu.com/10.04/serverguide/cups.html)

---

### Post by pdc on 2013-02-27
I think you need the printer drivers that Canon supply; for the ip4300

so if I aim to describe what to do:

Canon supply two packages for each printer:

1) what they call a [COLOR="Blue"]COMMON[/COLOR] package

and 

2) a [COLOR="Blue"]SPECIFIC[/COLOR] package for each printer.....in your case the ip4300series


.....for this older printer, Canon don't supply a .deb package, which ubuntu uses..........so one needs to download the rpm package they offer and convert it to deb with alien and then install

so one goes to the Canon Asia website...

[http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux)

and you download the [COLOR="Blue"]common[/COLOR] package first

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718403.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718403.html)

(it comes down as  [COLOR="SeaGreen"]cnijfilter-common-2.70-1.i386.rpm[/COLOR])

and then one goes here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900719301.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900719301.html)

for the [COLOR="Blue"]specific[/COLOR] package (which is [COLOR="SeaGreen"]cnijfilter-ip4300-2.70-2.i386.rpm[/COLOR])

.....*[COLOR="Plum"]if you copy and paste all the commands in red into a terminal............I use the menu line of the terminal[/COLOR]* ..........

so then you need to download and install alien 

> [COLOR="Red"]sudo apt-get install alien[/COLOR]

as described here in more detail

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html) (it is a very legit programme)

and then on to the conversion

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]sudo alien -i cnijfilter-common-2.70-1.i386.rpm[/COLOR]

and then install the ip4300 driver

> [COLOR="Red"]sudo alien -i cnijfilter-ip4300-2.70-2.i386.rpm[/COLOR]

......that should have the drivers installed.....all should be good

if you paste this

[http://localhost:631/printers/](http://localhost:631/printers/)

into a browser window, it lets you alter printer settings etc

let us know how you get along

---

### Post by mörgæs on 2013-02-28
First I would begin with a clean install of 12.10. 10.04 is running out of time.

Please discuss weapons legislation in another forum.

---

