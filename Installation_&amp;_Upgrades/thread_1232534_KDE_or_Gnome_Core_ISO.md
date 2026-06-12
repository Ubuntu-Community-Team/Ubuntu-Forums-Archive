---
title: "KDE or Gnome Core ISO?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by krimzen85 on 2009-08-05
Hey all,
 
I just downloaded Ubuntu Server onto one of many Server's at my job, but I am going to need a GUI function for what I need them for.
 
Furthermore, I do not have access to the INET for foreign devices at my place of employment, so if I want to run the sudo get-apt command, I will have to lug these home one by one to do it.
 
I was wondering, to make things easier, is there a KDE or Gnome CORE ISO image available or download that I could just burn directly to CD and load into the drive on my server, and install it that way? Or would that wipe out the Ubuntu Server I just installed?
 
By core, I mean, not the full desktop package so that server performance does not suffer, but still sufficient enough that the server can operate as most normal servers will. 
 
These servers are not going in a production environment.

---

### Post by zvacet on 2009-08-05
You can install Gnome.KDE or XFCE from alternate CD.BUrn alternate iso and then put CD in the drive and type

```
sudo apt-cdrom add

sudo apt-get update

sudo apt-get install ubuntu-desktop 
```


for KDE

```
sudo apt-get install kubuntu-desktop
```

---

### Post by krimzen85 on 2009-08-06
Thanks.
 
What do you mean Alternate?

---

### Post by krimzen85 on 2009-08-06
Nevermind, I understand.
 
So I guess I will need to change the boot priority in the server so that it doesn't boot the desktop ISO image and mess up Ubuntu Server huh?  That way it will prompt Ubuntu Server login, and then I can type the sudo commands after logging in right?

---

### Post by SuperSonic4 on 2009-08-06
There is an alternate ISO available - this is a non-live CD with a text based installer.

Do you really need a full DE to do the job though? Perhaps LXDE or a WM + PCMan file manager will do the job

---

### Post by aysiu on 2009-08-06
> **krimzen85 said:**
> Thanks.
 
What do you mean Alternate?
Go to [the Ubuntu download page](http://www.ubuntu.com/GetUbuntu/download) and select the Alternate CD, not the Desktop CD.

See the attached screenshot for more details.

The **Desktop CD** is a live/installer CD. It does not contain the .deb packages needed for the Gnome desktop environment. It contains a compressed copy of a working live session. When you install it, it just makes a copy of the default live session to your computer. That's why the Desktop CD installation takes only about twenty minutes.

The **Alternate CD** is just an installer CD and it actually contains the .deb packages needed for installation. During installation it selects, unpacks, and sets up each individual .deb file. That's why the Alternate CD installation can take over an hour.

If you do not have an internet connection and want to add Gnome, you need the Ubuntu Alternate CD, so you can install the .deb packages it has. The Desktop CD does not have those .deb packages.

Same deal for Kubuntu if you want to add KDE. You need the Kubuntu Alternate CD, not the Kubuntu Desktop CD.

---

### Post by krimzen85 on 2009-08-06
Gotcha.
 
Two more questions:
 
1. Is the alternate CD going to just be the "core" desktop essentials? Or am I going to have all the bells and whistles of a standard PC desktop? I don't want my server performance to be crippled. Right now Linux Server and all of its packages are taking up 32gb out of 40gb.
 
2. My Servers are only 32 bit compatible, and from the download page, I see: "Alternate CD iso amd64" and "Alternate CD iso"
 
I want to select the option without the 64 right?

---

### Post by SuperSonic4 on 2009-08-06
1. There is also the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") which contains only the very, very basics and should install less to your system if that is what you want

2. Indeed

---

### Post by krimzen85 on 2009-08-06
Thanks. Is that Minimal CD also Alternate CD formatted?
 
 
Also, how do I know which of those files is Gnome / KDE?  I did see Jaunty alot on my server installation, so I guess I should download that.
 
Are they all Gnome?

---

### Post by aysiu on 2009-08-06
> **krimzen85 said:**
> Gotcha.
 
Two more questions:
 
1. Is the alternate CD going to just be the "core" desktop essentials? Or am I going to have all the bells and whistles of a standard PC desktop? I don't want my server performance to be crippled. Right now Linux Server and all of its packages are taking up 32gb out of 40gb. That's a toughy.

There is a more desktop-essentials metapackage called *gnome-core* (and the corresponding *kde-core*). A metapackage is just a pointer to other packages. Since the Alternate CD contains all the packages and bells/whistles *gnome-core* points to but may not include the the actual pointer called *gnome-core*.

Frankly, if you just want a GUI for your server, you're best off installing just *xorg* and *icewm*. Save yourself downloading an entire CD. Maybe APTonCD can help for that?

I don't think Linux servers need GUIs, though.

---

### Post by aysiu on 2009-08-06
> **krimzen85 said:**
> Thanks.  Is that Minimal CD also Alternate CD formatted?
The minimal CD will not have the packages you need. It just pulls packages off the internet. That's how it's able to be so minimal (the whole CD is 10 MB).

---

### Post by krimzen85 on 2009-08-06
Are icewm and xorg in the software library of Linux Server?
 
If not, I am going to have to burn an ISO of anything because I don't have internet out to the servers yet.
 
I like Icewm.  Is there a way to get Icewm onto CD-RW, and then run the sudo commands to install right from the ROM?

---

### Post by SuperSonic4 on 2009-08-06
IceWM is a window manager - it will install a GUI without all the bells and whistles you don't need on a typical server

---

### Post by aysiu on 2009-08-06
> **krimzen85 said:**
> Are icewm and xorg in the software library of Linux Server?
 
If not, I am going to have to burn an ISO of anything because I don't have internet out to the servers yet.
 
I like Icewm.  Is there a way to get Icewm onto CD-RW, and then run the sudo commands to install right from the ROM?
Not necessarily.

You have a computer somewhere with an internet connection, right? Presumably this is the one you would be downloading the CD with.

Instead of downloading a CD, either use an actual Ubuntu installation *or* a Ubuntu live CD on the internet-connected computer, install [APTonCD](http://aptoncd.sourceforge.net/screenshots.html) and use that to fetch the following packages:

icewm
xorg
xterm

Then copy those .deb packages to USB or burn them to CD. You can then either copy the packages from USB to your server and ```
sudo dpkg -i *.deb
``` or add the custom CD as a repository and install using regular *apt-get*.

Advantages of this approach over downloading the Alternate CD .iso: [list][*]The Alternate CD is almost 700 MB to download[*]The Alternate CD you definitely have to burn it to CD, wasting a blank CD instead of just using a USB stick[*]The Alternate CD doesn't contain IceWM or any lightweight window manager. Even *gnome-core* and *kde-core* are far more resource-intensive than any lightweight window manager like OpenBox, Fluxbox, or IceWM.[/list]

---

### Post by krimzen85 on 2009-08-06
You lost me a little bit.

I should mention that 30 hours ago I had no idea what sudo was.  I'm traditionally a layer 1-3 guy, but....short staffing has me doing 4-7, so.....

The only computer I can use with internet connection and admin rights to download is my personal computer, and that has Windows Vista.

Given that fact, is there any way to get Icewm from a machine using Windows Vista that I can take to work tomorrow and install on the server?

---

### Post by aysiu on 2009-08-12
Maybe Keryx might help you?
[http://keryxproject.org/](http://keryxproject.org/)

Apparently, it works on Windows (to get .deb files for Ubuntu).

---

