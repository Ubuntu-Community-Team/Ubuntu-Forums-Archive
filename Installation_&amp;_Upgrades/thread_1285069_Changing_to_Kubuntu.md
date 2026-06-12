---
title: "Changing to Kubuntu"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by AVHATION on 2009-10-07
I am running Ubuntu 8.04 (Hardy Heron). I have installed KMyMoney0.8.8 but  to get it work properly I think I need the KDE desktop.  Therefore I plan to use Kubuntu.  If I simply install Kubuntu will I lose all my existing Evolution Mail, Firefox bookmarks, and the various driver connections and virtual WinXP I have made with Ubuntu? Can I choose whether to start up with Ubuntu or Kubuntu if I wish?

---

### Post by ken_ver_2.5 on 2009-10-07
I may be wrong and I am sure I will be corrected. you can just install kde
from the package manager and log in to the kde desktop.
at least thats what I did in ubuntu 9.04

---

### Post by Bucky Ball on 2009-10-07
kde4 actually and yes, at the login screen choose 'Sessions' and KDE.

```
kde4-core
```

.... in Synaptics should do it.

---

### Post by Ms_Angel_D on 2009-10-07
What are the issues your having with kmymoney, you shouldn't need the whole of kde to run it? I ran it fine in the past without kde.

---

### Post by Hei Ku on 2009-10-09
You can run KMyMoney just fine without installing the whole KDE desktop. However, version 0.8.8 is very old, about 3 years old. You should install version 1.0.1 or 1.0.2.

There is a PPA available at: [https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

---

### Post by AVHATION on 2009-10-10
Thank you everyone for the advice above. In answer to Ms Angel D, the issue I have is that the tool for listing securities and then updating their prices seems not to work.

---

### Post by AVHATION on 2009-10-10
I have now added kde4-core (some 64 packages), with no apparent change to the desk top appearance, and the KMyMoney 0.8.8 security listing and share price updating tool does not work. How may I upgrade to KMyMoney 1.01 or 1.02 without losing the data I have entered into 0.8.8 please?

---

### Post by borahshadow on 2009-10-10
Just make sure that you export and backup your data and then upgrade with that ppa that was posted above. There are plenty of guides to help with PPA use. Just google it and you should be fine. Granted I've never done that but I don't see why it won't work unless the file format was changed from .8 to 1.0. If that was the case you could always go back to .8 and import that data that you exported.

If you want to install kubuntu then the proper thing to do is to install kubuntu-desktop from synaptic. then if you want to boot into kubuntu when you are at the login screen there should be an option somewhere to select KDE. You will be able to switch between KDE and GNOME by logging out and selecting the other one. Keep in mind that having both KDE and GNOME (Ubuntu and Kubuntu) will use more disk space. 

Also there should be no problem running Gnome applications in KDE (evolution etc) and KDE applications in Gnome (KMyMoney, amarok, kontact, etc) just a little bit more memory usage.

---

### Post by Hei Ku on 2009-10-10
The file format has changed, but the new version takes care of that. As usual, a backup is in order before running the new version.

---

### Post by AVHATION on 2009-10-11
Thanks again to all. I have  backed up KMyMoney on a memory stick. I have successfully added KDE-4 core and can use the KDE desktop. However, there is no change in the KMyMoney functions  of security list editor and price updating using either of the desktops. I have tried to follow the PPA link above but both Ubuntu and KDE desktops will not let me add the new third party source (step one:  button is greyed out). I have also  downloaded KMyMoney 1.0.2 but have not yet worked out how to install same. Any further ideas please?

---

### Post by Hei Ku on 2009-10-11
To add the PPA you have to start the package manager as superuser, that way it will not be grayed out.

---

### Post by AVHATION on 2009-10-12
Sorry to be so dim, but should I use Gnome or KDE desktop for this or does it not matter?  Also, how do I start package manager (Synaptic?) in superuser mode please? I am already the sole user and have the administrator privilege, but the option to add another third party source is greyed out.

---

### Post by borahshadow on 2009-10-17
when you open up synaptic (from the menu) does it ask you for a password? if it does then it is being opened in superuser mode. If it does not then something is wrong.

if you want to do it this way you can just open up a terminal (command prompt) and type(or copy) these one line at a time into that terminal
NOTE: I tested this on my system but I make no guarantees.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

sudo su

echo deb http://ppa.launchpad.net/claydoh/ppa/ubuntu hardy main >> /etc/apt/sources.list

echo deb-src http://ppa.launchpad.net/claydoh/ppa/ubuntu hardy main >> /etc/apt/sources.list

exit

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D09DE175

sudo apt-get update

```

You can then go into synaptic and mark all upgrades or you can do a ```

sudo apt-get upgrade

```

---

### Post by AVHATION on 2009-10-21
Well, I am making some progress thank you. :) I have now got both KDE4 and KMyMoney 1.0.2  installed, but I still cannot update stock prices; I cannot follow the instructions to add the stock's symbol and the security list editor is blank. The manual says I should "navigate to the investment summary view for the account in which the security is held". When I then click the left hand tab "Investments" the page is blank, but the drop down menu lists the stock accounts.  Perhaps I have entered them in the wrong place? :confused:

By the way, must I actually use the KDE desk top or may I stick with Ubuntu?

---

### Post by borahshadow on 2009-10-21
> **AVHATION said:**
> 
By the way, must I actually use the KDE desk top or may I stick with Ubuntu?

I'm not familiar enough with KMyMoney to help you with program features but, I can tell you that you are fine to use GNOME (ubuntu) if you want to.

Just as a clarifier in case you didn't know the desktop environment (DE) of 
Ubuntu is the GNOME desktop. Kubuntu uses KDE. That is really the differance between Ubuntu and Kubuntu. Applications will usually have no problem running in the other DE. So KMyMoney is a KDE app and it will run fine in GNOME.

---

### Post by AVHATION on 2009-10-22
Thank you to all who have contributed above.  I'll switch now to a KMyMoney forum for further advice. Over and out.
Regards
Henry

---

