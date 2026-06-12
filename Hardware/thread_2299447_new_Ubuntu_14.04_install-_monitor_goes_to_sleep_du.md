---
title: "new Ubuntu 14.04 install- monitor goes to sleep during booting"
date: 2015-10-18
forum: Hardware
---

### Post by jrn34exp on 2015-10-18
While first booting my system, the monitor says "no signal" and goes to sleep....but once I turn the power off and right back on, it performs just fine. When I installed my current version, I chose to encrypt my system; this is the first time I have chosen to encrypt, and the first time I have had this issue, so I assume it may have something to do with the encryption running. I can hit delete while it boots, or even after it goes to sleep, and a window appears where I can type my encryption password, and then the boot advances properly. What is wrong?

---

### Post by righN on 2015-10-18
I had this problem when installed Ubuntu 15.04 and fixed it with installing graphics drivers.

---

### Post by jrn34exp on 2015-10-18
Thanks for your reply. I have tried to install drivers for both my monitor and my graphics card, but everything I've read and done gets me nowhere....It's an HP S2031 monitor with a Radeon S740 /x2100 card. When I go to my system settings and pull down the "additional drivers" tab to check, there is nothing available. This is probably my 4th install of Ubuntu with the same system, and this is the first time I have had this issue.

---

### Post by buzzingrobot on 2015-10-19
Were the previous 3 installs on the same machine with the same Radeon but without the disk encryption?  Did those installs boot normally?

Did "Additional Drivers" offer a driver for the Radeon on those installs?

---

### Post by righN on 2015-10-19
[TABLE]
[TR]
[TD="class: votecell"]
 
              
[/TD]
                [TD="class: answercell"]      The following instructions explain how to install the latest ATI Catalyst video driver of Ubuntu 12.04 LTS (Precise Pangolin).
  
[LIST]
[*][**Ubuntu 12.10 instructions**]("http://askubuntu.com/a/129200/53498")

[*][**Ubuntu 13.04 instructions**]("http://askubuntu.com/a/286775/21195")
[/LIST]
  **Note**
  [INDENT]   AMD has released the **Catalyst 12.8** driver for  Linux systems in   August bringing some improvements and bug fixes. This driver is based  on the fglrx 8.982 release, and it improves support for Ubuntu 12.04  LTS.
 [/INDENT]  [HR][/HR]  To keep up to date with the latest driver information always refer to [AMDs official website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") as updates are published fairly regularly.
  [h=1]**Installing the AMD/ATI Catalyst drivers for 12.04 LTS**[/h]  [h=2]Tested: v12.4, v12.6, v12.8[/h]  [HR][/HR]  **Important Information and Preparation**
  Only use these instructions if you have opted **NOT** to use the official Ubuntu binaries.
  
[LIST]
[*]If you wish to use the official Ubuntu binaries or want to install the latest ATI Catalyst video driver for previous versions of Ubuntu, navigate to the [answer of this question]("http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu") and follow the instructions.
[/LIST]
  Before deciding, check if Ubuntu supports your video card [here]("http://wiki.cchtml.com/index.php/Hardware").
  
[LIST]
[*]If you are currently using the official Ubuntu binaries and want to install the latest ATI Catalyst video driver there is a prerequisite to purge some files. Before proceeding with these instructions. You can **Skip the step to purge** if you have a fresh install of Ubuntu 12.04.
[/LIST]
  **Removing (purging) existing drivers**
  sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
  [HR][/HR]  **Install these dependencies**
  You need to install some dependencies to your system, do this by running these in Terminal:
  sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
  [h=3]For 64-bit Only[/h]  sudo apt-get install ia32-libs-multiarch i386 lib32gcc1 libc6-i386
  [HR][/HR]  [h=3]Installing the lastest ATI/AMD driver[/h]  Download the appropriate driver for your machine [here from the AMD/ATI Website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")  and then enter the following into the terminal (remember to navigate to  where you extracted the driver to beforehand and make sure no other  .run files exist in that folder):
  sudo sh *.run --buildpkg Ubuntu/precise
  If it is required, a package manager window will open and install  some dependencies and after a while create the following four .deb  packages:
  fglrx_8.961-0ubuntu1_amd64.deb
fglrx-amdcccle_8.961-0ubuntu1_amd64.deb
fglrx-dev_8.961-0ubuntu1_amd64.deb
  Note: It will also create a file called  fglrx-installer_8.961-0ubuntu1_amd64.changes. If you wish you can read  this file to know the changes that have been affected through AMD/ATI  Catalyst and related information.
  **To install the created .deb files, type:**
  sudo dpkg -i *.deb
  Note: In case any of the packages are broken, open Synaptic Package  Manager and go to Edit -> Fix Broken Packages. In case you are new to  Ubuntu, broken here means that some dependent packages are not yet  installed. Once you sort out the issue as indicated above through the  Synaptic Package Manager, the problem of broken packages should be  resolved.
  [h=3]Continuing with the installation, type:[/h]  sudo aticonfig --initial
  **Before rebooting your computer:** If you are using a  beta version, you may want to remove the AMD "Testing" watermark.  Otherwise skip the next block of instructions.
  [INDENT]   [h=3]Beta versions: Removing the AMD "Testing" watermark[/h]      Edit the ATI signature file via "nano" or "gedit":
  sudo nano /etc/ati/signature
      OR
  sudo gedit /etc/ati/signature
      By replacing the "UNSIGNED" line with the following code:
  9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc
      Make sure to save before/on closing the file.
      That will remove the AMD "Testing" watermark (which you will now never   see) from the bottom right of your screen when you reboot   ([source]("http://ubuntuforums.org/showthread.php?t=2074962")).
 [/INDENT]  **Now go ahead and reboot your computer.**
  If all is right, the fglrx driver that corresponds to AMD/ATI  Catalyst will be installed and working on your system. To confirm the  drivers are working open a terminal and type:
  fglrxinfo
  You should get an output similar to the following:
  display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4300/4500 Series
OpenGL version string: 3.3.11631 Compatibility Profile Context
  Note: If you see any mention of MESA in the output, the fglrx drivers  have not been installed correctly. See the troubleshooting section for  more details
  You can make configuration changes through the AMD/ATI Catalyst  Control Center. It can either be found in your Application menu or you  can launch it through a terminal like this:
  sudo amdcccle
  **IMPORTANT NOTE:**
  Be aware that when you manually install fglrx, this can subtly break  your system, since the packaging system isn't made aware of your  changes.
  The [Launchpad]("https://en.wikipedia.org/wiki/Launchpad_%28website%29")  developers get many bug reports from users who do this and then later  discover after a few upgrades that their system starts behaving weird  because of those fglrx remnants.
     
I used this method and it's works perfectly.

---

### Post by jrn34exp on 2015-10-19
same machine, same video card and without encryption, correct. booted normally......and no additional drivers offered.

---

### Post by jrn34exp on 2015-10-19
Righn,
Thanks for the info....I will let you know if I decide to try this, but.........does this address the encryption package? I am firmly convinced now that the encryption causes it. When it happened today, and my screen went blank, I hit "delete" and immediately it asked for my encryption password. I entered it, and everything booted fine from there. That's the thing, my system is functioning great once I get past the initial boot. If my drivers for VGA/ATI weren't adequate, I would expect problems with my display, with surfing the internet and flash video, and with streaming netflix, would I not? Just thinking out loud. I noticed the warning in the method you pasted, and I don't want to become worse off. And this appears to be written for Ubuntu 12.04.

---

