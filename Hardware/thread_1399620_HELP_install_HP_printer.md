---
title: "HELP install HP printer"
date: 2010-02-05
forum: Hardware
---

### Post by bwsmith25 on 2010-02-05
I just bought an HP F2480 Deskjet All-in-One printer, and I was hoping that it would seamlessly work with Ubuntu 9.10 - well, it doesn't.

I can't even get it to print anything. I have tried installing drivers for the printer to no avail. I have looked through these forums and found other sites with instructions on installing drivers for this printer, and it doesn't work. Can someone please help me install drivers for this printer so it will work with Ubuntu?

I really don't want to go back to Windows, so someone please help me.

I'm relatively new to Ubuntu so I don't know much about the command line - if you have help tips please give them to me in "baby terms".

---

### Post by sgosnell on 2010-02-06
You should be able to make it work from System/Administration/Printing, then click the Add button.  It should find the printer and install the driver for you.  You might have to select the closest model if it doesn't show your exact model, but it should still work.  How did you install it originally?

---

### Post by bwsmith25 on 2010-02-06
That was the first thing that I tried, and it won't print. I tried installing HPLIP and it won't allow me to install it because it says that required dependencies are missing. I can't find out how to install the dependencies so I can't install HPLIP either.

---

### Post by bwsmith25 on 2010-02-06
When I attempt to install HPLIP, it tries to install all the dependencies, and fails 3 times. I get the error message ERROR CODE 255

Where can I find the following dependencies:

cups-devel
libusb
cups-image
libjpeg

I really need to get this printer working - printing is one of the most important things I do with my computer. And, if I can't get it to work I have to switch back to Windows - which I DO NOT want to do.

I thought Ubuntu was supposed to be user-friendly? If so, why can't I get my friggin printer to work seamlessly?

---

### Post by IcarusR on 2010-02-06
If you are trying to install HPLIP with synaptic it should install all deps automatically.

All should be in the repos, either use synaptic or....

```
sudo apt-get update
```

```
sudo apt-get install cups-devel libusb cups-image libjpeg
```

---

### Post by bwsmith25 on 2010-02-06
> **IcarusR said:**
> If you are trying to install HPLIP with synaptic it should install all deps automatically.

All should be in the repos, either use synaptic or....

```
sudo apt-get update
```

```
sudo apt-get install cups-devel libusb cups-image libjpeg
```

When I do this, it says that it can't find the package.

---

### Post by IcarusR on 2010-02-06
At a guess you do not have repositories setup.

See here for info & some available repos...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories")

---

### Post by bwsmith25 on 2010-02-06
I have discovered that my printer needs to use hplip 3.9.12

I have 3.9.8 on my computer right now.

How do I get 3.9.12? I have tried downloading the new version and installing it, but it keeps telling me that I don't have the required dependencies to install. I can't find the dependencies ANYWHERE and this is starting to drive me insane.

I'm at the point of deciding would I rather use Windows or never be able to print anything again?

Can someone PLEASE help me with this? I don't know what I'm doing and it's really starting to frustrate me. Had I known that Ubuntu would be this frustrating I never would have switched from Windows in the first place. At least when I had Windows my freaking printer worked.

---

### Post by tacantara on 2010-02-06
I recently downloaded 3.9.12 from HP's website.  They have a section dedicated to Linux drivers (I wish I had written down the URL).  If I recall correctly, the package you download from HP will check for missing dependencies and correct any that are missing.

The HP website does have the package in a .deb format, so installation will go relatively smoothly.

I found the link to HP's website:  [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by bwsmith25 on 2010-02-06
> **tacantara said:**
> I recently downloaded 3.9.12 from HP's website.  They have a section dedicated to Linux drivers (I wish I had written down the URL).  If I recall correctly, the package you download from HP will check for missing dependencies and correct any that are missing.

The HP website does have the package in a .deb format, so installation will go relatively smoothly.

I found the link to HP's website:  [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

That's the site that I tried. It doesn't work for me. I don't know what I'm doing wrong, but it doesn't work.

I've downloaded and attempted to install from that site at least 4 times.

Every time I try, it keeps telling me I don't have the dependencies.

Is there something that I have to install prior to the HPLIP that I just don't have?

---

### Post by sgosnell on 2010-02-06
You need to set the third-party repositories.  System/Administration/Software Sources.  Make sure all the boxes are checked.

---

### Post by bwsmith25 on 2010-02-06
Here are some screenshots of what I'm talking about.

Here is the message that I am missing dependencies:

[ATTACH]146289[/ATTACH]

And here is the error message when it tries to correct the dependency problem:

[ATTACH]146290[/ATTACH]

Based on these screenshots, can anyone out there help me get this printer to work? Thanks.

---

### Post by PRC09 on 2010-02-06
You may find some help here with the dependencies issue.I think you should be able to use the script for jaunty and try the install again..... 



[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

### Post by bwsmith25 on 2010-02-06
> **sgosnell said:**
> You need to set the third-party repositories.  System/Administration/Software Sources.  Make sure all the boxes are checked.

They are checked - still nothing works.

Any other ideas? 

Should I just completely remove Ubuntu 9.10 and reinstall it with the live CD? Would that work?

---

### Post by bwsmith25 on 2010-02-06
> **PRC09 said:**
> You may find some help here with the dependencies issue.I think you should be able to use the script for jaunty and try the install again..... 



[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

I've tried this too, and it doesn't work.

---

### Post by sau99ms on 2010-03-16
> **bwsmith25 said:**
> I've tried this too, and it doesn't work.

Hi,

Did you ever get this printer working on Ubuntu 9.10? I've just installed the printer and although it required a little tweaking to get the device manager to work so you can see the status of the cartridges etc it's all working fine now using the HPLIP drivers from the HP website.

Let me know if you're having any trouble and if you like I'll try and walk you through it.

Cheers,

Mark

---

### Post by Th3Alchemist on 2010-10-20
try:

```

sudo apt-get install aptitude

sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd  cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript  openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging  policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus  python-gobject python-dev python-notify python python-reportlab libsane  libsane-dev sane-utils xsane
```

then retry installation process, it worked for me...

---

