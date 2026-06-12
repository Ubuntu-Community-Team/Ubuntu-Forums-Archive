---
title: "installing drivers"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by antdemo45 on 2009-04-18
hello, ive ran into a problem, i have a dell vostro 1700 laptop running off a removeable harddrive with linux ubuntu on and it's my 1st time, i have installed java finally and now i;m in need of my graphic drivers being installed, my graphics is built in Intel® 915 Express Chipset Family and i have no idea how to install it, i found a download for the file and its xf86-video-intel 2.4.0 version and thats the one i need and its file has been extracted to my desktop, just totaly stuck and have no idea how to install it, i would appricate someone helping, thnx alot, i just love this ubuntu, complete change and its complicated and i love it lol i have just sat here for ages trying to work it out and try get help but all this iv'e tried just failes me lol so now its time for me to ask the pros

thnx alot

anthony

---

### Post by Shazaam on 2009-04-18
Did you go to System>Administration>Hardware Drivers first and check to see if there were any available?
What kind of a file did you download? .deb, .zip, .run, .bin, .rpm etc?
A good link for file installation...
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by balaknair on 2009-04-18
You do not need to download and install drivers seperately with Ubuntu. Ubuntu will do it for you automatically- the Intel drivers are open source and are already on the Ubuntu CD, and get installed when you install Ubuntu. If you have hardware that requires proprietary(non-open-source) drivers, as is the case with nVidia graphics and some Wireless chipsets, you can install them via the hardware drivers uitility as Shazaam noted above.

To install packages, use the Synaptic Package Manager(System menu> Administration> Synaptic). Open it, and search for the package you need(for example 'intel video driver' or 'xf86 video intel'), select the package and click 'Apply', and Synaptic will download and install the package for you(along with any dependencies).
(see screenshot attached)

An even simpler interface to install many common applications is to use the 'Add/Remove...' applet in the Application menu.

---

### Post by antdemo45 on 2009-04-19
thnx alot guys for your input, well i tried them, lots of things updates and my problem is, with the same laptop with vista on runescape runs perfect and now with ubuntu on i get horrible graphics

the file is on my desktop and i extracted it to the desktop im not sure when it is now as it has been extracted how would i install it?

---

### Post by balaknair on 2009-04-19
The xf86-video-intel 2.4.1 drivers are already available in the repositories for Ubuntu 8.10(which is what I'm assuming you're using) as part of the package *xserver-xorg-video-intel*.

Before trying to install the downloaded file(I think it would be in tar.gz format, but you haven't mentioned what format the file is in or where you got it from, what link you used) I strongly suggest you open the Synaptic Package Manager> search for Intel graphics driver> see if it is installed(installed version should be 2:2.4.1-1ubuntu10.4). I think you will find that it is installed, and the problem might be with your graphics settings.

If you need help finding a solution for your graphics problems, please post some additional information-

a) The version of Ubuntu you're using(Look in the 'About Ubuntu' file in System Menu> About Ubuntu if you're not sure). Did it come pre-installed on the computer or did you install it yourself?

b) Are you using 32-bit or 64-bit Ubuntu?

c) The full file name of the package you downloaded(including the bit at the end after the dot), the download link you downloaded it from, and the page you got the link from.

d) The details of your hardware and (an easy way to do that would be to open a terminal(Applications menu> Accessories> Terminal) and paste in the following commands and post the output here with your reply.
```
lspci | grep VGA
lsmod
```

e) The make/model of your computer would also be useful info, are you using a netbook, a conventional notebook(laptop), or a desktop PC.

Please remember that installing drivers from sources other than the Ubuntu repositories is not recommended for those new to Linux, and you may have to reinstall the driver again after each kernel update. OEM Ubuntu installs on specialized hardware like netbooks differ quite a bit from stock installs of Ubuntu, and the requirements may differ quite a bit.

---

### Post by antdemo45 on 2009-04-19
its ubuntu 8.10.

my laptop is a dell vostro 1700.

i tried already to install the driver still the same problem, the game looks like this :

[http://i41.tinypic.com/9h56ao.png](http://i41.tinypic.com/9h56ao.png)

i never had this problem on vista


thnx

---

### Post by balaknair on 2009-04-19
Thanks for the screenshot.

Question: On Ubuntu do you get graphics errors with normal usage or is it only with Runescape?

I don't know much about Runescape, but I believe it runs via a Java applet. So if regular graphics usage(desktop effects etc) works fine for you, it could be an error with Java. You might want to search the forums/google for stuff related to that. IMO it's more likely to be because of a Java error. Java runtime in Linux lags behind that in Windows. Are you using 32-bit Java on a 64-bit OS? That's another potential minefield.

The driver version you mentioned in your first post(v 2.4.0) is the same as that installed with Ubuntu 8.10(the one in Ubuntu is slightly newer- v2.4.1), so installing it IMO will not make any difference. If anything it could make things worse if not properly installed. To my knowledge, the drivers you currently have with Ubuntu 8.10 should work fairly well and if properly installed/configured should not give you any trouble. 

{Again, please read my previous post, more info is needed if others on the forum are to be able to help you. Specifically, the points I mentioned *a)* to *e)*.
eg: just mentioning Dell Vostro 1700 doesn't tell us much- the Vostro 1700 is available in a number of configurations, the(only) one I've seen comes with an nVidia GPU.}

To sum it up:
* Installing Intel 915 drivers- the driver you want to install is already installed

* Running Runescape- the error you get is probably not related to the Intel GPU/drivers, more likely to be because of Java. You might want to check this thread here
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=874986](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=874986)

---

### Post by antdemo45 on 2009-04-19
thanks alot for your input, ill have a look at that.

it probs is java your right, can;t see it being my drivers as i did what you guys said and it seems their upto date, i dont no about others games i dont play games just use runescape sometimes o well, ill have to buy a new harddrive because mine is broke, unless you can install vista on a removeable harddrive.

thnx again

---

### Post by upchucky on 2009-04-19
open a terminal, Application > Accessories > Terminal the  type this.

```
glxgears
```

you should see some spinning  gears and in one of the terminal windows that opens up, the frame rates should appear within about 20 seconds.

you should see frame rates of around 10,000 and up

this indicates that 3d is actually working. 

if you have low frame rates then there will be others with your vid card that have answers to getting it to work.

---

### Post by balaknair on 2009-04-19
> **antdemo45 said:**
> thanks alot for your input, ill have a look at that.

it probs is java your right, can;t see it being my drivers as i did what you guys said and it seems their upto date, i dont no about others games i dont play games just use runescape sometimes o well, ill have to buy a new harddrive because mine is broke, unless you can install vista on a removeable harddrive.

thnx again

I don't think MSFT allows you to legally install Vista on removable(USB or Firewire) drives. There probably are workarounds to enable you to get a working installation, I think I've seen one for XP, but I don't know for sure how well it would work.

Anyway, I hope you manage to get your drive fixed/replaced.

All the best.

---

### Post by antdemo45 on 2009-04-20
thnx guys, i really did wanna use ubuntu and go further with more linux software and get to know it, because vista is boring and theres so many gaps and holes, wanted to try something new, i was just getting use to ubuntu aswell lol, o well, ill rebuy a new harddrive an put vista back on, maybe duel boot sometime with ubuntu try that runescape again another time.



i cant access ubuntu either anymore, seems it keep crashing b4 i can load up, just says something about ubuntu shutdown 1% and all the wayto 100% then its like dos screen after that with my login, can't get actually on the ubuntu.

so much bull s i have come across, once this laptop has had its time, im going to personally throw the thing and beat it up with all the grief its caused me, lost all ma 30gb of music and all ma dj software, maybe not lost yet, but im sure its preety much lost, we will see when i get new hdd ill be able to put both in and have a look.

thnx alot guys fo your time

edit: how do i add reputation to you guys? does this forums have a rep bar?

---

### Post by balaknair on 2009-04-20
You might be able to retrieve some of your important data from the drive using an Ubuntu Live CD and an external drive.
Boot from the Live CD, and if you can access the hard drive on your laptop, you could transfer files on to an external drive. 
If you have partition table errors or corrupted sectors(possible if you've had crashes with a failing hard disk), utilities like testdisk have helped me save many a GB for my friends. I recommend photorec if you just want to get your photos, videos, music and documents on to a backup drive.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

Unless your disk is totally shot, you can recover most if not all your data.

All the best.

---

### Post by antdemo45 on 2009-04-20
yer thnx man, yer i'll wait ust orders a hdd on ebay, i'm browing a laptop now and that's how i installed ubuntu itself threw this laptop.

once the ebay item has come i can do it then.

---

