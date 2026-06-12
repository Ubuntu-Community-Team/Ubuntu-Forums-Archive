---
title: "Samsung CLP-315W problems"
date: 2009-11-29
forum: Hardware
---

### Post by mollydoggy1971 on 2009-11-29
I just bought this printer.  I have it on my network.  It is seen by the printer installation thing, but it doesn not install properly.  Upon installation, it prints a test page that says SPL-C ERROR - Please use the proper driver.  I went to the Samsung website and downloaded the Unified Linux Driver.  I extracted the archive, and now have a folder called "cdroot" on my desktop.  I don't know what to do with it, and the instructions provided on the Samsung website do not work.  I need VERY detailed instructions, as I am a noob, and have no idea what I am doing.  Please do not think you are talking down to me; in fact, pretend you are giving instructions to a 7 year old child.  I need to know EXACTLY what to do.  I will be taking notes, however, and will learn what it is that you've taught me, so I will eventually be able to do this on my own.  Thanks for your help!

---

### Post by mollydoggy1971 on 2009-11-29
Help?  Please?

---

### Post by jstapels on 2009-12-05
I just unboxed mine and am now in the process of getting it to work as well (waiting on the unified driver download). Not sure if you're still stuck but I found this thread:

[http://georgia.ubuntuforums.org/showthread.php?t=341621](http://georgia.ubuntuforums.org/showthread.php?t=341621)

You might want to check it out and see if it helps you.

---

### Post by mollydoggy1971 on 2009-12-14
> **jstapels said:**
> I just unboxed mine and am now in the process of getting it to work as well (waiting on the unified driver download). Not sure if you're still stuck but I found this thread:

[http://georgia.ubuntuforums.org/showthread.php?t=341621](http://georgia.ubuntuforums.org/showthread.php?t=341621)

You might want to check it out and see if it helps you.

I appreciate the link, but the problem I have is that thing is WAY too complicated for me.  I don't understand most of what it says, and the parts I do understand, I don't know how to make happen.  It says to "do this" and "do that" and I don't know how to "do" these things.  I have the Unified Linux Driver package.  I have no idea what to do with it.  They have instructions on the site I got it from, but they do not work.  I'm sure I'm doing something wrong that they assume I should know, but I don't know that I don't know!  This is why I've come to the forums for help.  Usually I've had very good responses and help with my few issues.  I don't know why people are ignoring me on this one.  Anyway, I thank you again for the link.  Perhaps you have gotten yours installed, and could tell me (in small words and such) how to do it!

---

### Post by mollydoggy1971 on 2009-12-27
Can nobody offer me assistance?  Does noone know how to install a printer driver?  Help please!

---

### Post by BatPenguin on 2010-01-03
> **mollydoggy1971 said:**
> Can nobody offer me assistance?  Does noone know how to install a printer driver?  Help please!

Hello there,

I don't have this particular printer but I'm actually considering getting it. While I surf for user experiences on it, I'd be happy to help you get the printer working. So, looking at the link posted above, what you probably should be doing is the part IIc. Please let me know how far along the instructions (if anything :) you get and I'll give you more detailed help. Like: paste the first part of those instructions that you don't get and I'll let you know how it's done. We should be able to get it going for you soon enough.

---

### Post by mollydoggy1971 on 2010-01-08
> **BatPenguin said:**
> Hello there,

I don't have this particular printer but I'm actually considering getting it. While I surf for user experiences on it, I'd be happy to help you get the printer working. So, looking at the link posted above, what you probably should be doing is the part IIc. Please let me know how far along the instructions (if anything :) you get and I'll give you more detailed help. Like: paste the first part of those instructions that you don't get and I'll let you know how it's done. We should be able to get it going for you soon enough.

Ok, I appreciate your willingness to tackle this with me.  I am now trying IIc.  I enter the first line of code into Terminal, and I get the following: mollydog@Ubuntu-PC:~$ deb [http://www-personal.umich.edu/-tjwatt/suldr/](http://www-personal.umich.edu/-tjwatt/suldr/) debian extra
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
mollydog@Ubuntu-PC:~$ 
Something has gone awry, and I know nothing about Linux, so I couldn't begin to troubleshoot.

---

### Post by BatPenguin on 2010-01-08
> **mollydoggy1971 said:**
> Ok, I appreciate your willingness to tackle this with me.

No problem. I'll give you some explanations and links while I do this, so please do study those so you'll learn it. These are some of the most important skills for using Linux, installing programs, so if you learn these, you'll be much more comfortable in Linux.

> **mollydoggy1971 said:**
> I am now trying IIc.  I enter the first line of code into Terminal, and I get the following: mollydog@Ubuntu-PC:~$ deb [http://www-personal.umich.edu/-tjwatt/suldr/](http://www-personal.umich.edu/-tjwatt/suldr/) debian extra

..Something has gone awry, and I know nothing about Linux, so I couldn't begin to troubleshoot.

Nothing's really wrong there, it just that you were not supposed to write that as a command. The instructions page says "Add the following line to your /etc/apt/sources.list, by editing the file as root (or using sudo), or by using Synaptic or other GUI to add a repository". What you actually did was just type into the terminal the line you were supposed to **add ** to the file. That's all, that's why it's complaining about not recognizing it as a command.

So, a short explanation: your Ubuntu computer installs programs from online sites known as "repositories". The main ones are maintained by Ubuntu and contain software authenticated by them. When you select a program to install for Ubuntu from Add or Remove Programs, it "pulls the program" from one of these repositories. As a user, you can add more of these repositories if you wish to install software that's not in the default ones. That's what we want to do here, add a repository that contains the printer driver we need.

The system maintains its list of repositories in a file called /etc/apt/sources.list . That is, the file is called sources.list (sources as in "sources you install software from") and it's located in the directory /etc/apt . So, we need to add a line that identifies the printer-driver containing server to this file, so the system knows how to use it. You can do this with a graphical tool called Synaptic (you can select it from Administration -> Synaptic), but since we're on the command line, let's do it like that. (For more on repositories, please read this: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) ) 

So: open up the terminal and edit the file with the program **gedit**. Since it's a system file, we need to do this with adminstrator rights, that is, using "sudo", so the system will prompt for your password to make sure you have the rights to do this. (for more: [https://help.ubuntu.com/8.04/administrative/C/terminal.html](https://help.ubuntu.com/8.04/administrative/C/terminal.html)) 

And since it is a system file and we're a bit worried about breaking something accidentally, let's make a backup of the file using the copy (cp) command. Like this:```


sudo cp /etc/apt/sources.list /etc/apt/sources.backup

```
After this, we can edit the original file:
```

sudo gedit /etc/apt/sources.list

```
Move to the end of the file and copy+paste the lines from the printer driver installation instructions into it:

deb [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) debian extra

Save the file and close it.

Now, we have the repository's name added. We also need to tell the system to trust it so we can install software from it without too many complaints, so copy paste this in the terminal:
```

wget -O - [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg) | sudo apt-key add -
```


This just gets (wget) the authentication information (the .gpg file) from a web site and submits that information (the pipe character |) to the command "sudo apt-key add" (which adds an authentication key, run as administrator).

Now the repository and the key to verify it should be added.

Now update the system's list of repositories: sudo apt-get update

You should see a list of repositories contacted, including the new one. 


Now install the driver itself:```


sudo apt-get install samsungmfp-driver samsungmfp-data

```

Now, if all went right, you should be able to add the printer and have its driver listed in the list. Try it and let me know if it worked. If it did, I'd be very interested in hearing a bit more about the print quality of this printer.

---

### Post by mollydoggy1971 on 2010-01-10
> Now, we have the repository's name added. We also need to tell the system to trust it so we can install software from it without too many complaints, so copy paste this in the terminal:
```

wget -O - [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg) | sudo apt-key add -
```


This just gets (wget) the authentication information (the .gpg file) from a web site and submits that information (the pipe character |) to the command "sudo apt-key add" (which adds an authentication key, run as administrator).



After typing in this line, I get the following message:  
mollydog@Ubuntu-PC:~$ wget -O [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg) | sudo apt-key add -
gpg: no valid OpenPGP data found.
mollydog@Ubuntu-PC:~$

Is this OK?  I'm not sure, but that seems to me that the command failed.  

Also, thank you VERY much for explaining this process so thoroughly.  This is exactly the type of information I need, so that I can learn what I'm doing, and why I'm doing it.

EDIT:  I went ahead and did the next step, just in case the previous thing was, in fact, fine.  After it displayed a bunch of URLs, it finished with the following: 
Fetched 327kB in 2min 43s (1,995B/s)                                           
Reading package lists... Done
W: GPG error: [http://www-personal.umich.edu](http://www-personal.umich.edu) debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C95104E509BAC46D
mollydog@Ubuntu-PC:~$ 

I'm guessing from this that I may have been correct, in that the previous command failed.  

One other thing...I have the Unified Linux Driver package physically located on my desktop.  Is it necessary to download it again from this repository?  I have no idea if it would be easier to use the one on my desktop, so I thought I'd throw that out there.  Thanks again!

---

### Post by BatPenguin on 2010-01-10
> **mollydoggy1971 said:**
> After typing in this line, I get the following message:  
mollydog@Ubuntu-PC:~$ wget -O [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg) | sudo apt-key add -
gpg: no valid OpenPGP data found.
mollydog@Ubuntu-PC:~$

Is this OK?  I'm not sure, but that seems to me that the command failed.

Yes, it failed. That's odd, I just tried it too and it didn't work, although the web page with the key is up there. Well, let's do it in two parts then. So first, open up a terminal and just download the key:

wget [http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg](http://www-personal.umich.edu/~tjwatt/suldr/suldr.gpg)

then, add it as a trusted key:

sudo apt-key add suldr.gpg 

Try that. If says OK, just continue following my instructions.

> **mollydoggy1971 said:**
> 
One other thing...I have the Unified Linux Driver package physically located on my desktop.  Is it necessary to download it again from this repository?  I have no idea if it would be easier to use the one on my desktop, so I thought I'd throw that out there.  Thanks again!

No, using the repository is much easier (even if it doesn't seem like that now with the key failing=). So if this works, you don't need the Unified driver you've downloaded. Part of the beauty of repositories is updates - the Ubuntu update manager program will notify you if there's an update to the driver.

---

### Post by mollydoggy1971 on 2010-01-14
Hooray!  It has worked perfectly!  It printed the test page, and it looks fabulous!  The color is lovely, and the black is crisp.  I have used this printer several times in Windows, and it works quite well there too.  I think this printer and I will be a happy couple for a long time to come!  Thank you so very much for your detailed help and patience with me.  I truly appreciate it, and have made careful notes, so that if I ever need to do it again, it will work, and I will learn from it.  Sadly, I do not have a lot of free time, as I work 2 jobs, and only have one day off every week, so I do not have a lot of free time to spend learning lots of new things...I have to go slowly, and take things as they come along.  Thanks again, my friend!

---

### Post by BatPenguin on 2010-01-14
> **mollydoggy1971 said:**
> Hooray!  It has worked perfectly!  It printed the test page, and it looks fabulous!  The color is lovely, and the black is crisp.  I have used this printer several times in Windows, and it works quite well there too.  I think this printer and I will be a happy couple for a long time to come!  Thank you so very much for your detailed help and patience with me.  I truly appreciate it, and have made careful notes, so that if I ever need to do it again, it will work, and I will learn from it.  Sadly, I do not have a lot of free time, as I work 2 jobs, and only have one day off every week, so I do not have a lot of free time to spend learning lots of new things...I have to go slowly, and take things as they come along.  Thanks again, my friend!

You're welcome! Glad it worked. You're well on your way to becoming a proficient Ubuntu user if you could follow and understand those instructions, good job. Just take your time getting to know Ubuntu, slow and steady is the best way to get around it. As long as you always make sure you know what you're doing when you're running something with "sudo", you'll be just fine :)

Now, if you don't mind answering a few extra questions about the printer now that you got it to run, I'd be very interested in a few things:

a) Could you please print a photograph, like some nice good-looking picture you've taken yourself etc, and let me know how it turns out and whether it's good enough quality to actually put in a frame or such? Is the quality far from what you'd get from ordering prints or is it pretty close, etc, how does it look?

b) Can you print normal photo-size pictures with it? Like does the paper tray allow you to put 10x15 photo paper etc. in it and print photos in that size?

Thanks!

---

### Post by mollydoggy1971 on 2010-02-08
> **BatPenguin said:**
> You're welcome! Glad it worked. You're well on your way to becoming a proficient Ubuntu user if you could follow and understand those instructions, good job. Just take your time getting to know Ubuntu, slow and steady is the best way to get around it. As long as you always make sure you know what you're doing when you're running something with "sudo", you'll be just fine :)

Now, if you don't mind answering a few extra questions about the printer now that you got it to run, I'd be very interested in a few things:

a) Could you please print a photograph, like some nice good-looking picture you've taken yourself etc, and let me know how it turns out and whether it's good enough quality to actually put in a frame or such? Is the quality far from what you'd get from ordering prints or is it pretty close, etc, how does it look?

b) Can you print normal photo-size pictures with it? Like does the paper tray allow you to put 10x15 photo paper etc. in it and print photos in that size?

Thanks!

Sorry it's taken a bit to get back with you...I've been out of town, and no laptop!  I've printed photos, and they look pretty good, as long as you put them on photo paper.  Regular printer paper looks like an above average inkjet.  You can't use oversize paper, as the paper try only holds 8 inch wide paper maximum, and maybe 12.5 inches long maximum.

---

### Post by BatPenguin on 2010-02-08
> **mollydoggy1971 said:**
> Sorry it's taken a bit to get back with you...I've been out of town, and no laptop!  I've printed photos, and they look pretty good, as long as you put them on photo paper.  Regular printer paper looks like an above average inkjet.  You can't use oversize paper, as the paper try only holds 8 inch wide paper maximum, and maybe 12.5 inches long maximum.

OK, no problem - thanks! Sounds good, I'll probably end up getting one of these eventually.

---

### Post by BatPenguin on 2010-08-06
> **BatPenguin said:**
> OK, no problem - thanks! Sounds good, I'll probably end up getting one of these eventually.

I just installed the driver on another computer and noticed that the repository's moved to: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

So just modify the instructions above to match that address (key and repository). Works great as usual, very nice and trouble-free printer under Ubuntu.

---

### Post by hungrywolf99 on 2011-06-30
This is the easiest way I found of installing drivers for the Samsung CLP-315W on Ubuntu 10.10 and 11.04. This also assumes that you have already set up the following printer in your network and is ready to be used.
 

 Firstly download your drivers from the following page:
 

 [http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP00&prd_ia_cd=&prd_mdl_cd=CLP-315W/XEU&prd_mdl_name=CLP-315W&srchword=CLP-315W%2016/4ppm%20-%20%20Mono/Colour%20Network%20&%20Wireless%20Ready](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?menu=SP00&prd_ia_cd=&prd_mdl_cd=CLP-315W/XEU&prd_mdl_name=CLP-315W&srchword=CLP-315W%2016/4ppm%20-%20%20Mono/Colour%20Network%20&%20Wireless%20Ready)
 

 You can get away with only downloading the Unified Driver but if you want you can download the Smart Panel as well. Expand one or both of the files by right clicking them and choosing Extract Here option.
 

 Make sure you know where you download it to. For this example all files were downloaded to Downloads/Samsung/ The full path would be given below for ease of access.
 

 **/home/<user name>/Downloads/Samsung/cdroot/Linux/**
 

 Obviously <user name> would be your account name so replace that with your account name. If that is confusing you just go to places and then Downloads and right click on any of the directories and get the properties and you will be able to see the direct path to this area.
 Please note that the second extracted folder will have the name “cdroot 2”. I changed it to “cdroot2” for ease of access.
 

 Now open your terminal by choosing the Ubuntu icon (top left), Accessories, Terminal.
 

 Please key in the following:
 

 ***cd /home/<user name>/Downloads/Samsung/cdroot/Linux***
 

 then key in this:
 

 ***ls***
 

 you will now see the list of files in that directory. One of which will be **install.sh**
 

 Now just key in the following:
 

 ***sudo sh install.sh***
 

 you will now be asked for your admin password. Once you key that in there will be some process and a popup window will appear. Here you will make your choices and detect your printer and and finally it will give you the opportunity to send a test print.
 

 This will conclude the installation of your printer driver.
 If you want to install the Smart Panel, just change directory to:
 

 ***cd /home/<user name>/Downloads/Samsung/cdroot2/Linux/smartpanel/***
  

  and key in the following:
 ***sudo sh install.sh***
  

  this will install the Smart Panel as well. But I found out that this is not really that necessary.
  

  I would like to thank Samsung US help desk for **NOT** helping me with solving this problem. I was requested to call Samsung UK during office hours.
  

  Please feel free to comment on my notes and thank you for reading.
  

  The Hungry Wolf

---

### Post by comradekingu on 2013-01-29
The above doesnt work well on debian, it produces a copy of text output on each print mirrored in a kind of side by side view. With spacing errors in between.


Just add the printer through system-config-printer 1.3.7 with cups installed as a normal ipp printer.
Then revisit the config sites and add ipp://192.168.1.whateveryourprinterIPis where it says URL.


It will find it itself and provide configuration, which is a bit swing and miss, one computer it was monochrome, but thats easily changed.

---

### Post by sandyd on 2013-01-29
**Necromancing - Thread closed**
As per the Ubuntu Forums code of conduct, please do not post in threads more than one year old. Ubuntu changes greatly betweeen releases, and as a result, what applies/is discussed in this thread may not apply to new versions of Ubuntu.

Thanks!

---

