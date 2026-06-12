---
title: "Ubuntu vs Fedora LiveCD Nvidia"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by measekite on 2009-03-06
**I would like to know why the following facts are the way they are:**

[B]
Point of Reference[/B]
I have been using Feisty 7.04 for over two years.  I have a GForce 6600 Nvidia card attached to a Viewsonic DVI monitor.  After installation I only got 800x600 in resolution.  I had to chase down the drivers directly from Nvidia and do a somewhat confusing install---cannot remember details now) to get it to work in the native 1680x1050.  I also had to chase down a special driver for my Canon IP4000 and install it twice; once for each paper source and duplex was not available.

Now it is getting close to upgrade so I created LiveCDs for a few distros and am comparing Ubuntu Intrepid with Fedora 10.  Fedora seems a little faster and less of a problem.

**Results of quick test:**
[COLOR=Teal]**[SIZE=4]Fact1[/SIZE]**
**Fedora**[/COLOR]
Fedora LiveCD automatically found my nvidia card and automaticaly set the resolution correctly.

I installed and tested the suggested driver for my Canon IP4000 and all features worked properly.

[B][SIZE=4]
[/SIZE][/B][COLOR=Teal]**[SIZE=4]Fact2[/SIZE]**
**Ubuntu**[/COLOR]

Three versions after Feisty the Intrepid LiveCD did not install the nvidia driver.  When I issued the command to install it manually from the repository the machine locked.  All I could get was 800x600.

I did not test, as yet the Canon printer.  I will update this post when I get a chance to test it.

==================

I do not understand why Fedora was able to correctly install nvidia and Ubuntu could not.  My first impression is Fedora requires less work and aggravatiion for me.  (But the Ubuntu forum is light years ahead of the Fedora Forum plus it is more friendly.)

Also I really like the Fedora colors and do not prefer Ubuntu brown, tan and red.

[SIZE=5][COLOR=RoyalBlue]Your comments are welcome.:popcorn:[/COLOR][/SIZE]

---

### Post by PilotJLR on 2009-03-06
FACT 1:
Fedora uses a newer "nv" driver, which is an open source 2D only nvidia driver. It works quite well in 2D, which is why the resolution is correct. Note that it does NOT work in 3D or provide OpenGL.

FACT 2:
Really hard to say why... all I can tell you is installing the proprietary nvidia driver has always been simple for me with Ubuntu. Try again with a current version, and then let's troubleshoot if needed.

The important takeaway is that the open source 2D driver and the proprietary driver are different things! Both Fedora and Ubuntu are very good distros, though in different ways.

FACT: Brown bears are better than black bears.  :)

---

### Post by measekite on 2009-03-07
> **PilotJLR said:**
> FACT 1:
Fedora uses a newer "nv" driver, which is an open source 2D only nvidia driver. It works quite well in 2D, which is why the resolution is correct. Note that it does NOT work in 3D or provide OpenGL.

FACT 2:
Really hard to say why... all I can tell you is installing the proprietary nvidia driver has always been simple for me with Ubuntu. Try again with a current version, and then let's troubleshoot if needed.

The important takeaway is that the open source 2D driver and the proprietary driver are different things! Both Fedora and Ubuntu are very good distros, though in different ways.

FACT: Brown bears are better than black bears.  :)

**Thank you for you reply as it was thoughtful.**

I plan on making my upgrade (2 machines) by June and will stay with Feisty until then when things slow down for me.

I plan on choosing between the latest Ubuntu and the latest Fedora.  Right now I am on the fence but leaning toward the Fedora OS but feel the this Ubuntu support forum is far superior to the Fedora Forum.  It seems that more propeller heads gravitate toward Fedora and even more to Slackware and Gentoo.

You seem to be familiar with both distros.  I assume that your preference is Ubuntu.  Would you explain why other than just liking the look and feel?

The other thing that I mentioned is that with the Fedora LiveCD I was able to install my Canon IP4000 and have all of the features including duplex.

In Feisty I had to kludge and manipulate and finally am able to do most of the stuff but not duplex and borderless photos.  I do not understand what drivers their distro has that Ubuntu does not.  That is another reason why I am leaning toward Fedora.

I would like to see reasons why I should stay with Ubuntu.  It appears to be the most popular distro.

Another favorable Fedora feature is that for the year of support they provide (not 18 months--unfortunately) they will upgrade the applications in the repo to new versions where Ubuntu does not.

However, if a new version comes out a couple of months after an Ubuntu release you can get it in another 4 if you want to upgrade the OS.
[B]
Speaking of Upgrades[/B]

It would not be so bad if you could automatically update to the new release and all of the configuration is done for you but I hear that is not the case.  I also hear it is better to reformat and do a clean install.  What do you think on that?

---

### Post by tommcd on 2009-03-07
> **measekite said:**
> [B]
I would like to see reasons why I should stay with Ubuntu.  It appears to be the most popular distro.

You may be interested in this:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=1)
Fedora and Ubuntu performance was very close in those benchmarking tests at Phoronix.
Personally, I think APT is a more elegant package manager than Yum. I just have a preference for Debian based distros over .rpm based distros. Both Fedora and Ubuntu are very good though, and performance is similar. So it is your choice.
> **measekite said:**
> [B]

Speaking of Upgrades[/B]
It would not be so bad if you could automatically update to the new release and all of the configuration is done for you but I hear that is not the case.  I also hear it is better to reformat and do a clean install.  What do you think on that?

Doing a dist-upgrade from 7.04 to 8.10 will likely not work, and is not recommended. You should upgrade in sequence (i.e. 7.04 > 7.10 > 8.04 > 8.10). You should do a clean install of Ubuntu 8.10 instead. It will be much faster, easier, and will give you a cleaner system.

For the nvidia driver, just install **nvidia-glx-180** from the Ubuntu repos. It should work just fine with the Nvidia 6600.

---

### Post by PilotJLR on 2009-03-07
Both Fedora and Ubuntu are good distros... personally, I use Ubuntu, though I've spent a lot of time with Fedora as well. A few years ago, I used only Fedora.

The reason I've changed to Ubuntu is that I got tired of updates breaking things... Fedora is a testbed, so developers take risks and the users sometimes lose functionality. The compelling reason to use Fedora is that you get to see features that other distros (such as Ubuntu) may adopt in 6+ months. Innovation like plymouth, newest Gnome and X, newest KVM, etc, all happen in Fedora first. Red Hat basically funds all this.

But, if you want stability and consistency... Ubuntu is a better pick. Aside from the location of config files and package manager tools, most Linuxes are the same, so your skills will 90% transfer between Ubuntu and Fedora.

What I do now is keep Ubuntu on my workstation, and test out Fedora in a virtual machine.

---

### Post by measekite on 2009-03-07
> **PilotJLR said:**
> Both Fedora and Ubuntu are good distros... personally, I use Ubuntu, though I've spent a lot of time with Fedora as well. A few years ago, I used only Fedora.

The reason I've changed to Ubuntu is that I got tired of updates breaking things... Fedora is a testbed, so developers take risks and the users sometimes lose functionality. The compelling reason to use Fedora is that you get to see features that other distros (such as Ubuntu) may adopt in 6+ months. Innovation like plymouth, newest Gnome and X, newest KVM, etc, all happen in Fedora first. Red Hat basically funds all this.

But, if you want stability and consistency... Ubuntu is a better pick. Aside from the location of config files and package manager tools, most Linuxes are the same, so your skills will 90% transfer between Ubuntu and Fedora.

What I do now is keep Ubuntu on my workstation, and test out Fedora in a virtual machine.

While I still have not decided what you said makes a lot of sense.  Any way you have time to provide some details on how you set up a virtual machine in Ubuntu (which one) and how you run Fedora in it?

Also, I would imagine you could run both Fedora and Windows in this virtual machine at the same time.

---

### Post by PilotJLR on 2009-03-07
Due to work reasons, I use VMware Workstation... for a free option, I'd recommend VirtualBox, which is very similar.

By installing VirtualBox, you can test out anything you like (be it any Linux or Windows), without affecting the host system. It's a great way to test distros before you install them onto physical hardware.

Here is some good info: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

