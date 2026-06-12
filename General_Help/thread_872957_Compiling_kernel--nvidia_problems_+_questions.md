---
title: "Compiling kernel--nvidia problems + questions"
date: 2008-07-28
forum: General Help
---

### Post by logos34 on 2008-07-28
I'm getting ready to try compiling a custom kernel (the manual debian way if possible) for my regular installation, but when I used KernelCheck yesterday the nvidia config didn't come out too nice.  The restricted drivers manager is blank even though the 'nvidia' driver is in use (glx-new).  Nvidia-settings was unresponsive.  I then tried EnvyNG, but still same thing.  Now I did get the resolution and everything fixed (by simply copying my existing xorg file to the test parititon I was doing the kernel compile on).  But I'd like to do everything right this time.  

Do I need to top follow the separate 'restrictedModulesCompilation' if I just want to use the nvidia-glx-new driver and be able to use nvidia-settings config gui?  

What about pulse-audio support--anything special I need to do so it works with alsa?

---

### Post by logos34 on 2008-07-28
bump

---

### Post by PmDematagoda on 2008-07-29
About the Nvidia-glx package, it most likely will not work with a kernel you compile yourself since the Nvidia kernel module is made by compiling it against the kernel source, the nvidia-glx package consists of a Nvidia driver module made specifically for the corresponding current Ubuntu kernel version and not to any other third-party kernel unless they are similar to each other in a way that would make the Nvidia driver module happy which results in it's failure/improper functionality. So in order to get the best results, you are advised to install the Nvidia driver yourself for best results.

Important NOTE:- Do not move/remove the kernel source files from which you installed your custom kernel from, if you do then the Nvidia installer will not be able to find the kernel source which it requires to build the Nvidia module and will fail. If you have moved/removed the kernel source, then you may need to obtain the same kernel source again and relink it to /lib/modules/kernel-version/build.

About PulseAudio and ALSA, all you need to ensure is that the appropriate ALSA drivers have been included in the kernel you compiled, if the ALSA drivers for your audio card are present, that PulseAudio will work automatically.

---

### Post by sdennie on 2008-07-29
I agree with what PmDematagoda said and would like to give a few tips:

1) If you use the Ubuntu kernel config as your base, it probably won't have the Intel iwl wireless drives enabled by default so you'll have to enable them in menuconfig or xconfig.

2) If you use the Ubuntu kernel config as your base, it probably won't have the Intel snd_hda_intel driver enabled by default so you'll have to enable them in menuconfig or xconfig.

3) Custom kernel installs don't magically create firmware directories for that kernel so, you'll have to do it by hand.  Alternatively, you can use this simple script: [http://ubuntuforums.org/showpost.php?p=5472677&postcount=10](http://ubuntuforums.org/showpost.php?p=5472677&postcount=10)

4) Things like nvidia drivers and virtualbox drivers are kernel specific and so building a new kernel, you won't have them.  The link in #3 has links to how to automatically build them for new kernels at the bottom (assuming you are using non-Ubuntu versions of them).

Hope that helps.

---

### Post by logos34 on 2008-07-30
Thanks again for all your help, guys, but it looks like I'm going to have to forget about custom compiled kernel for now.  I was able to do it and run the EnvyNG installed nvidia driver on a test x64 hardy partition, but it doesn't want to work on my regular ubuntu studio 8.04 x64 installation.  Nvidia just won't cooperate...Unless I want to use the 'vesa' driver I guess I'm out of luck.

---

### Post by sdennie on 2008-07-30
I'm not sure what the problem with your nvidia drivers are.  I've used custom kernels and nvidia for several years and have not had any problems.  Have you tried using the downloaded drivers and one of the many guides on installing them on Ubuntu?

---

### Post by logos34 on 2008-07-30
yeah, tried these releases:

Linux x64 (AMD64/EM64T) Display Driver

Version: 173.14.05 -->fails concluding 'sanity check'
Version: 173.14.09-->won't even build kernel module
Version: 177.13 beta-->won't even build kernel module

Neither does EnvyNG installed driver work (using 173.14.09)...Blank screen on reboot...Can't seem to hit upon a  working a xorg.conf config.  This despite the fact that I got it to work on my test custom kernel installation (KernelCheck ultimate).  It's all in my other posts.

Maybe I need to try the 169 releases:

169.12
189.07
169.09

which is essentially what the nvidia-glx-new is using

add: would be nice to figure out a way to use the 173.14.09 release, though, because it says:
> [COLOR=red]Added preliminary support for Linux 2.6.26.[/COLOR]

---

### Post by sdennie on 2008-07-30
I don't think anything earlier to 173.14.09 will work with 2.6.26 without patching it.  The errors you get while trying to build that version might be useful (I think the log lives in /var/log/nvidia-installer.log).

---

### Post by logos34 on 2008-07-30
> **vor said:**
> I don't think anything earlier to 173.14.09 will work with 2.6.26 without patching it.  The errors you get while trying to build that version might be useful (I think the log lives in /var/log/nvidia-installer.log).

I posted the log here:
[http://ubuntuforums.org/showthread.php?t=873790](http://ubuntuforums.org/showthread.php?t=873790)

I guess my main problem is I can't even successfully build the kernel module and install the driver against the 2.6.24-19 source, let alone the 2.6.26... (but maybe that's due to what you said)

I probably should just go straight ahead and compile the 2.6.26 kernel, THEN try the nvidia kernel module build against that source, using 173.14.09 or beta 177.13

---

### Post by sdennie on 2008-07-30
What are the logs for the .09 driver?  I'm not sure that .05 will work.

---

### Post by logos34 on 2008-07-30
I didn't save it, but it hardly gets started, just fails right away--something like 'cannot build module'

---

### Post by sdennie on 2008-07-30
That output would be very useful.  I'm running 2.6.26 with a manually installed nvidia 173.14.09 and it works fine so, it's certainly possible to do it.

---

### Post by logos34 on 2008-07-30
ok, then that gives me hope...I'll do what I said before and hopefully I won't have to keep bugging you guys with my qusetions!

thanks again.

(believe or not I used to be a semi-pro when it came to manually installing the nvidia drivers--mostly way back in Suse days--but ubuntu -glx has made it too easy)

---

### Post by logos34 on 2008-07-30
At the risk of beating a dead horse...

I just noticed this re failed 'sanity check' with libnvidia files.

Here is how the nvidia-glx-new has things arranged:

> user@ubuntu:~$ ls -l /usr/lib | grep libnvidia*
lrwxrwxrwx  1 root  root        23 2008-07-10 18:18 libnvidia-cfg.so.1 -> libnvidia-cfg.so.169.12
-rw-r--r--  1 root  root    127160 2008-07-09 11:46 libnvidia-cfg.so.169.12
[COLOR=Green]lrwxrwxrwx  1 root  root        23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.169.12
-rw-r--r--  1 root  root      3352 2008-07-09 11:46 libnvidia-tls.so.169.12[/COLOR]
user@ubuntu:~$ ls -l /usr/lib/tls | grep libnvidia*
[COLOR=Green]lrwxrwxrwx 1 root root 23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.169.12
[COLOR=Blue]lrwxrwxrwx 1 root root 26 2008-07-10 18:18 libnvidia-tls.so.169.12 -> ../libnvidia-tls.so.169.12[/COLOR][/COLOR]
user@ubuntu:~$ ls -l /usr/lib32 | grep libnvidia*
lrwxrwxrwx 1 root root       23 2008-07-10 18:18 libnvidia-cfg.so.1 -> libnvidia-cfg.so.169.12
-rw-r--r-- 1 root root   110432 2008-07-09 11:46 libnvidia-cfg.so.169.12
[COLOR=Green]lrwxrwxrwx 1 root root       23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.169.12
-rw-r--r-- 1 root root     2236 2008-07-09 11:46 libnvidia-tls.so.169.12[/COLOR]
user@ubuntu:~$ ls -l /usr/lib32/tls | grep libnvidia*
[COLOR=Green]lrwxrwxrwx 1 root root   23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.169.12
-rw-r--r-- 1 root root 2284 2008-07-09 11:46 libnvidia-tls.so.169.12[/COLOR]

Note how the one in blue refers up a level.


But the official 173.14.05 driver is doing the links slightly differently (IIRC):

> user@ubuntu:~$ ls -l /usr/lib | grep libnvidia*
[COLOR=Black]lrwxrwxrwx  1 root  root        23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black] -rw-r--r--  1 root  root      3352 2008-07-09 11:46 libnvidia-tls.so.173.14.05
user@ubuntu:~$ ls -l /usr/lib/tls | grep libnvidia*
[/COLOR] [COLOR=Black]lrwxrwxrwx 1 root root 23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black][COLOR=Red] lrwxrwxrwx 1 root root 26 2008-07-10 18:18 libnvidia-tls.so.173.14.05[/COLOR]
user@ubuntu:~$ ls -l /usr/lib32 | grep libnvidia*
[/COLOR] [COLOR=Black]lrwxrwxrwx 1 root root       23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black] -rw-r--r-- 1 root root     2236 2008-07-09 11:46 libnvidia-tls.so.173.14.05
user@ubuntu:~$ ls -l /usr/lib32/tls | grep libnvidia*
[/COLOR] [COLOR=Black]lrwxrwxrwx 1 root root   23 2008-07-10 18:18 libnvidia-tls.so.1 -> libnvidia-tls.so.173.14.05
[/COLOR][COLOR=Black] -rw-r--r-- 1 root root 2284 2008-07-09 11:46 libnvidia-tls.so.173.14.05[/COLOR]

(i've left out the -.cfg files for clarity sake.)

One in red differs--it is NOT a link with target in parent dir

---

### Post by sdennie on 2008-07-30
You can't use 173.14.05 with 2.6.26.  Try 173.14.09.  Also, nvidia-glx-new installs in a different way to the manually installed drivers.  I recommend removing nvidia packages before installing the downloaded drivers:

```

sudo apt-get purge nvidia*

```

---

### Post by logos34 on 2008-07-30
Ok, I have good news:

Success at last--well almost. USB seems to be the one thing that doesn't work.  So I can't use my USB mouse.

I built the 2.6.26 linux-image and -header debs on my regular installation.  Then I installed Ubuntu Studio x64 on a spare partition and copied the debs, the 'linux-2.6.26' folder and the NVIDIA-Linux...173.14.09...run driver over.  Installed the debs and ran

> sudo sh NVIDIA-Linux-x86_64-173.14.09-pkg2.run --kernel-source-path=/home/user/linux-2.6.26
NOT =/usr/src/linux-headers-2.6.26-rt-k8-amd64

which is how the header installed.

Only one complaint (not fatal) near end:
> 
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
[COLOR=Red]WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.173.14.09'); assuming successful
         installation.[/COLOR]
-> done.
[COLOR=Green]-> Runtime sanity check passed.[/COLOR]
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 173.14.09)
   is now complete.
the files all seemed to be there when I restarted and checked.  So I guess it's nothing to worry about.

Configure nvidia-settings...checked sound--ok...Boots fast (but not quite as quickly as it does on regular x64 ubuntu).  

What I get on boot:

> Decompressing linux...Parsing ELF...done.
Aperature beyond 4GB.  Ignoring.I only have 512 MB ram.  I looked in xconfig for a ~ 'HIGHMEM' or 
high memory' option to disable but didn't see anything.  

BTW I followed the xconfig recommendations here:
[http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)
[http://ubuntuforums.org/showpost.php?p=1835811&postcount=1](http://ubuntuforums.org/showpost.php?p=1835811&postcount=1)
[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

But USB isn't working, and that's a real problem.  My USB mouse (trackball to be precise) cursor is just stuck on screen.   I can only use the keyboard.  Restarted.  No change.

Neither lsusb or lshw show any usb devices.  No 'HID' device or 'USB Trackball'.  So either I accidentally unselected some USB setting in make xconfig, or its a fluke.

$ sudo lshw 
> *-usb:0 UNCLAIMED
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:1 UNCLAIMED
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: latency=0 maxlatency=1 mingnt=3lsusb is blank.  I expected this:
> 
$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: **ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)**
Bus 001 Device 001: ID 0000:0000  So it sees the usb controller but not the attached device(s).

Sorry to bore you with the details.  But any tips appreciated.  (From anyone reading this post)

---

### Post by logos34 on 2008-07-30
I went back and checked the .config file...the only reference to usb is this:

> #
# Open Sound System
#
# CONFIG_SOUND_PRIME is not set
CONFIG_AC97_BUS=m
**CONFIG_HID_SUPPORT=y**
CONFIG_HID=m
# CONFIG_HID_DEBUG is not set
CONFIG_HIDRAW=y
**# CONFIG_USB_SUPPORT is not set**
CONFIG_MMC=m
# CONFIG_MMC_DEBUG is not set
# CONFIG_MMC_UNSAFE_RESUME is not setBut that's under the Sound section--it said it referred to external usb sound devices, I think.  So I may have disabled it.



*EDIT--

Doesn't look good.  No 'usb' in lsmod.  None.  So somehow usb modules didn't get built.  

Sh*t.

back to building another kernel....

---

### Post by logos34 on 2008-07-30
Nevermind--found the answer

No wonder no USB modules got built--it was UNCHECKED!

The checkbox was here (looking at xconfig screen):

> ...
+    Sound
+ **x** HID Devices
[COLOR=Red]+       USB support[/COLOR]
      MMC/SD card support

...There's a ton of stuff inside--OHCI, EHCI, etc. USB printer, wifi, masstorage support, etc. etc.--all disabled.  Did I say sh*t?

Jeez, I managed to select 'HID' but how did I miss THAT?  DUH!  Funny there's a mentally handicapped institute in our neighborhood--I'll need it...

---

### Post by logos34 on 2008-07-30
UPDATE (for anyone still interested):

--Selected 'USB' and went throu it, checking any device support I might concievably need in the future. Recompiled kernel.

My custom 2.6.26 kernel works perfectly now!

One thing I've noticed, though: the 'voluntary preemption' (Desktop) kernel setting seems to give slightly better performance than real-time/low-latency 'involuntary preemption.'  I have the timer set to highest -- 1000 Hz.

Shutdown, suspend and hibernate are incredibly fast.  Bootup is noticeably faster than generic x86_64, but on this point the voluntary preemption is the fastest.  (Not much diff even after I disbled unnecessary programs/daemons in services and ran sysv-rc-conf.

Apps open faster, but that will slow down once I load up the panels and gnome desktop with assorted ram-hogging crap/eye candy. 

All things considered, however, I'd have to say that the generic x64 -rt kernel is pretty darn good after you get back to real-world gnome desktop configuration, with everything loaded in.  Despite the positive learning experience, I'm still mulling whether or not to switch to the custom -26 on my regular installation.  Upgrades will require reinstalling the nvidia driver (unless I use the auto script VOR provided).

---

### Post by PmDematagoda on 2008-07-30
If the kernel boots up and worked properly for sometime, then it can be safe to use it. But make sure you have a backup working kernel as well.

---

