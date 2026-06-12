---
title: "Wireless driver issues"
date: 2009-10-08
forum: Hardware
---

### Post by DeltaSierra on 2009-10-08
Hi there guys, I'm a newly converted Linux user and am finding the experience brilliant so far, apart from not being able to use wireless on my Linux machine.

So the lowdown is, I had a spare laptop lying around at home, a HP 6715b, and decided to install the Ubuntu 9.10 Beta on it. I have managed to get it to recognize the wireless adapter, but the drivers included with the OS don't work. I have trawled countless forums and found a fair amount of coverage on this issue with a multitude of solutions, but none of them seem to work for me. Could be a beta issue, but I am more inclined to believe it's user error, as I'm fairly new to Linux. I am getting accustomed to using Terminal, it's surprisingly logical and straight forward, I'm starting to see just how limited the Windows command line really is, but I'm still learning.

Anyway, any help at all would be very much appreciated!

Cheers!

---

### Post by Vibin Lakshman on 2009-10-09
> **DeltaSierra said:**
> Hi there guys, I'm a newly converted Linux user and am finding the experience brilliant so far, apart from not being able to use wireless on my Linux machine.

So the lowdown is, I had a spare laptop lying around at home, a HP 6715b, and decided to install the Ubuntu 9.10 Beta on it. I have managed to get it to recognize the wireless adapter, but the drivers included with the OS don't work. I have trawled countless forums and found a fair amount of coverage on this issue with a multitude of solutions, but none of them seem to work for me. Could be a beta issue, but I am more inclined to believe it's user error, as I'm fairly new to Linux. I am getting accustomed to using Terminal, it's surprisingly logical and straight forward, I'm starting to see just how limited the Windows command line really is, but I'm still learning.

Anyway, any help at all would be very much appreciated!

Cheers!

Try to install Ndiswrapper , which is a Windows adapter . I believe you know how to do it through synaptic manager .. This will solve your problem 90% . If still it doesnt work , try to install restricted properiety software, this will be show in your taskbar while you try to connect wireless . Check that radiobutton and installation will start automatically

---

### Post by DeltaSierra on 2009-10-19
Hello again, sorry I didn't reply, I've been having a bit  of an intense time at work (object oriented Python scripting to access Win Active Directory through LDAP - massive headache!).
Anyway, I've already tried ndiswrapper several times without much success. I have gone for a fresh install of 9.10 after trying without success to install 9.04 (I have 32 and 64 bit versions on five different cd/dvds, all freeze before install or live cd boot :-x). When I try to install ndiswrapper from a .deb (both the version included on the install disk and another I downloaded) I get an error: 'Bad file descriptor', and with
sudo apt-get install ndiswrapper-utils-1.9I get nothing either. Is there something I'm missing? 'Cause I did have it going at one point. Anyway, I hope someone can shed some light on the matter for me :).

---

### Post by Dr_Bobby on 2009-10-19
On 9.04 you should have ndiswrapper pre-installed.  If not just:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

If that isn't working, post any error messages you are getting.

After that, simply run

```
sudo ndiswrapper -i yourdriver.inf
```

Where yourdriver.inf is the windows driver file for your card.

Then:

```
ndiswrapper -l
```

To confirm installation.  Then

```
sudo ndiswrapper -m
```

To add a module to startup.

---

### Post by DeltaSierra on 2009-10-20
If I try to install ndiswrappper through terminal I get

```
Reading package lists... Done 
Building dependency tree... Done 
E: Couldn't find package ndiswrapper-common
```

(Same without the -common)

If I try the ndiswrapper .deb on the install disk and one i downloaded I get

```
dpkg: unable to read file descriptor flags for <package status and progress file descriptor>: Bad file descriptor
```

Not sure what's going on, I have had ndiswrapper working before in 9.10 using this method.

---

### Post by Greg Xix on 2009-10-20
> **DeltaSierra said:**
> ... I have gone for a fresh install of 9.10 after trying without success to install 9.04 (I have 32 and 64 bit versions on five different cd/dvds, all freeze before install or live cd boot :-x). When I try to install ndiswrapper from a .deb (both the version included on the install disk and another I downloaded) I get an error: 'Bad file descriptor',...



I HIGHLY recommend using a Flash Live USB Startup solution for your installs. It easily takes about 5 minutes to make one, and your Ubuntu will install in half the time of a CD/DVD. PM me and I will give you instructions on how to create one if you dont know how.

---

### Post by DeltaSierra on 2009-10-21
Well, I've tried everything so far, and only had a bit of success tonight. I tried installing both the 32 and 64 bit versions of 9.04 with the same error, got a bit further by turning apci off, but the install still crashed. I did however finally get ndiswrapper to install, along with ndisgtk like so:

```
sudo dpkg -i ndiswrapper-common_1.53-2ubuntu1_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.53-2ubuntu1_amd64.deb
sudo dpkg -i ndisgtk_0.8.4-1_amd64.deb
```

I then followed this method [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) and that got me further than ever before, but still not working. Could it be that the driver does not work with the 64 bit OS?

Anyway, I'll keep trying :)

---

### Post by DeltaSierra on 2009-10-22
Ha Ha, I am happy to report that I am happily writing this post from my laptop, after doing some more messing around last night and installing another 64 bit driver for my card I finally gave up, but turning it on just then to have another crack at it, I noticed the wireless icon had changed, and voila! :P

Thanks for all the help guys, I'm happy to finally be on Linux fully!

---

### Post by dt_matthews on 2009-11-08
> **DeltaSierra said:**
> Ha Ha, I am happy to report that I am happily writing this post from my laptop, after doing some more messing around last night and installing another 64 bit driver for my card I finally gave up, but turning it on just then to have another crack at it, I noticed the wireless icon had changed, and voila! :P

Thanks for all the help guys, I'm happy to finally be on Linux fully!

Hi there DeltaSierra, any chance you could give me a link for the driver you have got working, i have a 6715b and just can get the wifi to work!

cheers dude,
dan

---

### Post by DeltaSierra on 2009-11-09
Sure mate, I just recently redid the wireless installation with the full release version of karmic, works like a charm.

Just find and install the following debs in the following order (apt-get install doesn't work, just double click the packages, and skip those steps on the install guide):
ndiswrapper-common_1.53-2ubuntu1_all.deb
ndiswrapper-utils-1.9_1.53-2ubuntu1_amd64.deb
ndisgtk_0.8.4-1_amd64.deb

Then download and extract the following .exe:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=au&prodTypeId=321957&prodSeriesId=3368540&prodNameId=3356624&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-66462-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=au&prodTypeId=321957&prodSeriesId=3368540&prodNameId=3356624&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-66462-1)

The bcmwl5 files are the ones you want.

Now follow the instructions at [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

That should hopefully work!

---

