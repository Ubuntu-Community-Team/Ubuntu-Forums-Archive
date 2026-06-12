---
title: "Cannot boot ubuntu 8.10 login session is no longer valid"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by alibaba163 on 2009-04-09
HI Guys,
        I am considerably newbie to ubuntu but and old windows programmer. I am working on kdevelop, gtk, gtkmm.

Just for testing purposes I removed libglade* by using following command.

sudo apt-get remove libglade*

later on when I resumed it using

sudo apt-get install libglade* 
It installed successfully BUT my firefox was not working. It was throwing assertion failure message when I was trying to browse any website.

I thought I would give a restart to my machine (ubuntu 8.10) and it would be fine but when I restarted it. I could'nt boot my machine. 

During booting phase, one of the messages in black screen says.

"fsck died with exit 3                  [fail]"

and then the login screen is different color(greyish) than the normal login window for gnome.

Also when I try to login it say that "CURRENT LOGIN SESSION IS NOT VALID ANYMORE" (with greyish login screen having username and password prompt) and following login session at the bottom

1. Default
2. KDE
3. GNOME.


Now when I pop-in my username and password it just gives me black and colored screen (containing different colored character) and then system freezes on that screen.


ANY HELP WOULD BE REALLY APPRECIATED!!!

Regards,

Alibaba.

---

### Post by alibaba163 on 2009-04-09
HI Guys,
        I am considerably newbie to ubuntu but and old windows programmer. I am working on kdevelop, gtk, gtkmm.

Just for testing purposes I removed libglade* by using following command.

sudo apt-get remove libglade*

later on when I resumed it using

sudo apt-get install libglade* it installed successfully BUT
my firfox was not workinging. It was throwing assertion failure message when I was trying to browse any webside.

I thought I would give a restart to my machine (ubuntu 8.10) and it would be fine but when I restarted it. I could'nt boot my machine. 

During booting phase, one of the messages in black screen says.

"fsck died with exit 3                  [fail]"

and then the login screen is different color than the normal login window for gnome.

Also when I try to login it say that "CURRENT LOGIN SESSION IS NOT VALID ANYMORE" (with greyish login screen having username and password prompt) and following login session at the botton

1. Default
2. KDE
3. GNOME.


Now when I pop-in my username and password it just gives me black and colored screen (containing different character) and that system freezes on that screen.


ANY HELP WOULD BE REALLY APPRECIATED!!!

Regards,

Alibaba.

---

### Post by alibaba163 on 2009-04-09
HI Guys,
        I am considerably newbie to ubuntu but and old windows programmer. I am working on kdevelop, gtk, gtkmm.

Just for testing purposes I removed libglade* by using following command.

sudo apt-get remove libglade*

later on when I resumed it using

sudo apt-get install libglade* it installed successfully BUT
my firfox was not workinging. It was throwing assertion failure message when I was trying to browse any webside.

I thought I would give a restart to my machine (ubuntu 8.10) and it would be fine but when I restarted it. I could'nt boot my machine. 

During booting phase, one of the messages in black screen says.

"fsck died with exit 3                  [fail]"

and then the login screen is different color than the normal login window for gnome.

Also when I try to login it say that "CURRENT LOGIN SESSION IS NOT VALID ANYMORE" (with greyish login screen having username and password prompt) and following login session at the botton

1. Default
2. KDE
3. GNOME.


Now when I pop-in my username and password it just gives me black and colored screen (containing different character) and that system freezes on that screen.


ANY HELP WOULD BE REALLY APPRECIATED!!!

Regards,

Alibaba.

---

### Post by LowSky on 2009-04-09
sudo apt-get remove libglade* also uninstalled all of the packages associated with it. when you remove all of them it could lead to this failure.

try booting to recovery mode and using the command

sudo apt-get install ubuntu-desktop

that might reinstall other packages that were removed.

you might also have to recreate a user account


if that is the case it might be better to do a reinstall (with no formating) to regain a function user account

---

### Post by alibaba163 on 2009-04-09
Can anyone Reply to my thread please!!!!!!

Thanks

---

### Post by dwhitney67 on 2009-04-09
You must have done something more than just remove libglade; perhaps you removed something (important) that depended on libglade.

The other possibility is that the HDD is failing, or has bad sectors.

If I were in your situation, I would just reinstall Ubuntu.  Hopefully you placed your /home directory into a separate partition that can be preserved.

---

### Post by alibaba163 on 2009-04-09
HI Guys,
        I am considerably newbie to ubuntu but and old windows programmer. I am working on kdevelop, gtk, gtkmm.

Just for testing purposes I removed libglade* by using following command.

sudo apt-get remove libglade*

later on when I resumed it using

sudo apt-get install libglade* it installed successfully BUT
my firfox was not workinging. It was throwing assertion failure message when I was trying to browse any webside.

I thought I would give a restart to my machine (ubuntu 8.10) and it would be fine but when I restarted it. I could'nt boot my machine. 

During booting phase, one of the messages in black screen says.

"fsck died with exit 3                  [fail]"

and then the login screen is different color than the normal login window for gnome.

Also when I try to login it say that "CURRENT LOGIN SESSION IS NOT VALID ANYMORE" (with greyish login screen having username and password prompt) and following login session at the botton

1. Default
2. KDE
3. GNOME.


Now when I pop-in my username and password it just gives me black and colored screen (containing different character) and that system freezes on that screen.


ANY HELP WOULD BE REALLY APPRECIATED!!!

Regards,

Alibaba.

---

### Post by Frank Kotler on 2009-04-09
You young people are so impatient! :)

According to "man fsck" error 3 would indicate (the sum of):

1 - File system errors have been corrected

2 - System should be rebooted

Sounds like that's what *started* the problem, though. I can't imagine why doing a remove/install with apt-get should have done that to your system, but if it did, it did.

If you haven't got too many "personal files" on the system, I'd just reinstall. If you *do* have stuff you don't want to lose, perhaps boot to liveCD and transfer your files - don't forget address book and bookmarks, if you want 'em... perhaps to a USB stick... *then* reinstall from scratch.

We're not supposed to have to do that in Linux!!!

If you can log in as root, go to "single user mode", unmount the drive in question, and run fsck from there, it might help. I don't think "sudo" will work...

Sorry not to be able to offer more help, but hey, you asked for a reply! :)

Seriously, best of luck with it!

Best,
Frank

---

### Post by bapoumba on 2009-04-09
Moved to Installation & Upgrades.

When you removed the packages, did you also remove a lot of dependencies?
You can boot in recovery mode (at grub menu, hit escape to show grub menu if necessary), you'll be root after login. This is a text mode session (no X).
Make sure you have central packages such as ubuntu-desktop installed:
```
apt-cache show ubuntu-desktop
```

---

### Post by bapoumba on 2009-04-09
Merged 3 other threads in here.. Please _do not_ start multiple threads on the same subject, it is not going to help.

---

