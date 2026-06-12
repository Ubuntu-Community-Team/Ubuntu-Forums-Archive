---
title: "Some questions about ubuntu"
date: 2008-11-24
forum: General Help
---

### Post by BH30 on 2008-11-24
Hi all..

I have installed Ubuntu last night , it's nice

But i have some notes could you help me with it please :KS

1- How i can switch keyboard language ? for example in windows we use alt+shift what about Ubuntu ?

[COLOR="Red"]PS [/COLOR]: I have already installed the other language package which am talk about only how to switch it is my problem :(

2- Regarding to backup , how i can perform full backup ? can i use Norton ghost ? it's ok ?

3- How i can access to command prompt in Ubuntu ?

Thanks ..

---

### Post by Sef on 2008-11-24
> 1- How i can switch keyboard language ? for example in windows we use alt+shift what about Ubuntu ?[COLOR=Red]PS [/COLOR]: I have already installed the other language package which am talk about only how to switch it is my problem :sad:

You can switch keyboard layouts:  cursor on the top bar > right click > double click keyboard indicator.   

For switching languages and not the keyboard, I have gone into System > Preferences > SCIM Input Method Set up. 

> 2- Regarding to backup , how i can perform full backup ? can i use Norton ghost ? it's ok ?You could use [Clonezilla]("http://clonezilla.org/") or [Partimage]("http://partimage.org/Main_Page").    Norton Ghost is for Windows.

> 3- How i can access to command prompt in Ubuntu ?Applications > Assessories > Terminal

---

### Post by BH30 on 2008-11-24
You are best Sef, Thank you

I have another thing pls , exe programms can't installed on Ubuntu ?

There is no antivirus fixed on this OS ? or in Ubuntu no need that ?

When i got back home i'll check that

---

### Post by ju2wheels on 2008-11-24
> **BH30 said:**
> You are best Sef, Thank you

I have another thing pls , exe programms can't installed on Ubuntu ?

There is no antivirus fixed on this OS ? or in Ubuntu no need that ?

When i got back home i'll check that

You have two options for installing windows (exe) applications. One is using Wine, however this doesnt support all exe applications fully. You can try installing it and see if it works and hope for the best, or check winehq.org to see the compatibility rating.

The second option is installing Windows inside a virtual machine using VirtualBox or VMWare to run windows software.


Antivirus is not really needed on Linux unless you share files with Windows users a lot. It is more to protect them against viruses, as Windows viruses dont work on Linux, and there are so few Linux viruses you can ignore them (Linux has been patched against them already). In the end though, its personal preference if you want to install it. The package is clamav and clamtk for the GUI.

---

### Post by hyper_ch on 2008-11-24
regarding viruses:

> **RequinB4 said:**
> I think one thing that there are two things that haven't been mentioned.

First, anti-virus is not really anti-virus - it is virus-checking.  AV works (for 99.999% of the time, there are exceptions) by comparing files or parts of files to known patterns of virus interaction.  Since there have been, what, 10 known viruses that will affect a GNU/linux desktop, and none of them running in the wild, the question "should we be vigilant and not be cocky about our virus protection?" is irrelevent because until someone makes a sucessful virus for GNU/Linux there isn't much to check.

Second, there is the beleif that we should run AV to protect those we contact via the internet getting infected.  Assuming we're not talking about a mail or SAMBA server or something, let's think about this for a second - what are the possible outcomes?

1)  Linux box doesn't get a virus.  No problem.

2)  Linux box gets a virus, and doesn't transmit it.  No harm done, maybe a few wasted bytes of space.

3)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box has equivalent or better anti-virus.  They don't get infected, so no harm done.

4)  Linux box gets a virus, and transfers it to a Windows box, and the Windows box doesn't have antivirus or it fails to detect.  Windows user is very sad.

So, let's examine 4.  Since the box doesn't have antivirus, and has an open connection to the internet, and (for the sake of argument) is running unsafe applications such as IE or Outlook, its security is already very low.  In fact, it's far, far, far more likely that they get the virus not from  you but from normal browsing or from ANOTHER windows box which is ACTIVELY propagating the virus.  Add the fact that the probability of 1, 2, and 3 is also MUCH higher than 4, and you begin to see my point.

So you must ask yourself - By running AV on your GNU/Linux desktop, are you protecting against the VERY unlikely, or just delaying the inevitable?

---

### Post by scouser73 on 2008-11-24
> 2- Regarding to backup , how i can perform full backup ? can i use Norton ghost ? it's ok ?

What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by BH30 on 2008-11-24
Thanks all.

Because i have some softwares i have to bee in my ubuntu

like msn messenger and MS frontpage and other FTP programs cute FTP or others

I have checked installing winzip it appears error . I think so many programs can't be used in Ubuntu

---

### Post by hyper_ch on 2008-11-24
> **BH30 said:**
> I have checked installing winzip it appears error . I think so many programs can't be used in Ubuntu

Have you ever tried to run a playstation 3 game on Wii or Xbox?

---

### Post by ju2wheels on 2008-11-24
> **BH30 said:**
> Thanks all.

Because i have some softwares i have to bee in my ubuntu

like msn messenger and MS frontpage and other FTP programs cute FTP or others

I have checked installing winzip it appears error . I think so many programs can't be used in Ubuntu

You can install aMSN instead of MSN Messenger and Filezilla instead of Cute FTP. I think you should start looking for Linux alternatives instead of trying to trouble yourself installing Windows specific software.

Ubuntu has built in ZIP capabilities so Winzip is really not needed. If you want to zip a file or folder just right click on it and press "Create archive".

---

