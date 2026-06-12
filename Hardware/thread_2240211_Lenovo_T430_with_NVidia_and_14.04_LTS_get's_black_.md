---
title: "Lenovo T430 with NVidia and 14.04 LTS get's black screen - BIOS Settings"
date: 2014-08-18
forum: Hardware
---

### Post by Silverdragondw on 2014-08-18
Hello all,

I have had problems with my Lenovo T430 with built in nVIDIA NVS 5400M. After installing the propietary driver from nVIDIA 331, the laptop screens mostly stays black. Even the background light is off (as it would have no power)
A setting in the BIOS is confusing the driver/Ubuntu. It has set in the BIOS to: Config -> Display -> Discrete Graphics, NOT to NVIDIA Optimus (as it is set by default).

---

### Post by fireflower on 2014-08-19
I'm surprised there aren't more threads on this issue in this forum. I've tested 4 distros of 14.04.1 LTS and they all explode after I switch to proprietary drivers for my Nvidia GPU. The [Linux Mint graphics hardware forum](http://forums.linuxmint.com/viewforum.php?f=59) is a kind of hell for lost souls whose only sin was using a Nvidia GPU. I realize Canonical hates them but Mint is still a flavor of Ubuntu, which means if something is wrong with Mint it's also gone wrong with Canonical's flagship Ubuntu. Lo and behold, upon testing, vanilla Ubuntu explodes too, as does Ubuntu Gnome. No, updating repositories and installing the latest greatest drivers doesn't work, except that it crashes even faster. What makes it even worse is these crashes are often unrecoverable, as in, the machine no longer boots. Thus far the only difference is I have been able to resurrect flagship Ubuntu after a few boots by managing to switch back to stock open-source drivers using a GUI that looked like it was a time-traveller from 1980. Mint itself was unbootable, but you can in fact change the graphics drivers using the live USB, so it was recoverable, and in a far more elegant manner.

---

### Post by yancek on 2014-08-19
I've seen numerous posts here also regarding problems with Nvidia drivers and Ubuntu  I have an HP Desktop with an Nvidia GeForce 6150SE nForce 430 graphics card and continue to experience problems with Ubuntu 14.04.  It is actually a little bizarre as each time I do a cold boot to 14.04, the bottom half of the screen is black and the top half has horizontal lines (series of dashes actually).  I can't login or do anything.  If I power off manually and then power on again, it boots to the login screen, no problem and I can login and use it.  Obviously, it is not my primary system so it doesn't really matter to me.

I've installed the recommended proprietary/tested nvidia drivers.  I've had 14.04 installed for 2 months and have tested this numerous times and I think I was actually able to cold boot to login on one or two occasions.  This problem doesn't exist with Ubuntu 12.04 on the same computer.  I also have Slackware 14.1, PCLinuxOS, Mint 13 & 17, Linux Lite, Zorin 9 and CentOS on the same machine and the only system with this problem is 14.04 which leads me to believe it is a combination of Ubuntu 14.04 and the Nvidia drivers.

---

### Post by fireflower on 2014-08-19
Found a fix: [Noobs lab]("http://www.noobslab.com/2013/08/latest-nvidianvidia-optimus-drivers-for.html") (or is it noob slab?) has a year-old post from when 13.10 was new.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```
Worked for me. I would've posted an hour ago but I was playing Minecraft. It's an ideal stress-tester to ensure your problem has been fixed. It needs 3D rendering support to play, and that is exactly what the Nouveau drivers aren't allowed to do by Nvidia.

As to why a company would make an intentionally defective product, we must delve into politics. Microsoft is trying to use Nvidia to make life difficult for Linux. The Ubuntu family of distros is eating up more of Microsoft's market share. Linus literally gave Nvidia the finger over it. Hopefully Nvidia will one day drop the "trade secrets" crap and open its code, so Canonical doesn't have to make its own users go through this crap.

---

### Post by Tryfon on 2014-09-15
fireflower your solution didn't work for me. Is there perhaps anything in your configuration that you forgot to mention?

---

### Post by anika200 on 2014-09-15
> **Tryfon said:**
> fireflower your solution didn't work for me. Is there perhaps anything in your configuration that you forgot to mention?
Do you have the "nomodeset" in the linux boot line in grub?

---

### Post by Tryfon on 2014-09-16
Is the "nomodeset" option required for the NVidia proprietary drivers or for the Nouveau? I am asking because I am interested into using the NVidia ones.

---

### Post by anika200 on 2014-09-16
> **Tryfon said:**
> Is the "nomodeset" option required for the NVidia proprietary drivers or for the Nouveau? I am asking because I am interested into using the NVidia ones.
Oh, I thought you were using Nvidia drivers. (whoops I thought you were the op) Yes there are certain Nvidia boards that need the nomodeset option.
I do not think the Nouveau drivers need that solution however I am not familiar enough with Nouveau to know for sure.

---

### Post by LaJuan on 2014-10-12
Hi,

I'm running 14.04 LTS 64Bit and it runs just fine. Can't figure out why I can't get the finger scanner to work to lock and unlock the unit. Have you tried that feature?

---

### Post by Nate_Gallaher on 2014-10-30
I had a similar problem recently.  I also found that turning off AMT, RapidStart, and VT-d in the BIOS allowed me to boot into X successfully.  Prior to doing that, I would boot to a black X screen using both the nouveau and nVidia drivers.

---

