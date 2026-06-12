---
title: "Could not apply the stored configuration for monitors"
date: 2013-04-14
forum: Hardware
---

### Post by saulspatz on 2013-04-14
I am an ubuntu newbie.  I generally run a laptop with a second monitor plugged in.  Today, after the update manager ran, I got the error message, "Could not apply the stored configuration for monitors."  My screens are all screwed up.  The resolution is wrong on both monitors, and instead of having a dual monitor display, I have the same display on both monitors.

I googled the error message and found the advice to remove  ~/.config/monitors.xml.  I did so, and the error message went away, but the screens are still screwed up.  Can someone please tell me how to put it back the way it was?

---

### Post by TheFu on 2013-04-14
Dual monitor setup is different based on the GPU driver used. Are you Intel, AMD or nVidia?

Sometimes reinstalling the video driver after a kernel update will reset the settings nicely.

---

### Post by saulspatz on 2013-04-14
> **TheFu said:**
> Dual monitor setup is different based on the GPU driver used. Are you Intel, AMD or nVidia?

Sometimes reinstalling the video driver after a kernel update will reset the settings nicely.

Thanks for the quick response.

lspci gives:
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])

Please explain how to reinstall the  driver.

---

### Post by TheFu on 2013-04-14
> **saulspatz said:**
> Thanks for the quick response.

lspci gives:
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])

Please explain how to reinstall the  driver.

I don't know how to do it with Intel, but with nvidia or AMD/ATI, it comes down to a** sudo apt-get --reinstall install {package_name}**
In theory, the DKMS tool would see a new kernel and re-link the GPU drivers into the new kernel automatically. Sometimes that seems to be boinked and I've had to manually for a re-link. Doing a re-install of the driver package would be the easiest way that I know.

```
$ dpkg -l |grep nvidia
ii  nvidia-current                             290.10-0ubuntu1~lucid~xup1                      NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases                  290.10-0ubuntu1~lucid~xup1                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                            290.10-0ubuntu1~lucid~xup1                      Tool of configuring the NVIDIA graphics driv

```
Perhaps running a **dpkg -l|grep -i intel** would provide a hint?  Also, looking through the **lsmod** list for intel GPU driver could be helpful too. Sorry, I'm not much help.

---

### Post by saulspatz on 2013-04-14
> **TheFu said:**
> I don't know how to do it with Intel, but with nvidia or AMD/ATI, it comes down to a** sudo apt-get --reinstall install {package_name}**

Perhaps running a **dpkg -l|grep -i intel** would provide a hint? 

This is the part of dpkg that looks like it might be relevant:
ii  xserver-xorg-video-intel                  2:2.17.0-1ubuntu4.3                     X.Org X server -- Intel i8xx, i9xx display driver
rc  xserver-xorg-video-intel-lts-quantal      2:2.20.9-0ubuntu2~precise2              X.Org X server -- Intel i8xx, i9xx display driver

Would you guess that I should try reinstalling both of these?  If so, would the order matter, do you think?

Thanks again for replying so quickly.

---

### Post by TheFu on 2013-04-14
> **saulspatz said:**
> This is the part of dpkg that looks like it might be relevant:
ii  xserver-xorg-video-intel                  2:2.17.0-1ubuntu4.3                     X.Org X server -- Intel i8xx, i9xx display driver
rc  xserver-xorg-video-intel-lts-quantal      2:2.20.9-0ubuntu2~precise2              X.Org X server -- Intel i8xx, i9xx display driver

Would you guess that I should try reinstalling both of these?  If so, would the order matter, do you think?

Thanks again for replying so quickly.

The Quantal version seems to have been removed already. That's what the "rc" at the beginning means, I think. Could that be the issue - going from 2.20.9 to 2.17.0?  I don't know, just asking.

---

### Post by saulspatz on 2013-04-14
> **TheFu said:**
> The Quantal version seems to have been removed already. That's what the "rc" at the beginning means, I think. Could that be the issue - going from 2.20.9 to 2.17.0?  I don't know, just asking.

I have no idea; like I said, I'm a newbie.  Is there a way to find out what the update manager did yesterday, do you know?

---

### Post by saulspatz on 2013-04-14
Problem solved.
I went to System Settings/Displays and reconfigured dual monitors.  All that happened, apparently was that the settings I had before got trashed.  When I did this originally, the correct monitor resolutions were detected by the system, I think.  At least I don't recall having set them myself.  That's why I thought I had to get the resolutions correct before setting up the dual monitors again.   A goo link for setting up dual monitors is [http://www.thegeekstuff.com/2009/08/ubuntu-tips-how-to-setup-dual-monitor/](http://www.thegeekstuff.com/2009/08/ubuntu-tips-how-to-setup-dual-monitor/)
The one thing it doesn't mention is that if you find that you have to drag a window off the wrong edge of the screen to move it to the other monitor, all you have to do is drag the icon for the monitor on the Display Settings window to the other side.

---

