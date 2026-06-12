---
title: "new user need help"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by ubunewtu on 2009-06-27
Hi ubuntu forum im a new user and need help i found the wireless driver i need and downloaded it my qustion is where do i extract the file to?:confused:

---

### Post by philcamlin on 2009-06-27
is it a .deb?

if it is just double click and away you go

---

### Post by ubunewtu on 2009-06-27
its a tar.bz2 if i need to do something within the terminal i am fimilar with it

---

### Post by ad_267 on 2009-06-27
What wireless card do you have and where did you get the driver from?

---

### Post by linuxmagick on 2009-06-27
From a terminal:

cd to the directory you downloaded the file to
tar -xvjf filename.tar.bz2
The above line will extract the contents of the file.

Beyond that, you'll either need to provide some more info about the driver and where you downloaded it from so someone can help you install it, or check to see if a README or INSTALL file is included in what you just extracted.

---

### Post by ubunewtu on 2009-06-27
ive got a brodcom 43 something im runing a compaq v5000 i forgot the comand that tells me the specs of whats installed i followed a bunch of redirects from the forums [wireless-regdb-2009.04.17.tar.bz2 is the driver i downloaded

---

### Post by linuxmagick on 2009-06-27
lspci -v

The above command may be the command you were referring to.

---

### Post by ubunewtu on 2009-06-27
isnt there more to it something like ispci -v | ???

---

### Post by philcamlin on 2009-06-27
is there an install.sh inside of it ?

double click it and see whats inside

---

### Post by linuxmagick on 2009-06-27
> **ubunewtu said:**
> isnt there more to it something like ispci -v | ???

If you know what you're looking for you could grep, like:

lspci -v | grep Broadcom

But lspci -v should work.  You'll just have to look through the results to find your wireless card.

I am probably wrong as I've never heard of the file you downloaded, but it doesn't even seem like a driver to me.  Has anyone else heard of wireless-regdb?  

Back when I was cursed with a Broadcom wireless card, I either had to use fwcutter or ndiswrapper along with the Windows drivers in order to get the card to work under Linux.

---

### Post by ubunewtu on 2009-06-27
Source: [http://wireless.kernel.org/download/wireless-regdb/wireless-regdb-2009-01-15.tar.bz2](http://wireless.kernel.org/download/wireless-regdb/wireless-regdb-2009-01-15.tar.bz2) no there is no install inside the folder damn i feel realy stupid right now cuz i havnt been taking notes of what im doing

---

### Post by philcamlin on 2009-06-27
[B]404 - Not Found:(

got it ...

[/B]tar -xjvf <filename>

then use the readme

---

### Post by ubunewtu on 2009-06-27
if i go to compaq they give me windows 2000, xp, nt. drivers if i use fwcutter will it work on any of them is it like try them all till it works. im going to junk this unknown file i downloaded cuz it appears to be the wrong thing

---

### Post by ubunewtu on 2009-06-27
ah ok so the card is 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by linuxmagick on 2009-06-27
I would strongly suggest searching the forums for BCM4318.  I'm sure there are already some discussions out there for getting this card working.  Here's one thread I found that may point you in the right direction:
[URL="http://ubuntuforums.org/showthread.php?t=1196928&highlight=BCM4318"]
http://ubuntuforums.org/showthread.php?t=1196928&highlight=BCM4318[/URL]

---

### Post by ubunewtu on 2009-06-27
ok so i had remembered that it did a bunch of up dates and my wireless light went out i am really upset withmyself instead of checking to see if there was a driver in admin i made it complicated but im a new user so i guess i shouldnt be to hard on myself and in the long run i learned some commands id just like to thank everyone who had spent time to help me out

---

### Post by linuxmagick on 2009-06-27
> **ubunewtu said:**
> ok so i had remembered that it did a bunch of up dates and my wireless light went out i am really upset withmyself instead of checking to see if there was a driver in admin i made it complicated but im a new user so i guess i shouldnt be to hard on myself and in the long run i learned some commands id just like to thank everyone who had spent time to help me out

No need to be so hard on yourself.  We all make mistakes and end up doing things the hard way.  As long as we can learn from what we do, then everything will be alright.:D

---

### Post by ubunewtu on 2009-07-05
im trying to install java but i dont know my password for su is there a way to reset it?

---

### Post by ubunewtu on 2009-07-05
its the password to gain root acess is it wise to put java there is is there a better place?

---

### Post by ubunewtu on 2009-07-05
never mind i got it through the little help lines in the terminal

---

### Post by linuxmagick on 2009-07-05
I'm happy you were able to figure it out:).  With Ubuntu, you should never need to login as root using su.  Instead, just put sudo in front of the command you're trying to run.  When you are prompted for the sudo password, just put in your regular password.  The sudo command lets the command you're trying to execute run with root privileges and then lowers those privileges once the command has completed.  This is a lot safer than just logging in as root.

---

### Post by ubunewtu on 2009-07-06
hiya gang i installed a deb file to the terminal (at least i think i did) now what command do i use to run it?

---

### Post by linuxmagick on 2009-07-06
```
sudo dpkg -i yourfile.deb
``` will install the file.

---

### Post by ubunewtu on 2009-07-06
linux do u know anything about the game urban terror ive been trying to install it for like three hours the last thing i did was install the deb file it said it was installed to the terminal and after that im lost (i know this is probably not the place to be asking about things like this but ive been trying for to long to get this thing up and running)

---

### Post by ubunewtu on 2009-07-06
k i got it i need to fiddle for longer before i cry out for help ty

---

### Post by linuxmagick on 2009-07-06
Cool.  I was going to say that if you didn't get any errors while installing the deb file, it probably created a menu entry you could use to launch the game.

---

### Post by ubunewtu on 2009-07-07
yes it did create a munu ive learned that working with deb files is way better than other files and on a side note urban terror is a very addicting game and thats unusual for me since its the very first pc game i play

---

### Post by ubunewtu on 2009-07-08
me again i found a driver from amd for the processor in my laptop (turion64) it says its a Bzip archive (application/x-bzip) i hate zip files and would like some help to get it installed. never mind thinking of reinstalling with the 64bit version

---

### Post by ubunewtu on 2009-10-26
ok so one of those times i know im posting in the wrong place so sorry but i was wondering if anyone knew the location of the redhat fedora forums just did a fresh install and need to get a wlan usb working

---

