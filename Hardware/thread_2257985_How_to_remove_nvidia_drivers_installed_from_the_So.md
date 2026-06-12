---
title: "How to remove nvidia drivers installed from the Software &amp; Updates ?"
date: 2014-12-23
forum: Hardware
---

### Post by javierdl on 2014-12-23
I would like to try [installing the 340.46 driver]("http://linuxg.net/how-to-install-the-nvidia-340-46-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems").
I noticed in this [thread]("http://askubuntu.com/questions/542591/ubuntu-14-10-nvidia-driver") it was recommended to [remove manually installed drivers]("http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers") before installing the above mentioned driver. 
Does this apply to drivers from the S&U panel too? 
Or can I just go ahead and install it?

Thanks guys,

JDL

---

### Post by oldfred on 2014-12-24
Even if installed from Ubuntu repository I would uninstall old drivers, just to avoid issues.

 What is installed
dkms status


nVidia may have created this, but it is not standard anymore, so if it does not work that is ok.
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

              sudo apt-get update
sudo apt-get upgrade

    sudo apt-get purge nvidia-*

Double check that everything is removed that is nVidia. Then you can install ppa and update.

There are several ppa, and each usually adds all the newer drivers when released, even the beta versions.
So if you have a very new card/chip from nVidia you may need those newer drivers. But with older cards the new driver may only fix minor issues, but varies by card. I have older card(s) and never had issues with slightly older version in Ubuntu repository.

To check what nVidia has released and what is recommended for your card. Some older cards, now consider the 340 version as legacy or the newest you can install.

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

You can see all the drivers in this ppa. Many others than nVidia also. But has 340,343 & 346
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)

And this one now has both 340 & 346
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by grahammechanical on 2014-12-24
I would activate the open source video driver before purging the proprietary video drivers. Just to be on the safe side of things.

Regards

---

### Post by houstonbofh on 2014-12-24
Note that nvidia-common is a default install and ubuntu-desktop depends on it.  It does not need to be removed to "remove the drivers" as it is used to detect nvidia cards, not drive them.
nvidia-3** and nvidia-settings will need to be removed.  But consider carefully.  I had some of the nvidia ppa's and had problems way to often.  Now I am back to the classic repo versions.

---

### Post by deadflowr on 2014-12-24
> **houstonbofh said:**
> Note that nvidia-common is a default install and ubuntu-desktop depends on it.  It does not need to be removed to "remove the drivers" as it is used to detect nvidia cards, not drive them.
nvidia-3** and nvidia-settings will need to be removed.  But consider carefully.  I had some of the nvidia ppa's and had problems way to often.  Now I am back to the classic repo versions.

?
From my current apt-cache policy
```
nvidia-common:
  Installed: (none)
  Candidate: 1:0.2.91.7
  Version table:
     1:0.2.91.7 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     1:0.2.91.4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```
Curious...

---

### Post by Yellow Pasque on 2014-12-25
> **deadflowr said:**
> ?
nvidia-common ... Curious

nvidia-common is obsolete in Ubuntu 14.04/Trusty
> This is a transitional package for ubuntu-drivers-common. You can remove it after upgrading.

---

### Post by deadflowr on 2014-12-25
> **Temüjin said:**
> nvidia-common is obsolete in Ubuntu 14.04/Trusty

Thanks, my curiosity has been sated. 

I would assume since the OP mentions Software and Updates that Trusty or up is what they are running.
"Software and Updates" did not/does not exist for Precise.

---

### Post by javierdl on 2014-12-25
Thank you all so much for your replies. I wish all this video cards drivers business was way simpler though :(

JDL

---

### Post by javierdl on 2014-12-26
I switched to Win8.1 to see what Nvidia driver I'm using there, it's 331.65. With it Blender can make use of BOTH graphics cards for rendering with CUDA, which is just what I want to do in Ubuntu. Unfortunately that [driver is only for Windows]("http://www.nvidia.com/download/driverresults.aspx/68799/en-us") :(

JDL

---

### Post by Yellow Pasque on 2014-12-26
You should be able to use multiple GPU's in Linux Blender with any recent Nvidia driver. 
>  Can I use multiple GPUs for rendering?
Yes, go to User Preferences > System > Compute Device Panel, and configure it as you desire. 
-- [http://wiki.blender.org/index.php/Doc:2.6/Manual/Render/Cycles/GPU_Rendering](http://wiki.blender.org/index.php/Doc:2.6/Manual/Render/Cycles/GPU_Rendering)

> I wish all this video cards drivers business was way simpler though
It would be simpler if Ubuntu kept their nvidia drivers updated...

---

