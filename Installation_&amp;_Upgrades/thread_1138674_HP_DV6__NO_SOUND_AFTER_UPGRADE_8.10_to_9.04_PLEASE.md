---
title: "HP DV6  NO SOUND AFTER UPGRADE 8.10 to 9.04 PLEASE HELP"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by manolis_nestor on 2009-04-26
I have just upgrade ubuntu from 8.10 to 9.04 and I lost the sound. 
aplay gives 
manolis@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
manolis@ubuntu:~$ 

PLEASE HELP ME

---

### Post by chek2fire on 2009-04-26
Many people have the same problem. You can see and here

[http://ubuntuforums.org/showthread.php?t=1134447](http://ubuntuforums.org/showthread.php?t=1134447)

one quick solution is to change everything in sound settings to oss and to wait for one fix update

---

### Post by manolis_nestor on 2009-04-27
> **chek2fire said:**
> Many people have the same problem. You can see and here

[http://ubuntuforums.org/showthread.php?t=1134447](http://ubuntuforums.org/showthread.php?t=1134447)

one quick solution is to change everything in sound settings to oss and to wait for one fix update

OSS does not work for me. Any  ideas?
:confused::confused::confused:

---

### Post by moe46 on 2009-04-28
Hi

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

Not sure if the solution for your problem will be found there
but i found that site very helpful and u might need it in the future

Its a very complete guide for all things HP Pavilion

Hope it helps,
Mushiden

---

### Post by manolis_nestor on 2009-04-30
> **moe46 said:**
> Hi

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

Not sure if the solution for your problem will be found there
but i found that site very helpful and u might need it in the future

Its a very complete guide for all things HP Pavilion

Hope it helps,
Mushiden

Dear Mushiden
 Thank you about your help, but the problem **was not** solved.

---

### Post by pissedoffdude on 2009-04-30
> **manolis_nestor said:**
> I have just upgrade ubuntu from 8.10 to 9.04 and I lost the sound. 
aplay gives 
manolis@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
manolis@ubuntu:~$ 

PLEASE HELP ME

I had the same issue with that card.  The solution was to upgrade to the latest kernel:

```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
cd /usr/src
sudo -s
wget -c http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.29.tar.bz2 && tar -xvjf linux-2.6.29.tar.bz2
rm -rf linux && ln -s /usr/src/linux-2.6.29 linux && cd /usr/src/linux
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.30-rc4.bz2
bzcat patch-2.6.30-rc4.bz2| patch -p1
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig

```

in this next step, you can enable any wireless drivers (though your wireless driver may already been enabled)
```
make xconfig
```

now time to compile it:
```
make-kpkg clean
```
```
CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 kernel_image 
kernel_headers modules_image
```  
You can replace that 386 with anything. It won't affect it because it's just what you want to call it.  

Then install it:
```
cd .. && dpkg -i linux*2.6.30*.deb
```

If you have an nvidia or ati video card, you're gonna have to reinstall its drivers.  

Reboot, play with some of the volume settings, and you should have sound

---

### Post by manolis20m on 2009-05-13
THANKS A LOT pissedoffdude! But now I have instaled ubuntu 8.10 again. The sound is perfech. I will upgrade only if a pach solves the problem.

---

### Post by mahboop on 2009-05-30
[COLOR="Green"]hi my friends,
I have the same problem with the same laptop (hp pavilion dv6 with ubuntu 9.04)
I'm doing the steps that Mr. (pissedoffdude) said then I'll tell you the result
---
see you[/COLOR]

---

### Post by mahboop on 2009-05-30
Hi my friend pissedoffdude,

I did all the step peacefully, but I got this error with the last command. Here is my terminal output:

```

root@mahboop-laptop:/usr/src/linux# **cd .. && dpkg -i linux*2.6.30*.deb**
Selecting previously deselected package linux-image-2.6.30-rc4.
(Reading database ... 209105 files and directories currently installed.)
Unpacking linux-image-2.6.30-rc4 (from linux-image-2.6.30-rc4_386_i386.deb) ...
Done.
Setting up linux-image-2.6.30-rc4 (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc4
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-rc4
root@mahboop-laptop:/usr/src# 


```
and after rebooting, **the problem isn't solved**.
> **pissedoffdude said:**
> 
play with some of the volume settings, and you should have sound
I don't know which setting to play with to get my sound back.
please help...

---

### Post by pissedoffdude on 2009-05-31
> **mahboop said:**
> Hi my friend pissedoffdude,

I did all the step peacefully, but I got this error with the last command. Here is my terminal output:

```

root@mahboop-laptop:/usr/src/linux# **cd .. && dpkg -i linux*2.6.30*.deb**
Selecting previously deselected package linux-image-2.6.30-rc4.
(Reading database ... 209105 files and directories currently installed.)
Unpacking linux-image-2.6.30-rc4 (from linux-image-2.6.30-rc4_386_i386.deb) ...
Done.
Setting up linux-image-2.6.30-rc4 (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc4
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-rc4
root@mahboop-laptop:/usr/src# 


```
and after rebooting, **the problem isn't solved**.

I don't know which setting to play with to get my sound back.
please help...

Looks like you're missing the header files.  To install them, do the following:
  Boot ubuntu with the old kernel that you did not compile.  Then use synaptic to **completely** remove the 2.6.30rc4 kernel.  After that, open a terminal and type in```
cd /usr/src/linux
sudo -s
CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 kernel_headers modules_image
cd .. && dpkg -i linux*2.6.30*.deb

```

When it asks about the menu.lst, tell it to install the new version, which should be the top option. You will still more than likely receive an nvidia error towards the end, but just ignore it for now. 
 
Be sure you have a copy of the latest nvidia drivers if you are unable to start x when you boot the new kernel.  Once your up and running you should have sound.  If you don't, make sure no channels are muted in ```
alsamixer
```

---

### Post by mahboop on 2009-05-31
hello,
I started my ubuntu on the old kernel linux-image-2.6.28-rc4
I removed linux-image-2.6.30-rc4 as you said.
I executed the command one by one, but I got the same error:
```

root@mahboop-laptop:/usr/src/linux-2.6.29# cd .. && dpkg -i linux*2.6.30*.deb
Selecting previously deselected package linux-headers-2.6.30-rc4.
(Reading database ... 208994 files and directories currently installed.)
Unpacking linux-headers-2.6.30-rc4 (from linux-headers-2.6.30-rc4_386_i386.deb) ...
Selecting previously deselected package linux-image-2.6.30-rc4.
Unpacking linux-image-2.6.30-rc4 (from linux-image-2.6.30-rc4_386_i386.deb) ...
Done.
Setting up linux-headers-2.6.30-rc4 (386) ...

Setting up linux-image-2.6.30-rc4 (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc4
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-rc4
root@mahboop-laptop:/usr/src# 

```
---
What should I do??
Knowing that the sound is working fine in the same laptop 
but with Vista :(
I don't like using it, but it is there for emergency events.
-
Regards

---

### Post by pissedoffdude on 2009-06-01
> **mahboop said:**
> hello,
I started my ubuntu on the old kernel linux-image-2.6.28-rc4
I removed linux-image-2.6.30-rc4 as you said.
I executed the command one by one, but I got the same error:
```

root@mahboop-laptop:/usr/src/linux-2.6.29# cd .. && dpkg -i linux*2.6.30*.deb
Selecting previously deselected package linux-headers-2.6.30-rc4.
(Reading database ... 208994 files and directories currently installed.)
Unpacking linux-headers-2.6.30-rc4 (from linux-headers-2.6.30-rc4_386_i386.deb) ...
Selecting previously deselected package linux-image-2.6.30-rc4.
Unpacking linux-image-2.6.30-rc4 (from linux-image-2.6.30-rc4_386_i386.deb) ...
Done.
Setting up linux-headers-2.6.30-rc4 (386) ...

Setting up linux-image-2.6.30-rc4 (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc4
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 1186.
dpkg: error processing linux-image-2.6.30-rc4 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-rc4
root@mahboop-laptop:/usr/src# 

```
---
What should I do??
Knowing that the sound is working fine in the same laptop 
but with Vista :(
I don't like using it, but it is there for emergency events.
-
Regards

Are you able to boot the new kernel?  If you are, sound should be working now.  Check the settings by right clicking the sound icon in your system tray and going to open volume control.  Then go to preferences and check all the playback channels.  After that, make sure none are muted.  If you still don't have sound, another thing you can try is adding a line to your alsa-base.conf file:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```and add the line
```
options snd-hda-intel model=hp-m4
```  Reboot, and let me know how it goes.

---

### Post by mahboop on 2009-06-04
[B][COLOR="Green"]Hi,
I did what you said exactly when booting on the new (30) kernet.
Then I did the sound setting but [COLOR="DarkRed"]NO SOUND[/COLOR]. I added the line in that file and rebooted the system. When I first logged in I heard a sound but I tried to play any audio file that I have but [COLOR="DarkRed"]NO SOUND IS WORKING[/COLOR].
-
I'm sorry for bothering you my friend :)
Regards[/COLOR][/B]

---

### Post by zman58 on 2009-06-04
Test sound with Live CD before you install. Consider installing from scratch if Live CD provides sound but upgrade broke it. Try the 32 bit i386 desktop version if you are not using that already.

---

### Post by pissedoffdude on 2009-06-04
> **mahboop said:**
> [B][COLOR="Green"]Hi,
I did what you said exactly when booting on the new (30) kernet.
Then I did the sound setting but [COLOR="DarkRed"]NO SOUND[/COLOR]. I added the line in that file and rebooted the system. When I first logged in I heard a sound but I tried to play any audio file that I have but [COLOR="DarkRed"]NO SOUND IS WORKING[/COLOR].
-
I'm sorry for bothering you my friend :)
Regards[/COLOR][/B]

Hmm, weird that you'd hear the start-up sound but not anything else.  Another suggestion I'll give is to play around with the settings in system>preferences sound.  If still nothing after that, have a look at this [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by mahboop on 2009-06-08
[COLOR="Green"]Hi[COLOR="DarkRed"] *[/COLOR],

The sound is working now. I don't know how & why.
I just started ubuntu today and I found the sound is working.

Thanks to you all for helping
Regards,[/COLOR]

---

### Post by mahboop on 2009-06-10
Hi all,

Another problem: if I want to install any application, I get this error:
```

mahboop@mahboop-laptop:~$ sudo apt-get install man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
man-db is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.30-rc4 (386) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.30-rc4
) points to /boot/initrd.img-2.6.30-rc4
 (/boot/initrd.img-2.6.30-rc4) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.30-rc4
) points to /boot/vmlinuz-2.6.30-rc4
 (/boot/vmlinuz-2.6.30-rc4) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 588.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-rc4
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
**Failed** to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30-rc4.postinst line 1186.
dpkg: **error** processing linux-image-2.6.30-rc4 (--configure):
 subprocess post-installation script returned error exit status 2
**Errors** were encountered while processing:
 linux-image-2.6.30-rc4
E: Sub-process /usr/bin/dpkg returned an error code (1)
mahboop@mahboop-laptop:~$ 


```
---
I can't download packages....??
-
Any help??

---

### Post by mahboop on 2009-06-10
If I update using "Update Manager", I get this error:
```

E: linux-image-2.6.30-rc4: subprocess post-installation script returned error exit status 2

```
--
....any solution??

---

### Post by pissedoffdude on 2009-06-12
> **mahboop said:**
> If I update using "Update Manager", I get this error:
```

E: linux-image-2.6.30-rc4: subprocess post-installation script returned error exit status 2

```
--
....any solution??

I've been using synaptic to upgrade my packages and am getting the same error.  Not too sure what its fix is, and I'm pretty sure it has something to do with using an unsupported package, but it doesn't seem to be affecting the packages that much. Regardless of the error, my packages are able to update, so I'm just ignoring it for now.  If anyone has any info on this, it would be appreciated if we could get a fix on this.

---

### Post by mahboop on 2009-06-23
[COLOR="Green"]Hi All,
when I update my kernel (linux-image-2.6.30-rc4)
I get an error says "[COLOR="DarkRed"]**there is a crash in your system, please report the problem**[/COLOR]".
When I click (Report Problem now), I get this:
---
[B][COLOR="DarkRed"]Problem in linux-image-2.6.30-rc40
The problem cannot be reported:

This is not a genuine Ubuntu package[/COLOR][/B]
----
Why this is happening???? 
Is there something called not genuine for Ubuntu???
Isn't that only for Windows stuff???
--
any solutions??
Regards[/COLOR]

---

### Post by mahboop on 2009-07-10
still waiting for a solution...

Regards

---

### Post by mahboop on 2009-08-20
^^^
:(

---

### Post by bedes on 2009-09-03
Im having the same issue - no sound on HP dv6 laptop.  Im running Linux Mint 7, is that the issue??

Im running the latest kernel and dl'd the patch v2.6.30-rc4.tar.bz2

I made it to make xconfig.  heres the output:

```
CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2

```

thanks for the help

---

### Post by mahboop on 2009-10-17
still waiting for a solution...

Regards

---

