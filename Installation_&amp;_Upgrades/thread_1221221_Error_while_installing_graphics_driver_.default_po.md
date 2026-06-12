---
title: "Error while installing graphics driver: ./default_policy.sh does not support version"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by XYZ1 on 2009-07-23
Hi,
I installed 9.04 on a HP t5730 Thin Client.

As soon as I'm logged in to the OS I have graphic errors.
This Thin Client has a ATI X1250 graphics chip.

Therefore I tried to install the ATI driver which I downloaded from the web.
But during the installation via the Gnome terminal I'm getting this error:



[FONT="Courier New"]user@ubuntu:~/Desktop$ sh ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.FoFMJW
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

[COLOR="Red"]Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-13-generic; make sure that the version is being
correctly set by --iscurrentdistro[/COLOR]

Removing temporary directory: fglrx-install.FoFMJW
user@ubuntu:~/Desktop$ --iscurrentdistro
bash: --iscurrentdistro: command not found
user@ubuntu:~/Desktop$ iscurrentdistro
bash: iscurrentdistro: command not found
user@ubuntu:~/Desktop$ -iscurrentdistro
bash: -iscurrentdistro: command not found
user@ubuntu:~/Desktop$[/FONT] 



What can I do?

---

### Post by Deicider on 2009-07-24
have the same prob right now :S

---

### Post by XYZ1 on 2009-07-25
I've found this thread on the german Ubuntu forums:
[http://forum.ubuntuusers.de/topic/ati-catalyst-display-driver-laesst-sich-nicht/](http://forum.ubuntuusers.de/topic/ati-catalyst-display-driver-laesst-sich-nicht/)

According to this thread It seems like the Kernel and the XServer of Ubuntu 9.04 are too new for this ATI driver.
Only ATI Catalyst 9.5 will support the Kernel and XServer of Ubuntu 9.04. 


So does that mean we could only use an older version of Ubuntu?

Would be good if somebody can confirm this as I'm a Linux beginner...

---

### Post by markbuntu on 2009-07-25
Yes, you need to use and older version of ubuntu to use a driver from ati that will work with the x1250. But....many people are very happy using the open source ati and raden drivers with that card so you should try them out before doing anything drastic.

---

### Post by kandm-solutions.com on 2009-10-19
I don't remember where i read this but i think u can just downgrade xorg to allow for proper install w/o errors, I know i wouldnt want to to sacrafice my 9.04 installation. That would make me :( .

---

### Post by Mark Phelps on 2009-10-19
Couple of points of interest ...

You CAN downgrade the Xorg to allow installation of ATI restricted Linux drivers -- but when you do that, you have to "lock" a whole bunch of files to prevent them ever getting updated again.  This prevents you from benefiting from any Xorg updates after that.

Also, the latest Catalyst version that works with the discontinued cards is "legacy 9.8" -- for MS Windows.  That superceded v9.3 with some critical patches. But last time I checked, Catalyst 9.3 for Linux had not been updated for legacy cards.

Nothing newer than Catalyst 9.3 (except for the "Legacy 9.8") will work with the default Xorg in Ubuntu 9.04 -- and newer.  Downloading and forcing a newer driver version will only render the display unusable and you will have to manually remove the driver and restore the open source driver to get your desktop back.

---

### Post by lephisto on 2010-01-26
WTF i can't believe that??? Why the f**** hast ATI support been (factical) dropped with Karmic?

---

### Post by brunolemos on 2010-06-29
Try a 'compapibility mode':

./ati-driver-installer-9-3-x86.x86_64.run **--listpkg**

then, chose one and try:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10

Bruno Lemos

---

### Post by Mark Phelps on 2010-06-29
Bruno Lemos:

Why are you resurrecting a six-month-old thread? 

Also, your advice specified Ubuntu 8.10 -- but the OP specifically mentioned using 9.04.

Have you actually tried this hack and confirmed it works in 9.04?

---

### Post by triva911 on 2010-08-15
> **brunolemos said:**
> Try a 'compapibility mode':

./ati-driver-installer-9-3-x86.x86_64.run **--listpkg**

then, chose one and try:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10

Bruno Lemos

Thanks Dude!!! Its working on my pc ...

---

### Post by rodrigovilla3 on 2010-08-18
Hey sorry for re-reborn this theme but his solution actually works!! Hadn't find it in any other forum!

---

### Post by deadpoetnsp on 2010-08-26
> **brunolemos said:**
> Try a 'compapibility mode':

./ati-driver-installer-9-3-x86.x86_64.run **--listpkg**

then, chose one and try:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10

Bruno Lemos

Thank you Bruno! This worked :)

---

### Post by pavlovgg on 2010-09-02
> **deadpoetnsp said:**
> Thank you Bruno! This worked :)

Worked here as well.
Thank you

---

### Post by Gregmond on 2010-09-03
This still works for Maverick beta - Ubuntu 10.10 
although its Ubuntu/maverick rather than Ubunut/10.10 in the options :)

---

### Post by Claus7 on 2010-09-26
Hello,

> **Gregmond said:**
> This still works for Maverick beta - Ubuntu 10.10 
although its Ubuntu/maverick rather than Ubunut/10.10 in the options :)

+1 the installation proceeded without errors.

Regards!

---

### Post by tommytrying2linux on 2010-10-04
Hi, what is needed to be done after doing the --buildpkg command, im left with some deb files, which i tried to run with dpkg command to no avail.

---

### Post by Claus7 on 2010-10-05
Hello,

in order to install a deb file you just have to run it, which is usually done via double clicking the file. It is like the exe files in w'dose.

Regards!

---

### Post by s.duper on 2010-10-08
Hi I am using xubuntu 10.04, I tried what bruno has suggested but I am not sure which of the following to use :confused:

Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source

---

### Post by User Abuser on 2010-10-10
latest, 9.04, me thinks ;)

---

### Post by BlackFaceWa on 2010-10-15
It's a good solution!!!!!!!!!!!!!!!!!!!!!

---

### Post by Joze on 2010-10-17
Bruno, thanks ... saw it on the ati bin help ... but searching for a proper param found you answer. Kudos to you.

__Mark, this is a forum, and people share...most dont need people blaming at them for being collaborative ;). It's very strange question from a guy that have posted such a number.
Peace.

J.

---

### Post by Blond1n on 2010-10-29
Thx Bruno, helped me too to install the linux driver package but did not solve my problem, though ! ;)

---

### Post by travlemon on 2010-11-16
> **deadpoetnsp said:**
> Thank you Bruno! This worked :)

This worked for me too! Thanks so much!  Here is my hardware and OS info:

Video Card:  ATI Radeon 9550 with 256MB of video memory
OS:  Linux Mint 9 Xfce Edition, based on Ubuntu 10.04

Thanks again!

---

### Post by Exael on 2010-11-21
Hi, I'm using Ubuntu 10.10 and followed brunolemos instructions (I chose Ubuntu/9.04 in compatibility mode) up to the point where four .deb and one .changes files were created:

    (1) fglrx-amdcccle_8.593-0ubuntu1_i386.deb
    (2) fglrx-modaliases_8.593-0ubuntu1_i386.deb
    (3) xorg-driver-fglrx_8.593-0ubuntu1_i386.deb
    (4) xorg-driver-fglrx-dev_8.593-0ubuntu1_i386.deb
    
    (5) fglrx-installer_8.593-0ubuntu1_i386.changes

According to Claus7 I have to double click the .deb files in order to install them, but when I tried this Ubuntu Software Center popped up and displayed this message:
"**Dependency is not satisfiable: xorg-driver-fglrx**" for .deb files (1),(3),(4) and "**A later version is already installed**" for .deb file (2)

By searching I found that other people facing the same problem where instructed to open Synaptic Package Manager and enable all the available options in repositories settings (main, universe, restricted, multiverse). Those options were ALREADY checked in my system, except for the Source Code option. Nothing was mentioned about it so I left it unchecked.

I'm new to Linux so I don't really know what I did wrong or why do I get the error message when all other people in this thread seem to have no problem at all...

I also have some **questions**:

          i)   I suppose that I'm now using the open source ATI drivers, right?  Do I have to uninstall them before I install the new proprietary ones from ATI?
       ii)  ATI's installation instructions mention a dialog box installer when you open the original .run file. Am I going to see this installer when I finally manage to run the .deb files or is this a totally different method to install the drivers? 
    iii) Do I have to install all four .deb files and do I have to do it in any specific order?
     iv) The (2) .deb file already exists in my system, so should I not install it?

---

### Post by Zanthir on 2010-11-30
I have the same questions as Exael.

I tried installing the source first, but then didn't know what to do with the .tz file... I didn't get a .deb file.

So, I tried the 9.04 version. Now, like I said, I have the same questions as Exael, having four .deb files. Which ones do I install?

---

### Post by jimer3220 on 2010-11-30
Using Kubuntu Maverick and for a week I'm trying to fix the drivers for ATi radeon X1600
After runing the .run file in 9.04 compatibility.
 I'm getting same files as [Exael]("http://ubuntuforums.org/member.php?u=1192171") plus 
fglrx-kernel-source_8.593-0ubuntu1_i386.deb.

I unistalled the fglrx-modaliases that was already in my system and installed the new.
Finally with the right order(satisfing dependencies) I installed all deb files.
(In order to do that you should first completely uninstall any fglrx-related from the repositories.)

After these steps AMD/ATI proprietary driver showed up in my additional driver(hardware driver) list. I push the button to activate but nothing happens....:mad:

After that I tried aticonfig --initial but I was  missing xorg.conf. I created a xorg .conf 
using Xorg -configure , redone aticonfig --initial wich worked  but no luck ...still the drivers cannot be activated.

I ended up with a black screen on boot and finally I switched in open-source radeon drivers.

Also tried fglrx drivers in repositories but the situation is even worse. Drivers wont even appear in additional drivers list.

---

### Post by LinuxPim on 2010-12-28
Even in dec 2010 this problem remains...

I tried the last compatibility suggestion using 9.04, but it failed under Ubuntu Maverick.
In the past I often needed to fix this Xserver and driver issues using xconfig in SuSe, Debian and Redhat distro's.
Never the less I've been out of this game for the last 5 years.
Since Ubuntu was supposed to be targeting the linux nitwits to knockoff microsoft, I was hoping this driver horror was fixed as well :(.

I'm glad to see that for most parts it is more user friendly.
Never the less I have a ASUS X1600/1650 Series ATI compatible graphics card and an AMD64 CPU (initially made available through VMWare player /w autodetect mode set)
Under Maverick I cant get the display recognized, yielding to the fact that 3D acceleration is not available.
So an Linux installation that actually fits the hardware still remains to be a nerdy task costing days of effort.
Thats not going to help knocking off microsoft.

Does anyone have a clue on how to set a proper ATI driver in Ubuntu Maverick for the X1600/1650 series?
I mean microsoft can do it, so why cant we? X|

---

### Post by deadpool15 on 2010-12-29
> **brunolemos said:**
> Try a 'compapibility mode':

./ati-driver-installer-9-3-x86.x86_64.run **--listpkg**

then, chose one and try:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10

Bruno Lemos
how do you tried a "compapibility mode" ?

---

### Post by david7saad on 2011-01-23
> **brunolemos said:**
> Try a 'compapibility mode':

./ati-driver-installer-9-3-x86.x86_64.run **--listpkg**

then, chose one and try:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10

Bruno Lemos

excuse me how do I run compapibility mode ? with terminal ?
i don't really know what compapibility mode is

anyone please give me an explanation about this issue. I also get error when I install the ati driver x86 x86_64 linux 9-3 like this :
> Uncompressing ATI Proprietary Linux  Driver-8.593.............................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..........................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

[COLOR=Red]Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-13-generic; make sure that the version is being
correctly set by --iscurrentdistro[/COLOR]

it's driving me crazy. anyone tell me how do i run compapibility mode ?
I will always check monitoring this thread.

i use ubuntu 10.10 and vga ati x1550

---

### Post by bourger on 2011-01-24
> how do I run compatibility mode ? with terminal ?
Exactly! Just type ```
sudo sh ./ati-driver-installer-9-3-x86.x86_64.run --listpkg
``` in terminal and hit Enter.
Then execute the next command(s).

---

### Post by david7saad on 2011-01-24
ok there are 6 debs in my home folder. i installed them, then i rebooted, but just black screen. in additional drivers i can't activate the driver in recovery mode. it means that it doesn't work.. or any solution? wanna be successful instal ati driver on my ubuntu :(

---

### Post by tedrogers on 2011-12-18
Brilliant thanks BRUNO!

---

### Post by MuSlIm on 2011-12-20
First good tray, but still nothing...
I am getting this

```
 ATI Technologies Linux Driver Installer/Packager 
==================================================
List of generatable packages:

Package Maintainer(s): Aric Cyr <aric.cyr@gmail.com>
                      Mario Limonciello <superm1@gmail.com>
Status: *UNVERIFIED*
Debian Packages:
	Debian/sid
	Debian/unstable
	Debian/etch
	Debian/stable
	Debian/lenny
	Debian/testing
	Debian/experimental

Package Maintainer(s): Niko Mirthes <nmirthes@gmail.com>
                      Michael Larabel <michael@phoronix.com>
Status: *UNVERIFIED*
Fedora Packages:
	Fedora/FC3
	Fedora/FC4
	Fedora/FC5
	Fedora/FC6
	Fedora/F7
	Fedora/F8
	Fedora/F9
	Fedora/F10
	Fedora/RHEL3
	Fedora/RHEL4

Package Maintainer(s): Anssi Hannula <anssi@mandriva.org>
Status: *UNVERIFIED*
Mandriva Packages:
	Mandriva/2006.0
	Mandriva/2007.0
	Mandriva/2007.1
	Mandriva/2008.0
	Mandriva/2008.1
	Mandriva/2009.0
	Mandriva/2009.1

Package Maintainer(s): Bowen Zhu <bwzhu@redflag-linux.com>
Status: *UNVERIFIED*
RedFlag Packages:
	RedFlag/RF50
	RedFlag/RF60

Package Maintainer(s): ATI
Status: Verified
RedHat Packages:
	RedHat/RHEL4_64a
	RedHat/RHEL4
	RedHat/RHEL5_64a
	RedHat/RHEL5

./packages/Slackware/ati-packager.sh: line 36: unexpected EOF while looking for matching `]'
./packages/Slackware/ati-packager.sh: line 387: syntax error: unexpected end of file
Package Maintainer(s): Bob Walmsley <bob@walmsley.com.au>
Status: *UNVERIFIED*
SuSE Packages:
	SuSE/SLE10-IA32
	SuSE/SLE10-AMD64
	SuSE/SUSE103-IA32
	SuSE/SUSE110-IA32
	SuSE/SUSE103-AMD64
	SuSE/SUSE110-AMD64
	SuSE/SLE11-IA32
	SuSE/SUSE111-IA32
	SuSE/SLE11-AMD64
	SuSE/SUSE111-AMD64

Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
Status: *UNVERIFIED*
Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch

Removing temporary directory: fglrx-install.IASD4l
@@@@@@@@@@@-HP-Compaq-nx6325-EY344ET-ABD:~$ ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/8.10
[B][COLOR="Red"][SIZE="4"]bash: ./ati-driver-installer-9-3-x86.x86_64.run: Permission denied
[/SIZE][/COLOR][/B]
```

can you please help me, ad thenks...

---

### Post by Martificiam on 2012-02-19
> **david7saad said:**
> ok there are 6 debs in my home folder. i installed them, then i rebooted, but just black screen. in additional drivers i can't activate the driver in recovery mode. it means that it doesn't work.. or any solution? wanna be successful instal ati driver on my ubuntu :(

I'm experiencing the exact same problem. When I go to recovery mode and try to activate the driver, nothing happens. What should I do? I'm running Linux Mint 11 LXDE, which is based on Ubuntu 11.04.

---

### Post by MAFoElffen on 2012-02-19
> **Martificiam said:**
> I'm experiencing the exact same problem. When I go to recovery mode and try to activate the driver, nothing happens. What should I do? I'm running Linux Mint 11 LXDE, which is based on Ubuntu 11.04.
I think this may help you... Here you go:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

Please note than when you get this this step:
> Then build the debian packages.  Look to where is says [COLOR=Red]natty[/COLOR] below in red, if you are installing for onieric, replaced that with [COLOR=Red]oneiric[/COLOR]. Meaning that you have to tell it what distro and version of to build the debian packages for!
```

sudo chmod +x (your_Installation_filename).run
sudo sh (your_installation_filename).run --buildpkg  Ubuntu/[COLOR=Red]natty[/COLOR]
```You'll have to change it to "what" distro and version of the debian based operating system you are running. That builds the debian packages to a specific distro/version to match it.  Otherwise you will get the "...does not support version..." error.

You'll notice in the very first post of this thread, that the OP did not use any run options in his/her sh command line.  Those options are needed to tell it what to do.

---

### Post by BriteLeaf on 2013-03-13
> **deadpoetnsp said:**
> Thank you Bruno! This worked :)

briteleaf@LinuxBox:~/Downloads$ ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty
Created directory fglrx-install.cG4IrT
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/jaunty
Resolving build dependencies...
Continuing package build
Package /home/briteleaf/Downloads/xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb has been successfully generated
Package /home/briteleaf/Downloads/xorg-driver-fglrx-dev_8.593-0ubuntu1_amd64.deb has been successfully generated
Package /home/briteleaf/Downloads/fglrx-kernel-source_8.593-0ubuntu1_amd64.deb has been successfully generated
Package /home/briteleaf/Downloads/fglrx-amdcccle_8.593-0ubuntu1_amd64.deb has been successfully generated
Package /home/briteleaf/Downloads/fglrx-modaliases_8.593-0ubuntu1_amd64.deb has been successfully generated
Package /home/briteleaf/Downloads/libamdxvba1_8.593-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.cG4IrT
briteleaf@LinuxBox:~/Downloads$ 

Worked for me! =)

Thanks Bruno! =)

---

### Post by QIII on 2013-03-13
Thank you for sharing.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread **closed.***

---

