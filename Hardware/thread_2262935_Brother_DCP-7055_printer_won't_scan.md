---
title: "Brother DCP-7055 printer won't scan"
date: 2015-01-28
forum: Hardware
---

### Post by ckrles on 2015-01-28
Hi, everybody. I have a problem with my multifunction printer Brother DCP-7055 and Xubuntu 14.0.1. I can print, but I CANNOT scan. When I use the app simple scan, it says that the scanner is not detected, even though in the options it actually appears. Later on, I tried to open simple scan as root with the command sudo simple-scan. It appears as detected, but it doesn't work. After opening it as a root I noticed another problem which is: when I open again simple-scan (not as root) the scanner doesn't even appear. Reinstalling simplescan didn't bring back the detected but non-working scanner. Now it can only detect the scanner (after a few seconds) when simplescan is opened as root, but it keeps not working.

I downloaded their Driver Install Tool from their website and followed their instructions and the installation reported successful.

Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)
 The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download
 Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.
 Step3. Enter this command to extract the downloaded file:
 **Command: gunzip linux-brprinter-installer-*.*.*-*.gz**
 Step4. Get superuser authorization with the "**su**" command or "**sudo su**" command.
 Step5. Run the tool:
 **Command: bash linux-brprinter-installer-*.*.*-* Brother machine name **
 Step6. The driver installation will start. Follow the installation screen directions. 
 
 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)
For Network Users: Choose Y(Yes) and DeviceURI.

 The install process may take some time. Please wait until it is complete.



I don't know where the problem is. I talked to brother support and they didn't help me. I followed their installation guide.

I'm pretty sure the problem is not with Xubuntu 14.04 (I have it fully updated). I had the same problem with ubuntu 14.04 based distros Linux Mint 17 KDE and Zorin 9. It was detected, but it didn't work. I also asked for help in Mint's forums, but no luck.

However, last year I was using Zorin 6 (based on Ubuntu 12.04) and both the printer and scanner worked perfectly.

Could you, please suggest any solutions?

---

### Post by JeQhdMD on 2015-01-28
[https://github.com/pdewacht/brlaser](https://github.com/pdewacht/brlaser)

Uninstall all current printer drivers and delete/remove the printer, then install the above and re-add your printer.   This driver is supposed to work with your printer model.

---

### Post by ckrles on 2015-01-28
> **JeQhdMD said:**
> [https://github.com/pdewacht/brlaser](https://github.com/pdewacht/brlaser)

Uninstall all current printer drivers and delete/remove the printer, then install the above and re-add your printer.   This driver is supposed to work with your printer model.

 Thank you for your help. I'm kind of a newbie on linux. I don't know how to uninstall/remove the driver. Can I simply install this driver without deleting the official brother one and then add a new printer selecting the new driver? I mean, going to the printer settings, and adding a new printer and choosing this driver.

I just had a quick loot at the zip file and I honestly have no idea about how to install it. I'm kind of a newbie. I just see a lot of files. Could you help me please?

Thank you.

---

### Post by JeQhdMD on 2015-01-28
Well, this is an example of a driver that's not packaged for ubuntu . . or source code that has to be compiled for your kernel.   I haven't done any compiling since retiring from IT 5 years ago, but after looking at these files, you need to do a few things:

1)  Check your installed software for the package "build-essential" (in case it's required . . . may not be in this case.) . . . it is often installed as part of the ubuntu base.
2)  There is usually a read-me file that gives instructions how to do the install (e.g., how to build the package).  It's often a script file, that triggers the install file.   In this case, the script file is "autogen.sh"
3)  Download the whole repo (repository) as a zip file (see the button on right of repo "Download Zip".  
4)  The zip file will be in your "home>downloads" folder
5)  Unzip the file (right click it in files manager) and select "extract here"
6)  Right click the file autogen.sh and check that it is "executable" (open the properties dialog window and check the "permissions" tab (ensure the checkbox that says "allow executing file . . . " is checked) (it should be)
7) Run the script in a terminal window by opening a terminal window (ctrl+alt+t) and then change to the directory where the script file is (cd /path-to-your-folder)
8) When you're in the downloads (or wherever the file is) . . you can execute the script by typing "sudo ./autogen.sh . . . enter your password and hopefully the developer has set up this script so it generates the install build for your system.

Re uninstalling the current drivers . . . normally is done via Synaptic (install it and do a search for the driver name . . you then highlight the file and right click it to get uninstall options . . . click apply and you're done)

One final suggestion - - as I'm pretty rusty on building  programs (was not my main focus in job) . . you may want to have a moderator move this thread to the developers forum where more people familiar with the terminal and can add their input on the install process and code . . but this should help get you started. 

  Note, normally, the epson and hp printers are MUCH easier to install on linux machines as there are specific "deb" files that really simplify the install process.   Epson "Workforce" printers are my personal favorites.

---

### Post by ckrles on 2015-01-29
_[Thank you very much, ]("http://ubuntuforums.org/member.php?u=1841810")_[[COLOR=#000000]JeQhdMD[/COLOR]]("http://ubuntuforums.org/member.php?u=1841810"), I'll give it a try to install and compiled it. Unfortunately, as I said before, I'm kind of a newbie. I'll do my best, but I may bother you with some other doubts which appear during the process.

I didn't find "build-essential" in my system (xubuntu 14.04 lts), but I found "build-essential-packages". I guess they're the same, but I'm not sure. Are they?

I have a doubt. What do you mean by *"Re uninstalling the current drivers . . . normally is done via Synaptic  (install it and do a search for the driver name . . you then highlight  the file and right click it to get uninstall options . . . click apply  and you're done)"* Are you refering to Brother's official drivers? I thought I wouldn't need to remove them (i don't know how), but just to install and choose the new driver when adding a new printer. Could I do that?

I think your suggestion about asking a moderator to move the thread to the developer's section is ok. Shall I ask them? Or will they simply do? I don't know.

Thank you very much.

---

### Post by plucky on 2015-01-29
> Could you, please suggest any solutions? 

I have found with the installer script that you need **tcsh** and **csh** installed before you run the script or else the scanner drivers do not install properly.Also you need to install **sane-utils**
```
sudo apt-get install tcsh csh sane-utils
```

Then run the installer script and reboot.

Good Luck

---

### Post by JeQhdMD on 2015-01-29
Thanks Plucky!   Glad you tested the script . . . . 

ckrles,

Good input above from Plucky.   Re your questions  . . . you may not need to uninstall the drivers from Brother.   Sometimes it's cleaner that way (easier to debug) . . as building a driver is more prone to errors and dependency feedback.   But leave those as you put some work into that install.

The build-essential and build-essential-packages are the same, . . . they are the other apps (linkers, compilers, etc.) that are needed to "build" packages.   Even ms-windows developers use similar tools before they add the nice "install-wrappers" around the exe's (so users never have to venture out of "user-space").   Anyway - - I think you're ready to run the script, just make sure you're in the right folder/directory so the script can access the other files it needs.   If you get error feedback, be sure to report back on the error code.

---

### Post by Mitch_Harris on 2015-01-30
> **plucky said:**
> I have found with the installer script that you need **tcsh** and **csh** installed before you run the script or else the scanner drivers do not install properly.Also you need to install **sane-utils**
```
sudo apt-get install tcsh csh sane-utils
```

Then run the installer script and reboot.

Good Luck

Spent the better part of today trying to get the scanning portion of a Brother laser printer to work. At the last moment of patience for the day  I read your post. Installing both csh and tcsh together did the trick contra Brother documentation. Some sort of minor miracle. Thanks.

---

### Post by plucky on 2015-01-30
> Spent the better part of today trying to get the scanning portion of a Brother laser printer to work. At the last moment of patience for the day I read your post. Installing both csh and tcsh together did the trick contra Brother documentation. Some sort of minor miracle. Thanks. 

What is the model number of your Brother printer?

It might help someone else who is searching for the same printer.

And I am also looking to purchase an All-in-one laser printer.

---

### Post by Mitch_Harris on 2015-01-30
> **plucky said:**
> What is the model number of your Brother printer?




brother HL-2280DW 

Perhaps the least expensive printing solution avaliable. Purchased last year, I struggled with the scan option then as well. Mashing the instructions repeatedly eventually obtained the scanning function but I didn't understand why. On a reinstall it was back to the same problem. Clearly the solution was found in your tip. In addition to changing 'or' to 'and' for tcsh and csh in the documentation they should add inputting brscan-skey to start-up. I don't think it mentions that on the install instructions.

Thanks again, saved loads of frustration.

---

### Post by ckrles on 2015-01-30
It works on a laptop as root with simple scan, but not as regular user.  However, I can't mak it work in another computer with the same  configuration.

Edit:On the other computer I can only make it work xsane in root mode (not working with root in simple-scan), however, on the first attempt to scan xsane returns "Invalid argument" If I try to run it in NON-root mode it also returns "Invalid argument".

---

### Post by ckrles on 2015-01-30
I can't figure it out. I can't install the scrpt using your instructions. In Xubuntu 14.04 I go to the folder where the script is and I right-click open terminal here, then I try to run the script with sudo ./autogen.sh as you old me and it doesn't work. It reports 

./autogen.sh: 9  ./autogen.sh:   autoreconf: not found


I can't find instructions inside the readme file and other files,

---

### Post by ckrles on 2015-01-30
Xsane opens as root. I get a warning in capital letters indicating that  it is dangerous. Is it really dangerous to open it as root? Or the  system is simply being cautious (I'n surprised I don't get that warning  with simple scan when in root)

This is my current status:

Both  the laptop and the desktop can use the scanner with xsane, but ONLY as  root (warning message pops up, is it that dangerous????) I would like to  be able to run xsane as normal user. The points is that it is my wife  desktop at work. I don't want to mess to much with it, that's why I try  solutions and suggestions on my laptop first. Her knoledge about linux  is even lower than mine, so I'd like to avoid her using the terminal,  specially if danger warning appear. Another thing is that I find simple  scan interface easier, so I'd rather have it work than xsane (if  possible).

Sorry guys. I guess I probably ask to much, so thank you very much to all those who can provide a solution.

---

### Post by Mitch_Harris on 2015-01-30
Hi ckrles,

If you go back to the Brothers driver download page. On the install script download page, there is a section called "Read before Downloading" and then "Notes before Downloading" and finally a link to "Before the installation." On this last page, there are number of preliminary steps before installation. Have you already created those folders and installed those driver/utilities they suggest?

---

### Post by ckrles on 2015-01-30
To be honest, I didn't notice it. But a few months ago when I was using linux mint 17 kde I remember goig through those steps and being unsuccessful. I'll give a try again this time to see if it works.

Thank you very much.

---

### Post by Mitch_Harris on 2015-01-30
per plucky's instruction if it asks to install tcsh or csh, install both.

---

### Post by JeQhdMD on 2015-02-01
Try to install the script from Terminal window again . . . navigate to the script directory (where you downloaded and then expanded the file(s)).

Then do:  [B]sh ./name_of_file.sh.  (if this doesn't work, precede the sh with sudo (but you shouldn't need it as you're in your home directory tree)

More info in thread below . . important to be in the right folder.

[/B][http://askubuntu.com/questions/122428/how-to-run-sh-file](http://askubuntu.com/questions/122428/how-to-run-sh-file)

note:   you might try to move the script along with the other support folders/files into your /home/bin folder.   If it doesn't exist, create it (just use files program to do).   Then, do a system restart (boot) and try the script commands above again.  Make sure the file is executable, and that you are the owner.   Remember there are at least 15 ways to do the same thing in Linux . . . use google till you find the right answer (although, if the script was obtained from the official  GIT HUB . . . it should work period.)

---

### Post by pdc on 2015-02-01
Hi ckrles; .............sounds like it is all getting frustrating and difficult; time to pull the hair out; 

________________

Brother provide instructions [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

and for Ubuntu, [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) there is a very small file that you download as a debian package; as ubuntu uses debian; and it should be magic dust and make things work

_______________

the above link lists the file [SIZE=4][COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR][/SIZE], ver.1.0.0-1 and if you click to download it your system should ask if you want to save or open it; open it is another way of saying INSTALL so if you take that option; install; then reboot: any joy? (Hopefully, lots of joy!!)

---

### Post by mollie4168 on 2015-03-10
Just wanted to say thanks JeQhdMD for posting the github link.  I've gotten my Brother DCP7065SN working in the past through the information on Brother's website + forum help for the scanner (as others posted here), but that link was abundantly easier.  However, the readme file does not have instructions.  It took some trial and error and googling, but I was missing the CUPS development driver, so I installed that (libcups2-dev), ran sudo ./autogen.sh, and then added the printer from the printer menu.  I didn't have to do anything extra for the scanner.  Even with my missteps, it was way easier than before.  Thanks!

---

