---
title: "Trying to install for first time  Old AMD K6-2"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by metalchewy on 2009-07-31
I'm new to installing Ubuntu.

I recently put a new hard drive in my PC so the old 40GB hard drive went to the old crashed system.  I used Partition Magic to remove all partitions from the drive.  I downloaded the latest and greates ubutnu ISO and tried to install.  

It is an AMD K6-2 400 with 196MB of Ram.  Not a very high hp machine, but for web browsing, I was hoping to get linux to install.  

At any rate, I had and older put in the 9.0.4 disc and it goes to the boot screen, I select install, and the screen goes black and never comes back.

I had an ISO from a previous version that I looked at  a year or so ago Ubunto 7.0.4, 2007 build, and it gives a Kernel Panic when the installer tries to run.

Can anyone tell me whether there is some easy way to get this to install?  Any boot options to force it?  


Help is greatly appreciated.

---

### Post by running_rabbit07 on 2009-07-31
Try Xubuntu 9.04, 8.10, or 8.04. They should all work.

Edit: I recommend Xubuntu because it is lighter than Ubuntu on your system. The 7.04 version is no longer supported. *.04 is a Long Term Support distro so you will be supported until 2011.

---

### Post by metalchewy on 2009-07-31
Thanks, Downloading it now.  Will let you know how it goes.

---

### Post by running_rabbit07 on 2009-07-31
You are very welcome.

---

### Post by oldos2er on 2009-07-31
The minimum for (Gnome) Ubuntu is 256MB RAM. I doubt if less would run acceptably.

---

### Post by Bucky Ball on 2009-08-01
Xubuntu Alternate Install CD (not Desktop; the graphics will probably choke your ram before you get far). Alternate is a text based installer so uses bugger-all system graphics and system resources to install. I doubt you will ever get the Desktop ISO to work so I would cancel that download now if it isn't Alternate ISO.

:)

---

### Post by metalchewy on 2009-08-01
The xubuntu download finishes in about 5 minutes.  I have also started the xubuntu alternate download and will give it a try.

Thanks

---

### Post by Bucky Ball on 2009-08-01
If you can get Xubuntu in, you can expand from there, adding things until the hardware starts to fall over then back off a bit. You will find the limits of the hardware pretty quickly. :)

---

### Post by metalchewy on 2009-08-01
Even the Alternate Disk was failing.  I did a memtest, all it did was put up errors.

I reseated the memory and now the install runs, It would even start the install on the desktop disc, but I changed over to the alternate disc to start small and add as I go.

Thanks for the help.


Working thru installation now.

---

### Post by Bucky Ball on 2009-08-01
Excellent work, metalchewy. Persistence, gotta like that. 

Yea, think you would have failed with the Desktop ISO. Good luck with it and let us all know.


(ps: if you end up really get into Ubuntu and have the inclination later on, it is possible to install from a command line, add the desktop environment so you can see what you are doing and really just build the OS you want with only the applications you want. ;-))

---

### Post by metalchewy on 2009-08-01
Thanks Bucky Ball.

The alternate installation didnt run so smoothly.  The alternate install eneded up getting all the way to writing the linux kernal and failed.  

I retried the install and then it started failing on writing some of the packages, SO, I thought, what the heck and put the desktop disc in to see if it would install.  Install status shows 30%.  Fingers crossed

---

### Post by Bucky Ball on 2009-08-01
Always check the disk for defects before install (second option on the Install ISO from memory). Safest way is to torrent the ISO. The torrent file is available for download also.

---

### Post by rtalcott on 2009-08-01
I have a k6-2 on an old Gateway...256 meg of RAM...running 9.04 Server...no gui but have apache, ftp server etc. on it...runs nicely...low power....cheap (it was free) and very quiet...great low volume web server.
rt

---

### Post by metalchewy on 2009-08-01
The install from Xubuntu Desktop Disc just completed installing.  

System is up and running with Gnome.  Not to bad performance-wise for an old K6-2/400

Looks like most the hardware is isntalled and working in the OS as well.  The SCSI Card and the Iomega drives are up (ZIP and JAZ). 

THe only thing not working is the old soundblaster card. 

Thanks for your help.

---

### Post by Bucky Ball on 2009-08-01
A pleasure and excellent news! You say you installed Xubuntu but you are running the Gnome desktop environment? Xubuntu uses Xfce. 

That would be the desktop environment for you to use on that system and you can install it so it is selectable from the 'Sessions' menu on the login screen. If you hit 'Sessions' you will see the desktop environments you have loaded.

Search for 'xfce4' in System->Administration->Synaptic Package Manager

[URL="http://www.psychocats.net/ubuntu/xubuntu"]
[/URL]

---

### Post by metalchewy on 2009-08-01
My Mistake.  Xfce.  Its working.  


Thanks again.

---

### Post by Bucky Ball on 2009-08-01
Good news. You can try installing Gnome and if it falls over, uninstall again. At least your up and Xubuntu is an excellent place to start. (I use it as the base install on my two high powered machines.) :)

---

### Post by running_rabbit07 on 2009-08-01
> **Bucky Ball said:**
> Good news. You can try installing Gnome and if it falls over, uninstall again. At least your up and Xubuntu is an excellent place to start. (I use it as the base install on my two high powered machines.) :)

I have Xubuntu on my laptop and it works great. It still loads up the CPU to around 70% at idle but I am happy I can use it on the net now.

 I previously had 2000Pro on it which topped out at IE6 before they stopped supporting it and of course IE6 is obsolete to most servers that I deal with for college.

---

