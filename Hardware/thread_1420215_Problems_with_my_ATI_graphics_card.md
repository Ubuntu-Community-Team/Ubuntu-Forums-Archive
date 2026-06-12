---
title: "Problems with my ATI graphics card"
date: 2010-03-02
forum: Hardware
---

### Post by Nickkelbackk on 2010-03-02
I just installed ubuntu studio edition a few days ago. I have all the apps that i need from windows. The only thing I have a problem is with graphics. I cant run any games as it lags to much. On windows I could run all my games on max settings so, it is not my radeon 4850s fault. When I try to install the proprietary ati graphics drivers I get this: 

```
Created directory fglrx-install.RrJaUQ
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.702................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 7.4 and later releases 64-bit
loki_setup: directory: (null)
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.RrJaUQ
```This is what is says in the fglrx-install.log:

```
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.702 to DKMS
```When I try to open Catalyst Control Center, it says I have no compatible ati driver installed. I am not sure what to do. If I cannot play games, linux will have to go. If you need me to do anything else, just say so. 

Thank you, Trevor

---

### Post by Nickkelbackk on 2010-03-03
Could anybody tell me how to uninstall my current drivers so I cann install new ones and actually use 3d content.

---

### Post by marius311 on 2010-03-03
```
sudo aptitude remove fglrx-amdcccle fglrx-kernel-source fglrx-modaliases libamdxvba1 xorg-driver-fglrx xorg-driver-fglrx-dev 

```

It looks like you're using the newest fglrx from ATI's site. The newest couple of versions have been pretty unstable for me. You might want to try the version in the Ubuntu repository right now, I've had better luck with it.

---

### Post by Nickkelbackk on 2010-03-03
I am using 8.66 not 8.702 like it says it installs. oh I also ran envyng and installed its reccomended drivers (8.66) and now i lag when i am scrolling a page in firefox. also i have no cursor. I heard this might be fixed by changing the color depth from 24 to 16 in xorg.conf. I cannot save changes to xorg.conf so, how am I supposed to edit it. Lastly, Ati ccc now just crahes upon opening instead of giving me an error message. Help would be greatly aprpreciated.

---

### Post by Yellow Pasque on 2010-03-03
Your system sounds pretty messed up. Try and get it back to the original state: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Then you can just enable the proprietary driver that comes with Karmic.

---

### Post by Nickkelbackk on 2010-03-03
Ok, I am now back to where I started. I tried to run Nexuiz and it was extremely laggy. took me 10 minutes to hit the quit button. not sure what to do now. any help would be appreciated.

---

### Post by Yellow Pasque on 2010-03-03
> Ok, I am now back to where I started.
Did you install the proprietary driver or are you now using the open-source driver that comes pre-installed?

---

### Post by Nickkelbackk on 2010-03-03
whatever the command that you gave me intalled. I do not think it is the proprietary one as I have no CCC, but am not sure. How do I tell?

---

### Post by Yellow Pasque on 2010-03-03
You;re now using the open-source drivers. You can either try installing the proprietary driver again or follow this to enable 3D hardware acceleration on the open-source drivers: [https://help.ubuntu.com/community/RadeonHD#For%20Group%202%20Cards](https://help.ubuntu.com/community/RadeonHD#For%20Group%202%20Cards)

---

### Post by anihilat0r on 2010-03-03
@[Nickkelbackk]("http://ubuntuforums.org/member.php?u=854162"): Try starting from the scratch, following this small guide, it helped me to get past some errors:
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper  debconf libstdc++6 dkms libQtGui4 
sudo wget  www2.ati.com/drivers/linux/ati-driver-installer-10-2-x86.x86_64.run
sudo chmod +x ./ati-driver-installer-10-2-x86.x86_64.run
./ati-driver-installer-10-2-x86.x86_64.run --extract
cd fglrx-install*/arch/x86_64/usr/lib/
ln -s libatiuki.so.1.0 libatiuki.so.1
cd ../../../..
sudo ./ati-installer.sh 10.2 --buildpkg Ubuntu/karmic
cd
sudo dpkg -i *.deb
sudo aticonfig --initial -f

```

Change it according to your system and ati-driver version... and purge the old install before you try it (this gave me a lot of headache..)
It's basically the official guide from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) with a small hack.

People claim, it should work, so try. I however have a similar problem, i can't install the  driver (Catalyst 10.2) on x86_64/9.10/radeon hd5770. I don't want to open a new thread so:

It compiles fine and builds the packages (.deb), but there are some files missing in the /etc/ati/ and /usr/share/ati/ directory compared to installing it just by running the   p, li { white-space: pre-wrap; }  "ati-driver-installer-10-2-x86.x86_64.run" file and aticonfig complains with 

"aticonfig: error while loading shared libraries: libGLcore.so.1: cannot open shared object file: No such file or directory" (it doesn't do that when running the installer)


To summarize my problem and efforts of trying and googling the past 3 days:
I ended up with two possible outcomes - 



1.) Installing by running ati-driver-installer-10-2-x86.x86_64.run normally - gives me a functional aticonfig and config files in /etc/ati/ & /usr/share/ati but

Xorg/KDE starts without DRI and OpenGL support, reports kernel module version mismatch

2.) Installing by extracting/building packages/installing pckgs. manually - i get a functioning kernel module which succesfully loads at Xorg/KDE startup with DRI and OpenGL support (or at least the Xorg.log claims that), however 

[LIST]
[*]there are files missing in /etc/ati & /usr/share/ati is empty at all!
[*]aticonfig reports "aticonfig: error while loading shared libraries: libGLcore.so.1: cannot open shared object file: No such file or directory"
[*]**Xorg/KDE freezes** right after logging in at the KDE boot screen and displays only a black screen when switching to a terminal & back. dmesg and Xorg.0.log give no error or useful information in this situation...
[/LIST]
Any help is greatly appreciated, i'm close to giving it up :/

---

### Post by Nickkelbackk on 2010-03-03
Temujin, I did everything that link says and still have no 3d acceleration... any help would be appreciated

---

### Post by syncmasterpt on 2010-03-03
I've just upgraded to KDE 4.4.1 and ATI 10.2 using an ATI 4870 card, and I can confirm that logging in into KDE hangs. Going to the console and back in, just shows a black screen.

Downgrading to the ATI 10.1 driver, everything works ok.

Just my 2c.

---

### Post by anihilat0r on 2010-03-03
I had no luck with 10.1 either... behaves all the same

---

### Post by Yellow Pasque on 2010-03-03
> Temujin, I did everything that link says and still have no 3d acceleration... any help would be appreciated
Post the output of glxinfo command and /var/log/Xorg.0.log

---

### Post by BobDoLe on 2010-03-07
I'm having the same issue, so I'll add to this thread.

I'm running 9.10 and I've had this issue for any catalyst driver I've tried (9.10, 9.12, 10.1, 10.2 - I followed the directions for a clean wipe of all drivers before attempting to re-install) for a radeon hd 4650 that was just dropped in. I've been researching this issue for hours and I keep going around in circles - seems like countless people have the same problem with no real solution. 

I run the ATI installer and although the gui indicated it was installed properly, the terminal indicated this: ```
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

```

So I take a look at fglrx-install log output:
```

Creating symlink /var/lib/dkms/fglrx/8.702/source ->
                 /usr/src/fglrx-8.702

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
su nobody -c "cd /var/lib/dkms/fglrx/8.702/build; sh make.sh --nohints --uname_r=2.6.31-20-generic --norootcheck"....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.702 with DKMS
[Error] Kernel Module : Removing fglrx-8.702 from DKMS

```
After this, I do the 'aticonfig --initial' and reboot.

The problem is that everything moves very slow. As to be expected, xorg log shows this:

 X```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

and fglrxinfo...
[code]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

```

Please HELP!!
Thanks!

---

### Post by BobDoLe on 2010-03-08
i gave up - ended up just re-installing 9.10. went with 64bit to finally take advantage of the processor. installed proprietary using jockey-gtk and it worked without a hitch.

edit: or so i thought. card was still running about half as fast as it should have. ended up ditching the whole system and went with an AMD Phenom II setup with a 1gig ddr5 ati card. reinstalled 9.10 and proprietary driver installation completed just fine (after dependencies installed). 

GOOD LUCK to anyone who is having this problem.

---

### Post by anihilat0r on 2010-03-11
@BobDole: Thank you for the info, even if i kinda hoped to avoid reinstalling the whole system (reminds me of the old M$ Windows days...). My only question is now, is your new graphics card by any chance an ATI 5000-series? Thx.

---

### Post by BobDoLe on 2010-04-20
> **anihilat0r said:**
> @BobDole: Thank you for the info, even if i kinda hoped to avoid reinstalling the whole system (reminds me of the old M$ Windows days...). My only question is now, is your new graphics card by any chance an ATI 5000-series? Thx.

yes. xfx's ATI HD5670 with 1gig DDR5. went with 2 in crossfire, although now i'm noticing the extra card doesn't increase performance even though everything in aticonfig and amdccle says its working fine and setup properly.. that's another issue. i'm now dual booting windows and the setup is awesome.

---

