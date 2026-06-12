---
title: "GeForce GT 240M"
date: 2009-09-02
forum: Hardware
---

### Post by NertSkull on 2009-09-02
I have discovered that a driver does not exist (yet, hopefully) for this video card.  Does anyone have any suggestions on a work-around?  I love ubuntu and don't want to be pushed away because I can't get simple graphics working.  I can't get videos, or desktop effects to work or similar things because there is no linux driver.  

Any help would be GREATLY appreciated.

More info:

The card is the NVIDIA GeForce GT 240M. 

[http://www.nvidia.com/object/product_geforce_gt_240m_us.html](http://www.nvidia.com/object/product_geforce_gt_240m_us.html)

The drivers listed there take me to the 200 series drivers.  But the 240M is not listed in the 200 series drivers.  I tried installing other 200 series drivers but to no avail.  I could get them installed, but I ended up with 6 mini screens on my laptop screen.

Is there any way I can get an idea if they are even working on a linux driver for this card?  Or am I just out of luck?  

I really appreciate any help with this.

---

### Post by NertSkull on 2009-09-02
I've found a few places with beta drivers that claim they can make the 240M work (they all actually say they are for the 240, not the 240M, I don't know if that matters).

Anyway, I've tried installing those drivers but I end up with 6 crappy resolution screens on my laptop.  Clearly I'm not installing it right.  Does anyone have any advice on this?

I'm thinking I might need to do something more because in some of the documentation I've been reading it mentions having headers, development packages, etc installed.  Do I need to do that?  How do I do that?

Thanks

---

### Post by BearPowers on 2009-11-09
Bumping this cause I am getting a laptop with this card.

---

### Post by mivo on 2009-11-09
According to a German Ubuntu forum, 9.10 should support the 240M out of the box. The latest Nvidia drivers seem to support it in any event. (Some laptops have a modified version of the chipset, in which case you may be out of luck in regard to Linux. Acer comes to mind.)

---

### Post by tobiasb on 2009-11-11
[http://www.multicom.no/PartDetail.aspx?q=p:10578807;c:100560](http://www.multicom.no/PartDetail.aspx?q=p:10578807;c:100560)

would you guys reccomend med getting this one or not? its with that screen card and its an acer :)

Thanks in advance.

Tobias
:KS

---

### Post by tobiasb on 2009-11-11
btw, it seems the driver for the screen card is out a week ago: 

[http://ubuntuforums.org/showthread.php?t=1303982](http://ubuntuforums.org/showthread.php?t=1303982)

---

### Post by tobiasb on 2009-11-11
I just called the support there and they dont have the gt 240m on that laptop it was a typoo on the webpage :( sorry for bothering you guys.

---

### Post by mivo on 2009-11-11
Acer is one of those manufacturers who sometimes alter chipsets, which means that they don't work with the official Nvidia drivers, but require you to use Acer's drivers. That is somewhat acceptable Windows (though not really), but fatal for Linux. Needs to be checked/googled on a case by case base, though.

---

### Post by kkm on 2009-11-15
Go to System->Administrtion->Hardware Drivers. It will search for the driver and will display the driver. click on the activate driver butten and after some time when the installation is over, reboot the machine in order to load the driver in to kernel. After reboot you will get 6 mini screens. then click on alt+ctrl+1 and go to a text terminal to work better. login with your user name and enter the command 'sudo bash'. After that;
do, 
cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf.newbackup
vi /etc/X11/xorg.conf
there you will see a section called "Device' there add the below line

 Option "ModeValidation" "NoTotalSizeCheck"

After the editing, the Device section will look like as follows:-

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "ModeValidation" "NoTotalSizeCheck"


This will do the trick. Reboot your machine. But this also giving some problem. After you reboot and login to your account every thin is okay. But when you log out, X server resets and the screen gets flickery. Any body has any idea ?

---

### Post by steve8track on 2009-11-19
If you need to try some Nvidia drivers by installing them yourself, in case it's helpful, I'll try posting a little tutorial here.  I am away from my ubuntu laptop right now, so I'll have to go by memory.

First, you'll have to install the linux-headers from the repositories.  It will be something like:

```
sudo apt-get install linux-headers-`uname -r`
```

Then, you'll want to download the latest nvidia drivers:

[Nvidia Drivers]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Then, you'll need to turn off gdm (the login manager), so log out (I don't know if this works with the new gdm the same, I have only done this with 9.04 Ubuntu Studio).

Go to a Virtual Console (Ctrl+Alt+F1 or another F# key for example, F7 takes you back to the login or one of the numbers near 7).

Login the the virtual terminal, then:

```
sudo /etc/init.d/gdm stop
cd /Desktop #go to the directory where you downloaded the Nvidia drivers
sudo sh Nvidia-190.0.whatever.sh --update

```

Something like that, maybe --update is wrong, you can probably use --help to see what other options are.  Without the flag the driver you downloaded will be used, with it, the script will try to download any later versions for you.

```
sudo /etc/init.d/gdm restart

```

I hope this works for you or is somehow helpful.  This way you can get newer drivers than are in the repository, but it will require you to rerun it every time new linux headers are installed, so don't delete the drivers unless you want to download them again, which can be difficult if you forget to do that until after your screen is broken.  Then you'll likely log in with the older headers from grub.

Good luck and let us know if this video card works well or not after you do.

PS: I forgot, you also would need to set the driver in xorg.conf to use nvidia.

This also might be useful:
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html")

---

### Post by kkm on 2009-11-21
I run the command. The command is as follows:-

root@kaushikam:~# ./NVIDIA-Linux-x86-190.42-pkg1.run  --update

it told me that the drivers are up to date. so still the problem exists.

---

### Post by realzippy on 2009-11-21
[B]./NVIDIA-Linux-x86-190.42-pkg1.run
[/B]

is the command to install the driver.The --update option checks newer,but 190.42 **is** the newest.

---

### Post by kkm on 2009-11-21
I forgot to tell you that when I checked in the net I found out that the Ubuntu team is giving the driver version 180, while the new one is available with the nvidia (190.42). Hence i downloaded it and installed. Now I am having the driver version 190.42. Still the problem remains.

---

### Post by bdr529 on 2009-11-22
> **kkm said:**
> Go to System->Administrtion->Hardware Drivers. It will search for the driver and will display the driver. click on the activate driver butten and after some time when the installation is over, reboot the machine in order to load the driver in to kernel. After reboot you will get 6 mini screens. then click on alt+ctrl+1 and go to a text terminal to work better. login with your user name and enter the command 'sudo bash'. After that;
do, 
cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf.newbackup
vi /etc/X11/xorg.conf
there you will see a section called "Device' there add the below line

 Option "ModeValidation" "NoTotalSizeCheck"

After the editing, the Device section will look like as follows:-

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "ModeValidation" "NoTotalSizeCheck"


This will do the trick. Reboot your machine. But this also giving some problem. After you reboot and login to your account every thin is okay. But when you log out, X server resets and the screen gets flickery. Any body has any idea ?

Thanks for your advice!  It works for me too. I've got a Packard-Bell Notebook with the GT 240M. But the same flickery screen after log out.

---

### Post by NertSkull on 2009-12-01
I don't know if this is still relevant to anyone.  But this is how I finally got the card working on my computer.

This is where I detailed how I fixed it

[http://www.nvnews.net/vbulletin/showthread.php?p=2079295](http://www.nvnews.net/vbulletin/showthread.php?p=2079295)

Here is another post with more information from others.  Just in case others haven't found it and it may potentially be useful.

[http://ubuntuforums.org/showthread.php?t=1255793](http://ubuntuforums.org/showthread.php?t=1255793)

I know some of this is a few months old.  But installed Karmic on my laptop about 2 weeks ago (right after a new set of drivers was released by Nvidia directly showing 240M support) but I still couldn't get it to work.

I'm still have suspend/fuzzy issues with the screen, but at least it works most of the time.

Hope this helps at lest someone in addition to the wonderful advice found above.  I think its pretty much the same stuff but explained differently.  I know I always have to have things explained 10 times before I can catch on.

---

### Post by kkm on 2009-12-22
you can find another good advice at "http://www.nvnews.net/vbulletin/showthread.php?p=2116312". But still the fuzzy screen problem remains

---

### Post by cajual on 2009-12-22
I have posted and reviewed the flicker/fuzzy issue extensively, but it remains to be seen as to whether or not there is a fix.  You can check my post for the bug number in order to post that it affects you.  The more people complain of the bug, they higher priority it may get.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/482456)

---

### Post by kkm on 2010-01-05
hi, cajual


I did as you said.

---

### Post by kkm on 2010-02-22
nvidia has released beta drivers. you can find out at "ftp://download.nvidia.com/XFree86/Linux-x86/195.36.03/". I installed NVIDIA-Linux-x86-195.36.03-pkg0.run	and now every thing is fine. No fuzzy screen any more.

---

### Post by NertSkull on 2010-03-07
Oh thats pretty awesome.  I hope you are right.  I'm tied up right now away from my laptop, but hopefully next week I'll check this out and see if it works for me as well.

Thanks for the heads up.

---

### Post by pingu1 on 2010-03-08
Anybody got experience with downloading nVidia's drivers from their website and then using compiz with these drivers? Does it generally work fine?

---

### Post by realzippy on 2010-03-08
yes.it works perfectly!

---

### Post by pingu1 on 2010-03-08
Thank you realzippy!
Great!

---

### Post by NertSkull on 2010-03-08
So maybe I'm searching in the wrong place.  But it looks like this new driver has a bug and has been pulled from the nvidia site.

[http://www.nvnews.net/vbulletin/showthread.php?p=2178512](http://www.nvnews.net/vbulletin/showthread.php?p=2178512)

[http://www.nvnews.net/vbulletin/announcement.php?f=14](http://www.nvnews.net/vbulletin/announcement.php?f=14)

So it appears any of you who have installed it may want to check things are running okay for you.

If anyone sees this get fixed, let us know.  Thanks!

---

### Post by NertSkull on 2010-03-17
So it appears a day ago or so they released 195.35.15 which supposedly fixes the fan control issue.

Don't know if it fixes the screen flicker or not.  But I intend on trying to install this later today and I'll post how it goes on my computer.

Hopefully it works.

---

### Post by NertSkull on 2010-03-19
Works for me.  The new drivers make everything great.  No more fuzzy screen, no more user switching problems, suspend works great, all problems I was having are fixed.

The only thing that I had to do was install the drivers under the right linux headers, and everything was good from there.

---

