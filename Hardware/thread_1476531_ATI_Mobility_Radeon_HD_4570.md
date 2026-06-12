---
title: "ATI Mobility Radeon HD 4570"
date: 2010-05-07
forum: Hardware
---

### Post by punchdrunkgrunt on 2010-05-07
I have the above graphics card in my Kubuntu laptop (Acer Aspire 7535G). That is to say, it's *in* my laptop, but it's not doing anything. The 7535G uses a hybrid solution, and I'm stuck with the low power HD 3200 with the fglrx driver. When I was using Karmic I tried switching by changing the BusID in xorg.conf but just ended up looking at a blank screen on reboot.

The ATI release notes for their drivers list the Mobility Radeon HD 4500 as supported, but not the 4570 specifically. Nevertheless searching through the forums reveals a number of people having (minor) problems with their Mobility HD 4570s and fglrx, which suggests it does work with proprietary drivers.

So my question is: Is it possible to get a Mobility Radeon HD 4570 working with fglrx under Kubuntu 10.04? If so, how?

FYI lspci | grep VGA gives
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```

Thanks.

---

### Post by klab233 on 2010-05-09
i have a dell 1557, and seem to have everything working ok, but im not sure exactly what problems are out there and don't know how to check for them....  Is there a good way to check and see if everything is running right, system of tests maybe.  Thanks for all the help

---

### Post by punchdrunkgrunt on 2010-05-10
Bump

:)

---

### Post by jrave on 2010-11-12
I just overcome this step in the problem. I am still stuck with a black screen when I try to use the 4570. Here is what I did to get this far:

I booted in windows
Downloaded and installed the bios update to version 2.04 from acer's website

Note! Acer specifies this bios version is for windows 7 only. which is what I have. I do not know what will happen to your windows install if you use this with vista.

rebooted to ubuntu
removed all traces of flgrx driver:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

ensured I had the correct packages to build the driver:

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 ia32-libs
```

downloaded the latest Catalyst drivers at [http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run")

Built and installed the deb packages for my distro (Maverick - yours may be different. Replace as necessary)

```
sh ati-driver-installer-10-10-x86.x86_64.run --buildpkg Ubuntu/maverick
sudo dpkg -i fglrx*.deb
```

and ran ```
sudo aticonfig --lsa
```

to discover that ati now recognizes both of my cards.

Still working to get the 4570 to display properly. I have read that it works ok as a single card, so I retain hope.

---

### Post by clevertomato on 2010-11-17
For what it's worth, I have a 4570 and have had problems along the way. I fix them, then sometimes a kernel update breaks things, and for the moment they seem to be fixed. I made sure my system was clean of any other installation of fglrx drivers, downloaded catalyst 10-10 from ATI/AMD and installed using the automatic option (didn't build my own package). Catalyst 10-6 worked fine for quite a while, but with the latest kernel (32-25 I think) it stopped doing 3D. So 10-10 works for me now. It's the only way I've been able to get everything working on my Dell Studio 1555 (brightness keys, 3D, suspend/resume) along with noapic setting. BTW I'm running Lucid 10.04.

---

### Post by jastonas on 2011-10-29
> **jrave said:**
> and ran ```
sudo aticonfig --lsa
```

to discover that ati now recognizes both of my cards.

Still working to get the 4570 to display properly. I have read that it works ok as a single card, so I retain hope.

Same problem here. I have Aspire 7535 and I need to use my HDMI cable.

I installed the latest catalyst drivers from ati (11.9) and it recognises my second adapter but I don't know how to change to it!

```
* 0. 01:05.0 ATI Radeon HD 3200 Graphics
  1. 02:00.0 ATI Mobility Radeon HD 4500 Series

* - Default adapter
[CODE]
```[/CODE]

Note: Catalyst center shows me the option to change the GPU and that I need to restart for settings to take effect. After restart, everything is back to normal and back to the 3200 card :(

---

