---
title: "Radeon HD 7450m"
date: 2012-03-15
forum: Hardware
---

### Post by cascader on 2012-03-15
Hello . . .

Installed latest Ubuntu 11.10 on my new HP Pavilion G6-1310AX Notebook (according to shop tag), everything installed perfectly except . . .

Using the [COLOR="navy"]System Settings -> Additional Drivers[/COLOR] to load (activate) the proprietary drivers [COLOR="Navy"]ATI/AMD proprietry FGLRX graphics driver[/COLOR] all well and good until I reboot, at which point my 'puter stops short somewhere about the time it should load the graphical interface . . . the operating system loads as I can Alt-F2 to a different tty . . . but

I have searched and attempted a couple of little diversions but have little experience when it comes to figuring out what is happening . . .

If there is a simple answer maybe someone can help . . . [-o<

---

### Post by winh8r on 2012-03-15
You might get some results having a look at this:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")

Like all these things though, read it all through before you adjust anything, and write down anything that you do change in case you need to revert to the previous setting.

Hope this helps you,

---

### Post by cascader on 2012-03-17
Thanks winh8tr for responding . . . much appreciated . . .

Not having any joy, have tried various methods as described at [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide), each time with a fresh install. Ubuntu loads but seems to stop at loading the GUI. I am able to access command line via Alt-F2 via another tty, but all mods to xorg.conf have fallen flat . . .

Anyways, attempt 236 coming up, perseverance is the name . . . but please anyone with any input, especially if you have had this problem . . .

Cascader

---

### Post by cascader on 2012-03-18
Joy . . .

Thank you winh8tr for the [link]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide"), eventually worked a charm . . .

For anyone who is interested why solved . . . seems that even tho the tag stated Radeon HD 7450 the graphics card is indeed a HD 6470M, which I discovered using [COLOR="Blue"]$ lspce -nn | grep VGA[/COLOR]. This led me to discover that I had to use the latest Catalyst driver from [ATI]("http://www2.ati.com/drivers/linux/") . . . and just followed the command line instructions per the wiki . . .

So - smiling.

Cascader

---

### Post by kalyfas on 2012-03-24
Hello,

  I try to install HD 7450 in Ubuntu Oneiric. Can you say me how you install it? I hope your news. Thanks

---

### Post by cascader on 2012-03-24
Hello Kalyfas

I had to do a manual install from the AMD/ATI site. I used the method outlined here:: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide) - as posted by **[COLOR="Green"]winh8tr[/COLOR]**

So from the link, I followed these instructions to the letter . . .
[B]
[SIZE="2"]Installing Catalyst Manually (from AMD/ATI's site[/SIZE])[/B]

I recommend copying and pasting the commands to ensure there are no typing mistakes and speed up the install process. Remember to use Ctrl + Shift + V or Shift + Insert to paste into the terminal (or go to the terminals menu, select edit and click paste).

***Before you start***

If you have previously attempted installing Catalyst, remove any leftover files by following the Removing the Driver section. Make sure universe and multiverse are enabled in your repository sources (System -> Administration -> Software Sources). or Applications->Ubuntu Software Center->Edit->Software sources->Other software: check canonical partners.

Install the prerequisite packages:
[COLOR="Blue"]sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases linux-headers-generic[/COLOR]

If you are using the x86_64 architecture (64 bit):
1. Install "ia32-libs" before proceeding!
[COLOR="blue"]sudo apt-get install ia32-libs[/COLOR]

2. Create a symlink from /usr/lib64 to /usr/lib[1] :
[COLOR="blue"]sudo ln -svT lib /usr/lib64[/COLOR]

***Download the latest Catalyst package.***

This package contains both the 32-bit and 64-bit driver.
[COLOR="blue"]cd ~/; mkdir catalyst12.2; cd catalyst12.2/
wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run)
chmod +x amd-driver-installer-12-2-x86.x86_64.run[/COLOR]

***Create .deb packages.***

[COLOR="blue"]sudo sh ./amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/oneiric[/COLOR]

It may take a while...
Install .debs.

[COLOR="blue"]sudo dpkg -i fglrx*.deb[/COLOR]

***Generate a new /etc/X11/xorg.conf file***

Unfortunately, there is no sure way to generate the ATI version of the Xorg.conf file. It is entirely dependent on your configuration. The following subsections will attempt to address possible (and tested) variations for their respective configurations.
Generic Config

This will work for most people:
[COLOR="blue"]sudo aticonfig --initial -f[/COLOR]
Test your installation

NOTE: if you don't reboot first, fglrxinfo gives an error message. Reboot the computer and type
[COLOR="Blue"]fglrxinfo[/COLOR]

into the terminal. If the vendor string contains ATI, you have installed the driver successfully. Using fglrxinfo on a system with Catalyst 11-8 and a RadeonHD 4550 returns:
[COLOR="Red"]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4550 (This line may be different depending on what graphics card you are using.)
OpenGL version string: 3.3.11005 Compatibility Profile Context[/COLOR] (This line may be different depending on what graphics card and Catalyst version you are using.)
Now, try:
[COLOR="Blue"]fgl_glxgears[/COLOR]

If you experience issues or a hang, you may need to disable fast TLS.
[COLOR="blue"]sudo aticonfig --tls=0[/COLOR]

[COLOR="Red"]**Hope this helps, Cascader**[/COLOR]

---

### Post by kalyfas on 2012-03-25
Do not use your this line first?????
**Command line **

sudo apt-get install fglrx fglrx-amdcccle Thanks for your reply and I hope your news again.

---

### Post by cascader on 2012-03-25
Hi Kalyfas . . .

Not sure what you mean . . . the method above is the one I used on a fresh install. I had **no** drivers installed previously. I did not use the Ubuntu drivers install program found under System Settings.

Also, all of the instructions described above (in [COLOR="Blue"]blue[/COLOR]) I entered via the terminal **Xterm**.

Really, I am not the best person to ask about all of this, I just followed the method as posted and it worked. I had tried various methods before this, and after every failed attempt I reinstalled Ubuntu from scratch.

Also, I am sorry if it takes a while to get back to posting at this thread . . . I work full time and study. I use Ubuntu because I do not want to use MS stuff but I am not a die-hard enthusiast. It is great that there is a viable alternative to windows, but there are many people who know and understand computers and operating systems better than I do.

[COLOR="Red"]Anyway, best of luck, Cascader[/COLOR]

---

### Post by kalyfas on 2012-03-25
Thansk agai Cascader.. I will try it.

---

### Post by rakkenes on 2012-04-04
First of all, thanks for a good sumary of the more complex original.

Secondly the new version of catalyst is also out now ([12.3).]("http://wiki.cchtml.com/index.php/12.3")

Thirdly, when I followed this instruction, it worked well, but the watermark was still there, so to fix that I followed these instructions.

[http://phoronix.com/forums/showthread.php?69777-lolsed-Get-Rid-Of-Unsupported-Hardware-Testing-Only-Watermark](http://phoronix.com/forums/showthread.php?69777-lolsed-Get-Rid-Of-Unsupported-Hardware-Testing-Only-Watermark)

PS: make sure you have ruby installed before you go to init 1, and make sure you put the script in a folder that you can reach in such a low level (e.g not in your encrypted home directory).

it is nice to have proper setup finally! thanks

---

### Post by cascader on 2012-04-09
Glad you got some joy from this [COLOR="Blue"]rakkenes[/COLOR]  . . .

I have had no problem with a watermark . . . thanks for the heads up on the new version . . . probably going to leave my config the way it is tho, I have a good working setup that does what I want, so basically it's a case of why fix something that ain't broke . . . I do like to do a fresh install every six months or so, also a good time to upgrade to a newer version . . .

[COLOR="Red"]Cheers Cascader[/COLOR]
ps: wish I could get rid of that pesky "Gutsy Gibbon" reference in my sidebar, punishment for going over to [COLOR="SeaGreen"]mint[/COLOR] for a while (well, years really) . . . one post closer ;-)

---

