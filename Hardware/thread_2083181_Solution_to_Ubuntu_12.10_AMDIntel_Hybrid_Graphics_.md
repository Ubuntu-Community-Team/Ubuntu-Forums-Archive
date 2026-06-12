---
title: "Solution to Ubuntu 12.10 AMD/Intel Hybrid Graphics not working"
date: 2012-11-11
forum: Hardware
---

### Post by HackerFinn on 2012-11-11
First I want to clarify that I did not write this guide I am merely rewriting and publishing.
Marian Lux wrote the original at askubuntu.com. All credit goes to him.
Link to original post: [here]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working").

This tutorial worked for me personally, and I have AMD Radeon HD 4600M integrated graphics card in my laptop. 

**[SIZE="4"]Pre-Install:[/SIZE]**

Three terminal-commands:

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6
sudo apt-get install dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install linux-headers-generic xserver-xorg-core libgcc1
```
Optional if 64 Bit - two terminal-commands:

```
sudo apt-get install ia32-libs lib32gcc1 libc6-i386
cd /usr ; sudo ln -svT lib /usr/lib64
```
Download from this direct-link: [https://launchpad.net/~andrikos/+archive/ppa/+sourcepub/2755647/+listing-archive-extra](https://launchpad.net/~andrikos/+archive/ppa/+sourcepub/2755647/+listing-archive-extra) the files and this two .deb packages into an empty folder

xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb
where XXX should be your architecture identifier (x86 or amd64)

Execute the following two terminal-commands in the folder with downloaded .deb files:

```
sudo dpkg -i xserver-xorg-video-intel*.deb
sudo dpkg-reconfigure Xorg
```
Then reboot your machine

Note - this is from the PPA: [https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal](https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal)

Important - There have been released a security update for "xserver-org" from the official Ubuntu repositories which mad the system crash again (no login screen). All you have to do is to install the newest two xserver-org-video-intel*.deb's (downloaded and installed as described above) from the PPA [https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal](https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal) again. You can also add this PPA on your system for preventing this issue. The PPA may have too many other packages, so you may want to do it (downloading the two .deb-files and installing them) manually. Another solution is, to de-select the "xserver-org"-packages if there are official Ubuntu security updates available.

**[SIZE="4"]Installation:[/SIZE]**

Get the current ATI Catalyst driver e,g 12.11 Beta (Marian Lux have tested it with this release):

```
wget -c [http://goo.gl/QRHCk](http://goo.gl/QRHCk) -O catalyst-12.11-beta-x86.x86_64.zip
```
Unzip the .zip and make it executable. Then go to the folder with the unzipped .run-file in terminal and type:

```
sudo sh ./amd-driver-installer-XXX.run --buildpkg Ubuntu/quantal
```
Replace XXX with the correct name of the file

Install the created .deb-files with the following terminal-command in the current directory:

```
sudo dpkg -i fglrx*.deb
```

**[SIZE="4"]Post-Install:[/SIZE]**

Enter the terminal command

```
sudo aticonfig --initial -f
```
Reboot your system

```
sudo reboot
```
optional - fixing the bug for direct rendering on the integrated card:

```
gksu gedit /etc/X11/Xsession.d/10fglrx
```
Add the string "/usr/lib/x86_64-linux-gnu/dri/" on your 64Bit system that the line finally looks like this:

LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
Add the string "/usr/lib32/dri/" on your 32Bit system, so that the line finally looks like this:

```
LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/lib32/fglrx/dri:/usr/lib32/dri
```

**[SIZE="4"]Links for more knowledge:[/SIZE]**

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

[http://ubuntuforums.org/showthread.php?t=1930450&page=51](http://ubuntuforums.org/showthread.php?t=1930450&page=51)

[http://www.upubuntu.com/2012/10/install-amd-catalyst-1211-beta-driver.html](http://www.upubuntu.com/2012/10/install-amd-catalyst-1211-beta-driver.html)

---

### Post by Carlos Araujo on 2012-11-11
applicable to radeon 7570M ?

---

### Post by HackerFinn on 2012-11-12
> **Carlos Araujo said:**
> applicable to radeon 7570M ?

I think so, but I am honestly not sure. Your best bet would be to try it. Worst case scenario, is that it won't work. :)
If this works for you, please report back. :)

---

### Post by rainerlopes on 2012-11-13
Hi!

Works like a charm on 7600M @ Sony Vaio SVE14A15FBB!

Thanks!
Rainer

---

### Post by menaaboud on 2012-11-22
After Installing the Driver, my laptop is overheated. it was overheating before and i thought using the High performance card would help , but haven't. 
I don't have the same on windows. is there a way to fix this ? or to shutdown the Intel card if it was on but the system doesn't detect it ?

---

### Post by menaaboud on 2012-11-24
> **menaaboud said:**
> After Installing the Driver, my laptop is overheated. it was overheating before and i thought using the High performance card would help , but haven't. 
I don't have the same on windows. is there a way to fix this ? or to shutdown the Intel card if it was on but the system doesn't detect it ?

Any one ?

---

### Post by exploder on 2012-11-24
I did not have overheating on my laptop but it was running quite hot though. For me I just could not use anything Ubuntu based because I was getting artifacts, strange cached images appearing and startup and shutdown just looked terrible. All that was with the proprietary drivers, it was even worse with the open source drivers....

I ended up installing Fedora 17 on the laptop just to be able to use it. The version of x-server and the ATI drivers seems to be the issue in my case why I had so many problems in Ubuntu and it's variants. I followed a guide in the Fedora forums to get the proprietary driver installed and everything works great.

The last 2 Ubuntu releases work fine on 3 desktops with NVidea graphics, just had a little trouble on one system of choosing the right driver but it was not that difficult to get it sorted out though. 

I really do not see any solid solution for ATI hybrid graphics in Ubuntu right now. PCLinuxOS also worked with my laptop after installing the proprietary driver but I had problems with sound not working in applications. I had system sounds and that was it. I am pretty sure I could have got help with the sound issue but it was late and I just wanted to get the laptop running. 

Fedora worked for the most part out of the box but the open source drivers did not always let the system boot fully. A hard reboot would get me back to the desktop though. After installing the proprietary drivers the laptops graphics have been problem free. I have been using the laptop for 3 days, running it all day with no issues.

These are just my experiences and what I went through to get my laptop running. Someone might have a solution for Ubuntu but I never found anything that completely solved my problems. If you can not get your graphics to work under Ubuntu I would take a look at Fedora first to save yourself all of the trouble I went through. Linux is Linux and as long as everything works I do not mind running a different distribution.

Edit: At one point I thought I had the graphics issue solved in Ubuntu but a look in System Monitor showed that it was not fixed. One of the cores of my quad core processor kept spiking to 100% in an endless loop. Make sure you look in System Monitor for this.

---

### Post by KegHead on 2012-12-01
Hi!

I just ordered the following:

AMD Athlon II X4 640 Propus 3.0GHz Socket AM3 95W Quad-Core Desktop Processor ADX640WFGMBOX

Am I going to have problems?

Thanks!

KegHead

---

### Post by HackerFinn on 2012-12-08
> **KegHead said:**
> Hi!

I just ordered the following:

AMD Athlon II X4 640 Propus 3.0GHz Socket AM3 95W Quad-Core Desktop Processor ADX640WFGMBOX

Am I going to have problems?

Thanks!

KegHead

To be honest, I don't really know.
The card you ordered is not a Radeon series card.
Just try the proprietary drivers Ubuntu suggests.
If you have any problems, please do not hesitate to ask me. :)

---

### Post by leonardt on 2013-01-21
Confirming that this works for me on an HP Envy 15 3040 nr running Radeon HD 7690M.

Also the [original askubuntu post]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working") has useful scripts for switching cards.

---

### Post by HackerFinn on 2013-01-21
> **leonardt said:**
> Confirming that this works for me on an HP Envy 15 3040 nr running Radeon HD 7690M.

Also the [original askubuntu post]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working") has useful scripts for switching cards.

Thank you very much leonardt. :)

I am sure that this will come in handy to some folks. :)

---

### Post by harpal on 2013-01-25
hey I followed the guide.. Instead of downloading the .deb files from the ppa and then again downloading the updated files, I directly installed the updated files manually. Then I reconfigured Xorg and rebooted my laptop. But then the virtual console opens up.
Please help me get rid of this.

I have 7600m card.

---

### Post by Dannybrgc on 2013-01-29
Hey guys,

(Newbie here; First Reply from me, hope it helps.)

After doing a bunch of research, I finally got my Hybrid setup to work, somewhat with AMD catalyst 13.1 on my laptop. Only thing is that, when you switch to the low -end graphics card,  Ubuntu interface and dash will dissappear (as usual, but does allow log in; so dont switch from High-end to low-end once installed).   =/

Once installed with this guide (_Manually_ via terminal, not automatically) ,  my computer was able to detect and run everything perfectly with the HD RADEON GPU, including the driver.  After all, what most of us are really after, is to be able to use our HD Radeon Cards to their maximum potential. This is good enough for me, for now, until a real solution is found about actually swithing GPUs without crashing, as AMD Catalys 13.1 prompts you too.

( When installed, You will need to have your pc connected to the wall at all times, as full battery only lasts about 20 mins without charger on the high-end GPU)

_Set up:_
Ubuntu 12.10 (64-bit)
HP DV6 (2nd gen i7 3.1 GHz (turbo))
8 GB RAM,  320GB Hard Drive
Integrated Intel graphics with hybrid  _RADEON HD 6770M_

_Guide: _
[http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

I do not take any credit for this guide what so ever. 

_P.S:_  Please pm and let me know if any of you have found a solution regarding the switching of GPU's in Catalyst after reboot.

Thanks

---

### Post by kecinzer on 2013-04-02
Thank you for guide, but I can't no longer download intel xorg deb files. After I switch to integrated graphic, I can't login into Ubuntu.

---

### Post by AngelGenchev on 2013-11-27
-**Already fixed** by update -
I had a problem trying fglrx even that OpenGL dri worked. When I was on intel graphics, every time I logged off the X session, my PC did soft lock-up (Xubuntu 12.10, Dell3350). And I couldn't stop video tearing with the fglrx driver on my external VGA display. So neither IGPU nor DGPU granted me a painless experience.
Didn't solve, but cleared the X.org setup to original intel+FOSS radeon (switcheroo), where I'm **not** happy again, because since previous 2 updates (kernels,xorg), the FOSS Radeon driver begun to have problems with suspend/resume and text console<->X console switching. When DGPU is turned off via switcheroo interface, it soft lockups for 1-2 minutes trying to call something in the DGPU's atombios.
A workaround found here: [HybridGraphics-Fix Suspend-wake freeze]("https://help.ubuntu.com/community/HybridGraphics#Fix_Suspend.2BAC8-Wake_Freezing")

---

