---
title: "Uninstalling/Removing Adobe Air Applications."
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by bhishan on 2009-03-24
How do I uninstall/remove Adobe Air applications?

---

### Post by Partyboi2 on 2009-03-25
Open a terminal and
```
dpkg --list | grep -i <program>
```then to remove
```
sudo dpkg -r <program>
```So for example if the program called bee is installed you would
```
dpkg --list | grep -i bee
```which shows something like
```
ii  com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1 1.2 
```so to uninstall
```
sudo dpkg -r com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1
```

---

### Post by bhishan on 2009-03-25
> **Partyboi2 said:**
> Open a terminal and
```
dpkg --list | grep -i <program>
```then to remove
```
sudo dpkg -r <program>
```So for example if the program called bee is installed you would
```
dpkg --list | grep -i bee
```which shows something like
```
ii  com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1 1.2 
```so to uninstall
```
sudo dpkg -r com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1
```

thanks

---

### Post by Regenerate on 2009-04-19
when I try this (with dpkg --list | grep -i skimmer) nothing happens. What is going wrong?

---

### Post by Partyboi2 on 2009-04-19
Skimmer is installed as fallon
```
dpkg --list | grep -i fallon
```

---

### Post by budhajeewa on 2009-09-07
Thanks, the tip is working !

---

### Post by gaylapdancer on 2009-09-15
I would have picked that Adobe would have provided a control panel or something to remove these apps, but obviously we will never need to uninstall any AIR app. 

Thanks very much for the tip.

---

### Post by Bernard Opic on 2010-03-03
I wrote [Uninstaller for Adobe AIR]("http://blogs.media-tips.com/bernard.opic/uninstaller-for-adobe-air/") to automate this.

---

### Post by dddw on 2010-05-19
> **Bernard Opic said:**
> I wrote [Uninstaller for Adobe AIR]("http://blogs.media-tips.com/bernard.opic/uninstaller-for-adobe-air/") to automate this.

awesome tool, thanks!

---

### Post by buddhaflow on 2010-06-28
This is inexcusably retarded on Adobe's part. What is this nonsense? What if I don't know the name of the program? Absolute Rubbish. Very disappointed in Adobe.

Mr. Opic's package seems to only uninstall AIR itself, not specific AIR programs. Am I using it wrong?

---

### Post by gfe on 2010-09-04
It worked fine for me. When I opened it, it listed not only Adobe Air, but the two AA applications I had installed. I clicked on one of them, and it was deleted fine. I should note that I'm using Adobe Air 2.

---

### Post by casbahdk on 2010-12-26
> **Bernard Opic said:**
> I wrote [Uninstaller for Adobe AIR]("http://blogs.media-tips.com/bernard.opic/uninstaller-for-adobe-air/") to automate this.

I am using LXDE. The app refuses to work if it can't find GNOME or KDE as window manager. Any chance of a work around?

I have also tried **dpkg --list | grep -i prezi**, but it only lists the desktop shortcut, despite that htop lists PreziDesktop3 as residing in /opt Grepping PreziDesktop3 doesn't return anything.

---

### Post by Bernard Opic on 2011-01-14
> **buddhaflow@yahoo.com said:**
> This is inexcusably retarded on Adobe's part. What is this nonsense? What if I don't know the name of the program? Absolute Rubbish. Very disappointed in Adobe.

Mr. Opic's package seems to only uninstall AIR itself, not specific AIR programs. Am I using it wrong?
The new [Uninstaller for Adobe AIR]("http://blogs.media-tips.com/bernard.opic/uninstaller-for-adobe-air/") version 1.1.0 improves installed AIR Applications detection.

---

### Post by casbahdk on 2011-01-26
I discovered that at least in my case, it was possible just to search for the application in Synaptic and uninstall it.

---

### Post by Bernard Opic on 2011-01-26
> **casbahdk said:**
> I discovered that at least in my case, it was possible just to search for the application in Synaptic and uninstall it.
I installed Linux Mint 10, first with Gnome. The application launched but the Adobe AIR runtime was not detected.

I changed the Adobe AIR runtime detection as it is slightly different on Linux Mint.

I added LXDE, and configured it as me default window manager on startup.

I can use the application on Linux Mint.

Here are the download URLs for the 32-bit and 64-bit Debian package files for testing.
[LIST]
[*][32-bit version]("http://blogs.media-tips.com/bernard.opic/downloads/uninstaller-for-adobe-air_1.1.1_i386.deb")
[*][64-bit version]("http://blogs.media-tips.com/bernard.opic/downloads/uninstaller-for-adobe-air_1.1.1_amd64.deb")
[/LIST]
Please let me know if that works also for some of you. If not, I will be interested by a dump of your environment variables.

Best regards,
Bernard Opic

---

### Post by Bernard Opic on 2011-02-10
Hello,

For your information, I published yesterday the version 1.1.1 which adds support for LXDE.

Best Regards,
Bernard Opic

---

### Post by syed.rakib.al.hasan on 2011-05-06
> **bernard opic said:**
> i wrote [uninstaller for adobe air]("http://blogs.media-tips.com/bernard.opic/uninstaller-for-adobe-air/") to automate this.

great stuff!!!!

---

### Post by balta on 2011-05-20
> **Partyboi2 said:**
> Open a terminal and
```
dpkg --list | grep -i <program>
```then to remove
```
sudo dpkg -r <program>
```So for example if the program called bee is installed you would
```
dpkg --list | grep -i bee
```which shows something like
```
ii  com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1 1.2 
```so to uninstall
```
sudo dpkg -r com.adobe.air.samples.bee.419d633a757e8b26dd2bdb301927ba7ba7490f38.1
```

worked perfectly for grooveshark desktop app, adobe is totally retard on this.

thanks

---

### Post by iamxeph on 2011-06-05
> **Bernard Opic said:**
> I installed Linux Mint 10, first with Gnome. The application launched but the Adobe AIR runtime was not detected.

I changed the Adobe AIR runtime detection as it is slightly different on Linux Mint.

I added LXDE, and configured it as me default window manager on startup.

I can use the application on Linux Mint.

Here are the download URLs for the 32-bit and 64-bit Debian package files for testing.
[LIST]
[*][32-bit version]("http://blogs.media-tips.com/bernard.opic/downloads/uninstaller-for-adobe-air_1.1.1_i386.deb")
[*][64-bit version]("http://blogs.media-tips.com/bernard.opic/downloads/uninstaller-for-adobe-air_1.1.1_amd64.deb")
[/LIST]
Please let me know if that works also for some of you. If not, I will be interested by a dump of your environment variables.

Best regards,
Bernard Opic

I tried 64-bit of this and worked great! thank you.

Is there any official ppa or website for the app?

---

### Post by bsulzen on 2011-06-08
Maybe I am missing something here. I went into Ubuntu Software Center (running Natty Narwhal) and then searched for the Adobe Air App I wanted to remove, "geemail" in my situation. Clicked the remove button and the app was removed. Probably does the exact same thing as the command line method in this thread, but this is probably easier for most people

---

### Post by Psimon on 2011-06-25
I tried using the uninstaller but get the following message: "Your desktop environment must be GNOME, KDE or LXDE"

I am using Gnome - any ideas?

---

