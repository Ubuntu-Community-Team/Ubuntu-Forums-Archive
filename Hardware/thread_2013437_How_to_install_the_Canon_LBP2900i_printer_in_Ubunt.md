---
title: "How to install the Canon LBP2900i printer in Ubuntu 12.04 LTS"
date: 2012-06-30
forum: Hardware
---

### Post by stevecook on 2012-06-30
Hi folks. My name is Steve Cook. I'm a newcomer to Ubuntu. I have been using it for three months now. The first two and a half months of which was on Ubuntu 10.04 LTS and the last two weeks on Ubuntu 12.04 LTS. 

I own a Canon LBP 2900i printer. Installing it on Ubuntu 10.04 LTS was a bleeding nightmare. But I managed it in the end. I had to install a start-up bash-script to re-set the printer every time Ubuntu started up (more on that later). But, once done, it worked fine. 

I have had a similar issue in Ubuntu 12.04 LTS. I am about to describe how I got it to work in Ubuntu 12.04 LTS. My description is aimed at new users like myself and so I will, no-doubt, be seen to be excessively labouring some things for the more experienced user. Regarding such experienced users, my apologies in advance.
 
 One other thing, it probably doesn't have any relevance, but I did all of the following from the &#8220;Gnome-Classic&#8221; shell in Ubuntu 12.04 LTS. I merely mention it for completeness. I don't see any reason why it shouldn't work in exactly the same way in the &#8220;Unity&#8221; shell.

------------------------------------------------------------------------------------------------------------------
 **Caveat**
 
 **You may feel free to copy my actions to get your Canon LBP 2900i printer to work on your own PC. However, you do so at entirely your own risk. I strongly urge you to save any important files from your &#8220;file system&#8221; drive to either another drive/partition or to a removable media. If you screw up on on anything and mess your system up, it is your own responsibility.**
 ----------------------------------------------------------------------------------------------------------------

 Here is precisely how I got the printer to work in 12.04:

1) Download the printer driver from the link below:

[https://github.com/raducotescu/CanonCAPTdriver/tarball/master](https://github.com/raducotescu/CanonCAPTdriver/tarball/master)
 
 You should get this dialogue window. Choose to open with &#8220;Archive Manager&#8221;

*(click on the image link and it should appear in a new window)*
[IMG]http://ubuntuforums.org/[IMG]http://i958.photobucket.com/albums/ae67/stevecook172001/download-printer-driver.png[/IMG][http://i958.photobucket.com/albums/ae67/stevecook172001/download-printer-driver.png](http://i958.photobucket.com/albums/ae67/stevecook172001/download-printer-driver.png)
 
It is in a zipped-up format called a "tar". Once downloaded, it should automatically open up in the program called "Archive Manager" (or. if you initially saved it instead, you can double click after it has downloaded and it will then open up in Archive Manager). For those who are brand new to this kind of thing, once it has opened in Archive manager, you could do what I  did and extract the folder containing the package of scripts to your user-name folder. This is the same folder that you will automatically start in when you open a terminal (more on this later).
 
Once extracted, navigate your way to your home folder (which is the same folder as your username........just to confuse matters!).
 
*(click on the image link and it should appear in a new window)*
[http://i958.photobucket.com/albums/ae67/stevecook172001/home-folder.png](http://i958.photobucket.com/albums/ae67/stevecook172001/home-folder.png)

 Once there you will see a new folder (the one you just extracted) called "raducotescu-CanonCAPTdriver-c8ea9f9". Double click the folder and inside there is a "README" file which you should read. It tells you how to run the bash script to install the driver. You have to do this from a terminal. Essentially, what you do is click on the terminal icon from the accessories menu. The terminal will open in your home folder.  

  *(click on the image link and it should appear in a new window)*
[http://i958.photobucket.com/albums/ae67/stevecook172001/terminal.png](http://i958.photobucket.com/albums/ae67/stevecook172001/terminal.png)

  To test if you are in your home folder, if you type:

 **ls**
 
 it will list all of the files and folders inside your home folder. One of the folders listed will be the one called "raducotescu-CanonCAPTdriver-c8ea9f9".  

  *(click on the image link and it should appear in a new window)*
[http://i958.photobucket.com/albums/ae67/stevecook172001/ls-terminal.png](http://i958.photobucket.com/albums/ae67/stevecook172001/ls-terminal.png)
 
 Type:
 
 **cd raducotescu-CanonCAPTdriver-c8ea9f9**  
 
 to go into the folder. If you again type:
 
 **ls**
 
 you should see the following files:

 canonLBP_install.sh
 canonLBP_uninstall.sh
 changelog
 DEBS
 LICENSE
 README
 
 When you sure you are are in the correct folder, you can then use the command that is given in the README file for running the correct script. It is:
 
 **sudo ./canonLBP_install.sh LBP2900**
 
 You will be prompted for password (the same one you use to log into Ubuntu). Type in your password and press the "Enter" key.

But, I also urge you to read the instructions fully in the README file as well as simply following my instructions here

Assuming all went well, above, the next step is:

2) Getting the printer to work!
 
 Assuming your printer is on, if you tried to print a document at this point, if would just hang in the print queue and would not print. This next step is what you need to do to make it actually work. It involves making something called a bash script.
 
 You first need to open a text editor. In the gnome-shell you can open one up from &#8220;accessories/gedit&#8221;. In the Unity shell I think it may just be called &#8220;text editor&#8221;, though I am not certain.
 
 Once opened, paste the following code into it:
 
 **#!/bin/bash**
**sudo modprobe usblp ** 
 **ls -l /dev/usb/lp0**
 **sudo -S lpadmin -x LBP2900-2**
 **sudo /etc/init.d/ccpd restart**
 **sudo /etc/init.d/cups restart**
 
 This code is is telling Ubuntu to:
 
 a) search for and make active the physical connection to the printer
 b) get rid of a second and unwanted printer that was created in the installation process (don't ask me why it was created, I don't know and care even less)
 c) restart the printer drivers
 
 Don&#8217;t worry if you don't understand the specific syntax of the code (neither do I). Just know that it works!
 
 Once you have pasted the code, save the file to your home folder as &#8220;reset-printer.sh&#8221;
 
 Then open up a terminal and type:
 
 **ls**
 
 You should see the file &#8220;reset-printer.sh&#8221; in the list of files and folders.
 
 Now type the following to make the file executable:
 
 **chmod +x reset-printer.sh**
 
 Congratulations, you have just written your first bash script!
 
 This script will be need to be used each time you start Ubuntu to make your printer work.
 
 To do this, close the terminal and then navigate your way to your home folder. You will again see the &#8220;reset-printer.sh&#8221; file.
 
 Double-click the file. A dialogue box will appear:

  *(click on the image link and it should appear in a new window)*
[http://i958.photobucket.com/albums/ae67/stevecook172001/run-exec.png](http://i958.photobucket.com/albums/ae67/stevecook172001/run-exec.png)
 
 Choose to &#8220;Run in terminal&#8221;
 
 The terminal will appear and again prompt you for your sudo password (this is the same password you use to log into Ubuntu) Type your password in and press the "Enter" key.

 At this point, your printer should now be working.
 
 You can test this by opening your word processor and typing something into it and then printing the document. At the print dialogue box, you may or may not see the second printer mentioned earlier. I'm not sure why it is sometimes there and sometime not. But no matter, it is not set as the default and doesn't seem to affect anything. The one you are using is set to default and so you don't need to change anything. Just press the print button and it should work.

I should note, the very first time you try this, there is a small possibility it might not work. If that happens, re-boot your machine, re-set the printer again with the "reset-printer.sh" file and it should be OK. From then on in, you should find it works every time.
 
 From now on, the first thing you will need to do after you have logged onto Ubuntu is to go to your home folder and double-click the &#8220;reset-printer.sh&#8221; file and then choose to run it in a terminal as before, type in your password, hit the enter key and you printer will be good to go for the rest of your session.
 
 You may well be happy enough to stop reading this tutorial at this point and simply re-set the printer manually like I have described every time you log onto Ubuntu. If, however, you are a nerd like me and are unsatisfied with having to do the above and would prefer for it to automatically happen every time Ubuntu loads so that it all feels more seamless and invisible, then please read my next section of this tutorial on how to automate the resetting of the printer using the same &#8220;reset-printer.sh" file you have just created. I'll be posting it up here tomorrow.  
 
 I'd do it now, but it's late, I'm knackered and I'm off to bed.

---

### Post by stevecook on 2012-07-01
OK folks, here's the second part of my tutorial on how to install the Canon LBP2900i printer on Ubuntu 12.04 LTS

This second part deals with automating the re-setting of the printer every time you re-boot your computer into Ubuntu (incidentally, I think switching your printer off and on during a session will require a re-set as well. In which case you would need to employ the manual method described in section 1 of this tutorial using the &#8220;printer-reset.sh&#8221; file)

I should say, the following method was used by me after trying other methods I read in other tutorials for running an automated bash script that included the &#8220;**sudo**&#8221; command. They all indicated that each sudo command in the script should be prefixed with &#8220;**echo yourpassword |**&#8221; (where &#8220;**yourpassowrd**&#8221; is replaced by your actual password that you use to log in with).

 However, this has never worked for me as the script, when run, has always still appeared in a terminal asking for the password. Obviously, if you need this script to run automatically, then having it come up and ask for the password is not what you want. I have since discovered  how to disable the sudo password prompt completely so you are *never* asked for it. That way an automated script including the sudo command will not ask for it either.

 The following steps  show how to first disable the sudo password prompt and then  how to get the printer to re-set automatically at boot-up.  

 **Be warned, though** (also see general caveat).  Disabling your sudo password requires that you edit a very important file called the &#8220;sudoer&#8221; file and if you screw up while you are editing it, you can knacker your entire system and you will have to re-write it. I know this because I have done precisely that myself on a previous occasion. Furthermore, disabling your sudo passsword prompt is viewed by some as leaving your system less secure. However, I am less personally concerned about this than others and so I have no problem with disabling it. It's a matter of taste and risk-tolerance I guess. In any event, you still have to enter your password at boot-up.

------------------------------------------------------------------------------------------------------------------
[B]Caveat

You may feel free to copy my actions to get your Canon LBP 2900i printer to work on your own PC. However, you do so at entirely your own risk. I strongly urge you to save any important files from your &#8220;file system&#8221; drive to either another drive/partition or to a removable media. If you screw up on on anything and mess your system up, it is your own responsibility.[/B]
----------------------------------------------------------------------------------------------------------------

1) Open up a terminal. Type &#8220;**sudo visudo**&#8221; and press the &#8220;**Enter**&#8221; key. After typing in your password at the prompt, press &#8220;**Enter**&#8221;. You will be taken into something called the &#8220;sudoer&#8221; file.
 
 2) Hold the down arrow key and you will see the cursor move to the bottom of the file. Paste the following line below all other lines (in order to paste using only the keyboard in a terminal, you need to press the CTRL/SHIFT/V keys simultaneously):
 
**yourusername  ALL=NOPASSWD: ALL **

where &#8220;yourusername&#8221; should be replaced with your actual user-name (mine, for example, is &#8220;stephen&#8221;)
 
 3) You now need to save and close the file. To do this you need to:

 a) press **CTRL **and** X**
 b) You will be prompted to type **Y** or **N **in order to save or discard the modifications. You must type Type **Y**
  c) You will be given another prompt for the name that is given.  Simply press the &#8220;**Enter**&#8221; key.
 
 You should now find you have dropped out of the sudoer file and are back at the normal terminal prompt. That's it, you can close the terminal at that point
 
4) Using your menu, go to something called &#8220;Startup Applications&#8221;, In the classic gnome interface, this is under tools. In the unity interface, I would think it will come up if you type it into the search box on the dash. It looks like this:

(click on the image link and it should appear in a new window)
[http://i958.photobucket.com/albums/ae67/stevecook172001/startup1.png](http://i958.photobucket.com/albums/ae67/stevecook172001/startup1.png)

5) Click on the &#8220;Add&#8221; button:

(click on the image link and it should appear in a new window)
[http://i958.photobucket.com/albums/ae67/stevecook172001/startup2.png](http://i958.photobucket.com/albums/ae67/stevecook172001/startup2.png)

6) For the Command, press the "browse" button and navigate to your &#8220;printer-reset.sh&#8221; file and choose it. For the Description, simply write "printer-reset" (or whatever you want) in the box.

7) Close the &#8220;add&#8221; dialogue box. You should now see this file listed as one of your start-up applications in the start-up-applications dialogue box. Close the start-up-applications dialogue box.

That's it. From now on, every time you start Ubuntu 12.04 LTS, this file will will run automatically, you will not be prompted for your password in a terminal and your printer will be ready to use immediately.

I hope this tutorial has been useful. If anything does not go as planned or expected, then please do write a reply in here and I will try and help if I can.

---

### Post by absalypson on 2012-07-15
Dear Stephen,

after weeks of of horror while trying my LBP2900 to work, I found several useless guides on the web for this problem. Nothing was able to help.  I even send an email to canon to ask them, what to do. but their answer was kind of: 'Your OS must be defective"...

Then, I found your instructions here...
...and, due to the perfect step-by-step description and the nice scripts, I was finally able to run my printer on Linux MINT 13!!!

Thank you for this and keep running your help to bloody new linux users like me... :D

---

### Post by chandraubunt on 2012-07-18
Hai,
      I have been trying to install canon LBP2900B laser jet printer      	 	 	 	in my lenovo desktop pc having ubuntu 12.04 *Precise **pango**lin.* 	 	   I tried to install  the driver from here _ [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)  _,but it wont work.There was no driver for 12.04 *Precise **pango**lin*. I followed  all your directions in this post  .After completing all steps  , when I try to print , it shows a error message like this  "There is a missing print filter for printer canon LBP 2900". Could you help me, please ?

---

### Post by stevecook on 2012-07-20
> **chandraubunt said:**
> Hai,
      I have been trying to install canon LBP2900B laser jet printer                         in my lenovo desktop pc having ubuntu 12.04 *Precise **pango**lin.*             I tried to install  the driver from here _ [https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)  _,but it wont work.There was no driver for 12.04 *Precise **pango**lin*. I followed  all your directions in this post  .After completing all steps  , when I try to print , it shows a error message like this  "There is a missing print filter for printer canon LBP 2900". Could you help me, please ?Hello Chandraubunt

I am so sorry, but I am a new user to Ubuntu and so am only able to provide advice as it *directly *and* specifically *pertains to the printer and OS I have described in my post (LBP2900i). If any of the variables involved (printer or OS) differ from mine, any consequent advice I may give is likely to be worse than useless.

If anyone who comes across this thread has more in depth knowledge relating to Chandraubunt's specific problem please do feel free to add your knowledge to this thread in order to help him.

In any event, I wish you well and hope you are able to resolve your problem, Chandraubunt.

---

### Post by stevecook on 2012-07-20
> **absalypson said:**
> Dear Stephen,

after weeks of of horror while trying my LBP2900 to work, I found several useless guides on the web for this problem. Nothing was able to help.  I even send an email to canon to ask them, what to do. but their answer was kind of: 'Your OS must be defective"...

Then, I found your instructions here...
...and, due to the perfect step-by-step description and the nice scripts, I was finally able to run my printer on Linux MINT 13!!!

Thank you for this and keep running your help to bloody new linux users like me... :DThank you for your kind words absalypson. I'm glad you got it running.

---

### Post by Sivella on 2012-07-21
**@ chandraubunt**

Could you tell us if you are running 32 or 64bits (12.04) ?
Thanks

---

### Post by stevecook on 2012-07-21
I should also add, for the sake of completeness, I am running 12.04 LTS 32-bit with a Classic-Gnome interface

---

### Post by chandraubunt on 2012-09-07
> **Sivella said:**
> **@ chandraubunt**

Could you tell us if you are running 32 or 64bits (12.04) ?
Thanks
hello sir 
        I  am very sorry for being late for this quiry. I am running 64 bits(12.04).
                                                                                        -Chandra

---

### Post by chandraubunt on 2012-09-07
> **stevecook said:**
> Hello Chandraubunt

I am so sorry, but I am a new user to Ubuntu and so am only able to provide advice as it *directly *and* specifically *pertains to the printer and OS I have described in my post (LBP2900i). If any of the variables involved (printer or OS) differ from mine, any consequent advice I may give is likely to be worse than useless.

If anyone who comes across this thread has more in depth knowledge relating to Chandraubunt's specific problem please do feel free to add your knowledge to this thread in order to help him.

In any event, I wish you well and hope you are able to resolve your problem, Chandraubunt.
Dear Stevecook,
                Thank you very much for reply, I am eagerly waiting for a solution  from this forum.

---

### Post by tachyon28 on 2012-10-04
@chandra
try installing [COLOR=Blue]ia32-libs[/COLOR] from synaptic package manager/USC and also [COLOR=Blue]ubuntu restricted extras[/COLOR] from software centre before following these instructions.

---

### Post by tonidito on 2012-10-10
Hi, some days ago I decided to upgrade my Ubuntu 10.04 to the newer Ubuntu 12.04. Everything went very well, and after some configuration I felt satisfied. Only a thing created some head scratching: my Canon printer LBP3010 could not print!
After some unsuccessfully attempts to make the driver functioning I decided to make some researches in Google. I tried all possible drivers, deb packages and following strictly all posts that I fount in the Internet, but... nothing, my printer seems to be dead!
My last chance was to recompile from source. First with unsuccessful results, due to many error that occurred during the compilation procedure. Again, after some head scratching and a few sleepless nights analyzing the source code, I get the right solution and now I have my LBP3010 fully functioning.

Note that the following procedure is valid for a 64 bit machine.

uname -a gives
Linux toni-laptop 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

In the following I will show the procedure that I followed in order to get the printer working.
First I downloaded the last driver package I found at the Canon web page:

Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz.

Now the procedure to compile.

First step
1) extract the tar.gz package to a folder of Your choice;
2) cd Linux_CAPT_PrinterDriver_V240_uk_EN/Src/
3) untar cndrvcups-capt-2.40-1.tar.gz  and cndrvcups-common-2.40-1.tar.gz
4) cd cndrvcups-common-2.40/
5) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
6) dpkg-buildpackage.

At the end of operation 6) You will find cndrvcups-common_2.40-1_amd64.deb package in Src directory.

7) install it (required for the next compilation steps) with the common 
    sudo dpkg -i cndrvcups-common_2.40-1_amd64.deb

Second step
1) cd cndrvcups-capt-2.40/
2) gedit debian/control and change "i386" with "amd64" al line 9, save and close file
3) gedit debian/rules and uncomment line 172 which will results, then, in 
    #    dh_shlibdeps
    Save and close
4) gedit statusui/src/ppapdata.c and add the header (this is to define variable ppd_size_t)
    #include <cups/ppd.h>
save and close file.
5) gedit cngplp/configure.in and add "AC_CONFIG_MACRO_DIR([m4])" at line 9, save and close
6) gedit cngplp/Makefile.am and add "ACLOCAL_AMFLAGS=-I m4" at line 5, save and close
7) run the following commands in the cngplp directory:
    libtoolize
    aclocal
    automake
8) cd .. 
9) dpkg-buildpackage

At the end of operation 9) You will find cndrvcups-capt_2.40-1_amd64.deb package in Src directory.

10) install it with 
    sudo dpkg -i cndrvcups-capt_2.40-1_amd64.deb

End of procedure.
From this point You should follow the printer configuration steps as stated in the previous posts.

I hope this will help the Ubuntu Community.
Kind regards

---

### Post by orlando.terte on 2012-10-28
Please help. When I double click on the "reset-printer.sh" it opens up to gedit automatically even after doing the chmod step. It doesn't give me the option to run it to the terminal.

---

### Post by pdc on 2012-10-28
please have a read at post #2 here

[http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon](http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon)

...........see if you can follow the instructions ........

...........if not, tell me how I can make them more clear ....

........lastly, subscribe to the thread: top right: thread tools then you can keep in touch ..........

---

### Post by stevecook on 2012-10-29
> **orlando.terte said:**
> Please help. When I double click on the "reset-printer.sh" it opens up to gedit automatically even after doing the chmod step. It doesn't give me the option to run it to the terminal.
Hi, what version of Ubuntu are you using?

---

### Post by Sivella on 2012-11-02
**@ tonidito**

Many thanks for your procedure. Since Ubuntu 10.10 and Canon driver v2.00, I failed to compile cndrvcups-capt for 64bits and I'm not enough expert to find the files to be modified.
 
I try it on 12.04-64bits (same kernel version).
Compilation cndrvcups-common still works.
Compilation cndrvcups-capt works and **at the end my LBP5000 works** too, but on step#7 when running automake command I have this message :

> user1@allusers-System:~/Linux_CAPT_PrinterDriver_V240_uk_EN/Src/
cndrvcups-capt-2.40/cngplp$ automake
configure.in:39: required file `./config.guess' not found
configure.in:39:   `automake --add-missing' can install `config.guess'
configure.in:39: required file `./config.sub' not found
configure.in:39:   `automake --add-missing' can install `config.sub'
configure.in:5: required file `./install-sh' not found
configure.in:5:   `automake --add-missing' can install `install-sh'
configure.in:5: required file `./missing' not found
configure.in:5:   `automake --add-missing' can install `missing'
cngplpmod/Makefile.am: required file `./depcomp' not found
cngplpmod/Makefile.am:   `automake --add-missing' can install `depcomp'
Makefile.am: required file `./INSTALL' not found
Makefile.am:   `automake --add-missing' can install `INSTALL'
Makefile.am: required file `./COPYING' not found
Makefile.am:   `automake --add-missing' can install `COPYING'An other issue is that :
> captstatusui -P LBP5000doesn’t open the Status Monitor. I have a "buffer overflow" error.

Have you any idea about that ?

Kind regards

Sivella

_**EDIT :**_ Canon driver version 2.50 is now available. I try your compilation procedure on 12.10-64bits.
The printer works. Same issues as mentioned for 12.04-64bits.

---

### Post by tonidito on 2012-11-12
Hi Sivella,
did You try the commands as super user (i.e. with sudo?)? Anyway the important thing is that You don't have errors.
Regarding the "buffer overflow" error in captstatusui probably it depends on a bug with a pointer  (or some pointers). I tried to check the code but I have no much time. I hope somebody could help me. Really, I do not miss this program; as amatter of fact I noted that the printer works perfectly even without it.
Kind regards

---

### Post by Sivella on 2012-11-12
Hi Tonidito,
Thanks for your answer.
I tried the commands as root (sudo) and non-root, I had the same message when running automake.
But anyway, my printer still printing on 12.04 and 12.10 with Canon drivers v2.4 and/or v2.5 compiled following your instructions.
Kind regards

---

### Post by shankara on 2012-12-19
Thank you for the help. :)

---

### Post by mamammi on 2013-01-13
Hi Steve,
     thank you very much for your detailed instruntions!! It works.....it prints!  :guitar:

---

### Post by stevecook on 2013-01-14
> **mamammi said:**
> Hi Steve,
     thank you very much for your detailed instruntions!! It works.....it prints!  :guitar:You're welcome mate

---

### Post by drjugaljpatel on 2013-03-11
I am getting this error when i try to run dpkg-buildpackage. How do i proceed from here?

dpkg-buildpackage: source package cndrvcups-common
dpkg-buildpackage: source version 2.50-1
dpkg-buildpackage: source changed by Canon Inc. <sup-debian@list.canon.co.jp>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build cndrvcups-common-2.50
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 4.0.0) libglib2.0-dev
dpkg-buildpackage: warning: build dependencies/conflicts unsatisfied; aborting
dpkg-buildpackage: warning: (Use -d flag to override.)

---

### Post by MarkMatis on 2013-03-27
This also works great for installing a Canon LBP6000 in Ubuntu 12.04 LTS 32-bit with the latest Canon 2.50-1 download.  Thanks!

---

### Post by tachyon28 on 2013-08-24
in ubuntu 12.04.3, the printer may be recognised as lp1 insted of lp0 as seen in /dev/usb. so all commands may have to be corrected.

---

### Post by stevecook on 2013-10-08
Hello from Steve Cook again.

Just an update folks:

I have been messing around and trying out various distros of Linux lately and have found that a few of the problems some people have been having with my solution for the Canon LBP2900 printer tend to be related to the very latest versions of, in particular, Ubuntu and Mint. I have a work-around but it's a bit of a mess about. Nevertheless, I thought I'd let you know.

**Ubuntu**

Download the drivers as mentioned in my earlier instructions.

Make a copy of my original instructions from this thread..

Save both of the above to an external storage device such as a USB.

Install a new copy of Ubuntu not later than version 12.04 on your PC. Do the install without internet access so it does not try to update while instaling.

As soon as the installation has finished, install the printer drivers as per my original instructions.

One you have done the above, the printer will work as described in the instructions.

At this point it is safe to update and/or upgrade Ubuntu since the update/upgrade will not undo the printer settings you have set up.

**Mint**

Same instructions as above, not later than version 13 Mint.

---

### Post by MarkMatis on 2013-12-08
As of 8 December 2013, updating to 12.04.3 makes the printer not work.  I had successfully set up an LBP6000 printer using these instructions back in March, and the computer had been successfully printing since then, but when the distro updated to 12.04.3, the printer stopped working.  It works fine on Windows 7, so I know it's not a hardware failure.  I am about to try backing out to an earlier distro to see if I can get it to work again, and will post the details when I am done.

---

### Post by MarkMatis on 2013-12-08
Installation throws errors:
Unpacking cndrvcups-common (from .../cndrvcups-common_2.50-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cndrvcups-common:
 cndrvcups-common depends on libglade2-0 (>= 1:2.4.2-2); however:
  Package libglade2-0 is not installed.
dpkg: error processing cndrvcups-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cndrvcups-common
Selecting previously unselected package cndrvcups-capt.
(Reading database ... 143180 files and directories currently installed.)
Unpacking cndrvcups-capt (from .../cndrvcups-capt_2.50-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cndrvcups-capt:
 cndrvcups-capt depends on libglade2-0 (>= 1:2.4.2-2); however:
  Package libglade2-0 is not installed.
 cndrvcups-capt depends on cndrvcups-common (>= 2.50); however:
  Package cndrvcups-common is not configured yet.
dpkg: error processing cndrvcups-capt (--install):
 dependency problems - leaving unconfigured

sudo apt-get install -f gives:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglade2-0
The following NEW packages will be installed:
  libglade2-0
0 upgraded, 1 newly installed, 0 to remove and 381 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.6 kB of archives.
After this operation, 194 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously unselected package libglade2-0.
(Reading database ... 143426 files and directories currently installed.)
Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1ubuntu1.1_i386.deb) ...
Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...
Setting up cndrvcups-common (2.50-1) ...
Setting up cndrvcups-capt (2.50-1) ...

Configuration file `/etc/ccpd.conf'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** ccpd.conf (Y/I/N/O/D/Z) [default=N] ? N

Configuration file `/etc/init.d/ccpd'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** ccpd (Y/I/N/O/D/Z) [default=N] ? N
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Repeating canonLBP_install.sh LBP6000 gives:
Installing driver for model: LBP6000
using file: CNCUPSLBP6018CAPTK.ppd
Installing packages...
You do have the libstdc++6 package...
(Reading database ... 143436 files and directories currently installed.)
Preparing to replace cndrvcups-common 2.50-1 (using .../cndrvcups-common_2.50-1_i386.deb) ...
Unpacking replacement cndrvcups-common ...
Setting up cndrvcups-common (2.50-1) ...
(Reading database ... 143436 files and directories currently installed.)
Preparing to replace cndrvcups-capt 2.50-1 (using .../cndrvcups-capt_2.50-1_i386.deb) ...
Unpacking replacement cndrvcups-capt ...
Setting up cndrvcups-capt (2.50-1) ...
Processing triggers for ureadahead ...
Modifying the default /etc/init.d/ccpd file...
Restarting CUPS...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 2654
Setting the printer for CUPS...
Setting the printer for CAPT...

 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP6000     : ccp         : //localhost:59687     : /dev/usb/lp0 : Modified

Setting CAPT to boot with the system...
update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 System start/stop links for /etc/init.d/ccpd already exist.
Starting ccpd...
 * Starting Canon Printer Daemon for CUPS: ccpd                          [ OK ] 
Checking status:
Canon Printer Daemon for CUPS: ccpd: 2387 2383

Power on your printer! :)
Go to System - Administration - Printing and do the following:
  1. disable LBP6000-2 but do not delete it since Ubuntu will recreate it automatically;
  2. set LBP6000 as your default printer;
  3. reboot your machine and print a test page.
Script author: 
    Radu Cotescu
    [http://radu.cotescu.com](http://radu.cotescu.com)

However, printer still does not work, regardless of whether Device URl is ccp://localhost:59787 or ccp://localhost:59687

Error message in Printer State is:
Idle - ccp send_data error, exit

Suspect incompatability with current version of libglade2-0

Debating whether to buy a new printer that does not require this level of entertainment, such as an Oki B 410D, or just buy a copy of WIndows 7, since this printer works fine in that OS...

---

### Post by stevecook on 2013-12-12
I'm so sorry to hear of the bother you are having. I'm going to see if I can come up with a new set of instructions/resources to cope with the latest version of Ubuntu. No guarantees, But I'll give it a go.

---

### Post by stevecook on 2013-12-15
Ok, I think I may have a solution:

I have just changed my OS to Xubuntu 13 and have experienced exactly the same problem with my old instructions not working anymore.

I have consequently found out if I download the following file and and install via the softare centre then go back and follow my original instructions on here for installing the Cannon lbp2900i printer, it suddenly works again. I've absolutely no idea why, but there it is. You are more than welcome to try it. The fille is called:

**[B][SIZE=2]gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb[/SIZE]**[/B]

You can download it from:

[http://packages.ubuntu.com/uk/lucid/all/gs-esp/download](http://packages.ubuntu.com/uk/lucid/all/gs-esp/download)

If you double-click the downloaded file, it should open in Software-Centre and then you can install from there.

I should say, I completely purged cups and reinstalled prior to installing the above deb and then installing the printer in the way previously shown in this thread.

Good luck

---

### Post by stevecook on 2013-12-15
deleted post due to double posting

---

### Post by MarkMatis on 2013-12-17
First attempt did not work.  Still getting the "Package libglade2-0 is not installed." when I intially run the installation.  I do sudo apt-get install -f which installs it.  I then have tried running reset-printer with no luck.  I have also uninstalled, reinstalled per Radu's script, done the apt-get to take care of the missing package, done ANOTHER install per Radu's script, and then reset-printer.  Either way, printing a test page seems to send, but nothing prints.  I do notice that if I wait a while, the system throws a Ubuntu error and asks to send a message.  Details say there is a non-Ubuntu package installed and recommend delete.  I had to swap out a U-Verse modem and set up a wireless connection, so I won't get a chance to upload tonight, but Wednesday I will try to undo everything, reboot, and restart from scratch.  I will upload the messages I get, and will post them to see if you can help me figure out where the problem is.  I see you said you had upgraded to 13, this computer is still at 12.04.3, which is where I initially found this failure.

---

### Post by MarkMatis on 2013-12-19
I was tied up yesterday and unable to go through thoroughly, but here is what I did today:

Initial steps:

   Initial steps:
 

 Uninstalled LBP6000 using Radu's script.
 Deleted Canon Pixma IP6600D printer.
 Removed reset-printer from Startup Applications
 Cleared thelma ALL=NOPASSWD: ALL from sudoer file
 Rebooted

---

### Post by MarkMatis on 2013-12-19
After 1st Reboot:
 

 Re-extracted Radu's files to make sure I had not corrupted anything.
 Left:
 /usr/sbin/lpadmin -p $PRINTER_MODEL -P /usr/share/cups/model/CNCUPS${PRINTER_SMODEL}CAPTK.ppd -v ccp://localhost:59687 -E
 as-is for initial attempt.  I understand that &#8220;59687&#8221; may need to change to &#8220;59787&#8221; and fix blacklist per
 [COLOR=#000080]_[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)_[/COLOR]
 Left canonLBP_install.sh referencing 2.20-1 for initial attempt even though latest driver is 2.60-1
 Downloaded and installed gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb through Ubuntu Software Center
 

 Opened terminal:
 thelma@thelma-A55MD2:~$ ls
 Desktop
 Documents
 Downloads
 examples.desktop
 google-earth-stable_current_i386.deb
 google-earth-stable_current_i386.deb.1
 gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb
 mickey -1.jpg
 mozilla.pdf
 Music
 out.jpeg
 paypaloct.pdf
 Pictures
 Public
 raducotescu-CanonCAPTdriver-c8ea9f9
 raducotescu-CanonCAPTdriver-c8ea9fOLD
 raducotescu-CanonCAPTdriver-release-2.4-0-gc8ea9f9.tar.gz
 reset-printer.sh
 Slideshows
  superbowl format jpeg
 Templates
 Videos
 thelma@thelma-A55MD2:~$ cd raducotescu-CanonCAPTdriver-c8ea9f9
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ ls
 canonLBP_install.sh  canonLBP_uninstall.sh  changelog  DEBS  LICENSE  README
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ sudo ./canonLBP_install.sh LBP6000
 [sudo] password for thelma:  
 Installing driver for model: LBP6000
 using file: CNCUPSLBP6018CAPTK.ppd
 Installing packages...
 You do have the libstdc++6 package...
 Selecting previously unselected package cndrvcups-common.
 (Reading database ... 202377 files and directories currently installed.)
 Unpacking cndrvcups-common (from .../cndrvcups-common_2.20-1_i386.deb) ...
 dpkg: dependency problems prevent configuration of cndrvcups-common:
  cndrvcups-common depends on libglade2-0 (>= 1:2.4.2-2); however:
   Package libglade2-0 is not installed.
 dpkg: error processing cndrvcups-common (--install):
  dependency problems - leaving unconfigured
 Errors were encountered while processing:
  cndrvcups-common
 Selecting previously unselected package cndrvcups-capt.
 (Reading database ... 202427 files and directories currently installed.)
 Unpacking cndrvcups-capt (from .../cndrvcups-capt_2.20-1_i386.deb) ...
 dpkg: dependency problems prevent configuration of cndrvcups-capt:
  cndrvcups-capt depends on libglade2-0 (>= 1:2.4.2-2); however:
   Package libglade2-0 is not installed.
  cndrvcups-capt depends on cndrvcups-common (>= 2.20); however:
   Package cndrvcups-common is not configured yet.
 dpkg: error processing cndrvcups-capt (--install):
  dependency problems - leaving unconfigured
 Processing triggers for ureadahead ...
 ureadahead will be reprofiled on next reboot
 Errors were encountered while processing:
  cndrvcups-capt
 Modifying the default /etc/init.d/ccpd file...
 Restarting CUPS...
 Rather than invoking init scripts through /etc/init.d, use the service(8)
 utility, e.g. service cups restart
 

 Since the script you are attempting to invoke has been converted to an
 Upstart job, you may also use the stop(8) and then start(8) utilities,
 e.g. stop cups ; start cups. The restart(8) utility is also available.
 cups stop/waiting
 cups start/running, process 2485
 Setting the printer for CUPS...
 Setting the printer for CAPT...
 

  CUPS_ConfigPath = /etc/cups/
  LOG Path        = None
  UI Port         = 59787
 

 

  Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status  
  ----------------------------------------------------------------------------
      [0]    : LBP6000 	:  		:                 	: /dev/usb/lp0 : New!!
 

 Setting CAPT to boot with the system...
 update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
  Adding system startup for /etc/init.d/ccpd ...
    /etc/rc0.d/K50ccpd -> ../init.d/ccpd
    /etc/rc1.d/K50ccpd -> ../init.d/ccpd
    /etc/rc6.d/K50ccpd -> ../init.d/ccpd
    /etc/rc2.d/S50ccpd -> ../init.d/ccpd
    /etc/rc3.d/S50ccpd -> ../init.d/ccpd
    /etc/rc4.d/S50ccpd -> ../init.d/ccpd
    /etc/rc5.d/S50ccpd -> ../init.d/ccpd
 Starting ccpd...
  * Starting Canon Printer Daemon for CUPS: ccpd                          [ OK ]  
 Checking status:
 Canon Printer Daemon for CUPS: ccpd: 2514 2510
 

 Power on your printer! :)
 Go to System - Administration - Printing and do the following:
   1. disable LBP6000-2 but do not delete it since Ubuntu will recreate it automatically;
   2. set LBP6000 as your default printer;
   3. reboot your machine and print a test page.
 Script author:  
 	Radu Cotescu
 	[http://radu.cotescu.com](http://radu.cotescu.com)
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ 
 

 While still in terminal, fixed errors:
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ sudo apt-get install -f
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Correcting dependencies... Done
 The following extra packages will be installed:
   libglade2-0
 The following NEW packages will be installed:
   libglade2-0
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
 2 not fully installed or removed.
 Need to get 0 B/52.6 kB of archives.
 After this operation, 194 kB of additional disk space will be used.
 Do you want to continue [Y/n]? Y
 Selecting previously unselected package libglade2-0.
 (Reading database ... 202630 files and directories currently installed.)
 Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1ubuntu1.1_i386.deb) ...
 Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...
 Setting up cndrvcups-common (2.20-1) ...
 Setting up cndrvcups-capt (2.20-1) ...
 

 Configuration file `/etc/ccpd.conf'
  ==> File on system created by you or by a script.
  ==> File also in package provided by package maintainer.
    What would you like to do about it ?  Your options are:
     Y or I  : install the package maintainer's version
     N or O  : keep your currently-installed version
       D     : show the differences between the versions
       Z     : start a shell to examine the situation
  The default action is to keep your current version.
 *** ccpd.conf (Y/I/N/O/D/Z) [default=N] ? N
 

 Configuration file `/etc/init.d/ccpd'
  ==> File on system created by you or by a script.
  ==> File also in package provided by package maintainer.
    What would you like to do about it ?  Your options are:
     Y or I  : install the package maintainer's version
     N or O  : keep your currently-installed version
       D     : show the differences between the versions
       Z     : start a shell to examine the situation
  The default action is to keep your current version.
 *** ccpd (Y/I/N/O/D/Z) [default=N] ? N
 Processing triggers for libc-bin ...
 ldconfig deferred processing now taking place
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ 
 

 Rebooted

---

### Post by MarkMatis on 2013-12-19
After 2nd Reboot:
 

 Recreated reset-printer.sh:
 

 #!/bin/bash
sudo modprobe usblp 
ls -l /dev/usb/lp0
sudo -S lpadmin -x LBP2900-2
sudo /etc/init.d/ccpd restart
sudo /etc/init.d/cups restart
 

 Made it executable:
 thelma@thelma-A55MD2:~$ chmod +x reset-printer.sh
 thelma@thelma-A55MD2:~$ 
 Ran reset-printer.sh while in terminal to show error message:
 thelma@thelma-A55MD2:~$ sudo ./reset-printer.sh
 [sudo] password for thelma:  
 ls: cannot access /dev/usb/lp0: No such file or directory
 lpadmin: The printer or class does not exist.
 
[LIST]
[*] 	Restarting Canon Printer Daemon for CUPS: ccpd                       	         * Stopping Canon Printer

[*] 	Daemon for CUPS: ccpd                          [ OK ]  	
[/LIST]
  * Starting Canon Printer Daemon for CUPS: ccpd                          [ OK ]  
                                                                          [ OK ]
 Rather than invoking init scripts through /etc/init.d, use the service(8)
 utility, e.g. service cups restart
 

 Since the script you are attempting to invoke has been converted to an
 Upstart job, you may also use the stop(8) and then start(8) utilities,
 e.g. stop cups ; start cups. The restart(8) utility is also available.
 cups stop/waiting
 cups start/running, process 2582
 thelma@thelma-A55MD2:~$ 
 

 

 (Note:
 There is no &#8220;usb&#8221; folder under &#8220;dev&#8221;.  There is a &#8220;sub&#8221; folder under &#8220;bus&#8221;, but there is no 
&#8220;lp0&#8221; under that &#8220;usb&#8221; folder.  The contents of that &#8220;usb&#8221; folder are folders &#8220;001&#8221; through &#8220;007&#8221; with one item in each.)
 

 After powering on the printer, setting LBP6000 as default, disabling &#8220;LBP6000-LBP6018&#8221;, opening LBP6000 and &#8220;Print Test Page&#8221;, after a couple of minutes the &#8220;Printer State&#8221; says &#8220;Idle-ccp send_data error, exit&#8221; and nothing prints.
 

 Uninstalled per Radu's script:
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ ls
 canonLBP_install.sh  canonLBP_uninstall.sh  changelog  DEBS  LICENSE  README
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ sudo ./canonLBP_uninstall.sh
 [sudo] password for thelma:  
 Found printer model LBP6000...
 Stopping ccpd daemon...
  * Stopping Canon Printer Daemon for CUPS: ccpd                          [ OK ]  
 Removing printer from ccpdadmin...
 

  CUPS_ConfigPath = /etc/cups/
  LOG Path        = None
  UI Port         = 59787
 

  Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status  
  ----------------------------------------------------------------------------
      [0]    : LBP6000 	: ccp 		: //localhost:59687 	: /dev/usb/lp0 : Delete
 

 Removing printer from lpadmin...
 Removing driver...
 (Reading database ... 202639 files and directories currently installed.)
 Removing cndrvcups-capt ...
 Purging configuration files for cndrvcups-capt ...
 Processing triggers for ureadahead ...
 ureadahead will be reprofiled on next reboot
 (Reading database ... 202436 files and directories currently installed.)
 Removing cndrvcups-common ...
 Purging configuration files for cndrvcups-common ...
 Removing runlevel scripts...
  Removing any system startup links for /etc/init.d/ccpd ...
    /etc/rc0.d/K50ccpd
    /etc/rc1.d/K50ccpd
    /etc/rc2.d/S50ccpd
    /etc/rc3.d/S50ccpd
    /etc/rc4.d/S50ccpd
    /etc/rc5.d/S50ccpd
    /etc/rc6.d/K50ccpd
 Cleaning redundant packages...
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages will be REMOVED:
   libglade2-0
 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
 After this operation, 194 kB disk space will be freed.
 (Reading database ... 202386 files and directories currently installed.)
 Removing libglade2-0 ...
 Processing triggers for libc-bin ...
 ldconfig deferred processing now taking place
 Done!
 Script author:  
 	Radu Cotescu
 	[http://radu.cotescu.com](http://radu.cotescu.com)
 thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$
 

 Edited his install file to use 59787 instead of 59687.  Rebooted.

---

### Post by MarkMatis on 2013-12-19
After 3rd Reboot:
 

 Opened terminal:
 thelma@thelma-A55MD2:~$ sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf
 

 [sudo] password for thelma:  
 

 thelma@thelma-A55MD2:~$ 
 [SIZE=3](file was blank, so only entry is now:[/SIZE]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]# cups talks to the raw USB devices, so we need to blacklist usblp to avoid[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]# grabbing them[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]# blacklist usblp[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]per [/SIZE][/FONT][COLOR=#000080]_[[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]https://help.ubuntu.com/community/CanonCaptDrv190[/SIZE][/FONT]]("https://help.ubuntu.com/community/CanonCaptDrv190")_[/COLOR][FONT=Liberation Serif, Times New Roman, serif][SIZE=3])[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Reinstalled installed gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb through Ubuntu Software Center[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Opened terminal:[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~$ ls[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Desktop[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Documents[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Downloads[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]examples.desktop[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]google-earth-stable_current_i386.deb[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]google-earth-stable_current_i386.deb.1[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]mickey -1.jpg[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]mozilla.pdf[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Music[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]out.jpeg[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]paypaloct.pdf[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Pictures[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Public[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]raducotescu-CanonCAPTdriver-c8ea9f9[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]raducotescu-CanonCAPTdriver-c8ea9fOLD[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]raducotescu-CanonCAPTdriver-release-2.4-0-gc8ea9f9.tar.gz[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]reset-printer.sh[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]reset-printer.sh~[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Slideshows[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]superbowl format jpeg[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Templates[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Videos[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~$ cd raducotescu-CanonCAPTdriver-c8ea9f9[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ ls[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]canonLBP_install.sh  canonLBP_uninstall.sh  changelog  DEBS  LICENSE  README[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ [/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ sudo ./canonLBP_install.sh LBP6000[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3][sudo] password for thelma: [/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Installing driver for model: LBP6000[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]using file: CNCUPSLBP6018CAPTK.ppd[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Installing packages...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]You do have the libstdc++6 package...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Selecting previously unselected package cndrvcups-common.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3](Reading database ... 202377 files and directories currently installed.)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Unpacking cndrvcups-common (from .../cndrvcups-common_2.20-1_i386.deb) ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dpkg: dependency problems prevent configuration of cndrvcups-common:[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cndrvcups-common depends on libglade2-0 (>= 1:2.4.2-2); however:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Package libglade2-0 is not installed.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dpkg: error processing cndrvcups-common (--install):[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dependency problems - leaving unconfigured[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cndrvcups-common[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Selecting previously unselected package cndrvcups-capt.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3](Reading database ... 202427 files and directories currently installed.)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Unpacking cndrvcups-capt (from .../cndrvcups-capt_2.20-1_i386.deb) ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dpkg: dependency problems prevent configuration of cndrvcups-capt:[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cndrvcups-capt depends on libglade2-0 (>= 1:2.4.2-2); however:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Package libglade2-0 is not installed.[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cndrvcups-capt depends on cndrvcups-common (>= 2.20); however:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Package cndrvcups-common is not configured yet.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dpkg: error processing cndrvcups-capt (--install):[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]dependency problems - leaving unconfigured[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Processing triggers for ureadahead ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]ureadahead will be reprofiled on next reboot[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Errors were encountered while processing:[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cndrvcups-capt[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Modifying the default /etc/init.d/ccpd file...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Restarting CUPS...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Rather than invoking init scripts through /etc/init.d, use the service(8)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]utility, e.g. service cups restart[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Since the script you are attempting to invoke has been converted to an[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Upstart job, you may also use the stop(8) and then start(8) utilities,[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]e.g. stop cups ; start cups. The restart(8) utility is also available.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cups stop/waiting[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]cups start/running, process 2526[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting the printer for CUPS...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting the printer for CAPT...[/SIZE][/FONT]

 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]CUPS_ConfigPath = /etc/cups/[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]LOG Path        = None[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]UI Port         = 59787[/SIZE][/FONT]

 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Entry Num  : Spooler	: Backend	: FIFO path		: Device Path 	: Status [/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]----------------------------------------------------------------------------[/SIZE][/FONT]
     [FONT=Liberation Serif, Times New Roman, serif][SIZE=3][0]    : LBP6000 	:  		:                 	: /dev/usb/lp0 : New!![/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting CAPT to boot with the system...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Adding system startup for /etc/init.d/ccpd ...[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc0.d/K50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc1.d/K50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc6.d/K50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc2.d/S50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc3.d/S50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc4.d/S50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]/etc/rc5.d/S50ccpd -> ../init.d/ccpd[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Starting ccpd...[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]* Starting Canon Printer Daemon for CUPS: ccpd                          [ OK ] [/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Checking status:[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Canon Printer Daemon for CUPS: ccpd: 2557 2553[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Power on your printer! :)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Go to System - Administration - Printing and do the following:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]1. disable LBP6000-2 but do not delete it since Ubuntu will recreate it automatically;[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]2. set LBP6000 as your default printer;[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]3. reboot your machine and print a test page.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Script author: [/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]	Radu Cotescu[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]	[http://radu.cotescu.com](http://radu.cotescu.com)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ sudo apt-get install -f[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Reading package lists... Done[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Building dependency tree       [/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Reading state information... Done[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Correcting dependencies... Done[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]The following extra packages will be installed:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]libglade2-0[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]The following NEW packages will be installed:[/SIZE][/FONT]
  [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]libglade2-0[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]2 not fully installed or removed.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Need to get 0 B/52.6 kB of archives.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]After this operation, 194 kB of additional disk space will be used.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Do you want to continue [Y/n]? Y[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Selecting previously unselected package libglade2-0.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3](Reading database ... 202630 files and directories currently installed.)[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1ubuntu1.1_i386.deb) ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting up cndrvcups-common (2.20-1) ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Setting up cndrvcups-capt (2.20-1) ...[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Configuration file `/etc/ccpd.conf'[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]==> File on system created by you or by a script.[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]==> File also in package provided by package maintainer.[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]What would you like to do about it ?  Your options are:[/SIZE][/FONT]
    [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Y or I  : install the package maintainer's version[/SIZE][/FONT]
    [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]N or O  : keep your currently-installed version[/SIZE][/FONT]
      [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]D     : show the differences between the versions[/SIZE][/FONT]
      [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Z     : start a shell to examine the situation[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]The default action is to keep your current version.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]*** ccpd.conf (Y/I/N/O/D/Z) [default=N] ? N[/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Configuration file `/etc/init.d/ccpd'[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]==> File on system created by you or by a script.[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]==> File also in package provided by package maintainer.[/SIZE][/FONT]
   [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]What would you like to do about it ?  Your options are:[/SIZE][/FONT]
    [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Y or I  : install the package maintainer's version[/SIZE][/FONT]
    [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]N or O  : keep your currently-installed version[/SIZE][/FONT]
      [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]D     : show the differences between the versions[/SIZE][/FONT]
      [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Z     : start a shell to examine the situation[/SIZE][/FONT]
 [FONT=Liberation Serif, Times New Roman, serif][SIZE=3]The default action is to keep your current version.[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]*** ccpd (Y/I/N/O/D/Z) [default=N] ? N[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Processing triggers for libc-bin ...[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]ldconfig deferred processing now taking place[/SIZE][/FONT]
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]thelma@thelma-A55MD2:~/raducotescu-CanonCAPTdriver-c8ea9f9$ [/SIZE][/FONT]

[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Exited terminal and rebooted.[/SIZE][/FONT]

---

### Post by MarkMatis on 2013-12-19
After 4th reboot:
 

  Opened terminal and ran reset-printer.sh to show error:
 

 thelma@thelma-A55MD2:~$ sudo ./reset-printer.sh
 [sudo] password for thelma:  
 ls: cannot access /dev/usb/lp0: No such file or directory
 lpadmin: The printer or class does not exist.
  * Restarting Canon Printer Daemon for CUPS: ccpd                                * Stopping Canon Printer Daemon for CUPS: ccpd                          [ OK ]  
  * Starting Canon Printer Daemon for CUPS: ccpd                          [ OK ]  
                                                                          [ OK ]
 Rather than invoking init scripts through /etc/init.d, use the service(8)
 utility, e.g. service cups restart
 

 Since the script you are attempting to invoke has been converted to an
 Upstart job, you may also use the stop(8) and then start(8) utilities,
 e.g. stop cups ; start cups. The restart(8) utility is also available.
 cups stop/waiting
 cups start/running, process 2343
 [COLOR=#000080]_[EMAIL="thelma@thelma-A55MD2"]thelma@thelma-A55MD2[/EMAIL]_[/COLOR]:~$
 

 Exited terminal.
 Powered up the printer.
 &#8220;System Settings&#8221; &#8220;Printing&#8221; set LBP6000 as default.  Disabled LBP6000-6018.
 Opened LBP6000 and tried &#8220;Print Test Page&#8221;
 After a couple of minutes, again got &#8220;Idle-ccp send_data error, exit&#8221; message for Printer State.
 

 Noted that &#8220;Device Url:&#8221; in LBP6000 Printer Properties shows ccp://localhost:59687 instead of &#8220;59787&#8221; as edited Radu script calls for.
 Manually edited that line to show ccp://localhost:59787. Clicked &#8220;Apply&#8221;.
 Powered off printer.
 Ran reset-printer.sh in terminal with same error as above.
 &#8220;System Settings&#8221; &#8220;Printing&#8221; Opened LBP6000 and tried &#8220;Print Test Page&#8221;
 After a couple of minutes, got the same &#8220;Idle-ccp send_data error, exit&#8221; message for Printer State.
 

 Any ideas on where to go from here?

---

### Post by stevecook on 2013-12-26
Bleeding hell man! I'm so sorry you've had such an almighty headache trying to get it to work. I'm at a loss now as I lack the necessary expertise to take you futher than you have already gone. I can only reiterate it worked for me in the way I described. Which is, of course, of abolutely no use to you whatsoever. I'm really sorry I can't help further at this point. I will go back and try and retrace my steps to see if there is anything I have missed and, if so, post it here. That's all I can do really. If we're really lucky, someone else who is more knowledgeable will see this thread and post something on here as well.

Steve

---

### Post by MarkMatis on 2013-12-27
Thank you for all your help!  Your initial post got me through the problems back in March, and it was working fine up until late November or early December when some Ubuntu update broke things.  I actually have gone all the way back to a clean install of 12.04.2 32-bit but have been unable to even get that to work.  It would seem there are some problems with libglade2-0 at very least, and it also seems that "/dev/usb/lp0" also now won't work, since I don't believe I got that error message from reset-printer.sh when I initially installed the printer.  It's a shame because this printer really works great under Windows.  I have dual boot on my machine due to some software I need to use which doesn't have a Linux version, so I ran my Christmas card envelopes with it.  About 10 seconds from turning it on until it's ready to print, it does crisp clear B+W printing, and since it uses toner instead of ink cartridges, it works great for someone who doesn't need to print things at least once a week.

Hope you had a Merry Christmas, and wishing you a Happy New Year!

---

### Post by stevecook on 2014-05-04
Okay, final update to this thread.

For all revisions of Ubuntu 12.04.* this works, at least on my Pentium D.

In order of operations:

(1) Install **Synaptic Package Manager** from the control centre, if you don't already have it installed on your system.

(2) Open Synaptic Package Manager.

(3) Copy and paste** ia32-libs** into the search box at the top of Synaptic Package Manager. The application will appear in a box below. Mark it for installation. Then press the apply button.

(4) Close Synaptic Package Manager when the above has been installed.

(5) Open the Software Centre.

(6) Copy and Paste **ubuntu restricted extras** into the search box. When it appears, below, install it.

(7) Close the Software Centre.

(8) Download the following file (**[B][SIZE=2]gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb) [/SIZE]**[/B]from [http://packages.ubuntu.com/uk/lucid/all/gs-esp/download](http://packages.ubuntu.com/uk/lucid/all/gs-esp/download) and, when downloaded, double click it and it will open in the Software Centre. When it does, install it. 

(9) Go back to the start of this thread and follow my original  instructions on here for installing the Cannon LBP2900 printer.

One final thing to note:

I have been trying to migrate across to Xubuntu from Ubuntu because I by far prefer the XFCE desktop over even Gnome and most certainly over Unity. What has previously stopped me is the terrible hassle trying, more or less unsucessfully, to get my LBP2900 printer to work in Xubuntu. By doing the above in Ubuntu 12.04 and then overlying it with an installation of Xubuntu dektop, I finally have what I want; an Xubuntu installation with the my damned printer working at the same time!

I should reiterate: all of the above works on my 32 bit installation. I cannot vouch for it working on the 64 bit.

---

### Post by pdc on 2014-05-04
thanks Steve; you have put a lot of work into the LBP series; 

I wasn't sure as I went back through your thread; as to which (32bit/64bit) that folks were running; (Seems to me the 32bit is a lot easier..........) ....

We have a 32bit 12.04 system; and I just installed the Canon CAPT driver 2.4 driver; (using deb packages); and it just works; ...(I did follow the Sivella guide [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) to register the printer etc)......I did try the radescu script on an early install....................

I was curious you recommend the ia32packages for a 32bit install; as I had understood they were only needed for a 64bit install

---

### Post by stevecook on 2014-05-04
Hi PCD. Thanks for the kind comments.

To be honest, my solution is based more on a Heath-Robinsonian, trial-and-error approach than it is based on a proper understanding of the underlying architecture. That is to say, by trial-and-error, I have discovered that installing all of the above in the order that I have indicated and then following that with my original instructions, the printer will install fully and flawlessly. However, if I follow only my oringinal instructions without the other steps, at least on my Pentium D, then the printer will not work. Neither will it work, at least on my Pentium D,  if I simply install the official debs. It may be that some of the above steps are unneccessary. But, if they are, they don't appear to do any harm.

---

### Post by stevecook on 2014-05-05
Okay, ignore my "final update" because I have another one...:D

All of the below quoted solution works for Xubuntu 14 32-bit aswell. The only additional thing I did was to install Xubuntu restricted extras as well as the Ubuntu restricted extras. I don't actually know if that was necessary but I did it for completeness and it doesn't appear to have had any deliterious effects. I now have the Canon LBP2900 printer working fully in a fresh Xubuntu 14 32-bit install.

> For all revisions of Ubuntu 12.04.* this works, at least on my Pentium D.

In order of operations:

(1) Install **Synaptic Package Manager** from the control centre, if you don't already have it installed on your system.

(2) Open Synaptic Package Manager.

(3) Copy and paste** ia32-libs** into the search box at the top of  Synaptic Package Manager. The application will appear in a box below.  Mark it for installation. Then press the apply button.

(4) Close Synaptic Package Manager when the above has been installed.

(5) Open the Software Centre.

(6) Copy and Paste **ubuntu restricted extras** into the search box. When it appears, below, install it.

(7) Close the Software Centre.

(8) Download the following file (**[B][SIZE=2]gs-esp_8.71.dfsg.1-0ubuntu5.5_all.deb) [/SIZE]**[/B]from [http://packages.ubuntu.com/uk/lucid/all/gs-esp/download](http://packages.ubuntu.com/uk/lucid/all/gs-esp/download) and, when downloaded, double click it and it will open in the Software Centre. When it does, install it. 

(9) Go back to the start of this thread and follow my original  instructions on here for installing the Cannon LBP2900 printer.

One final thing to note:

I have been trying to migrate across to Xubuntu from Ubuntu because I by  far prefer the XFCE desktop over even Gnome and most certainly over  Unity. What has previously stopped me is the terrible hassle trying,  more or less unsucessfully, to get my LBP2900 printer to work in  Xubuntu. By doing the above in Ubuntu 12.04 and then overlying it with  an installation of Xubuntu dektop, I finally have what I want; an  Xubuntu installation with the my damned printer working at the same  time!

I should reiterate: all of the above works on my 32 bit installation. I cannot vouch for it working on the 64 bit.

---

### Post by MarkMatis on 2014-07-11
> **stevecook said:**
> Okay, ignore my "final update" because I have another one...:D

All of the below quoted solution works for Xubuntu 14 32-bit aswell. The only additional thing I did was to install Xubuntu restricted extras as well as the Ubuntu restricted extras. I don't actually know if that was necessary but I did it for completeness and it doesn't appear to have had any deliterious effects. I now have the Canon LBP2900 printer working fully in a fresh Xubuntu 14 32-bit install.

I see you have moved from Ubuntu to Xubuntu.  Did you consider installing Trinity over Ubuntu:
[http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)
?

---

### Post by stevecook on 2014-09-01
Hi there. I have since moved back to Ubuntu with Gnome over the top. The reason being that I could not get LTSP to work with Xubuntu no matter how hard I tried. I use LTSP to run a couple of old machines elsewhere in my house.

---

### Post by boffin_infotech on 2014-12-23
how to install canon lbp 2900 printer in ubuntu 10.04

---

