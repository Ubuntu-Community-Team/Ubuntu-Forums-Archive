---
title: "UbuntuStudio 9.10 Installation Step Failed"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by ario on 2009-11-04
Hi everyone.
I recently downloaded **ubuntustudio 9.10**. First of all there was no live cd image, Just alternate dvd installation iso images. I downloaded the iso image completely then tried to install it. Every thing was ok until it asked me for which part of installation packages you want to install. I selected audio editing softwares. it takes about 10 minutes and copied a lot of things into my hard drive and then returned this error:
[B]Installation Step Failed!
An installation step failed. You can try to run the failing item from main menu....
[/B]
I tried to install it by it's image in Sun Virtual Box or install it buy burning it on a dvd and boot my PC with that dvd. But both of ways take me to this error message.
I searched All over the net but I think no one tried this OS before me or no one has reported the same error.
I'm so sad. After downloading more than 1.4GB of data with very slow Internet now that it! just a red error message. :cry:
Any suggestions?
Thanks for your attention guys.

---

### Post by ario on 2009-11-05
No answers? I checked the dvd for any defects but no problem found. Is anyone in the world installed ubuntu studio 9.10?
Oh my god! Is this really a fake iso image with a fake website [www.ubuntustudio.org](www.ubuntustudio.org) that no one tried it before?!?

---

### Post by xyppy on 2009-11-05
This probably isn't the answer you're looking for,but I followed [these directions]("http://ubuntuforums.org/showthread.php?t=900676&highlight=install+ubuntustudio") when I installed studio in 9.04.  I haven't tried them yet for 9.10, but they will probably work.

---

### Post by dond on 2009-11-05
I have same problem as ario, neither on Vbox or bare machine does it install completely.

---

### Post by xyppy on 2009-11-05
> **xyppy said:**
> This probably isn't the answer you're looking for,but I followed [these directions]("http://ubuntuforums.org/showthread.php?t=900676&highlight=install+ubuntustudio") when I installed studio in 9.04.  I haven't tried them yet for 9.10, but they will probably work.

I just used the above method to install UbuStu 9.10.  If you want UbuStu, this may be the best way for you to get it.

---

### Post by dond on 2009-11-05
xyppy's method worked fine for me with 9.04 (both on Vbox and single boot machines). Thanks. However, when I install 9.10 Ubuntu or Kubuntu I lose wireless connectivity, so can't proceed further. Lots of posts on this issue but so far I'm unable to resolve it and am sticking to 9.04.

---

### Post by MIJ-VI on 2009-11-14
HOW TO INSTALL UBUNTU STUDIO 9.10 WITHOUT HAVING THE INSTALL #%$&%# FAIL!:

1) Install Ubuntu Studio 9.10 as per normal but DON'T install the Audio Applications (if you do, the install will fail).

2) After installing Ubuntu Studio, re-boot your computer and insert the Ubuntu Studio 9.10 install DVD.

3) Go to System-->Administration--Software Sources and check mark the Ubuntu Studio DVD you see in the Software Sources dialog box. Now click the close button.

4) Go to System-->Administration and launch Synaptic Package Manager and then click the Origins button on the lower left hand side. (This will cause three entries for the Ubuntu Studio install DVD to appear in the upper left hand side.)

5) Click 'All' above the three entries and type: network-manager-gnome into the Quick search box, check mark network-manager-gnome, and Apply the changes. After network-manager-gnome has been installed you'll have to re-boot your PC. Eject the Ubuntu Studio 9.10 install DVD and re-boot. When your machine has re-booted you'll see the NetworkManager Applet icon in the menu bar on the right hand side (this allows convenient control of wired & wireless networks and also supports Roaming Mode). Now connect to the Internet.

6) Once again insert the Ubuntu Studio 9.10 install DVD, launch the Synaptic Package Manager, click 'All' above the three entries, and type: ubuntustudio-audio into the Quick search box, and then check mark ubuntustudio-audio. Doing this will automatically check mark all of Ubuntu Studio's audio applications.

EDIT: (To install on a machine which has no Internet connection, type ttf-mscorefonts-installer into the search box at this point and then un-mark the ttf-mscorefonts-installer. THIS is the only installer on the Ubuntu Studio 9.10 install DVD which requires a 'Net connection.)

Now Apply the changes AFTER MAKING SURE that your PC is connected to the Internet BEFORE you install the audio apps.

Why? Because one of the items which is installed with the audio applications is the MS Core Fonts package *rolls eyes* which the Synaptic Package Manager has to retrieve via the Internet from Source Forge.

If your machine isn't connected to the Internet, the MS Core Fonts install will fail and display a dialog box saying so.

I suspect that THIS might be the reason why Ubuntu Studio 9.10 won't install the audio applications collection from its DVD onto a non-Internet connected PC.

--------

DISAPPEARING APPLICATION AND DOCUMENT WINDOWS:

After getting everything installed, and booting into the Ubuntu Studio 9.10 desktop, you will notice that a running application (or open document) simply disappears if its Minimize Window button is clicked.

A remedy...

Right-click the menu bar and drag down to 'New Panel'. (This will cause a new panel/task bar to appear at the bottom of the screen.)

Now right-click the new panel and drag to 'Add to Panel...', and then scroll down & select 'Window List' from the list of of items which appear in the pop-up window.

Next, drag 'Window List' to the lower left hand side of the new panel/task bar. From now on when ever you click the Minimize Window button on any app or doc, it'll collapse down to a new button in the new panel/task bar so that you can still get at it.

--------

AUDIO PROBLEMS:

'Can't hear audio which is routed into your PC's line level inputs? That's because said inputs are muted by default in Ubuntu/Ubuntu Studio 9.10.

To un-mute the line level inputs: Launch the Terminal (Applications-->Accessories-->Terminal), type alsamixer at the prompt, and then tap the Enter button on your PC's keyboard.

You'll see what you have to do to un-mute your PC's line level inputs (your keyboard's left & right arrow keys navigate, the up & down keys increase & decrease levels, and the 'M' key mutes & un-mutes the selected audio input(s) or outputs).
   
--------

SOMETHING I READ ON THE 'NET YESTERDAY (which seems to work...)

"Re: Notification ballons on Karmic Koala
There's a fix for this.

Notifications are handled by the package notify-osd. What we have to do is replace the default version with one from Julien Lavergne's PPA.

First of all add the following two repos to your sources list:

deb [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main

Then add the signing key:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0EF28BC1

and reload the package info:

sudo apt-get update

Then you can find notify-osd in Synaptic and install the new package. Once you've done that all the notifications will go back to the top right-hand corner where they belong."

- 'Can't recall the author's name...

--------

BTW. So far, so good with Ubuntu Studio 9.10 running on a Pentium IV @ 3.20 GHz + a 1 MB L2 mounted on an ASUS P4P800-E Rev. 1.02 sporting 3 GB of RAM! :-)

---

### Post by SATANOCLAUSE on 2009-11-14
Thanks MIJ! At first I thought the ISO (amd64) was corrupt but it wasn't... good troubleshooting....gnight:KS

---

### Post by TheChefSLC on 2009-11-14
Thanks for sharing this information. It worked perfectly!

This is definitely better than how i had it running before. Just installed ubuntu 9.10 then installed the ubuntu studio packages from repos.

---

### Post by ario on 2009-11-15
Thanks a lot MIJ-VI. I used your solution, It's better than the other way which says installing ubuntu 9.10 first and then downloading the whole stuff from repositories. Because we all here downloaded ubuntu studio DVD and we won't download about 500MB of data again. so a solution based on existing DVD is the best.
**1st**. I've i**nstalled "ubuntu studio 9.10 alternate" normally**. When it asked me about which package groups to be installed I have selected none of them. So it installed and came up very fast.
**2nd**. I ran **synaptic packaged manager** from Main menu>System>Administration
**3rd**. I clicked reload buttun but that was my mistake!
**4th**. I clicked **went to repositories and selected both cdrom check boxes and deselected all other repositories** (I won't download anything for now).
**5th**. I clicked **reload in synaptics windows**. It told me:
```
Failed to fetch cdrom. Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

```
**6th**. I entered "**sudo apt-cdrom add**" in a new terminal window and entered my password.
**7th**. Clicked **reload in synaptic window**. 
**8th**. I can install new packages from cd-rom then. there is some packages in All Region in left column of synaptic windows those are not installed already. I've selected "ubuntustudio-audio" package there. and clicked apply and it installed them all.
The DVD is now working for me and the problem is **SOLVED**.
Thanks for help.

---

### Post by r0st1 on 2010-02-17
Thanks for the info.

However, for me this did not work exactly like that:

- after selecting 'cd-rom' in software sources and clicking close, I got a list of error messages saying need to use apt-cdrom

- running apt-cdrom gave a list of complaints about non-exisiting (yes, typo from original) files and couple of 'could not open's


What I did differently:

- after succesful base-install without any 'studio software': log in to the system - run 'sudo apt-get update' and 'sudo apt-get upgrade'

- no need for network-manager-gnome (wired net connection ok on base install)
 
 - added the cd-rom as software-sources using the 'Other Software' tab 'Add CD-ROM' button ...which did hang in the end unmounting the cd (just hit the close button after couple of minutes), but seemed to work as after that the cd-rom appeared in the Synaptic Package Manager

After this installing the ubuntustudio-audio and -plugins using SPM worked fine. Note that got no more complaints about mscorefonts eventhough I did not un-check the package (without network connection it might be needed to un-select the font package).

---

### Post by SagnaB on 2010-03-04
I just have to say to all who have assisted with input (more-so to the entire Ubuntu Community), a Very Big Thank you. For all of you help so many of us solve problems we individually encounter along our Ubuntu journey.

CHEERS!

---

### Post by travlemon on 2010-10-10
i know this reply is a bit late, but i just wanted to tack on another piece of feedback, as i had the same problem, but a much different (and easy) experience in clearing up the issue.  

while installing ubuntu studio 10.04 from the dvd, i was getting the red screen that advised that an installation step failed.  the step that failed was setting up software, like most of you had received as well.  

the first time i was prompted to choose packages (2d 3d creation software, audio, video, plugins, and the like), i only selected audio and the dssi/ladspa plugins because i am using it for music.  on the first run through, the installation failed, giving the error message about an installation step failing.  the installation asks if you'd like to try to retry one of the installation steps to continue, so i just chose the step to select software again.  i chose my audio and dssi/ladspa plugins options again, and continued the installation.  

this time, it asked if i wanted to do some kind of update (i'm sorry i was half asleep at night and wasn't expecting this screen). it basically asked if i wanted to merge data or install updates, so i chose to install updates. it then asks if you'd like to download a language pack, then proceeds to download various updates to complete the installation, and it actually worked for me.  i finished the rest of the installation as normal and was able to boot into ubuntu studio.  this all took place today, and i've been letting it do system updates for the past 15 minutes or so, and it seems to be running fine.  hope this helps!

again, sorry for the vague description, i didn't quite have my guard up to make note of all the steps i performed.  but in short, you want to just try repeating the step to select software, and choose to install updates, when prompted.

---

