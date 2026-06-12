---
title: "livecd with installation option"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2009-11-10
Hi all,
 
I have created a customized Karmic LiveCD ... and I want to make it installable as well.
 
I have the isolinux.cfg as:
 
============================
[INDENT]*default live*
 
*label live*
*menu label ^Try Ubuntu without any change to your computer*
*kernel /casper/vmlinuz*
*append file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --*
 
*label install*
*menu label ^Install Ubuntu*
*kernel /casper/vmlinuz*
*append file=/cdrom/preseed/ubuntu.seed boot=casper **only-ubiquity **initrd=/casper/initrd.gz quiet splash --*
 
*label memtest*
*menu label Test ^memory*
*kernel /install/memtest*
 
*DISPLAY isolinux.txt*
*TIMEOUT 300*
*PROMPT 1*
initrd=/casper/initrd.gz quiet splash --
[/INDENT]===========================
 
When I booted the LiveCD with live option (boot: live ) .. everything was working as it was created. But when I booted with option install at boot prompt .. (boot: install) .. it booted as with option live (it went to live system), and did not go to installation procedure. I have installed ubiquity on before creating the filesystem.squashs file.
 
I am not sure what I was missing or what I have configured wrong ?
 
Any suggestion where I should look at ?
 
Thanks in advance, 
 
Dang

---

### Post by uonedang on 2009-11-12
I think that the problem is at the file: filesystem.squashfs which does not go to installation mode when the system boots up with option only-ubiquity ... If that is correct, what do I need to do, what packages or any configuration needed,   when I build the filesystem.squashfs? 

Any suggestion is appreciated ...

Thanks

Dang

---

### Post by uonedang on 2009-11-16
Hi all,

After installing the xfce4, it worked ... I will need to use fvwm for the system ...

Is there any way that I can configure the ubiquity to work with fvwm or fvwm-crystal?

Thanks,

Dang.

---

### Post by srinivaz_n on 2009-11-19
Hi,
 
 
You said that you got it working after installing "xfce4"
 
can you give me details , how you did the complete thing.
even, i am trying to make the live cd installable ...
 
 
regards,
Nivaz

---

### Post by uonedang on 2009-11-20
Hi srinivaz_n,

I eventually got it work  .... 

I installed the gdm and gdm-guest-session, ubuqity, fvwm ... and disable/remove the gnome desktop environment ... (this is for my purpose of using the fvwm window manager instead of other wm or desktop environment).

Thanks,

Dang

---

### Post by srinivaz_n on 2009-11-22
ok,

u mean to say that ,while customizing the required packages for live cd...u installed the above mentioned things and u have the config file as deined above and the install option worked for u...

and... even i dont want the UI part. i want to remove the ui component and i just want to get the live cd installable from command line....

---

### Post by uonedang on 2009-11-23
Hi srinivaz_n,
 
what i have allows me to enter "install" option from command line at "boot:" prompt when the box is booted with this media, and i am not running live session yet ....
 
I am not sure what your requirement is .. if you can elaborate more ...
 
Thanks,
 
Dang

---

### Post by srinivaz_n on 2009-11-23
Hi,
 
 
 
Yah, i dont need any desktop environment, and as well i just want the command line interface only [like the DOS]
 
So, you said that you are able to go to "install" mode during boot session. And after that, is it really installing / any problems occured ?
 
So, can you give me a sequence of steps , you followed for making it to enter "install" mode during boot session. 
 
And in my case, the following error occurs:
 
can't open file */cdrom/preseed/ubuntu.seed  `no such file or directory*
 
*can you let me know, how are you creating this preseed file ??*
 
 
*Regards,*
*-Srinivas*

---

### Post by uonedang on 2009-11-24
srinivaz_n,

I use window manager  ... but I am using only the light fvwm  .... If you want .. you can build the iso with window manager ... but you do not include that for the installation ... 
by excluding these packages from casper/filesystem.manifest-desktop file.

I guess that I have the same problem as you at the moment ... I have the preseed file
defined as you mentioned in your post .. but it does not seem to have effect .. and I did not see the complain about missing preseed file ... The installation process is just executed with manual request for input ...  I am not sure where it went wrong or what I have configured wrong ... 

I have include the preseed/ubuntu.seed in the iso ... 

How to write preseed file can be found at: 

[https://help.ubuntu.com/9.10/installation-guide/amd64/preseed-contents.html](https://help.ubuntu.com/9.10/installation-guide/amd64/preseed-contents.html)

I am still looking at getting the preseed file  affective for the installation process 

Thanks

Dang

---

### Post by srinivaz_n on 2009-11-25
ok,
 
Thanks for the info,
 
and ,,...
 
i have installed ubiquity on my target cd , while creating the live cd.
 
and then when i enter "install" mode, it enters to the live-cd mode,...
 
thats fine, and when i am trying to run "ubiquity --only" from the live mode,
 
the /var/log/installer/debug file shows me following errors:
 
 
 
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 457, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 442, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 241, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 261, in __init__
    self.locale = i18n.reset_locale()
 
NameError: global name 'i18n' is not defined.

---

### Post by uonedang on 2009-11-25
hi srinivaz_n

I am not sure about this .. because i used ubiquity-frontend-gtk instead of ubiquity-frontend-kde. I think that you need a desktop environment installed to get around this problem ... and this desktop environment can be removed after the installation is done by excluding these packages in the *casper/filesystem.manifest-desktop* file.

I used light window managers/desktop environments (fvwm, xfce4 or metacity, and I guess any x-window-manager), and the ubiquity would work when it is run from the live CD.  Please correct me here if I am incorrect here ... 

I have several issues when I tried to install from boot prompt:

1) install selected ==> live CD: this problem was resolved be adding either xfce4 or metacity (fvwm does not work when install from boot prompt .. not sure why ). I do not know exactly what are the only necessary packages needed ....  If any one knows .. please post and it would help to simplify the packages.

2) To make the preseed file affective, replace only-ubiquity with automatic-ubiquity in the isolinux.cfg file.

3) I still have problem unresolved ... the installation hangs when it is doing the installation .. (I posted on the other thread [ubiquity installation hang]("http://ubuntuforums.org/showthread.php?t=1336411") ) .. and I am currently working on it ... I guess there is something wrong with my pre-seed file 
itself.


Thanks

Dang

---

