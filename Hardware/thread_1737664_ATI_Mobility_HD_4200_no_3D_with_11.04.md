---
title: "ATI Mobility HD 4200 no 3D with 11.04"
date: 2011-04-23
forum: Hardware
---

### Post by ddarsow on 2011-04-23
My ATI graphics card works fine with 10.04, but am unable to get either Unity(3d) or even classic Gnome with 11.04. Unity 2D works. I have the FGLRX driver enabled.
Anyone got a solution to this?

---

### Post by coffeecat on 2011-04-23
Yes. Use the open source driver, not the fglrx. I have the Mobility Radeon HD4200 on one of my laptops and 11.04/Unity works just fine with the open source ATI driver. So well in fact that I wouldn't dream of using the fglrx driver.

The fglrx driver can take a bit of purging. It can be as persistent as it is irritating. You might find this link helpful:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by ddarsow on 2011-04-23
That didn't do it. Same thing still happens, I can't get past the login screen (unless booting to a Unity 2D session). Neither Unity 3D nor Classic Gnome will boot. Additionally, I now get screen tearing and artifacts when opening or closing windows in Unity 2D which I did not get with the proprietary FGLRX driver.

I tried both the 1st and 2nd options from the previous link with the same results. Could it be something other than the video driver? I was just assuming it was due to the video driver. This laptop (DEll Inspiron M5010) worked perfectly with 10.04, but I really like the Unity interface and would prefer to have 11.04 on this machine although my main production machine will remain 10.04 till 12.04.

---

### Post by coffeecat on 2011-04-24
> **ddarsow said:**
> I tried both the 1st and 2nd options from the previous link with the same results.

If the 1st option is the one headed "How it works", the try the option "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch", to be sure there is absolutely no trace of fglrx still interfering. I find Unity/11.04 to be absolutely pain-free with the same video card and the open source driver. Although i haven't tried 2-d Unity - I haven't needed to.

Rather confusingly, ATI make a Radeon HD4200 (no mobility in name) which is different from the mobility 4200. To be sure that we are really talking about the same video chipset, post the output of:

```
lspci | grep VGA
```I'll do the same from my ATI laptop. Also, I haven't used Unity on that laptop for a week or so, so I'll update it to make sure that a recent update hasn't broken the video driver for the mobility HD4200. I'll post back later.

---

### Post by coffeecat on 2011-04-24
> **coffeecat said:**
> I'll post back later.

I'm posting from my laptop, freshly updated and rebooted within the hour. Unity, compiz and 3d are still working fine with the open source ATI driver. Here's my output from lspci to compare with yours:

```
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]

```

If your lspci output is the same, and running all the commands under "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch" doesn't fix this, I have two more suggestions:

Installing the fglrx driver creates an xorg.conf file which is not needed for the ati/radeon driver. Those instructions don't explicitly tell you to remove xorg.conf, although "sudo dpkg-reconfigure xserver-xorg" may do this - I don't know. To be sure that a residual xorg.conf is not interfering with the ati driver,r un these commands as well:

```
cd /etc/X11
sudo mv xorg.conf xorg.conf.old
```

If all this fails, boot up from the Natty live CD/USB. If you get Unity/3d then this means that something is still wrong with your hard drive installation. If not, then I'm out of ideas.

---

### Post by ddarsow on 2011-04-24
```
$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
```

---

