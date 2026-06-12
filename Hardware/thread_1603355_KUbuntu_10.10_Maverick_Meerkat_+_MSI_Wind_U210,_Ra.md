---
title: "KUbuntu 10.10 Maverick Meerkat + MSI Wind U210, Radeon Graphics, Ralink 3090 Wireless"
date: 2010-10-22
forum: Hardware
---

### Post by omniuni on 2010-10-22
Hello! As I have been working on my MSI Wind U210, I have decided to write up this guide to getting Maverick Meerkat working on this machine. It includes some parts that will be of interest to others as well, such as some Radeon cards with KWin, and rt3090 wireless cards.

This post contains the following parts:
**Part 1. Choosing 32 or 64 bit, and making rt3090 work**
**Part 2: Flickery Graphics / Compositing(32 or 64 bit)**
**Part 3: Dual Monitors with a Radeon**
**Part 4: KWin won't enable desktop effects after upgrade**
**Part 5: KWin Crashes X**
**Part 6: Improving Font Rendering**
**Part 7: Multimedia Buttons, extra mouse buttons, etc.**

Let's start with whether it will work:

Short answer; yes. Longer answer, yes, but right now KWin will crash X.

**Part 1: Choosing 32 or 64 bit, and making rt3090 work**

The wireless card will work out-of-the-box on 32-bit Ubuntu/Kubuntu. I don't know why, but you need to add a PPA to get the wireless card to work on 64-bit, although it does work, and works well. I will discuss graphics later, but for the moment, if you are using KDE, make sure desktop effects are OFF.


If you choose to go the 64-bit route, here is how you get the rt3090 driver working. It will set it up so that you should not have to re-compile it for every kernel update. Once done, it should just work.

a) Open your package manager, and click "Additional Sources" or similar to get the box to enter a new repository. Enter:
```
ppa:markus-tisoft/rt3090
```

b) This will import the repository with the appropriate key, but it will also specify "maverick" as the distribution. Edit the two new lines in your list, and change it to "lucid".

c) Refresh your package list, and install the package rt3090-dkms. If it isn't showing up, try from the command line:
```
sudo apt-get install rt3090-dkms
```

d) Blacklist the existing drivers. We need to edit a file as root, so I'm going to give you three ways to do this.
Terminal:
```
sudo nano /etc/modprobe.d/blacklist.conf
```
KDE (Press Alt+F2 or your key sequence for KRunner):
```
kdesudo kate /etc/modprobe.d/blacklist.conf
```
Gnome (Alt+F2):
```
gksu gedit /etc/modprobe.d/blacklist.conf
```


e) Append to the file:
```
#Balcklist RaLink drivers
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
```
~ Thanks to LPCapital
Save the file. If you are working from the command line, press Ctrl+X

f) Reboot, and the card should be working. For more information on this card and driver, please view the full thread at: [http://ubuntuforums.org/showthread.php?t=1274886&page=11]("http://ubuntuforums.org/showthread.php?t=1274886&page=11")

**Part 2: Flickery Graphics / Compositing(32 or 64 bit)**

You need to turn of kernel modesetting to get smooth 3D performance. To do this properly:

a) We need to edit a file.
Terminal:
```
sudo nano /etc/default/grub
```
KDE (Press Alt+F2 or your key sequence for KRunner):
```
kdesudo kate /etc/default/grub
```
Gnome (Alt+F2):
```
gksu gedit /etc/default/grub
```

b) Find the line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="  quiet splash"
```
Change it to say:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
```
Save the file. If you are working from the command line, press Ctrl+X

c) Apply the change to Grub for the first time. Once you do this, you won't have to do it again.
From the terminal:
```
sudo update-grub
```

d) Reboot, and 3D graphics should no longer be flickery.

**Part 3: Dual Monitors with a Radeon**

The Radeon driver does not like doing dual-screen configuration by default. *We need to specify a larger virtual screen for this to work.* First, compute your virtual screen size.

a) Take the two monitors you wish to use, and their native resolution, and add them together in the direction they will be sitting. The greater of the remaining dimensions is the other value. In other words, if the width of one is 1366x768, and the other is 1280x1024 and you want them sitting next to each other, your width is 1366+1280=2646, and your height is 1024. The idea is that we must allocate a virtual screen large enough to fit both monitors on. If in doubt, try using 3000 as your width, and 2000 as your height. If you are using two HD monitors (1920x1080) then you should try 4000 as your width, and 2400 as your height.

b) As usual we need to edit a file.
Terminal:
```
sudo nano /etc/X11/xorg.conf
```
KDE (Press Alt+F2 or your key sequence for KRunner):
```
kdesudo kate /etc/X11/xorg.conf
```
Gnome (Alt+F2):
```
gksu gedit /etc/X11/xorg.conf
```


c) The file may not exist yet. If it doesn't, create it. You need to add the following to it:
```
Section "Screen"
        Identifier      "Default Screen"
        SubSection "Display" #Get dual monitors working
                Virtual 3000 2000 #This is the important part
        EndSubSection
EndSection
```
*Replace 3000 2000 with the numbers you came up with earlier!*
*If the file already exists, please be intelligent with how you merge these changes!*
Save the file. If you are working from the command line, press Ctrl+X.

d) Re-Start X. You can do this from the command line:
```
sudo pkill X
```

You can now configure your dual monitors as you would normally, through any utility that uses randr, such as the KDE display properties.

**Part 4: KWin won't enable desktop effects after upgrade**

*This will CRASH X on some graphics cards using the "radeon" driver!* Either way, this will clear your kwin configuration, and allow you to enable them again. Users of other drivers who can not enable KWin desktop effects can use this method to get them back:

a) Open a terminal. If you are not already in your home folder:
```
cd ~
```
b) Run the following to remove KWin configuration:
```
rm .kde/share/config/kwin*
```
c) Exit the terminal. Open KRunner with Alt+F2, or whatever shortcut you have it set to. Execute:
```
kwin --replace
```

I posted this originally at: [http://ubuntuforums.org/showthread.php?p=10008619]("http://ubuntuforums.org/showthread.php?p=10008619")

**Part 5: KWin Crashes X**
OK, long story short here, I haven't figured it out yet. I filed a bug report on Launchpad, though. Please, take the time to visit and let them know that the bug affects you too. I am still looking for a good solution (OK, ANY solution) to this problem. It affects Maverick 32 and 64 bit. For more details, and to mark that the bug affects you visit:
[https://bugs.launchpad.net/ubuntu/+bug/663660]("https://bugs.launchpad.net/ubuntu/+bug/663660")

**Part 6: Improving Font Rendering**

This is probably one of the easiest things on this post. In your home folder there may already be a file called ".fonts.conf". If not, create it, if there is one, replace the contents. The contents of the file should be as follows:
```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font">
  <edit mode="assign" name="rgba">
   <const>rgb</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="autohint">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```
Save the file, log out, and log back in. You should now have significantly cleaner and more accurate fonts. It reduces sub-pixel hinting to keep your fonts from having colorful artifacts, and enables auto-hinting so that they scale smoothly and accurately to different sizes.

To give you an idea of what it does:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=173191&stc=1&d=1287779192[/IMG]


**Part 7: Multimedia Buttons, extra mouse buttons, etc.**

Just in case you want to do this, I posted an old tutorial, that is very useful for this:

[http://forums.devnetwork.net/viewtopic.php?f=30&t=95073]("http://forums.devnetwork.net/viewtopic.php?f=30&t=95073")

*If you are a user of the MSI Wind U210, and you have a  [ | \ ] button right next to the spacebar*, I'm sorry, that tutorial can't help you use it, but if you were wondering it is a [ < > ] button. I have NO IDEA why, how, or what it is doing there. 

Good luck, and happy upgrades! I will try to update this thread if I find a solution to the KWin crashing problem. If you have any ideas, or if this helps you please let me know.

-OmniUni

---

### Post by jur9en on 2010-10-25
Thanks for this thread!
It helped me with an EeePC 1001HA.

I upgraded from Ubuntu Lucid 10.04 to Maverick 10.10.
Out of the box the old solution for the wireless (the DKMS from Markus-tisoft) was disabled, but the wireless was working without it.

However, the computer did not shut down anymore; it frooze completely at shut down.
Same issue if you shut down the wireless card manually [Fn]-[F2].
So I followed your instructions for reinstalling the markus-tisoft DKMS for Lucid and blacklisting the old RT3090 files. I used Markus-Tisoft build (2010-08-27).

I tried your Font solution, but that didn't work for me.
I found out Maverick uses a new 'improved' font, which looks to me like I'm looking through some greasy glasses. 
I've reset the font to Lucid's 'Sans' and 'Subpixel smoothing' provides the most crisp solution for me (better than 'Best Contrast').

By the way; my first impression on the Netbook 'Unity' edition is "how can I minimize the launcer bar?". I haven't found the solution to this yet.
(This colourful left bar is always on, thus reducing my netbook screen to an even smaller size. I was already upset I couldn't turn off the ubuntu bar on top or run applications in a real full-screen mode.)

---

### Post by omniuni on 2010-10-25
Hi jur9en,

I'm glad your wireless is working now. I too was not very happy with the new UNR interface. I'd recommend you check out the KDE variant. One nice thing about the KDE netbook remix is that you can easily turn it off, and you can customize it. All of the bits of it that make it a netbook interface are available as widgets that you can use to build-your-own if you don't like what they already have.

The font solution is just one that I found works best for me. I was getting some colored fringing on the letters, and used this setting to decrease this, and improve the glyph shapes. It prevents the "heaviness" of fonts from suddenly jumping between certain font sizes.

If you don't like their default font, though (I don't care for it myself) you can try setting it to "Nimbus Sans" which I have always had good luck with.

---

### Post by andreseso on 2010-11-24
Maverick comes with the rt2860sta kernel module with which the Ralink RT 3900 works correctly. Unfortunately it comes with several other kernel modules which reduce drastically the quality of the wireless experience and which load by default.  I tried to remove one of these modules executing **rmmod rt2800** and my netbook froze, not even responding to REISUB, the magic key combination to reboot a dead Linux PC. 

It is possible to blacklist these modules fortunately.

Executing from the terminal **sudo gedit /etc/modprobe.d/blacklist.conf** I added to the end of the file
```
####################### Ralink RT3900
blacklist rt2800pci
blacklist rt2x00usb
blacklist rt2x00pci

```

---

