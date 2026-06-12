---
title: "Dual Monitors: help get HD5400 working beside HD4200"
date: 2011-02-06
forum: Hardware
---

### Post by misterbiskits on 2011-02-06
I am using Ubuntu 10.04.  I have been trying to get my second video card (for dual monitors) working, but no dice.
These are the cards I have:
```
mike@mike-linux:~$ aticonfig --lsa
* 0. 01:05.0 ATI Radeon HD 4200
  1. 02:00.0 ATI Radeon HD 5400 Series
* - Default adapter
```I am trying to get the 5400 working beside the 4200 which works fine.  Catalyst Control Center shows an unknown adapter for the 5400, and I have the option to enable it by choosing "Single Display Desktop (Multi Desktop)".  If I do this the system hangs at reboot, somewhere before the login screen.
If it matters the 4200 is onboard and default in the mobo bios.  The 5400 is pci-e.
I know there are linux drivers available for the HD5xxx series, I downloaded them here [(link)]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English"), but installing them (maybe I did it wrong) wound up breaking packages associated with ATI, fglrx etc., disabled my 3D capability on the 4200, and had no effect on the 5400.
After much newbie effort I've now fixed the broken packages, and have my 4200 working fine again with 3D.
Please help.

---

### Post by misterbiskits on 2011-02-06
well, add [this]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually") to the list of ubuntu guides that don't work.
Now to figure out how to get the drivers installed back on my 4200 as System>Administration>Hardware Drivers no longer gives me the option to install the proprietary drivers.
Frustrated.
edit:  installed fglrx, driver was made available, 4200 working now.

---

### Post by misterbiskits on 2011-02-06
if I set the 5400 as the primary boot device in the motherboard bios, and boot up, everything works fine off that card (the 5400) with the proprietary driver.  I think that rules out a compatibility/support problem.  
However, there is no longer an "unknown adapter" (the 4200) in the Catalyst Control panel, and it doesn't show in aticonfig:
```
mike@mike-linux:~$ aticonfig --lsa
* 0. 01:00.0 ATI Radeon HD 5450
* - Default adapter
```I see it's now called a 5450.  I am not sure what it actually is.
=/
I must say I am impressed at Ubuntu's resiliency after how much and how badly I messed up and corrected these drivers over the last couple of days.  The doesn't happen with the other operating system.
Now, where is that famous community support?  C'mon guys look at me suffering here - surely someone knows how to set up these two cards together?

---

### Post by misterbiskits on 2011-02-06
Although I tried it before to disasterous effect, enabling the 5450 in catalyst and rebooting has done the trick.  I now have two monitors.  Why?  Who knows.
After enabling Xinerama in Catalyst I can now move stuff back and forth between them, yay.  
I no longer have 3d, and taskbar icons, AWN look like crap. 
I'll work on that.

---

### Post by misterbiskits on 2011-02-11
If anyone should stumble upon this thread, [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually"), mentioned in an above post, worked after a clean install.  Condensed version shown below.

```
# Install the prerequisite packages:
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

# Download the latest Catalyst package.
cd ~/; mkdir catalyst11.1; cd catalyst11.1/
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-1-x86.x86_64.run

# Create .deb packages.
sudo sh ati-driver-installer-11-1-x86.x86_64.run --buildpkg Ubuntu/lucid

# Install .debs.
sudo dpkg -i fglrx*.deb

sudo aticonfig --initial -f --adapter=all

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

reboot

```

---

