---
title: "canon ip4700 printer/driver problem on 64bit karmic"
date: 2010-02-16
forum: Hardware
---

### Post by needastick on 2010-02-16
Hi guys,
I could use some help installing my new printer if anybody knows how. I bought this after checking that there was an available driver at Canon but now when I try to install it the config' tells me that it can't read the file. I have repeated the download but the results are just the same.[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=147254&thumb=1&d=1266320788[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=147254&d=1266320788")

I don't know whether it would be possible to edit the file, it seems a little unlikely, can anyone help me with an alternative. The machine worked perfectly on windows of course, this os is testing me and after this is sorted I've got to get the scanner to work...

Any answers in noobyspeak please, cheers.:wink: (I've moved this from installations)
                                                                                                                                              
                                                                             __________________
                Asus M4a785td-m-evo Radeon 4300 igpu Phenom II 550 Karmic             
                                                             [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8834682")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8834682")

---

### Post by needastick on 2010-02-17
bump, could anyone help me please?

---

### Post by dthuk on 2010-03-03
I'll try to help. I've just bought a Canon ip4700 and got it installed on Karmic.

The file you have there is a tgz file which is the Linux equivalent of a winzip file, ie. it has the files archived inside it.

What you need to do is to navigate to wherever you put the tgz file you downloaded. (If it's on your Desktop then that's easy, otherwise, use the Places menu) and double click it to open the archive manager. You will find three folders in there ending in 'deb'. Double click the one that doesn't have "guide" in its name. 
This should then bring up two files: one called 'install.sh' and the other is folder called 'packages', double click 'packages'.

You will find two more files ending in '.deb'. These are the installation packages that will install your driver. Double click the one with 'common' in the name first: the package installer will start up; then click the 'install' button and let it do its stuff. The close the package installer and repeat the process with the other '.deb' file. 

After this, plug in your printer with a USB cable. If it doesn't automatically find it after a few minutes, then go into the "System" menu and select "Administration->Printing".

The printer should then get installed.

Apologies for the woolly explanation, but I'm not at home where my Linux machine is so I'm doing this from memory.

---

### Post by needastick on 2010-03-04
Hi dthuk, thanks for your reply, I must admit I had about given up on this one. I still haven't got the printer working, but have made slight progress since my original post. I'm encouraged by your success.

I worked through what you posted and got to the installation part but received an error message saying wrong architecture i386 . I don't seem to be able to get beyond this. I seem to have downloaded a lot of drivers and converted them with alien, I'm wondering whether I ought to uninstall them and start afresh

Any guidance you may have gratefully received. Tony.

---

### Post by dthuk on 2010-03-05
The problem is that the driver package is written for a 32 bit system and you are using 64 bit. The first thing the package installer does is check your system, and when it discovers it's 64 bit, it gives the message you see. However, this may not be the end of the line. Often these 32 bit packages will still work, you just have to force the package installer to ignore the error.

I would uninstall the other stuff. It's not the source of the problem, but as I don't know what you've installed, there's always the risk that something will be muddying the waters. 

Now try the following:

Double click on your .tgz package as before.

In the archive manager window that pops up, double-click on "cnijfilter-ip4700series--3.20-1-i386-deb.tar.gz"

Double click on "cnijfilter-ip4700series--3.20-1-i386-deb"

Double click on "packages"

Now we are going to extract the two packages to your desktop:

Click on the first of the two files "cnijfilter-common_3.20-1-i386.deb" then click the "Extract" button at the top.

The file location window pops up. Select Desktop in the left hand pane and hit "Extract" button in the bottom right.

Select the second file "cnijfilter-ip4700series_3.20-1-i386.deb" and extract this to the Desktop in the same way.

Now, we need to go to the terminal screen by clicking on the "Applications" menu and selecting "Accessories->Terminal"

In the terminal type:

> cd Desktop

then we are going to install the packages but forcing them to ignore the error by typing:

> sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb

You will be asked for your password. Watch out for all the hyphens and underscore characters!

Now if this works, do the same for the other package by typing:

> sudo dpkg -i --force-architecture cnijfilter-ip4700series_3.20-1_i386.deb

after this, you can proceed as mentioned in my earlier post by plugging in your printer. I'm afraid I don't have a 64 bit system so I can't test whether this will work. We may find we need to install some other 32 bit support packages first if this doesn't work, so let me know how you get on and we'll take it from there.

Dave

---

### Post by needastick on 2010-03-05
Hi, thanks for your reply. I've been trying steadily since your post this morning but have not yet succeeded.

I've cleared most of the original downloads from the desktop and deleted the printer from the admin menu. The drivers appear to have gone as a search shows nothing, but I confess I have been unable to find a way of completely uninstalling with all the dependencies.

I re-downloaded the latest driver from Canon. Following your instructions I get as far as the forced install but it's telling me that the system can't access the archive- no such file. [Screenshot.jpg ]("http://ubuntuforums.org/attachment.php?attachmentid=149070&stc=1&d=1267790752")

Clicking on the file and trying the gdebi installer shows no file on the desktop either, although it shows the scanner drivers awaiting installation.

I've seen somewhere a reference to changing a file from i386 to amd64, do you think that may be relevant or am I way off the mark?

I appreciate your time, regards.

---

### Post by dthuk on 2010-03-05
I can see your problem further up the screen. When you typed "cd desktop" you used a small 'd' rather than a capital 'D' ie. you typed "cd desktop" rather than "cd Desktop" which is why you got the response "No such file or directory".

Unlike Windows, Linux is case sensitive.

The prompt in your terminal window should change from

tony@tony-desktop:~$

to 

tony@tony-desktop:~/Desktop$

which shows you're in the Desktop directory. 

It's because you weren't in this directory when you typed the commands that the package installer couldn't find them and gave the response "No such file or directory"

Best of luck!

Dave

---

### Post by needastick on 2010-03-05
Hi Dave,
             yesss, you were right, it was my upper case carelessness that was preventing the install. I'm not quite out of the woods as there was a hiccup when trying my first text document but the initial test was ok so I'm sure that can be sorted. I need to leave it now but I'll have another go in the morning and see if anything needs adding.

Thanks for your time and effort in helping me out, Tony.

---

### Post by r_avital on 2010-04-12
Removed, and apologies for the double posting, I promise to be more careful.

---

### Post by Johnny3 on 2011-01-23
> **dthuk said:**
> The problem is that the driver package is written for a 32 bit system and you are using 64 bit. The first thing the package installer does is check your system, and when it discovers it's 64 bit, it gives the message you see. However, this may not be the end of the line. Often these 32 bit packages will still work, you just have to force the package installer to ignore the error.

I would uninstall the other stuff. It's not the source of the problem, but as I don't know what you've installed, there's always the risk that something will be muddying the waters. 

Now try the following:

Double click on your .tgz package as before.

In the archive manager window that pops up, double-click on "cnijfilter-ip4700series--3.20-1-i386-deb.tar.gz"

Double click on "cnijfilter-ip4700series--3.20-1-i386-deb"

Double click on "packages"

Now we are going to extract the two packages to your desktop:

Click on the first of the two files "cnijfilter-common_3.20-1-i386.deb" then click the "Extract" button at the top.

The file location window pops up. Select Desktop in the left hand pane and hit "Extract" button in the bottom right.

Select the second file "cnijfilter-ip4700series_3.20-1-i386.deb" and extract this to the Desktop in the same way.

Now, we need to go to the terminal screen by clicking on the "Applications" menu and selecting "Accessories->Terminal"

In the terminal type:



then we are going to install the packages but forcing them to ignore the error by typing:



You will be asked for your password. Watch out for all the hyphens and underscore characters!

Now if this works, do the same for the other package by typing:



after this, you can proceed as mentioned in my earlier post by plugging in your printer. I'm afraid I don't have a 64 bit system so I can't test whether this will work. We may find we need to install some other 32 bit support packages first if this doesn't work, so let me know how you get on and we'll take it from there.

Dave
This should be a stickey. You explaned it real well. For a newbe. I have been trying to do this. But you were the the one that told me to put the pack on the desk top the to CD to get to it.
Thanks and god Bless Johnny(at 65++ I need alot of help)

---

### Post by asvestomix on 2011-07-04
> **dthuk said:**
> The problem is that the driver package is written for a 32 bit system and you are using 64 bit. The first thing the package installer does is check your system, and when it discovers it's 64 bit, it gives the message you see. However, this may not be the end of the line. Often these 32 bit packages will still work, you just have to force the package installer to ignore the error.

I would uninstall the other stuff. It's not the source of the problem, but as I don't know what you've installed, there's always the risk that something will be muddying the waters. 

Now try the following:

Double click on your .tgz package as before.

In the archive manager window that pops up, double-click on "cnijfilter-ip4700series--3.20-1-i386-deb.tar.gz"

Double click on "cnijfilter-ip4700series--3.20-1-i386-deb"

Double click on "packages"

Now we are going to extract the two packages to your desktop:

Click on the first of the two files "cnijfilter-common_3.20-1-i386.deb" then click the "Extract" button at the top.

The file location window pops up. Select Desktop in the left hand pane and hit "Extract" button in the bottom right.

Select the second file "cnijfilter-ip4700series_3.20-1-i386.deb" and extract this to the Desktop in the same way.

Now, we need to go to the terminal screen by clicking on the "Applications" menu and selecting "Accessories->Terminal"

In the terminal type:



then we are going to install the packages but forcing them to ignore the error by typing:



You will be asked for your password. Watch out for all the hyphens and underscore characters!

Now if this works, do the same for the other package by typing:



after this, you can proceed as mentioned in my earlier post by plugging in your printer. I'm afraid I don't have a 64 bit system so I can't test whether this will work. We may find we need to install some other 32 bit support packages first if this doesn't work, so let me know how you get on and we'll take it from there.

Dave

Hello,

this worked for me in 10.10 version.. but now i have the new (11.04) 64 bit

and not working.. it detects the printer normally but it doesn’t print when i give a print order.

---

### Post by asvestomix on 2011-07-04
> **asvestomix said:**
> Hello,

this worked for me in 10.10 version.. but now i have the new (11.04) 64 bit

and not working.. it detects the printer normally but it doesn’t print when i give a print order.
 Any idea on how to make it work?

---

### Post by -Shuji- on 2011-09-24
> **asvestomix said:**
> Any idea on how to make it work?

Asvestomix, I'm on the same boat.  I'm using iP4700 on Ubuntu 11.04 64bit.  I can't even install the drivers even with --force-architecture.  Were you able to fix this or did you just install a virtual XP and setup the printer there?

Shuji

---

### Post by Cimmo on 2011-11-19
This linked worked perfectly for me and Canon ip4700 but I am using Kubuntu 11.10 32 bit and not 64
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

---

### Post by -Shuji- on 2011-11-20
> **Cimmo said:**
> This linked worked perfectly for me and Canon ip4700 but I am using Kubuntu 11.10 32 bit and not 64
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

Cimmo, all I can say is thank you, thank you and THANK YOU.  My Canon iP4700 is now working on Ubuntu 11.10 64bit.  Couldn't have done it without your help.  You're the man!

Shuji

---

