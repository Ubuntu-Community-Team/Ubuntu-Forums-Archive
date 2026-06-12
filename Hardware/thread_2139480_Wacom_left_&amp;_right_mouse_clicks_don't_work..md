---
title: "Wacom left &amp; right mouse clicks don't work."
date: 2013-04-27
forum: Hardware
---

### Post by silversuds on 2013-04-27
Ubuntu 13.04
Wacom Intuos 3 4x6" Tablet Mouse (also known as a Puck)

In Ubuntu 12.10 the mouse buttons were fully functional, with the upgrade (fresh install) to 13.04 i can only move the cursor with the mouse.
(I had this issue when I upgraded OpenSuse also, that's why I switched to Ubuntu 12.10... and now I find I have the same problem.)
Thanks for any assistance!

---

### Post by rquint on 2013-04-27
You are not alone, tho' I'm afraid I can't provide a solution.  I have the same problem after upgrading to 13.04.  Both a Wacom Graphire and a Wacom Intuos 2 behave the same way.  Checking with lsusb show that both tablets are seen, and the Wacom Tablet applet in System Settings sees them, but they are unusable.  I had the same problem with 12.10 and the Intuos and switching to the Graphire seemed to be a fix, but now both tablets (and yes, I connected each them one at a time and rebooted between changes) are useless.

---

### Post by silversuds on 2013-04-28
Fortunately, the stylus remains fully functional for me... but the need to plug in an additional mouse is frustrating. (I hope the stylus works for you too!)
A theory is that the tablet driver files were updated in both the recent versions of Ubuntu and OpenSuse... I lack the experience necessary to downgrade the drivers. :(

---

### Post by vyrishkis on 2013-04-28
I downgrade xserver-xorg-input-wacom_0.19 to xserver-xorg-input-wacom_0.15 
[http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom](http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom) worked for my wacom graphire mouse. Sory my english is not good.

---

### Post by silversuds on 2013-04-28
How do I downgrade? No need to apologize for your english. :)

---

### Post by Favux on 2013-04-28
Hi,

That bug has been fixed in xf86-input-wacom with a recent commit:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=7a1aadb24b6573809d7324f2549bed749ad1a7f2](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=7a1aadb24b6573809d7324f2549bed749ad1a7f2)

You would need to clone xf86-input wacom since it is not yet available in a tar release.  See either:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)  or  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110304](http://forums.linuxmint.com/viewtopic.php?f=42&t=110304)

---

### Post by silversuds on 2013-04-29
> **Favux said:**
> Hi,

That bug has been fixed in xf86-input-wacom with a recent commit:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=7a1aadb24b6573809d7324f2549bed749ad1a7f2](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=7a1aadb24b6573809d7324f2549bed749ad1a7f2)

You would need to clone xf86-input wacom since it is not yet available in a tar release.  See either:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)  or  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110304](http://forums.linuxmint.com/viewtopic.php?f=42&t=110304)

Thank you for the reply :)
Would the update be available through the "software updater" eventually?
I'm relatively inexperienced and probably shouldn't attempt anything where I could accidentally break things...
already had to reinstall Ubuntu when i experimented with Krita's OpenGL option (as it became stuck in a crash loop I couldn't fix).

---

### Post by Favux on 2013-04-29
Very unlikely.  They rarely update something like a driver.  You generally have to wait for a new release that has the driver version (or later) you want.  I understand your trepidation.  It is possible they might backport the bug fix as a patch to the default version of xf86-input-wacom they are using in a particular release, but that is not real likely either.  By the way to determine your version enter in a terminal:
```
xsetwacom -Version
```

---

### Post by rquint on 2013-04-30
To Silversuds, it's fairly simple to downgrade.  This isn't the most efficent way, but it works for newbies like us. 

First, download version 1:0.15.99.1-0ubuntu0ricotz  from [http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom](http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom).  

Second, use synaptic to remove the current version of xserver-xorg-input-wacom (probably 1:01.19 ...).  You'll also be removing the xserver-xorg-input-all package, not a problem if the tablet is your only input device.

Third, from a command line in the directory where you're downloaded file is, run sudo dpkg -i xserver-xorg-input-wacom_0.15.99.1-0ubuntu0ricotz*.deb  (I entered it this way since I don't know whether you'll be using the 32 or 64 bit version.)

Best of luck,
Richard Quint

---

### Post by silversuds on 2013-04-30
> **Favux said:**
> Very unlikely.  They rarely update something like a driver.  You generally have to wait for a new release that has the driver version (or later) you want.  I understand your trepidation.  It is possible they might backport the bug fix as a patch to the default version of xf86-input-wacom they are using in a particular release, but that is not real likely either.  By the way to determine your version enter in a terminal:
```
xsetwacom -Version
```

darn... I have version 0.19.0
(I forgot to mention earlier I'm on a 32 bit machine)
once it's in a tar release install should be easier?

---

### Post by silversuds on 2013-04-30
> **rquint said:**
> To Silversuds, it's fairly simple to downgrade.  This isn't the most efficent way, but it works for newbies like us. 

First, download version 1:0.15.99.1-0ubuntu0ricotz  from [http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom](http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/xserver-xorg-input-wacom).  

Second, use synaptic to remove the current version of xserver-xorg-input-wacom (probably 1:01.19 ...).  You'll also be removing the xserver-xorg-input-all package, not a problem if the tablet is your only input device.

Third, from a command line in the directory where you're downloaded file is, run sudo dpkg -i xserver-xorg-input-wacom_0.15.99.1-0ubuntu0ricotz*.deb  (I entered it this way since I don't know whether you'll be using the 32 or 64 bit version.)

Best of luck,
Richard Quint

Hi Richard, thanks for the reply :)
I'm running on a 32 bit laptop with a trackpad... so I'm not sure I should remove xserver-xorg-input-all? (sry I neglected to mention 32 bit earlier)
I'm thinking it may be best for me to wait for a tar of the latest driver with the bug fix that Favux mentioned (If I understand i can run a tar to install)

---

### Post by Favux on 2013-04-30
No, a tar is not a deb.  With a tar (compressed file) or a git repository clone (of the file(s)) you still compile either.  Whereas a deb is an installation package that would contain the driver files and all you do is dbl. click on it for it to install.

See part II. of the BambooPT How To I linked to earlier to see the difference between compiling a tar or a git clone.  It actually is not that hard.  You just copy and paste the commands in a terminal in order hitting enter after each one.  In this case to get the bug fix you need to clone the git repository because they haven't released a tar of xf86-input-wacom containing the bug fix.  That'l probably happen in the next month or so.

---

### Post by smokecfh on 2013-05-25
Hi,

I too experienced this (using a Wacom Intuos 3, with a Wacom mouse type ZC-100-02).
After upgrading from Ubuntu 12.10 to Ubuntu 13.04, the mouse buttons stopped working. The stylus was still functioning properly.

I cannot reproduce the exact problem, but after some fiddling it went away.
Perhaps this could be of help to someone struggling with the same problem.

I tried the following, but cannot determine what exactly fixed it:

```

sudo apt-get remove xserver-xorg-input-wacom
sudo apt-get install xserver-xorg-input-wacom
sudo dpkg-reconfigure xserver-xorg-input-wacom
reboot

```

---

### Post by openjaf on 2013-05-27
Thanks!! This was driving me crazy.  Just performing the dpkg-reconfigure followed by a logout and log back in worked for me.  


> **smokecfh said:**
> Hi,

I too experienced this (using a Wacom Intuos 3, with a Wacom mouse type ZC-100-02).
After upgrading from Ubuntu 12.10 to Ubuntu 13.04, the mouse buttons stopped working. The stylus was still functioning properly.

I cannot reproduce the exact problem, but after some fiddling it went away.
Perhaps this could be of help to someone struggling with the same problem.

I tried the following, but cannot determine what exactly fixed it:

```

sudo apt-get remove xserver-xorg-input-wacom
sudo apt-get install xserver-xorg-input-wacom
sudo dpkg-reconfigure xserver-xorg-input-wacom
reboot

```

---

### Post by smokecfh on 2013-05-28
Strangely enough, the problem sometimes reappears.
If I power down the system for some time, clicking is disabled.
Simply restarting the machine makes the problem go away.

Any ideas?

---

### Post by abelthorne on 2013-06-20
Hello,
I have the same problem with a Graphire 2 tablet's mouse. The dpkg-reconfigure didn't fix it. Has the bug been reported on Launchpad (I can't find a report)? Any DEB package or PPA out there that would include a fixed version (if I understood correctly, the bug has been fixed upstream by Wacom)?

EDIT: I opened a bug report on Launchpad in case the Ubuntu devs want to backport a fix: [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1192968](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/1192968)
If you have a launchpad account, you can go there and click on "the bug affects me too".

---

### Post by pannini on 2013-06-28
Hi, The instructions here: [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom) worked for me on 13.04 32-bit. That is, I did:
[COLOR=#000000][FONT=sans-serif][FONT=monospace]
[/FONT][/FONT][/COLOR]sudo apt-get install xutils-dev libudev-dev 
git clone git://git.code.sf.net/p/linuxwacom/xf86-input-wacom
cd xf86-input-wacom
./autogen.sh --prefix=/usr --libdir=/usr/lib 
make
sudo make install



[COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by abelthorne on 2013-06-29
Thanks, I'll look into that.

You say that the autogen command is for 32 bits installs. Does it have to be modified for 64 bits installs (64b libs are in /usr/lib too, with 32b libs in /usr/lib32)?

---

### Post by pannini on 2013-06-29
Yes, I think on 64-bit the autogen command should be:

./autogen.sh --prefix=/usr --libdir=/usr/lib64

---

### Post by abelthorne on 2013-06-29
I have no /usr/lib64, only /usr/lib (which hosts the 64b libs) ans /usr/lib32 (for 32b libs). I know there used to be a different organization (with /usr/lib64) but it's a bit messy since.

I'll try with /usr/lib to begin.

EDIT: I have a problem during autogen:
```
configure: WARNING: doxygen not found - documentation targets will be skipped
configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
The first warning doesn't seem to be a big issue but I'm not sure what package to install for xorg-server... xorg-dev?

---

### Post by pannini on 2013-06-29
Not sure about this, but the link: [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dependencies) gives the dependencies to build xf86-input-wacom from source (on ubuntu) as:
xserver-xorg-dev
xutils-dev
libxi-dev
libxrandr-dev
libxext-dev
libx11-dev
libxinerama-dev
libudev-dev

---

### Post by abelthorne on 2013-06-29
It seems to work. Nice.

You may want to edit your message to remove "on 32-bit install" as it works on 64 bits too with the same command. ;)

EDIT: about the dependencies, libext-dev doesn't seem to exist anymore in Ubuntu 13.04 but the compilation worked fine without it.

---

### Post by silversuds on 2013-07-19
thank you all for your help!
(i managed to piece together the terminal code from replies here and sourceforge)
my wacom mouse seems to work fine now :D

one question:
xutils-dev libudev-dev should it be uninstalled now, or is it necessary (what is it exactly)?

---

### Post by abelthorne on 2013-07-19
> **silversuds said:**
> one question:
xutils-dev libudev-dev should it be uninstalled now, or is it necessary (what is it exactly)?
Unless you need it to compile something else, you could remove it without issues. The -dev packages are source code usually needed only to provide files for compilation.

---

### Post by silversuds on 2013-07-19
thank you abelthorne! i'll keep them then (should the need to compile arise again).
i'm thrilled that the complete wacom tablet works now, no need for an additional mouse!
(and i managed not to break my installation!)
big thanks again to everyone in this thread! :D

---

### Post by babeliak on 2014-04-10
> **smokecfh said:**
> Hi,

I too experienced this (using a Wacom Intuos 3, with a Wacom mouse type ZC-100-02).
After upgrading from Ubuntu 12.10 to Ubuntu 13.04, the mouse buttons stopped working. The stylus was still functioning properly.

I cannot reproduce the exact problem, but after some fiddling it went away.
Perhaps this could be of help to someone struggling with the same problem.

I tried the following, but cannot determine what exactly fixed it:

```

sudo apt-get remove xserver-xorg-input-wacom
sudo apt-get install xserver-xorg-input-wacom
sudo dpkg-reconfigure xserver-xorg-input-wacom
reboot

```

Thank You so much, this really made/saved my day!
 I had non-functional mouse buttons on Wacom Graphire3 mouse/tablet and  dpkg-reconfigure fixed it
 after I installed xserver-xorg-input-wacom  
after I resolved 2 package dependencies 
after (forced) reboot on my (not-so) fresh (anymore) 12.10 LTS install.
Thank You!

---

