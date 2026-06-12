---
title: "Completly new to Linux and Ubuntu!"
date: 2008-11-24
forum: General Help
---

### Post by jcp7857 on 2008-11-24
I have seen some friends at school using this platform.  I am not all that computer savy so I wanted some support in putting this on my computer.

I have a Dell Inspiron 6000.  I currently have XP and would like to keep it along with Ubuntu.  I know I am going to have to partition my hardrive, and have no Idea where to start with that.

So any pointers or links to tutorials I would greatly appreciate it.  I know I will find a lot of info searching this topic but I am hoping for some very specific experiences with this and pointers for first timers like my self.

I have the download done, and will be putting it on a DVD today.  I am pretty sure I can do that, so later today or tomorrow I will be doing the install.

Thanks in advance,
jesse

---

### Post by jcp7857 on 2008-11-24
Also I would like to get links for all the add ons, such as Beryl and Wine and that stuff.

Thanks again

---

### Post by NewJack on 2008-11-24
This is a good place to start:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

or if you are installing Hardy:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

This is also a great place to start:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Here is a guide to help you get your Multimedia set up:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by oldos2er on 2008-11-24
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) will help with creating a dual boot system. Beryl is deprecated; instead compiz-fusion is installed by default (if your video card can support it). For info on installing software, see [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by jcp7857 on 2008-11-24
Thanks guys lots to read before I start this install.

---

### Post by eeeek on 2008-11-24
This is advice coming from a relatively new Linux user, so...

Burn the iso file to a CD-R. You don't need a DVD, although I don't think that would hurt. Most Ubuntu distros will fit on a 700 MB CD-R. Make sure you "Burn the ISO file to disc". This is different that just burning a regular file to a disc.

Then just pop the disc in your drive and boot up your computer. More than likely, your computer will boot to Ubuntu as a "Live" session. 

Once it finishes booting up, you will see a full setup on screen - but nothing has been installed to your hard drive yet. You can look around on this live session just to get a feel for it. 

You can turn off the computer and remove the CD. Next time you boot, Win XP will start up like Linux was never there.

As far as installing - you might mention which Ubuntu version you've downloaded (Ubuntu, Kubuntu, Xubuntu, etc - also 8.04, 8.10 etc)

The versions I've done - there's an "install" link in front of you on the desktop. It guides you thru the install in about 7 steps, once you finish, it takes around 40 minutes to install (well, it does for me anyways).

A word of caution - if you do install it to your hard drive - you need to be careful in the disk partition setup steps. Picking the wrong thing here could wipe XP off your box. As far as I know - that's the main step you want to be concerned with. Someone else besides me ought to help you with that part, though.

Again, this is advice from one new user to another. But this is what I've experienced.

Enjoy

---

### Post by jcp7857 on 2008-11-24
I am trying to install ubuntu 8.10.

I am currently getting a failure to read hardware drivers.  What do I do to try and fix this.

---

### Post by easoukenka on 2008-11-25
Where are you getting this error while booting up livecd?

---

### Post by jcp7857 on 2008-11-25
Problem was solved.  I am now using Ubuntu!!!  I had a disk error so I redownloaded Ubuntu off line and then burnt another cd and it fired right up.  Thanks for all the help.

Now I am trying to figure out how to get wine to bring in my programs from XP.  I cannot seem to find any on my C:drive through wine.  ANy pointers here will help greatly.

Thanks again,
Jesse

---

### Post by andrew.mckevitt on 2008-11-25
I suggest you try the howtoforge website, they have great step by step tutorials,

Try this one for the dual boot - I know it's for an earlier release of ubuntu, but the principles are the same.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

One you have a working dual boot system read this one

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

I have been using ubuntu for two years now, I stopped dual booting after about two months and have never looked back.

Welcome and good luck.

---

### Post by eeeek on 2008-11-25
You might mention what programs you're wanting to use in XP under Wine. There might be a Linux equivalent of the Windows program you want to use. You would be amazed of all the stuff to be found in the Ubuntu repositories. 

Go to Synaptic Package Manager and do a search of the task you're wanting to do and see what turns up.

---

### Post by Therion on 2008-11-25
> **jcp7857 said:**
> Now I am trying to figure out how to get wine to bring in my programs from XP.  I cannot seem to find any on my C:drive through wine.  ANy pointers here will help greatly.
Well with a new operating system comes a new way of thinking and doing.  After all, I'm assuming you installed Ubuntu to get AWAY from Windows to one degree or another, no?  

In Ubuntu physical drives are not assigned drive-letters as they are with Windows.  Most everything in Ubuntu is treated like a folder would be in Windows.  Hence you don't have a C: or E: you have something like **sda1** or **hda1**, depending on the type of drive, for example.  

Further, rather than trying to get all your old WinXP applications running in Wine, I might suggest you look for applications that will accomplish the same thing that are also native to the 'nix environment (substituting Open Office for MS Office, for example, or Amarok or Rhythmbox for iTunes or Windows Media Player).  You can find a good list of alternative applications here to get you started, but if you need more direction you can always post here and ask.

[http://www.osalt.com/](http://www.osalt.com/)

or 

[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

---

### Post by linux_tech on 2008-11-25
If you are interested in setting up dual or multi- boot these are the best step by step guides I've seen
The definitive dual-booting guide: Linux, Vista and XP step-by-step

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by jcp7857 on 2008-11-25
I trully just want the equivalent of Microsoft Word, Excel, and powerpoint.  I just want the documents to be .doc, .exl (?), and .ptt.  If there is something just like these please let me know.

---

### Post by lowerydb on 2008-11-25
I just started with Ubuntu a few days ago and I've been using Open Office to save and open Office 2003 doc files and have had no problems. It should be under applications > office, there is also an Open Office equivalent to PowerPoint and Excel.

---

### Post by wet_colored_arch on 2008-11-25
try this for office equivalents   [http://www.openoffice.org/index.html]("http://www.openoffice.org/index.html")

I have had good luck, at least with Word in cross compatibility but there are occasional formatting issues I have noticed.

If you must use windows, and you probably don't, consider
i) wine
ii) virtualization  (Virtual Box)
iii) dual boot (exit OS and reboot in Windows)

---

### Post by Therion on 2008-11-26
> **jcp7857 said:**
> I trully just want the equivalent of Microsoft Word, Excel, and powerpoint.  I just want the documents to be .doc, .exl (?), and .ptt.  If there is something just like these please let me know.
Those formats (.doc, .xls and .ppt) are Microsoft "proprietary" formats, meaning they're owned by Microsoft.  You can use Open Office though.  It will support the Microsoft formats and you can move between the two applications seamlessly; I do it all the time when going from my MS Office at work to Open Office at my home.

Writer is the OO version of Word, Calc is the OO version of Excel and Impress is the OO version of PowerPoint.  There are equivalent applications in the OO suite for MS Access and Publisher as well.

---

### Post by stoneage on 2008-11-26
I may be wrong, but I don't think OpenOffice can open Microsoft Access database files.

Word, Excel and Powerpoint - yes, but Access I don't think so.


Please correct this if I am wrong.

---

### Post by Therion on 2008-11-26
> **stoneage said:**
> Please correct this if I am wrong.
I'm not saying it's easy, or intuitive for that matter, but yes it CAN be done.

[http://www.openoffice.org/FAQs/ms-access/ms-access.html](http://www.openoffice.org/FAQs/ms-access/ms-access.html)

---

### Post by jcp7857 on 2008-11-26
Well thanks I am using Open Office now!

Next question I have is: If I save a package to my desktop how do I install it?
Thanks again

---

### Post by nzadLithium on 2008-11-26
depends on the type of package. If its a .deb package you just double click it and ubuntu will guide you through. 

Post back what sort of package it is :D

---

