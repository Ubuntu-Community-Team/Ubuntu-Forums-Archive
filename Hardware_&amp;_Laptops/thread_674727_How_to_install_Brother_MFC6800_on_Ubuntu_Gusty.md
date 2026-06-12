---
title: "How to install Brother MFC6800 on Ubuntu Gusty"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by iansane on 2008-01-22
When I first tried installing this printer on Ubuntu Gutsy 7.10, I ran into many problems and because of a need to get it installed and not getting answers to my questions about it, I made many mistakes and even had to perform a clean install at one point because I had broken my synaptic and apt-get and therefore could not remove the corrupted partially installed files. If you had similar problems and for what ever reason tried installing lprng and lpr from synaptic, they are not necessary and maybe should be removed to avoid future problems. I installed lpr and it put a real lpd file in the init.d file. I then had to reinstall a couple of the cupsys files. I replied to my own post with this info so I hope not to many people did what I did. This way worked, but it is not the correct way and therefore may not be a permanent solution. It may even cause serious problems that I am not aware of yet. If you did try this way and want to start over and do it right, first remove the mfc6800lpr package because it depends on lpd being there to uninstall correctly. Then you can uninstall the cupswrappermfc6800, lpr and lprng. For the synaptic packages, do a complete removal or it will not remove lpd from the init.d directory. Now that you are ready to do it right in only 4 steps, go to [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) and follow the links for your lpr driver and cupswrapper driver. You will need both. On the cupswrapper download page, notice the note: "to users of drivers with a "*" mark". This is the note about creating a symbolic link that I explain below. Download your drivers and follow the steps below.

Oh, by the way, unplug your printers usb and then go to System>Administration>printing and delete the mfc6800 printer. I also ended up with duplicate printers because I forgot to do this. After completeing all the steps, you can plug in your printer, wait a few seconds and a message will pop out in the top right corner of the screen with an option to configure your new printer. Have the printer console closed when you plug it in or if you click the configure button with the console open already you will have two windows open and end up with duplicate printers again. This is a step by step process and every step must be done in the correct order to avoid any errors and/or annoyances.

First things first. You must understand how symbolic links work because it is a required part of installing this printer. Brother tells us on the cupswrapper download page that lpd must be installed first and for this driver we must create a symbolic link linking "/etc/init.d/cups" or "/etc/init.d/cupsys" to "/etc/init.d/lpd.

This was very misleading for me because I did not fully understand how these links work, the wording is backwards (there is no lpd so how can we link something to it?), and it was on the cupswrapper page instead of the lpr download page as step 1, where it should be.

Step 1. What we want to do is create a symbolic link named "lpd" that is linked to "cups" or "cupsys". They did get the command right. It just didn't make sense to me until I created some links on my desktop to figure it out. So for the first step, go to the directory, "/etc/init.d" and see if you have cups or cupsys. There will be a file called cups or cupsys. If your using Ubuntu 7.10, it should be cupsys. Now open a terminal and type.

```
 sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd 
```

If you have cups, replace the word cupsys with cups. This has created a link called lpd in the init.d directory. The link directs the mfc6800lpr post install scripts to cupsys, but it thinks it is going to lpd. It's a trick, but it works.  (no more error, "lpd not found") All it is doing is stopping and restarting your printing service for the install.

Step 2. Now your NOT ready to start installing yet. If you do you will get "no such directory" errors for "/var/spool/lpd/MFC6800". Go ahead and create the following two directories. (lpd and MFC6800). I assume the MFC6800 is case sensitive.

```
 sudo mkdir /var/spool/lpd 
```
```
 sudo mkdir /var/spool/lpd/MFC6800 
```

Step 3. Now you can cd to the directory where you downloaded the two driver files. I renamed mine first to cut down on typing. Mine are "mfcCupsWrapper.deb" and "mfcLpr.deb". Either rename yours accordingly or replace my names with the correct names in the following commands. Be sure to install the lpr package first.

```
 sudo dpkg -i --force-all mfcLpr.deb 
```

Verify that you don't get any errors. The output will be something like "stopping common unix print system, installing mfc6800lpr, starting common unix print system. If you get an error you may want to stop here and ask someone on the forum before proceeding.

Step 4. Now if the lpr driver installed without error, you can install the cupswrapper package.

```
 sudo dpkg -i --force-all mfcCupsWrapper.deb 
```

Similarly, the output will say something like "stopping common unix print system, installing cupswrappermfc6800, starting common unix print system".

Step 5. One more thing. After booting up the next day, I had to go to System>Administration>Services and check the boxes next to the cups and lpd printer services. 

I hope this How-to helps clear up some problems for those of you who struggled with this as I did. I would appreciate if the forum admin, moderators, and anyone else knowlegeable on the subject would correct any errors you find and post any additional information. This is my first attempt at giving back to the Ubuntu community.

---

### Post by K.Mandla on 2008-01-22
Moved to Hardware and Laptops.

---

### Post by zeiz on 2008-01-28
I have the same problems with the same "brother". It's just hard to believe that I could find your post - exactly what I need! Thank you very much.
I am complete newbie in Linux and stuff like "symbolic link" is like Chinese roll to me. I used to find something but that was just couple of words at "guru" level and I had to leard Linux first to understand that advice. Your post is just what I need! Thank you very much for taking your time and writing the detailed instructions.

I assume that mfc6800's scanner installation is the same as cupwraps (after lpr)?

Thanks and regards,

---

### Post by iansane on 2008-03-14
Sorry I didn't think to check if anyone replied to this so it's a little late but yes the scanner driver and scan key driver installed as is, for me after this just like any other .deb package. No errors

---

### Post by gnidargpu on 2008-03-28
Thank you for your excellent guidnance for mfc6800.  I now have a working mfc.  Downloading the two drivers, and checking save to disk, put them on my desktop. Would not install from desktop using the guidance in your post.   Guidance from a friend worked, however. This was to make a new folder in both Home (user id folder name) directory and the Root directory.  Drag the two desktop icon files  to the new folder in the Home folder.  Then in terminal mode, and using the dir command, verify existance of the two new folders and the correct path to them.  Then enter cd /root. Then enter sudo mv /home/(user name)/(name of new folder)/(icon file name) /(new folder name in root)  Do this for both icons.  Verify that the files are now in the desired folders.  Then continue following directions in step three of your guidance.  I hope I remembered the steps correctly.  Perhaps you know a simpler way to get the files from the desk top to where they can be installed. Thanks for your great help.

---

