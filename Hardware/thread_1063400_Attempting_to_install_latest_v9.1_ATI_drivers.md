---
title: "Attempting to install latest v9.1 ATI drivers"
date: 2009-02-07
forum: Hardware
---

### Post by monikersupreme on 2009-02-07
I'm running an HP NC8000 laptop with a Radeon Mobility 9600 graphics card. 

I downloaded the i386 (32 bit) Catalyst drivers from amd.com and installed them by running in a terminal:

sudo sh ati-driver-installer*

... doing this initiated a script that seemed to install the driver, I was prompted to run "sudo aticonfig --intial -f" and restart. 

When I restart I get a prompt saying that there are no graphics drivers detected and that the display is running in low-graphics mode... 

What did I do wrong & how do I fix this?

Do I need to uninstall the driver... if so how do I go about doing this?

Thanks!

---

### Post by Yashiro on 2009-02-07
If you ran the installer there should be a file called fglrx-uninstall somewhere on your system. Do a search.

Safer install methods [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
Or try [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by monikersupreme on 2009-02-07
I tried envyng before running the manual install but it only registers the older (8.543 as opposed to the newer 8.573) version of the ATI driver. I'm assuming the driver hasn't been added to the Ubuntu repositories either as the Synaptic Package Manager doesn't have an updated version of the driver either.

I can't seem to locate any fglrx-uninstaller* anywhere... 

what now?

---

### Post by Yashiro on 2009-02-07
> 1) load synaptic and search for fglrx. remove any packages that match and are installed
2) if you installed via the ati-installer (not .deb packages) then you can check if there is a /usr/share/fglrx/ati-uninstall.sh (or something similar) and run it.
3) search your harddriver for matching fglrx files like: 'find / -type f -name "*fgl*"'. You should delete/move these files away, since if you did step 1 they are leftovers.

It should be called fglrx-uninstall.sh

---

### Post by vivichrist on 2009-02-07
I've tried to install the 9.1 ati drivers as .debs and failed miserably because a) I use the RT kernel b) I have the amd64 install. dkms fails to build the fglrx.ko module something to do with no finding fglrx-rt-compat.patch ... ? anyone got any idea where I could find said file?

---

### Post by vivichrist on 2009-02-08
actually I found file /var/lib/dkms/fglrx/8.573/build/patches/patches/
instead of /var/lib/dkms/fglrx/8.573/build/patches

---

### Post by vivichrist on 2009-02-08
and now it works! fantabulous! all I had to do was move the file:

/usr/src/fglrx/8.573/build/patches/patches/fglrx-rt-compat.patch

to directory:

/usr/src/fglrx/8.573/build/patches/

and run:

```
sudo dkms build -m fglrx -v 8.573

sudo dkms install -m fglrx -v 8.573
```

yay!!!!

---

### Post by monikersupreme on 2009-02-08
I found the fglrx-uninstall.sh... thanks for your patience Yashiro.

Will the v9.1 drivers eventually make it into the respository... should I just wait until there is an newbie-Ubuntu friendly way to install these?

---

### Post by Yashiro on 2009-02-08
There will be 'better' drivers in the next release of Ubuntu hopefully. I have been trying the Jaunty alpha builds but they still don't recognize my 4850. 

If you card is NOT recognized in Ubuntu, your best bet is to install the Ati drivers. However, I would not recommend the 9.1's.
Try the 8.10 build.

---

### Post by monikersupreme on 2009-02-08
When I access the "Hardware Drivers" utility I do not see any available drivers for my mobility 9600. 

The reason I was holding off installing the previous ATI drivers was that I'd read they were buggy with the r300 core. 

[http://phoronix.com/forums/showthread.php?t=14020&highlight=ubuntu+intrepid+radeon+mobility&page=4](http://phoronix.com/forums/showthread.php?t=14020&highlight=ubuntu+intrepid+radeon+mobility&page=4)

I considering actually backing up to v8.04 since it seems that people are having better luck with Hardy on some of the older hardware... but really I'm such a noob with Linux that I'm generally just taking a shot in the dark.

Is there there a resource that can explain all of this... mesa, VESA, fglrx, xorg.conf and how all of these @!$! drivers are installed???

Sorry... just frustrated. Not used to being this completely ignorant.

---

### Post by Yashiro on 2009-02-09
I just upgraded manually from 8.10 to 9.1.

The default installer failed. Some uber script from the Phoronix forums also failed. I'm not 100% sure why. I don't have the will to debug another guys monolithic bash script. 

Doing it manually as in the [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) guides always works. Making sure you remember to follow all the steps and checking for places where drivers may have been blacklisted. It's also important to install these drivers as root and without booting into X. Performing rmmod fglrx before starting also helps.

There are many guides out there already. Some are very in depth, some less so. I'd recommend following the one I linked for the Hardy build.

For anyone considering upgrading there seems to have been alot of work done to minimize vsync issues. Sadly Totem is unusable due to videos being scaled incorrectly and corrupted windows. 8.10 was fine in Totem.
XBMC and other ffmpeg based players are slightly better. You shouldn't need to force vsync, in fact if you do you will half your performance.
Games don't seem any different but I only ran a few tests with old stuff like Q3 and Doom.
Desktop performance under Compiz is faster and tearing is reduced.

---

### Post by RicRic on 2009-02-15
Hi, I am also trying to install that in Intrepid as well. But the following keeps on showing

sudo dkms install -m fglrx

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.

I googled a bit and only know it has something to do with the header files. I have the headers installed as default without any changes.(with all updates from default sources) How can I fix this?(or at least return to normal)

The best I can do is to return to 8.543 and at least it does not require me to use low-resolution login on startup. Yet the same problem still persists when I try to install in dkms. 

If that matters, I can use the 8.543 without problem before.

Any help is appreciated.Thanks...

---

### Post by Yashiro on 2009-02-15
[http://ubuntuforums.org/showpost.php?p=6709120&postcount=15](http://ubuntuforums.org/showpost.php?p=6709120&postcount=15)

Might help.

---

### Post by RicRic on 2009-02-15
There is no luck:(

1. there is no package "ia32libs"

2. I don't have /etc/modprobe.d/blacklist-local, so don't worry about it.

3. I added DISABLED_MODULES="fglrx" to /etc/default/linux-restricted-modules-common

4. I booted into recovery mode (of 2.6.27.11) and did the dpkg thing

The same thing happens.

more information:
if I type 

$fglrxinfo

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output s

$ sudo dkms install -m fglrx -v 8.573 

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.tream:  12

What else can I check?:confused:

more:
I tried to purge dkms in the recovery mode and install it again but it is the same. It does fine with the latest virtualbox-ose-source but not fglrx. It seems like fglrx is misleading dkms somehow...

I am using 32-bit lenovo T60 with ati X1300

---

### Post by NitrOuS on 2009-02-17
I don't know if it's helpful to use the following command
```
sudo aticonfig --initial -f
```
I also have some problems with ati drivers. When I use the following command
```
sudo atiode -P 10 -H localhost:0; echo$?
```
which is a test for ati drivers it return 2, which means that I have a problem with rendering. This is sth that I realised when trying to view videos using vlc or mplayer. I believe that there sth to do with the ati configuration... Does anyone know sth better? Using the following commands I messed up my desktop effects but I fixed video 
```

sudo aticonfig --sync-vsync=on
sudo aticonfig --xinerama=on

```
Is there sth to do to fix both my problems?

---

### Post by d-mart on 2009-02-19
To install the new drivers all i did was download the file from the ati website to my home directory.  Then type alt-F2 gksu nautilus navigate my way to the home directory right-click on the .run file go to properties then click the permissions tab and check the box that says allow executing file as program.  then double clicked the file and it installed.  

However, I should say that i had added some lines to my xorg.conf for the previous driver so when i rebooted the xserver wouldn't start but all i had to do was delete those lines i had added in my xorg.conf and then run aticonfig --initial -f and everything has been good from there.

Also just in case here is my xorg.conf and my gpu is a ati mobility x300

---

### Post by RicRic on 2009-02-20
Hey guys, I've given up the Linux-way, i.e. solved the problem by re-installing Ubuntu from scratch like a stupid Win user. Yet that doesn't mean I succeeded immediately. I screwed other things up like skype(cannot install) after every time I updated the headers. I encounter no problem(or at least fewer) without updating at all(that is, keeping everything as old as it was released) My understanding is those things that screw up are looking for the old header files that are removed by the update. I am quite a newbie so don't know much about the updating of header files, kernels and all that. Is there any way I can update the headers safely(or can keep the installations of old softwares work)?

---

### Post by NitrOuS on 2009-02-21
RicRic which ATI graphic card do you have? d-mart and RicRic can you run the following command 
```
sudo atiode -P 10 -H localhost:0; echo$?
```
and post in this thread the result returned?Thanks

---

### Post by Ansraliant on 2009-05-15
Hi!. I've tried to do that in terminal and the result is the following:

```

atiode -P60 -H localhost:0; echo $?
2

```

I've been searching in google, and everyone has the same result.
I do not know why the result is 2. I'm supposed to have direct rendering. According to glxinfo I have.

Good Luck!.

---

