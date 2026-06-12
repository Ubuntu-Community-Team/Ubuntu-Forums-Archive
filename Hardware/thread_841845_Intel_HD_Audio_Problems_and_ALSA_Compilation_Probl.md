---
title: "Intel HD Audio Problems and ALSA Compilation Problems"
date: 2008-06-26
forum: Hardware
---

### Post by Brando569 on 2008-06-26
Everytime I compiled a new kernel the sound wouldnt work and Ive found out that it seems like everyone and their grandmother has this problem due to the Intel HD audio onboard sound, my only difference is that I have a desktop (mine is actually labeled as nVidia Corporation MCP55 High Definition Audio (rev a2) but as soon as I compiled Intel HD as a module the mixer acted like it was fine, compared to before when I didnt have it selected and it said mixer not found, my audio codec is Analog Devices AD1988B) and most of the other problems Ive read about are on laptops. All of the modules are loaded correctly and when I play a song in Amarok it goes through with it but there isnt any sound.

I've tried a few different methods and nothing has worked. So I decided I would try and compile the newest version of ALSA to see if that would fix it, I didnt get very far though...



When I try to compile ALSA using sudo ./configure --with-cards=hda-intel it breaks about 30 seconds after I type "sudo make" with these errors:

```
/usr/src/alsa/alsa-driver-1.0.16/acore/timer.c: In function &#8216;snd_timer_request&#8217;:
/usr/src/alsa/alsa-driver-1.0.16/acore/timer.c:155: error: wrong type argument to unary exclamation mark
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore/timer.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.16/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.16] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.25'
make: *** [compile] Error 2
```




If I try and compile it using sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)  I get these errors:

```
/usr/src/linux-headers-2.6.25.9/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.25.9/arch/x86/Makefile_32.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.25.9/arch/x86/Makefile_32.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25.9'
make: *** [compile] Error 2
```



This seems to be a huge PITA and might be the final reason I need to get a sound card.

---

### Post by sdennie on 2008-06-26
I use snd_hda_intel and custom kernels and have never had any problems.  Did you use an Ubuntu kernel config as the basis for the new kernel configuration?  If so, it has snd_hda_intel and intel wireless disabled in that config and you'll have to explicitly enable them before compiling the kernel.

I'm not sure why you can't build ALSA against 2.6.25 but, you could try the ALSA 1.0.17 RC and see if that works (it built fine against 2.6.26rc7).

---

### Post by Brando569 on 2008-06-27
Technically I did use an ubuntu config to make it, I'm running linux mint 4 kde, but posted it here since I would probably get more responses since theres a larger user base. I did enable Intel HD under the Audio section in xconfig though, so thats not my problem.

I couldnt use "make oldconfig" since I'm going from 2.6.22-15 to 2.6.25-9 and read that it was wise not to do so, so I just copied my config from /boot/, I'm still slightly noobish when it comes to kernel compiling. I've attempted it probably 100 times in the past 5 or so years and have only had successfully working kernels maybe a quarter of the time. I wrote a bash script that takes all of the work out of compiling a kernel so all I have to type in is the kernel version (2.6.xx, only the xx part) and the patch version and it does the rest for me up until xconfig pops up then I have to config stuff myself, save it and it does the rest. What I'm getting at here is its entirely possible that some of my script is messed up and is screwing up stuff from the start! 

I was confused too on why I couldnt make ALSA. I'll mess around with all of this some more tomorrow when I'm actually awake. I'm glued to watching the episodes of House that I have on my computer lol

---

### Post by sdennie on 2008-06-27
What method are you using to build your kernel in your scripts?  Specifically, are you using make-kpkg?  I more or less use the guide here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) but with this script:

```

#!/bin/bash

make-kpkg clean
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-$1 kernel_image kernel_headers

```

Then run it with:

```

build-kern name

```

That will build standard looking Ubuntu style kernel packages.

---

### Post by Brando569 on 2008-06-27
this is my entire script, i believe that i initially based all of the commands off of the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158) but added in the variables myself. i also read somewhere while researching the intel hd audio problem that you dont need to use an initrd when you compile a custom kernel, how would i go about not including one? i removed the --initrd option from make-kpkg but it still ended up making one.

Feel free to use this if you want to even though its nothing special, im actually waiting for master_kernels new version of kernelcheck that comes out in a few days since his last version worked well but i didnt like the fact that it didnt check to see if you already had the kernel source and it would download a 40+mb package each time you ran it

```
#!bin/bash

clear
echo "what kernel version are you using? linux-2.6.what?"
read kernel_version

echo "what patch are you using? patch-2.6.$kernel_version.what?"
read patch_version

##get necessary stuff from the repositories
#sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget

#copying kernel source and patches
cd /usr/src
sudo cp /boot/config-`uname -r` .config
sudo cp ~/Downloads/kernels/linux-2.6.$kernel_version.tar.bz2 /usr/src
sudo cp ~/Downloads/kernels/patches/patch-2.6.$kernel_version.$patch_version.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.$kernel_version.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.$kernel_version linux
cd linux

#patching kernel
sudo bzcat /usr/src/patch-2.6.$kernel_version.$patch_version.bz2 | sudo patch -p1
#sudo cp ~/kernel/speed_hacked.config .config

#making kernel
sudo make xconfig
sudo make-kpkg clean
**sudo make-kpkg kernel_image kernel_headers**
sudo ln -s /lib/firmware/2.6.22-15-generic /lib/firmware/2.6.$kernel_version.$patch_version

#installing kernel and headers
cd ..
sudo dpkg -i linux-image-2.6.$kernel_version*.deb
sudo dpkg -i linux-headers-2.6.$kernel_version*.deb 

#nvidia driver
#sudo sh /home/bran/Downloads/NVIDIA-Linux-x86-173.14.09-pkg1.run --update --kernel-source-path=/usr/src/linux
```

ive attached my last config that i used to compile 2.6.25.9 in case you want to look at that too for any reason


edit:

i tried out your way and got this:

```
tamp-manual stamp-patch stamp-buildpackage stamp-debian
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian INITRD=YES
====== making target minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian || mkdir debian
mkdir: cannot create directory `debian': Permission denied
make: *** [minimal_debian] Error 1
Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 1096.
sudo: build-kern: command not found
```

---

### Post by Yellow Pasque on 2008-06-27
Here are some scripts to compile the latest version of ALSA: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by maulik001 on 2008-06-27
hey try this its kinda simple and worked on my toshiba P100 with HDA intel,

[http://ubuntuforums.org/showthread.php?t=842459]("http://ubuntuforums.org/showthread.php?t=842459")

---

### Post by master_kernel on 2008-06-27
> **Brando569 said:**
> this is my entire script, i believe that i initially based all of the commands off of the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158) but added in the variables myself. i also read somewhere while researching the intel hd audio problem that you dont need to use an initrd when you compile a custom kernel, how would i go about not including one? i removed the --initrd option from make-kpkg but it still ended up making one.

Feel free to use this if you want to even though its nothing special, im actually waiting for master_kernels new version of kernelcheck that comes out in a few days since his last version worked well but i didnt like the fact that it didnt check to see if you already had the kernel source and it would download a 40+mb package each time you ran it

```
#!bin/bash

clear
echo "what kernel version are you using? linux-2.6.what?"
read kernel_version

echo "what patch are you using? patch-2.6.$kernel_version.what?"
read patch_version

##get necessary stuff from the repositories
#sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget

#copying kernel source and patches
cd /usr/src
sudo cp /boot/config-`uname -r` .config
sudo cp ~/Downloads/kernels/linux-2.6.$kernel_version.tar.bz2 /usr/src
sudo cp ~/Downloads/kernels/patches/patch-2.6.$kernel_version.$patch_version.bz2 /usr/src

#extracting kernel
sudo tar -xvjf linux-2.6.$kernel_version.tar.bz2
sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.$kernel_version linux
cd linux

#patching kernel
sudo bzcat /usr/src/patch-2.6.$kernel_version.$patch_version.bz2 | sudo patch -p1
#sudo cp ~/kernel/speed_hacked.config .config

#making kernel
sudo make xconfig
sudo make-kpkg clean
**sudo make-kpkg kernel_image kernel_headers**
sudo ln -s /lib/firmware/2.6.22-15-generic /lib/firmware/2.6.$kernel_version.$patch_version

#installing kernel and headers
cd ..
sudo dpkg -i linux-image-2.6.$kernel_version*.deb
sudo dpkg -i linux-headers-2.6.$kernel_version*.deb 

#nvidia driver
#sudo sh /home/bran/Downloads/NVIDIA-Linux-x86-173.14.09-pkg1.run --update --kernel-source-path=/usr/src/linux
```

ive attached my last config that i used to compile 2.6.25.9 in case you want to look at that too for any reason


edit:

i tried out your way and got this:

```
tamp-manual stamp-patch stamp-buildpackage stamp-debian
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian INITRD=YES
====== making target minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian || mkdir debian
mkdir: cannot create directory `debian': Permission denied
make: *** [minimal_debian] Error 1
Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 1096.
sudo: build-kern: command not found
```
About that nvidia line at the bottom... does that actually work? (when it's uncommented of course)

---

### Post by Brando569 on 2008-06-27
> **maulik001 said:**
> hey try this its kinda simple and worked on my toshiba P100 with HDA intel,

[http://ubuntuforums.org/showthread.php?t=842459]("http://ubuntuforums.org/showthread.php?t=842459")

i was actually thinking about a bios update, since my version is 1402 and they have about 2 other versions between mine and the newest one

[QUOTE=master_kernel]About that nvidia line at the bottom... does that actually work? (when it's uncommented of course)[/QUOTE]

it does work, so to speak, but it downloaded the wrong version (i was running 173.14.09 and it downloaded 173.14.05 for some reason) and went it went through with it, it complained that the xserver was running. i highly recommend the way in the bottom of vors post(s) rather then mine.

---

### Post by sdennie on 2008-06-27
> **Brando569 said:**
> 
i tried out your way and got this:

```
tamp-manual stamp-patch stamp-buildpackage stamp-debian
exec make -f /usr/share/kernel-package/ruleset/minimal.mk debian INITRD=YES
====== making target minimal_debian [new prereqs: ]======
This is kernel package version .
test -d debian || mkdir debian
mkdir: cannot create directory `debian': Permission denied
make: *** [minimal_debian] Error 1
Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 1096.
sudo: build-kern: command not found
```

I'm not sure what would cause that.  Did you use sudo before the command and run it from the directory where the kernel source lives?

---

### Post by Brando569 on 2008-06-27
yep i tried it without sudo, with sudo and with sudo and removed fakeroot from the args, they all gave the same thing...

im about to install ubuntu 8.04 today since i know why it came out so horrible the last time (cdrom drive is screwing stuff up) and ill see if most of these problems are linux mint specific or ubuntu/computer problems.

---

