---
title: "How to Set up APC Smart-UPS ?"
date: 2009-11-04
forum: Hardware
---

### Post by Timothy Taylor on 2009-11-04
I'm in the process of moving away from Windows and I've been trying (without success) to get software to monitor & control my APC Smart-UPS under Ubuntu (9.04)

I downloaded the Linux version of APC's "PowerChute" app from their website (pbeagent-8.0.1-609.i386.rpm) but I can't find a way to install this.  The instructions say I should enter "rpm -i pbeagent-xxx.i386.rpm" in terminal, but (even using sudo and the correct path!) this only throws various error messages, the latest saying that I need to install "bin/sh" - which I thought was a standard Linux command??

Further investigation led me to try installing the "Apcupsd monitor" package.  Apcupsd doesn't recognise the UPS at all, possibly because it expects to find a network-connected UPS??  My UPS is connected to the serial port and doesn't have a network connection.  I know the serial cable & comms are OK, because PowerChute runs fine from Windows.

Anybody know how to get either PowerChute or Apcupsd to work?

---

### Post by Timothy Taylor on 2009-11-06
Just heard from APC tech support:  Ubuntu is not supported by their Linux software.  
Plonkers.  
:(

So that just leaves me hoping Apcupsd (or similar) can work...

---

### Post by gfowler on 2009-11-06
> **Timothy Taylor said:**
> Just heard from APC tech support:  Ubuntu is not supported by their Linux software.  
Plonkers.  
:(

So that just leaves me hoping Apcupsd (or similar) can work...

I've used apcupsd on both smart ups (apc 620) and dumb ups.  It will take some command line work to get it done.  Installing the software from the repositories and connecting up the UPS won't configure it to run.  My first step would be to suggest you get familiar with apcupsd by going to [http://apcupsd.org](http://apcupsd.org), in the documentation you will find a basic setup how-to.  Follow that and return here with you issues is probably the best course of action.
Jerry

---

### Post by BulletTootg on 2009-11-16
> **gfowler said:**
> I've used apcupsd on both smart ups (apc 620) and dumb ups.  It will take some command line work to get it done.  Installing the software from the repositories and connecting up the UPS won't configure it to run.  My first step would be to suggest you get familiar with apcupsd by going to [http://apcupsd.org](http://apcupsd.org), in the documentation you will find a basic setup how-to.  Follow that and return here with you issues is probably the best course of action.
Jerry



One of our tech's recently set up a [SUA1500RM2U]("http://excessups.com/smart-1500-rackmount-sua1500rm2u-p-57.html") to work with [apcupsd]("http://apcupsd.org/") I understood he spent quite a bit of time on it, but it's doable.



T

---

### Post by Timothy Taylor on 2009-12-17
Thanks for the replies.

Progress delayed by having to replace a dead battery.
Now pleased to report that I have my Smart-UPS 1500 working with Apcupsd now. Easy set-up following the instructions, including important ones like "sudo /sbin/apcupsd" :)

I've yet to discover whether I need to run this command every time I start my PC.  If so, is there an easy way to automate this?

Cheers!

---

### Post by gfowler on 2009-12-18
> **Timothy Taylor said:**
> Thanks for the replies.

Progress delayed by having to replace a dead battery.
Now pleased to report that I have my Smart-UPS 1500 working with Apcupsd now. Easy set-up following the instructions, including important ones like "sudo /sbin/apcupsd" :)

I've yet to discover whether I need to run this command every time I start my PC.  If so, is there an easy way to automate this?

Cheers!

I'm running apcupsd in a server and a hardy desktop and in both cases apcupsd starts up at boot up.  

Jerry

---

### Post by Timothy Taylor on 2009-12-18
> **gfowler said:**
> I'm running apcupsd in a server and a hardy desktop and in both cases apcupsd starts up at boot up.  

Jerry

Apcupsd only runs on my system if I type "sudo /sbin/apcupsd" in terminal.
Actually, that's not correct: what actually appears when I click [Applications/System Tools/APCUPSD monitor] is "gapcmon", which says it's the UPS monitor for APCUPSD.

There's no sign of apcupsd on any other menus.
:confused:

---

### Post by Timothy Taylor on 2009-12-18
I've just been plodding through some of the test stuff in the manual: apcaccess status seems to work OK as does apctest.  This suggests that apcupsd is working.  

I tried unplugging the mains from the UPS which kept the PC running OK, but there was no indication of power failure.  I was expecting some kind of notification, pop-up message or something?  The only hint I get that the UPS is powering the PC, is "running on battery" displayed in gapcmon - if it's running.

:confused:

---

### Post by gfowler on 2009-12-19
> **Timothy Taylor said:**
>   The only hint I get that the UPS is powering the PC, is "running on battery" displayed in gapcmon - if it's running.

:confused:

I suppose you could start gapcmon at bootup.  In the /etc/apcupsd directory there is a file 'changeme' that when configured that will send you an email when it goes on the UPS.  I think its original intent was a server based program locked in a dark room :) with no GUI !

Jery

---

### Post by Maverick7 on 2011-06-23
[http://www.crn.com/news/channel-programs/199000818/linux-ups-without-tears.htm;jsessionid=jD6JghU2QNwqQm-ilt7CzA**.ecappj03](http://www.crn.com/news/channel-programs/199000818/linux-ups-without-tears.htm;jsessionid=jD6JghU2QNwqQm-ilt7CzA**.ecappj03)

That may solve.

---

