---
title: "modem suggestions for Ubuntu 12.04"
date: 2014-04-08
forum: Hardware
---

### Post by ubscott on 2014-04-08
I have been trying to get two internal modems (e.g., Intel 537) that work fine under Windows Xp to be recognized by Ubuntu 12.04 (on a Dell Precision).  After having done a great deal of research in recent days I believe they are both winmodems, and that it will take a lot more effort than I wish to invest to get them to work, assuming it is at all possible.  

With Windows XP headed for the graveyard I'm sure that I'm not the only person trying to get Ubuntu 12.04 to work with a modem.  Does anyone have a modem suggestion to make where it requires minimal effort to install?  I prefer an internal modem but don't mind an external modem if necessary.  It would be nice to pick up a modem that Ubuntu recognizes as quickly as Windows XP recognized the other two modems.  Thanks.

---

### Post by ubscott on 2014-04-09
I've got 111 views but no responses.  Does anyone have a modem which Ubuntu 12.04 had no difficulty recognizing?  If so, what is the make/model?  Thanks!

---

### Post by mastablasta on 2014-04-09
most people do not use dialup modems these days. they use  3g modems or network connection to router (both are alot faster).  which is probably why you had so many views - they wanted to suggest 3g modem. you should write "dialup modem suggestion...." in thread title.

that is not to say that no one is using them anymore. About your modems have you followed the guides: 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

and here to install the driver if the modem is not recognised: [URL="https://help.ubuntu.com/community/DialupModemHowto/Intel537EP"]https://help.ubuntu.com/community/DialupModemHowto/Intel537EP
[/URL]
try with gnome-ppp first.

also perhaps it is time to explore other options to connect to internet. most pages will load very slow these days on dial up. though it still has it's use...

---

### Post by ubscott on 2014-04-09
Thanks for the reply.  I have already been looking at those pages.  There is a lot of work involved.  I didn't mention dialup because I'd like to be able to send a fax too.  I found a page that discusses data/fax modems, but it is three years old:
[http://ubuntuforums.org/showthread.php?t=1799761&page=2](http://ubuntuforums.org/showthread.php?t=1799761&page=2)

Does Ubuntu 12.04 have a command that lists the hardware that works nice with it?  I would like to be able to buy  hardware and not have to troubleshoot it.  Thanks.

---

### Post by ubscott on 2014-04-09
OK, this is probably the question I should have asked: If I buy an external (hardware?) modem, does it have a chance to work with Ubuntu?  My understanding is an external modem doesn't need software to run.  However, what I'm seeing when I search is that lots of people are having problems with their external modems and Ubuntu.  Thanks.

---

### Post by pdc on 2014-04-09
I guess there is a bit of curiosity about which country you are in: ..........meaning most folks are probably musing about whether there isn't a quicker way to help you get connected; from the depths of my memory of getting an external modem set up on linux over ten years ago, I seem to remember that as long as it wasn't a winmodem, it would work fine with linux; and ours did...............what type was it........well I am afraid it got binned when we got our first router; I supect most would say any external modem will work fine; we wish you all the best in your quest

---

### Post by slickymaster on 2014-04-09
What about Robotics Sportster 33.6 Faxmodem?

---

### Post by ubscott on 2014-04-09
PDC, you don't want to use a modem then don't.  Just trying to make a decision about a purchase without getting involved in major troubleshooting.  I said I'm on Ubuntu 12.04; so I don't need your thoughts about ten years ago.  I think lots of Windows XP people might be asking the same question soon.

---

### Post by mastablasta on 2014-04-10
fax? :-) i reject customers that send me fax...

by the way - it is possible to print any file to pdf and then send the pdf via email. there is no need for fax. again most people have emails these days .... but i guess some don't.


indeed Robotics might be a good option.

the intel you have doesn't involve too much work. you need to first install gnome-ppp (by the way in Kubuntu k-ppp is already included), then (if necessary) copy and paste the commands for last ubuntu version in the link.

> **Installing on 7.04**


As of the release candidate of Feisty Fawn, neither Phillipe Vouter's drivers nor Intel's drivers are compilable ([bug #98756]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98756")). If you know of a solution, please add it here. 
**IMPORTANT UPDATE:** It is possible to compile a working driver for Feisty Fawn (Ubuntu 7.04). First, you must get this driver from Mr. Phillipe Vouter: [Intel-537EP-2.70.95.0-for-2.6.20.tar.gz]("http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz") 
Next, just issue the following commands: 
sudo apt-get install build-essential
export MODEM_TYPE=537EP
sudo make clean
sudo make 537
sudo make installAnd that is it. You should be able to use your favorite dialing utility with your modem remembering that it is linked to **/dev/modem**. *([CarlosMarcano]("http://ubuntuforums.org/community/CarlosMarcano") = chuckman78)* 


if this part is even necessary since a lot of drivers are now in kernel already. else just copy these commands line by line and it should work (you may need to install build essentials and perhaps some libraries from software center)

---

### Post by ubscott on 2014-04-10
Mastablasta, thanks for the reply.  My version of Ubuntu is 12.04, so I wonder whether the procedures for Feisty Fawn will apply.  I'll try it though.  If it doesn't work then I'll consider picking up a Robotics external modem.  Thanks again.

---

### Post by mastablasta on 2014-04-11
what the instructions say in layman terms is download the (patched?) driver source code, install building tools, compile driver with those tools from source, install them. as long as you have all dependencies met the instructions should work. so good luck with those dependencies. if any additional ones are needed i suggets using synapcits package manager to ifnd them and install them. as long as you don't get into *"dependency hell"* ([http://en.wikipedia.org/wiki/Dependency_hell](http://en.wikipedia.org/wiki/Dependency_hell)) things should work out.

aslo let us know if they do not work to first troubleshoot them. and if they really do not work someone needs to update the page ;)

---

### Post by eightbits2010 on 2014-04-11
One of the reasons having a fax modem is that some business organazations will not open a email  PDF file. I guess the worry is security?
I do keep a XP PRO laptop which includes a fax modem. Of course, PDF files are a nice way to go but eliminates the ability
to not use email and the security concerns there that don't exist when sending a fax to another fax machine.

---

### Post by Coolgirl on 2014-04-12
[h=1]ARRIS / Motorola SB6121 SURFboard what I use never had a problem.. it just whizzes![/h]

---

