---
title: "Installing a Smart Board?"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by shadowvoice on 2008-02-07
I've used Windows for years, and I'm totally sick of it. I've tried to use Ubuntu, but I'm not a master of open source and I'm not very good at using it, although I am utterly in love with it! Anyway, I'm tired of using the Smart Board with Windows, and I want to use Ubuntu instead. I tried installing it on Ubuntu with no success, because I don't know what to do. I would really appreciate some help in installing the Smart Board in Ubuntu, please!

PS: The reason *I'm* having to do it is because our school's IT is not capable of doing her job, so I do most of her work for her (unannounced to her of course!).

---

### Post by KuraiDM on 2008-02-07
What version of Ubuntu are you using?

At this point SMART Technologies only supports Ubuntu 6.06 LTS with its latest release of SMART Board Software 9.7

If that's what you're using, I should be able to offer further assistance.

---

### Post by shadowvoice on 2008-02-07
I have 7.10, but I can get my hands on 6.06 LTS if that's what I need. Think you can help?

---

### Post by shadowvoice on 2008-02-07
Okay! Found a copy of 6.06 LTS sitting in one of my CD holders. Can you give me some assistance?

---

### Post by mooha on 2008-02-07
Welcome, Greeting to you, 

check this out
[http://www.youtube.com/watch?v=gxgqLpuq7JM](http://www.youtube.com/watch?v=gxgqLpuq7JM)

when you are using ubuntu you are not using Linux, you are using Gnu+Linux, because linux is just a kernel.

good luck

---

### Post by KuraiDM on 2008-02-20
Sorry for the lack of reply, been terribly busy. 

The process for installing SMART Board Software is fairly straightforward once you have Ubuntu 6.06 set up and ready to go. However, I should warn you, functionality is a little different between what you may be used to with Windows, unfortunately certain features inside Notebook, such as video and flash are not supported, and things such as Recorder and Video player are not either.

I'm at home right now, but once I get to work today I'll post the documentation with instructions on how to install SMART Board Software on Linux, though in the meantime, you can probably go to the [www.smarttech.com](www.smarttech.com) website and download the installation file for SMART Board Software 9.7.

Another thing to note is that version 10 will possibly be coming out in a few months for Linux, it's already going through Beta for Windows and Mac, while I don't believe full functionality parity will be met in the version 10 for Linux, they should be trying to address some of those issues.

---

### Post by KuraiDM on 2008-02-20
It's been a while since I've dabbled with the linux installation of SMART Board software, so I can't seem to find my documentation, however, if you visit [http://downloads.smarttech.com/media/products/sbs/linux/installing97linuxreadme.txt](http://downloads.smarttech.com/media/products/sbs/linux/installing97linuxreadme.txt) you should be able to go through with the installation. You may or may not need to open up the properties menu on the .package file and make sure the executable checkbox is checked. Generally speaking though, Autopackager should do most of the work for you when you launch the .package file.

---

### Post by crocuta on 2008-03-06
Hi. I've used smartboard 680 with Edubuntu 6.06, Edubuntu 7.04 and Ubuntu 7.10.   Like the previous poster said, you must download the software from their website. Once uncompressed you get a bunch of folders and main files:   "SMART Board Software 9.7.68.0.package" and "SMART Essentials for Educators 1.1.68.0.package".   

      On every machine and ubuntu version i had to right click them, go to properties, permissions and check the  checkbox that says "allow to run as a program".  Accept and reload the file manager window (F5).  Notice that the icons may change.

     First install "SMART Board Software 9.7.68.0.package".  It will ask you for your password twice and ask if you want to install support code.  Yes to all.     When the installation ends, you will see a floating windows with the Smartboard tools.

    As you probably know, the package "SMART Essentials for Educators 1.1.68.0.package" is used to install the resources: clipart, some photos, maps, sounds, etc.   You select a category from the catalog and it downloads from the web.   I have had problems with this  package in ubuntu 7.10;  the installation just does not finish.  However, there is a workaround that also happens to save you bandwith:
 
    On the SmartTech site there is a download called "SMART Essentials CD", which contains all the resources for offline installation. It only works on Windows but once installed you can export those from the Notebook as a .gallery file and install them offline on every GNU/Linux box.  As said before, everything but the videos and flash will work, at least on 9.7.

  Basically you do this:
On the Windows box -  Install the cd, open notebook and export all the resources as a .gallery file. It takes a few minutes and the result is a ~500MB file.

On the GNU/Linux box(es) - 
Copy the file somewhere.
Open the notebook AS ADMINISTRATOR:
 cd   /usr/local/SMART\ Technologies\ Inc/Notebook\ Software/bin/    
 sudo ./notebook
You must see a tool icon near the gallery that normally isn't there. Use this and look for "Add file to my content" or something like that (i have the spanish version).
Locate the file and wait a few minutes.

You should have now all the gallery installed. If when you reenter the Notebook the resources are not there, fiddle around with the options on the tool icon.   It has happened to me before, but be sure that once you got it right, the resources won't dissapear.

---

### Post by endysea on 2008-05-04
I found the following instructions at [http://forum.eeeuser.com/viewtopic.php?pid=241222](http://forum.eeeuser.com/viewtopic.php?pid=241222). I've tried it on my Fujitsu FMV-Biblo NB75J running Ubuntu 8.04, and it works beautifully.

1) Download and extract the package to your home folder. [http://www2.smarttech.com/st/en-US/Support/Downloads/SBS/SBSv97Linux.htm](http://www2.smarttech.com/st/en-US/Support/Downloads/SBS/SBSv97Linux.htm)

2) Open up a terminal window and type: sudo nautilus

3) Enter your password

4) Navigate to the SMARTBoardSoftware folder, double click on "SMART Board Software 9.7.68.0.package"

5) Answer all of the prompts in the affirmative

6) Enjoy
(You will need to run the Smartboard Service program in the gnome menu in order to activate the smartboard (it takes a minute) and the you are good to go.)

Note that when you run sudo nautilus, there may be some warnings. Ignore them, for everything works just fine despite those warnings.

---

### Post by endysea on 2008-05-04
> **shadowvoice said:**
> I've used Windows for years, and I'm totally sick of it. I've tried to use Ubuntu, but I'm not a master of open source and I'm not very good at using it, although I am utterly in love with it! Anyway, I'm tired of using the Smart Board with Windows, and I want to use Ubuntu instead. I tried installing it on Ubuntu with no success, because I don't know what to do. I would really appreciate some help in installing the Smart Board in Ubuntu, please!

PS: The reason *I'm* having to do it is because our school's IT is not capable of doing her job, so I do most of her work for her (unannounced to her of course!).
I found the following instructions at [http://forum.eeeuser.com/viewtopic.php?pid=241222](http://forum.eeeuser.com/viewtopic.php?pid=241222). I've tried it on my Fujitsu FMV-Biblo NB75J running Ubuntu 8.04, and it works beautifully.

1) Download and extract the package to your home folder. [http://www2.smarttech.com/st/en-US/S...BSv97Linux.htm](http://www2.smarttech.com/st/en-US/S...BSv97Linux.htm)

2) Open up a terminal window and type: sudo nautilus

3) Enter your password

4) Navigate to the SMARTBoardSoftware folder, double click on "SMART Board Software 9.7.68.0.package"

5) Answer all of the prompts in the affirmative

6) Enjoy
(You will need to run the Smartboard Service program in the gnome menu in order to activate the smartboard (it takes a minute) and the you are good to go.)

Note that when you run sudo nautilus, there may be some warnings. Ignore them, for everything works just fine despite those warnings.

---

### Post by felipeperucho on 2008-05-16
Thank you Endysea. The point was to execute the package as sudoer. The "sudo nautilus" command is essential, and is not well documented in the company instructions.

Thank you again. You have saved an important presentation for me for this monday :).

---

