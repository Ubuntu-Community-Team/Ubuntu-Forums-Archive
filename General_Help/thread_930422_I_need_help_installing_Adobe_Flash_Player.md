---
title: "I need help installing Adobe Flash Player"
date: 2008-09-26
forum: General Help
---

### Post by Superman 160703 on 2008-09-26
Hi im new to linux completely, I know probably as much as a monkey except basic stuff i just switched from windows. I need help installing Adobe Flash Player onto my computer. I followed the steps as adobe told me to 

       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

but during step 4 i ran into a small problem in the terminal it told me this 
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/superman/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/home/superman/Desktop/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

so i did what it said to do i went threw to the Mozilla file and deleted the xpti.dat file and tried reinstalling adobe flash player again... yet again i got the same message and i did find one thread that could help me but it was in the archive with no answer to it :(. So anyone out there with more brains in this stuff then me that could help me out. Any help is greatly appreciated i'm realy lost as what to do...

Thanks for your time
Superman


o yea  im not quite sure if im on just regular ubuntu or not XD ik thats not much of a help either

---

### Post by aysiu on 2008-09-26
Don't follow Adobe's steps. Follow these steps:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by Superman 160703 on 2008-09-26
yea it doesn't give me that little thing on the top i've been to youtube a million time already

---

### Post by jimmy the saint on 2008-09-26
open a terminal and type in 
```
 sudo apt-get install ubuntu-restricted-extras 
```

this will give you flash and a few extras like some better fonts, mp3 support and so on.  if you use another ubuntu varient (Xubuntu or Kubuntu) replace "ubuntu" with the one you use.  
Easy as pie!

---

### Post by Superman 160703 on 2008-09-26
right i did that and it got me to a menu where i had to hit enter terms of use stuff then i continued to a scroll down page where it wouldnt let me continue and i got fustrated and exited it then tried to redo it and it wont let me :( it says

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by jake1017 on 2008-09-26
The way I get flash is:
1. Go into Add/Remove Applications
2. Search for Flash (make sure "All available application" is selected)
3. Check "Macromedia Flash plugin" to be installed
4. Click "Apply Changes"
5. Wait until it finishes installing and then enjoy the wonders of flash

Hope this helps

---

### Post by Superman 160703 on 2008-09-26
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.


i got this message... help help help lol please

---

### Post by aysiu on 2008-09-26
> **Superman 160703 said:**
> Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.


i got this message... help help help lol please
As the message already tells you, you have another package management application already running.

If you have any of these applications open right now, close them:
Add/Remove Applications
Synaptic Package Manager
Adept Package Manager
Update Manager

Once you're done with that, close your web browser, and paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by Superman 160703 on 2008-09-26
i did that and i got

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Sycron on 2008-09-26
make sure that you have synaptic closed when you're doing that.

---

### Post by gjoellee on 2008-09-26
> **Superman 160703 said:**
> Hi im new to linux completely, I know probably as much as a monkey except basic stuff i just switched from windows. I need help installing Adobe Flash Player onto my computer. I followed the steps as adobe told me to 

       1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

but during step 4 i ran into a small problem in the terminal it told me this 
----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/superman/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `/home/superman/Desktop/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

so i did what it said to do i went threw to the Mozilla file and deleted the xpti.dat file and tried reinstalling adobe flash player again... yet again i got the same message and i did find one thread that could help me but it was in the archive with no answer to it :(. So anyone out there with more brains in this stuff then me that could help me out. Any help is greatly appreciated i'm realy lost as what to do...

Thanks for your time
Superman


o yea  im not quite sure if im on just regular ubuntu or not XD ik thats not much of a help either

You are doing it the hard way! Download a .deb file from my homepage: [http://kshoster.net/v2/?c=downloads&x=deb](http://kshoster.net/v2/?c=downloads&x=deb)

---

### Post by jimmy the saint on 2008-09-26
To download your .deb, he needs to navigate to your site, download it, run it, decide if he is going too keep it or discard it, then store it if he wants to keep it.  In addittion, his problem is that he is running more than one package manager at once, a problem that will not go away by downloading your .deb.  Finally,no offense, but I think it is probably wisest to trust the repositories than a .deb form outside.  

Just my thoughts.

---

### Post by Sycron on 2008-09-27
Well, it works ?

---

