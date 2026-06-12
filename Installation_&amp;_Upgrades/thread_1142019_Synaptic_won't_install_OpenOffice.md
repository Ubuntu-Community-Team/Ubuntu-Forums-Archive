---
title: "Synaptic won't install OpenOffice"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2009-04-28
I just installed UbuntuStudio 9.04 3 nights ago. I tried using Synaptic to install Openoffice. Everything went fine until Synaptic reached this line;

Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...

It just sat there and wouldn't do anything else. I couldn't shut down Synaptic. I did a warm reboot. When I tried to run Synaptic again it gave me a message telling me to run "sudo dpkg --configure -a" so I did in a terminal. Once again it wouldn't do anything beyond;

Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...

I tried to shut down the terminal and that locked up the computer. So, what do I do now? I have to get Synaptic working again. And, why didn't Openoffice install the first time?


Thankx for any help.

---

### Post by Partyboi2 on 2009-04-29
Hi , Open Office should be installed by default, what were the lines before  'Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...'can you open a terminal and post the whole output to
```
sudo dpkg --configure -a
```
hopefully this might provide some additional information.

---

### Post by Spaceman9 on 2009-04-29
Thankx for the help Partyboi2

I get this error message from Synaptic and the Software Updater when I try to run them now.

An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I tried running 'sudo dpkg --configure -a' in a terminal and got this

bruce@ubuntustudio:~$ sudo dpkg --configure -a
[sudo] password for bruce: 
Setting up ca-certificates-java (20081028) ...
creating /etc/ssl/certs/java/cacerts...
Certificate was added to keystore
  added certificate cacert.org/cacert.org.crt
Certificate was added to keystore

I got that when I tried installing Adobe Flash Player from a terminal and it stopped installing at 'Certificate was added to keystore'. 

I have KUbuntu 9.04 on my second drive and I'm having different problems with the software installer in KUbuntu. May Be I should have stuck with KUbuntu 8.10.

---

### Post by virgult on 2009-04-30
> **Spaceman9 said:**
> I just installed UbuntuStudio 9.04 3 nights ago. I tried using Synaptic to install Openoffice. Everything went fine until Synaptic reached this line;

Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...


I have a similar problem... and I think it's the rt kernel's fault. Here I posted my issue, making some photos to the console output:
[http://ubuntuforums.org/showthread.php?t=1143093](http://ubuntuforums.org/showthread.php?t=1143093)
Try entering "dpkg --configure -a" in a REAL terminal (tty1 or so) and see if the output is the same. I think it's a serious kernel bug... ubuntustudio developers should be noticed.

---

### Post by Spaceman9 on 2009-04-30
Virgult, I don't believe how dumb I am sometimes. After I installed Ubuntu-Studio the first time I didn't install the updates before I tried installing OpenOffice. I usually do things in a hurry. I can't believe how dumb I am. 

So, I decided to just reinstall Ubuntu-Studio and install the updates first.

Today I'm going to write on a blackboard 100 times "With any OS updates should always be installed before I do anything else."

I am really dumb sometimes. One of the packages in the update is for Synaptic. Now that the updates are installed Ubuntu-Studio and Synaptic are working perfectly.

May be that's causing the problem you're having. May be it's not.

With the rt kernels all I know about them is you have to make sure you have the right one for the version of the distro you're using. If you're using 8.04 the kernel for 9.04 might not work. When everything else fails though I usually just reinstall the OS. And with 9.04 you can try out the new etc 4 file system. Good luck with your kernel.

---

### Post by virgult on 2009-05-03
> **Spaceman9 said:**
> Virgult, I don't believe how dumb I am sometimes. After I installed Ubuntu-Studio the first time I didn't install the updates before I tried installing OpenOffice. I usually do things in a hurry. I can't believe how dumb I am. 

So, I decided to just reinstall Ubuntu-Studio and install the updates first.

Today I'm going to write on a blackboard 100 times "With any OS updates should always be installed before I do anything else."

Ok, seems they've just released the update to fix this bug. I updated the system before installing OO.o, but probably they hadn't fixed the issue yet. I'm gonna try again tonight. :)


> 
With the rt kernels all I know about them is you have to make sure you have the right one for the version of the distro you're using. If you're using 8.04 the kernel for 9.04 might not work. When everything else fails though I usually just reinstall the OS. And with 9.04 you can try out the new etc 4 file system. Good luck with your kernel.

Mine is a fresh install, exactly as yours... no mess with the kernel. ;)

Tnx for the help, anyway.

---

### Post by Gormsen on 2009-05-06
I have the same problem with Ubuntu Stuido and OpenOffice, and I'm glad to know that there is a solution. 

But is there a way to save the existing installation? I've already made modifications and would like to avoid a reinstallation.

/Alex

---

### Post by Spaceman9 on 2009-05-16
You could try reinstalling ubuntustudio and don't reformat your home partition, just reformat the root partition. You'd still have some of the openoffice folders and files in the home partition but everything for openoffice in the root partition would be gone. Then you'd still have to reinstall whatever software you installed after reinstalling the CD and update files.

I know there's someway to copy or move all the files and folders you don't want to lose to a different drive or partition but I've never done that because I just reinstall.

If you don't need everything in openoffice try using Abi Word. It's a great replacement for the word processor in openoffice. If you want to write a play or anything for radio, TV or a movie script try Celtx.

If you really need openoffice install Ubuntu and use Synaptic to install the audio, graphic and other packages from ubuntustudio into Ubuntu. If you do it that way you will also need to install from Synaptic the rt kernel.

Ubuntu shouldn't have any problems with openoffice. I know for a fact Kubuntu doesn't have any problems with openoffice. But it's not ubuntustudio.

If you have 2 hard drives you could install Kubuntu on one and ubuntustudio on the other one. I did that and it works great. Or you could install both on one drive.

---

### Post by Gormsen on 2009-05-16
Thanks for the suggestions. It'll be a new installation then - most of my customizations were in the software added later.

I only need a simple word editor, so I't try Abi Word.

/Alex

---

