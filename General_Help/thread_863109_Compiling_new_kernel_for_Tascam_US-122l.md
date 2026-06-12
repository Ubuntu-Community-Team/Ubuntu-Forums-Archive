---
title: "Compiling new kernel for Tascam US-122l"
date: 2008-07-18
forum: General Help
---

### Post by Earl_Maroon on 2008-07-18
I recently bought the Tascam US-122l (USB sound card, not yet supported in ALSA), thinking that it was the same as the US-122 (which is supported by ALSA). I have found a walkthrough that has been claimed to work for this and it involves compiling and installing a patched kernel. The thing is, the walkthrough is for Debian, and while I know that Ubuntu is based on Debian I'm not sure quite how compatible the walkthrough is. I assume it would be pretty fatal for my current install if I broke the kernel. There is one particular line which mentions *amd64.deb, but I use an x86. If someone could take a look at this and let me know if this is safe and if there is anything that needs to be changed for my purposes I'd be very grateful.

The walkthrough is at:
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

---

### Post by keithacole on 2008-07-28
i also bought a us-144(us-122l) and have been following this tutorial

[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

which does involve compiling a new kernel, since its a new kernel im fine with it, but after its compiled i will have to patch it for RealTime

my issue is there are errors in my quest

after compiling the kernel i get errors
```
 MODPOST 1911 modules
ERROR: "snd_hwdep_new" [sound/usb/usx2y/snd-usb-us122l.ko] undefined!
WARNING: modpost: Found 15 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.25.4'
make: *** [debian/stamp-build-kernel] Error 2

```

and then the next command after that are

```

 dpkg -i ../linux-image-2.6.25.4-us122l_1_amd64.deb
 dpkg -i ../*-modules-2.6.25-us122l_*1_amd64.deb

```

naturally there are no amd64.deb's but i did find the linux-image of the kernel, but the modules*.deb is not there, was it not built due to the module error from the kernel compiling?

when i continue on i get errors here with this command
```
CFLAGS="-Wall -g -O2" ./configure --prefix=/usr \
	    --mandir=\$${prefix}/share/man \
	    --infodir=\$${prefix}/share/info \
	    --host=$(shell dpkg-architecture -qDEB_HOST_GNU_TYPE) \
	    --build=$(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE) \
	    --enable-static

```

i am told 3 times about bash commands being bad, unfortunately i cant copy and paste it here but its generic bash command errors

the next step was packaging and i get this error
```
chmod: changing permissions of `/usr/lib/alsa-lib/libasound_module_pcm_jack.a': No such file or directory
make[2]: *** [install-asound_module_pcm_jackLTLIBRARIES] Error 1
make[2]: Leaving directory `/usr/src/alsa-plugins-1.0.16/jack'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/usr/src/alsa-plugins-1.0.16/jack'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

```

---

### Post by federicobriata on 2008-08-03
Ciao!

Lets leave for the moment RealTime patch...
You must follow the guide step by step. You can't skip some part.
The modules* will be only when 'make-kpkg kernel_image modules_image' will not give error.

As superusers type:
# cd /usr/src/linux
than paste all output of:
# cat .config | grep SND
If you don't get:
CONFIG_SND_HWDEP=m
that's maybe the problem, you can add it when you are in 'menuconfig'

Anyway some more detail will be useful to help you...
Which kernel are you using? which ubuntu version?
I'm installing now ubuntu 8.04 hardy heron, I'll try to add us122l support as soon as I can.. :)

Federico

---

### Post by dcuder on 2008-08-10
Here's the output of cat .config | grep SND

CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
# CONFIG_SND_MIXER_OSS is not set
# CONFIG_SND_PCM_OSS is not set
# CONFIG_SND_SEQUENCER_OSS is not set
# CONFIG_SND_RTCTIMER is not set
# CONFIG_SND_DYNAMIC_MINORS is not set
CONFIG_SND_SUPPORT_OLD_API=y
CONFIG_SND_VERBOSE_PROCFS=y
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
# CONFIG_SND_DUMMY is not set
# CONFIG_SND_VIRMIDI is not set
# CONFIG_SND_MTPAV is not set
# CONFIG_SND_MTS64 is not set
# CONFIG_SND_SERIAL_U16550 is not set
# CONFIG_SND_MPU401 is not set
# CONFIG_SND_PORTMAN2X4 is not set
# CONFIG_SND_ADLIB is not set
# CONFIG_SND_AD1816A is not set
# CONFIG_SND_AD1848 is not set
# CONFIG_SND_ALS100 is not set
# CONFIG_SND_AZT2320 is not set
# CONFIG_SND_CMI8330 is not set
# CONFIG_SND_CS4231 is not set
# CONFIG_SND_CS4232 is not set
# CONFIG_SND_CS4236 is not set
# CONFIG_SND_DT019X is not set
# CONFIG_SND_ES968 is not set
# CONFIG_SND_ES1688 is not set
# CONFIG_SND_ES18XX is not set
# CONFIG_SND_SC6000 is not set
# CONFIG_SND_GUSCLASSIC is not set
# CONFIG_SND_GUSEXTREME is not set
# CONFIG_SND_GUSMAX is not set
# CONFIG_SND_INTERWAVE is not set
# CONFIG_SND_INTERWAVE_STB is not set
# CONFIG_SND_OPL3SA2 is not set
# CONFIG_SND_OPTI92X_AD1848 is not set
# CONFIG_SND_OPTI92X_CS4231 is not set
# CONFIG_SND_OPTI93X is not set
# CONFIG_SND_MIRO is not set
# CONFIG_SND_SB8 is not set
# CONFIG_SND_SB16 is not set
# CONFIG_SND_SBAWE is not set
# CONFIG_SND_SGALAXY is not set
# CONFIG_SND_SSCAPE is not set
# CONFIG_SND_WAVEFRONT is not set
# CONFIG_SND_AD1889 is not set
# CONFIG_SND_ALS300 is not set
# CONFIG_SND_ALS4000 is not set
# CONFIG_SND_ALI5451 is not set
# CONFIG_SND_ATIIXP is not set
# CONFIG_SND_ATIIXP_MODEM is not set
# CONFIG_SND_AU8810 is not set
# CONFIG_SND_AU8820 is not set
# CONFIG_SND_AU8830 is not set
# CONFIG_SND_AZT3328 is not set
# CONFIG_SND_BT87X is not set
# CONFIG_SND_CA0106 is not set
# CONFIG_SND_CMIPCI is not set
# CONFIG_SND_OXYGEN is not set
# CONFIG_SND_CS4281 is not set
# CONFIG_SND_CS46XX is not set
# CONFIG_SND_CS5530 is not set
# CONFIG_SND_CS5535AUDIO is not set
# CONFIG_SND_DARLA20 is not set
# CONFIG_SND_GINA20 is not set
# CONFIG_SND_LAYLA20 is not set
# CONFIG_SND_DARLA24 is not set
# CONFIG_SND_GINA24 is not set
# CONFIG_SND_LAYLA24 is not set
# CONFIG_SND_MONA is not set
# CONFIG_SND_MIA is not set
# CONFIG_SND_ECHO3G is not set
# CONFIG_SND_INDIGO is not set
# CONFIG_SND_INDIGOIO is not set
# CONFIG_SND_INDIGODJ is not set
# CONFIG_SND_EMU10K1 is not set
# CONFIG_SND_EMU10K1X is not set
# CONFIG_SND_ENS1370 is not set
# CONFIG_SND_ENS1371 is not set
# CONFIG_SND_ES1938 is not set
# CONFIG_SND_ES1968 is not set
# CONFIG_SND_FM801 is not set
# CONFIG_SND_HDA_INTEL is not set
# CONFIG_SND_HDSP is not set
# CONFIG_SND_HDSPM is not set
# CONFIG_SND_HIFIER is not set
# CONFIG_SND_ICE1712 is not set
# CONFIG_SND_ICE1724 is not set
# CONFIG_SND_INTEL8X0 is not set
# CONFIG_SND_INTEL8X0M is not set
# CONFIG_SND_KORG1212 is not set
# CONFIG_SND_MAESTRO3 is not set
# CONFIG_SND_MIXART is not set
# CONFIG_SND_NM256 is not set
# CONFIG_SND_PCXHR is not set
# CONFIG_SND_RIPTIDE is not set
# CONFIG_SND_RME32 is not set
# CONFIG_SND_RME96 is not set
# CONFIG_SND_RME9652 is not set
# CONFIG_SND_SIS7019 is not set
# CONFIG_SND_SONICVIBES is not set
# CONFIG_SND_TRIDENT is not set
# CONFIG_SND_VIA82XX is not set
# CONFIG_SND_VIA82XX_MODEM is not set
# CONFIG_SND_VIRTUOSO is not set
# CONFIG_SND_VX222 is not set
# CONFIG_SND_YMFPCI is not set
# CONFIG_SND_USB_AUDIO is not set
CONFIG_SND_USB_USX2Y=m
CONFIG_SND_USB_CAIAQ=m
CONFIG_SND_USB_CAIAQ_INPUT=y
CONFIG_SND_USB_US122L=m
# CONFIG_SND_VXPOCKET is not set
# CONFIG_SND_PDAUDIOCF is not set
# CONFIG_SND_SOC is not set

As you can see CONFIG_SND_HWDEP=m is ok, but nothing's workin'...

---

### Post by keithacole on 2008-08-11
i have redone my system and dont show any sign of the patch as yet. i will wait for you to complete then i will try again.

---

### Post by federicobriata on 2008-08-16
Hello,
I add preliminary howto for Ubuntu 8.04 Hardy Heron.

For Ubuntu intrepid should be the same step except for libasound2-plugins sections, where with 'apt-get source alsa-plugins' you'll get alsa-utils 1.0.16 instead of 1.0.15.

Please let me know if is working.

[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

Best regards,

Federico

---

### Post by keithacole on 2008-08-18
im trying your new method out now. so far no errors, except for having a hard time grabbing the patch, (kept timing out on the download)

but kernel is compiling now.

i read in about he issues between usb 1 and 2, should the device be on usb 1 instead of 2? with this patch?

---

### Post by keithacole on 2008-08-18
OK, everything got compiled and i ran into no errors, except that the device is still not listed  in /proc/asound/cards

i see the module snd-usb-us122l i modprobe it and pull the cable on the interface, i check dmesg and there are no errors, but still the device doesnt list under /proc/asound/cards

is it because of alsa 1.0.15 ?

---

### Post by federicobriata on 2008-08-18
Hi!
after kernel patches you should get it with cat /proc/asound/cards.

First test I didn't get working too in usb2,
I check kernel messages (sudo dmesg) and something wasn't good with ehci patch, I removed ehci_hcd (sudo rmmod ehci_hcd) plug it again and was working but in usb1 mode.
Than I've seen that us122l-patches.tar.bz2 witch I download from gmane.org was an empty file, so I rebuild kernel with ehc patch and now is ok.
Maybe have you got the same inconvenience? :)

I also realize that I miss few step for Alsa-plugins STEP for Ubuntu, now usb_stream is included correctly in libasound2-plugins.

Regards,
Federico

---

### Post by keithacole on 2008-08-20
sudo rmmod ehci_hcd) did not work for me. i still dont have the device show up in /proc/asound/cards. but it does show up in lsusb.

could you create a .deb package from your system that would work?

---

### Post by LevTermen on 2008-08-22
Karsten Wiese's patches are making their way into the ALSA driver, from v1.0.18rc1 (check the [changelog]("http://www.alsa-project.org/main/index.php/Changes_v1.0.17a_v1.0.18rc1")).

Unfortunately I have an US-144 for testing...

I first compiled Kernel Vanilla 2.6.25.4 under Ubuntu 8.04 Hardy Heron following Federico Briata's tutorial.

I then tried to modify snd-usb-us122l_0.5.patch l.771-781
```

+static struct usb_device_id snd_us122l_usb_id_table[] = {
+	{
+		.match_flags =	USB_DEVICE_ID_MATCH_DEVICE,
+		.idVendor =	0x0644,
+		.idProduct =	USB_ID_US122L
+	},
+/*  	{ */		/* US-144 maybe works when @USB1.1. Untested. */
+/* 		.match_flags =	USB_DEVICE_ID_MATCH_DEVICE, */
+/* 		.idVendor =	0x0644, */
+/* 		.idProduct =	USB_ID_US144 */
+/* 	}, */

```into```

+static struct usb_device_id snd_us122l_usb_id_table[] = {
+/*	{*/
+/*		.match_flags =	USB_DEVICE_ID_MATCH_DEVICE, */
+/*		.idVendor =	0x0644, */
+/*		.idProduct =	USB_ID_US122L */
+/*	},*/
+  	{ 		/* US-144 maybe works when @USB1.1. Untested. */
+ 		.match_flags =	USB_DEVICE_ID_MATCH_DEVICE, 
+ 		.idVendor =	0x0644,
+ 		.idProduct =	USB_ID_US144
+ 	},

```

Even after multiple replugs and reboots, dmesg outputs
```

snd-usb-us122l: probe of 5-5:1.1 failed with error -5

``` with an additional "couldn't __get_free_pages()" error message (generated from sound/usb/usx2y/usb_stream.c)...

Might be due to my patch mashup.

I also tried to compile this latest ALSA driver version (--with-cards=snd-us122l among other configure flags), but no related module gets built. The changelog reads "build stub for us122l", hence probably still some inactivated code snippets...

I guess I'll go fetch a Native-Instrument Audio Kontrol 1 tomorrow...

Good luck!

---

### Post by federicobriata on 2008-08-25
@keithacole
Ok I'll create package also for 32bit and public, as fast I can. 

@LevTermen
what's output of dmesg?
have you tried to remove usb2 module and test the card on usb1.1? You can get how to do this from previous post and now also from [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting)

---

### Post by keithacole on 2008-08-26
> **LevTermen said:**
> Karsten Wiese's patches are making their way into the ALSA driver, from v1.0.18rc1 (check the [changelog]("http://www.alsa-project.org/main/index.php/Changes_v1.0.17a_v1.0.18rc1")).


so if i compile and use the .18rc1 alsa driver will the interface work then?

---

### Post by keithacole on 2008-09-01
i acquired an Alesis QSR sound module last night. getting the tascam 144 working  would be great right about now becuase of its midi interface..


any progress guys?

---

### Post by federicobriata on 2008-09-09
Sorry for the delay...
Finally are available binary (for i386 and amd64) packages patched to work with US-122L.

Time for testing... :guitar:

[http://pub.briata.org/us-122l/](http://pub.briata.org/us-122l/)

[http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_amd64.deb](http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_amd64.deb)
[http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_amd64.deb](http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_amd64.deb)

[http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_i386.deb](http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_i386.deb)
[http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb](http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb)

The wiki [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) is updated.

Ciao,
Federico

---

### Post by ceverett on 2008-09-09
will these recognize the tascam usb-144 ???

---

### Post by keithacole on 2008-09-20
> **federicobriata said:**
> Sorry for the delay...
Finally are available binary (for i386 and amd64) packages patched to work with US-122L.

Time for testing... :guitar:

[http://pub.briata.org/us-122l/](http://pub.briata.org/us-122l/)

[http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_amd64.deb](http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_amd64.deb)
[http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_amd64.deb](http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_amd64.deb)

[http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_i386.deb](http://pub.briata.org/us-122l/libasound2-plugins_1.0.15-1ubuntu3_i386.deb)
[http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb](http://pub.briata.org/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb)

The wiki [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) is updated.

Ciao,
Federico









i get this error with linux-image-2.6.25.4-us122l_1.bri_i386.deb

```
keith@keith-desktop:~$ sudo dpkg -i /usr/src/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb 
[sudo] password for keith: 
(Reading database ... 166491 files and directories currently installed.)
Unpacking linux-image-2.6.25.4-us122l (from .../linux-image-2.6.25.4-us122l_1.bri_i386.deb) ...
Done.
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /usr/src/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.25.4-us122l/kernel/fs/cifs/cifs.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-rt
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /usr/src/us-122l/linux-image-2.6.25.4-us122l_1.bri_i386.deb
keith@keith-desktop:~$ 

```

im still not using the inteface :(

is linux-image-2.6.25.4-us122l_1.bri_i386.deb supposed to only be 5MB ?

---

### Post by edgar83 on 2008-09-23
> **ceverett said:**
> will these recognize the tascam usb-144 ???

UP!

I'm also interested!

ciao!

---

### Post by Earl_Maroon on 2008-11-06
The i386 kernel package seems to be missing...

---

### Post by 255 on 2008-11-23
***Beware that this is more likely a "hack" than a solution!***

Hi Folx,

I found a quick-n-dirty way to squeeze some sound out of that Tascam box without having to apply any patches.

First I installed a real-time kernel. In my case: ```
apt-get install linux-image-2.6.27-3-rt
``` Because a non-rt kernel produced lots of buffer under/overruns.
After booting with that kernel I took the [**Alsa 1.0.18 Installation Script**]("http://ubuntuforums.org/showthread.php?t=962695") to get the latest Alsa version. 
[Changelog sais]("http://www.alsa-project.org/main/index.php/Changes_v1.0.17a_v1.0.18rc1") needed drivers are already included in that version - so no patching necessary! :)
```
./AlsaUpgrade-1.0.x-rev-1.10.sh -f
```
Luckily the script does all the compiling mumbo-jumbo. But there is still that high-speed-usb-problem, where a kernel patch would be necessary. 
Now comes the dirty part: after rebooting with the new alsa version installed I just get rid of that usb-module: ```
rmmod ehci_hcd
```
Now the US-122l is recognized when plugged in and works as described in [federicobriatas wiki]("http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa") with Jack. To get rhythmbox working I configured gstreamer as described in [this howto]("http://ubuntuforums.org/showthread.php?t=554457").

Until a patched kernel is available that works for me, while doing some office work and just using the interface for music listening purposes. Since I don't have any other USB devices here to test with, I don't know the consequences resulting from that rmmod command for external drives, scanners etc... my usb-mouse works fine, though.

Best regards,
Flo

---

### Post by florian_roger on 2008-11-26
Hello everybody

I'm also trying to get Us-122l working on my Ubuntu Intrepid,
following [HTML]http://wiki.briata.org/doku.php?id=testing_us122l_under_linux[/HTML]

I have some doubt about the return of this command:
```
olivier@torcy:/usr/src$ ls | grep bri
linux-image-2.6.25.4-us122l_1.bri_i386.deb

```

I've done the first dpkg command and it resulted:
```
 sudo dpkg -i linux-image-2.6.25.4-us122l_1.bri_*.deb
Sélection du paquet linux-image-2.6.25.4-us122l précédemment désélectionné.        
(Lecture de la base de données... 108024 fichiers et répertoires déjà installés.)  
Dépaquetage de linux-image-2.6.25.4-us122l (à partir de linux-image-2.6.25.4-us122l_1.bri_i386.deb) ...
Done.                                                                                                  
Paramétrage de linux-image-2.6.25.4-us122l (1.bri) ... 
Running depmod.                                                                  
Finding valid ramdisk creators.                                                  
Using mkinitramfs-kpkg to build the ramdisk.                                     
initrd.img(/boot/initrd.img-2.6.25.4-us122l                                      
) points to /boot/initrd.img-2.6.25.4-us122l                                     
 (/boot/initrd.img-2.6.25.4-us122l) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.25.4-us122l.postinst line 583.
vmlinuz(/boot/vmlinuz-2.6.25.4-us122l                                                                                    
) points to /boot/vmlinuz-2.6.25.4-us122l                                                                                
 (/boot/vmlinuz-2.6.25.4-us122l) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.25.4-us122l.postinst line 583.   
Running postinst hook script update-grub.                                                                                
Searching for GRUB installation directory ... found: /boot/grub                                                          
Searching for default file ... found: /boot/grub/default                                                                 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst                                                
Searching for splash image ... none found, skipping ...                                                                  
Found kernel: /boot/vmlinuz-2.6.27-7-generic                                                                             
Found kernel: /boot/vmlinuz-2.6.25.4-us122l                                                                              
Found kernel: /boot/memtest86+.bin                                                                                       
Updating /boot/grub/menu.lst ... done                                                                                    

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

```
But I have a problem after:
```
olivier@torcy:/usr/src$  sudo dpkg -i *-modules-2.6.25-us122l_*1.bri_*.deb
dpkg*: erreur de traitement de *-modules-2.6.25-us122l_*1.bri_*.deb (--install)*:
 ne peut pas accéder à l'archive: Aucun fichier ou dossier de ce type            
Des erreurs ont été rencontrées pendant l'exécution*:                            
 *-modules-2.6.25-us122l_*1.bri_*.deb 
```

What should I do?
Is it a problem with my .config.

Note: I made sudo make defconfig in place of oldconfig, and changed the values using fr.wikipedia & fr.doc-ubuntu tutorials on compilling new kernel.

Thank you in advance for help.

regards

Florian

---

### Post by 255 on 2008-12-01
Hi again!

I don't know why or how, but my US-122L suddenly works with my 'regular' kernel and without removing the ehci module. Since I am not that experienced with linux I can't get no reason why it is working now. The US122L is recognized without any error messages during the boot-up process. Maybe the 2.6.27-7-generic kernel is already patched somehow? 

Here is what I did so far:
- I tried to recompile kernel 2.6.25 and alsa as described in this thread before, but failed.
- Then I used the alsa update script (1.0.18), a rt kernel, added rt-permisions as described in the wiki and by removing the ehci it worked.
- Now it works fine with alsa-1.0.18 and kernel 2.6.27-7-generic on intrepid.

Maybe this could help someone, I think the key is to update (and compile) alsa and add the rt permissions. After using the right .asoundrc and set jack to use usb_stream it could work.

So long,
Flo

---

### Post by albyblueska on 2008-12-04
Hi 255.
I followed your method fot the us 122 L and it works fine but in jackd i have some errors with alsa-lib.

Have you succesfully run us-122L on jackd?

> and set jack to use usb_stream it could work.
How?


Thanks...

---

### Post by 255 on 2008-12-04
> **albyblueska said:**
> Hi 255.
How?

Thanks...

Hi albyblueska!

I found out my soundcard number via
```
cat /proc/asound/cards
 0 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 003/002)
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
```
in my case "0" and put it into the .aoundrc:
```
pcm.!usb_stream {
        @args [ CARD ]
        @args.CARD {
                type string
                default "0"
        }

        type usb_stream

        card $CARD
}
```
as you can see in [fredericobriatas wiki]("http://wiki.briata.org/lib/exe/fetch.php?w=&h=&cache=cache&media=ok.png") the interface field has to be set to "usb_stream:0".
"0" in my case since it is card #0. Also try playing around with the other variables marked with a red dot. My US only takes a Frames/Period value as low as 128 maximum.
I hope this can help you.

Best regards.

---

### Post by albyblueska on 2008-12-05
Thanks for your reply.
Then,
```

alberto@alberto-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xc8000000 irq 10
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/003)

```

```
alberto@alberto-laptop:~$ cat .asoundrc
# The usb_stream plugin configuration

pcm.!usb_stream {
	@args [ CARD ]
	@args.CARD {
		type string
		default "1"
	}

	type usb_stream

	card $CARD
}

```

and my output with the command
 jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2
is:

```
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
Couldn't configure usb_stream
: Invalid argument
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns

```

any ideas?
Test with aplay, arecord ([http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)) works fine.
The problem is only with jack.

Which version of jackd do you have?

Thanks..

---

### Post by 255 on 2008-12-05
I get the exact same error if I try a lower Frames/Period setting. Try -p128 or -p256 instead.

---

### Post by albyblueska on 2008-12-08
Yeah...:guitar:

Now it works...(with a period of 128)
Thanks so much 255.

---

### Post by alternasid on 2009-01-04
hello to everyone, sorry for my English.
I recently bought a Tascam us-122l, I followed the guide various proposals but I can not make it work! Using intrepid with kernel 2.6.27-11-generic, can someone help me? :( :( :(
thank you very much
daniele

---

### Post by momo54 on 2009-01-07
Hi,

1/ I upgraded  my ubuntu intrepid ibex 8.10 to to 9.04 (jaunty jackalope) with a:
```
$ sudo update-manager -d
```

2/ i removed the ehci_hcd module with a:
```
$ sudo rmmode ehci_hcd
```

3/ i plugged in my us-122l and i  have :
```

momo54@lila:~$ cat /proc/asound/cards 
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at irq 5
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/002)
momo54@lila:~$ 

```

4/ :D

---

### Post by luispa on 2009-01-07
Hi,

This is a very interesting post. It seems to be far easy to make the 122L works with kernel 2.6.27 and ALSA 1.0.18a, that's not my situation. This is what I did:
- Upgrade to kernel 2.6.27 (Image and Headers). Created a symlink called linux pointing to the newest linux headers.
- Ran the AlsaUpgrade-1.0.x-rev-1.15.sh script choosing the last snapshot
- Edited .asoundrc:
pcm.!usb_stream {
	@args [ CARD ]
 	@args.CARD {
  		type string
  		default "1"
  	}
  
  	type usb_stream
  
  	card $CARD
}
- Restart my computer.

This is what happened:
- During the booting process I received these messages:
	usb 6-2: device descriptor read/64, error -110
	usb 6-2: device descriptor read/64, error -110
	usb 6-2: device not accepting address 5, error -110
	hub 6-0: 1.0: unable to enumerate usb device on port 2
	usb 1-2: device descriptor read/64, error -110
	usb 1-2: device descriptor read/64, error -110
	usb 1-2: device descriptor read/64, error -110
	usb 1-2: device descriptor read/64, error -110
	usb 1-2: device not accepting address 5, error -110
	hub 1-0: 1.0: unable to enumerate usb device on port 2

- cat /proc/asound/cards gave me this output:
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe020000 irq 16

If I unplug the USB cable and plug it again the situation goes a bit better:
cat /proc/asound/cards
 0 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 006/006)
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe020000 irq 16
asoundconf list
Names of available sound cards:
US122L
SB

However, the 122L is not available for aplay or arecord:
aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 1: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: SB [HDA ATI SB], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

arecord -l
**** Lista de CAPTURE Dispositivos Hardware ****
tarjeta 1: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: SB [HDA ATI SB], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: SB [HDA ATI SB], dispositivo 2: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

It seems the Tascam 122L is the first ALSA audio device, so I tried to play a song file with a different software:
ecasound -o:alsa,hw:0 -i:/US122-24bit-48k.wav 
********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'rt' buffering mode selected.
(eca-chainsetup) Audio object "/US122-24bit-48k.wav", mode 
... "read".
(audio-io) Format: s24_le, channels 2, srate 48000, interleaved.
ERROR: Connecting chainsetup failed: "Enabling chainsetup: AUDIOIO-ALSA: Unable to 
... open ALSA-device for playback; error: No such file or directory"

And to record a soundfile:
ecasound -i:alsa,hw:0 -o:test.wav
********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'rt' buffering mode selected.
ERROR: Connecting chainsetup failed: "Enabling chainsetup: AUDIOIO-ALSA: Unable to 
... open ALSA--device for capture; error: No such file or directory"

If I start jackd:
sudo jackd -RP50 -dalsa -dusb_stream:0 -r48000 -p128 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... usb_stream:0|usb_stream:0|128|2|48000|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:0
control open "usb_stream:0" (No such file or directory)
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
...

And then try to play an audio file using jack:
sudo ecasound -i:/US122-24bit-48k.wav -o:jack
********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
Enhanced3DNow! detected
SSE2 detected
(eca-chainsetup) 'rt' buffering mode selected.
(eca-chainsetup) Audio object "/US122-24bit-48k.wav", mode 
... "read".
(audio-io) Format: s24_le, channels 2, srate 48000, interleaved.
Enhanced3DNow! detected
SSE2 detected
(eca-chainsetup) Audio object "jack", mode "write".
(audio-io) Format: f32_le, channels 2, srate 48000, noninterleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
(eca-engine) Using realtime-scheduling (SCHED_FIFO:50).

Everything seems to work OK but there's no sound.

The same happens if I try to record a clip with a mic plugged in the 122L:
sudo ecasound -o:/test.wav -i:jack
********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
Enhanced3DNow! detected
SSE2 detected
(eca-chainsetup) 'rt' buffering mode selected.
Enhanced3DNow! detected
SSE2 detected
(eca-chainsetup) Audio object "jack", mode "read".
(audio-io) Format: f32_le, channels 2, srate 48000, noninterleaved.
(eca-chainsetup) Audio object "/test.wav", mode "read/write".
(audio-io) Format: s16_le, channels 2, srate 48000, interleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
(eca-engine) Using realtime-scheduling (SCHED_FIFO:50).
(eca-engine) Using realtime-scheduling (SCHED_FIFO:50).
(eca-engine) Using realtime-scheduling (SCHED_FIFO:50).
^C- [ Controller/Processing stopped (cond) ] -------------------------------------
- [ Engine exiting ] -----------------------------------------------------------
(eca-control-objects) Disconnecting chainsetup: "command-line-setup".
(audioio_jack_manager) Connection closed!
- [ Chainsetup disconnected ] --------------------------------------------------

The resulting test.wav is a muted file.

If I try to start jack with qjackctl I get this message:
sudo qjackctl

ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
19:31:04.435 JACK was stopped successfully.
19:31:04.436 Post-shutdown script...
19:31:04.437 killall jackd
jackd: ningÃºn proceso eliminado
19:31:04.858 Post-shutdown script terminated with exit status=256.
19:31:06.512 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I don't know how to solve it, probably a very simple thing I'm missing. I'll really appreciate any ideas.

Thank you very much in advance.

Luis Pablo

---

### Post by luispa on 2009-01-07
My mistakes:

> **luispa said:**
> And then try to play an audio file using jack:
sudo ecasound -i:/US122-24bit-48k.wav -o:jack

It should be:
sudo ecasound -i:/US122-24bit-48k.wav -o:jack_alsa

> **luispa said:**
> The same happens if I try to record a clip with a mic plugged in the 122L:
sudo ecasound -o:/test.wav -i:jack

It should be:
sudo ecasound -o:/test.wav -i:jack_alsa

Now, it works as expected using jack. The main remaining issue is I need to plug the 122L after boot the computer, not before. 

Is there anybody using the 122L as an ALSA pcm device?

Thank you in advance.

---

### Post by floatingpoint on 2009-01-13
This thread could really use a solution. The Tascam US-122L is quite a popular piece of hardware.

I followed the instructions given at [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux]("http://wiki.briata.org/doku.php?id=testing_us122l_under_linux") as advised above. 

When I got to "Packing & Installing, in 'Debian Way'", I followed the instruction:
```
 make-kpkg --append-to-version -us122l --initrd kernel_image modules_image
```

This took aaaages, but I think it worked correctly.

However, the next instruction:
```
cd /usr/src
 ls | grep bri
   gspca-modules-2.6.25-us122l_01.00.20-1+1.bri_amd64.deb
   linux-image-2.6.25-us122l_1.bri_amd64.deb
   madwifi-modules-2.6.25-us122l_0.9.4~rc2-1+1.bri_amd64.deb
   virtualbox-ose-modules-2.6.25-us122l_1.5.4-dfsg-4+1.bri_amd64.deb
 dpkg -i linux-image-2.6.25-us122l_1.bri_*.deb
 dpkg -i *-modules-2.6.25-us122l_*1.bri_*.deb
```

I assume that means "ls | grep bri" followed by each of the .debs, one by one?
Anyway, when I try that, this happens:
```
kevin@kevin-desktop:/usr/src$ ls | grep bri gspca-modules-2.6.25-us122l_01.00.20-1+1.bri_amd64.deb
grep: gspca-modules-2.6.25-us122l_01.00.20-1+1.bri_amd64.deb: No such file or directory

```

If i do "ls" none of these files are present (in /usr/src/)

Any ideas? Federico?

---

### Post by federicobriata on 2009-01-18
Hi!

As probably you know linux 2.6.28 and alsa 1.0.18 there is support Tascam US-122L, that means Ubuntu Jaunty support our card. 

The following method is valid for Ubuntu Intrepid, and alternative would be upgrade to Ubuntu Jaunty.

Thanks to Philippe ([http://pagesperso-orange.fr/La-page-Web-of-Phil/](http://pagesperso-orange.fr/La-page-Web-of-Phil/)), I could patched and recompile binary for using us-122l on intrepid with linux_2.6.27 and alsa_1.0.17.

ehci-hcd + snd-usb-us122l -> [http://pub.briata.org/us-122l/intrepid-2.6.27/linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb](http://pub.briata.org/us-122l/intrepid-2.6.27/linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb)

usb_stream-plugin -> [http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb](http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb)

~/.asoundrc -> [http://pub.briata.org/us-122l/src/us122l-patches_2.6.25/.asoundrc](http://pub.briata.org/us-122l/src/us122l-patches_2.6.25/.asoundrc)

Source patch -> [http://pub.briata.org/us-122l/intrepid-2.6.27/src/](http://pub.briata.org/us-122l/intrepid-2.6.27/src/)

Please verify with md5sum before install them:

$ md5sum libasound2-plugins_1.0.17-0ubuntu5_i386.deb -> 1e3cf4b7ba62b22f82f7a36cdcf20e94

$ md5sum linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb -> 3bb22bb6b6ecd15196f9327fddd121dc

step1 and step2 on [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) are not necessary with files gives above.

Than see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa) for use with PCM

and/or see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime) for use with jackd.

For any problem see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting)
or mailme.

grazie,
federico

---

### Post by Earl_Maroon on 2009-01-21
Thanks for that, federico, but I'm still having trouble.
My us122l is detected, but when I try to test it using the sample commands you give in your walkthrough I get an error saying no such directory. Also, the kernel doesn't seem to support my wireless card, but maybe that's specific to my laptop.
In any case, I'm closer than before to being able to use my hardware. So thanks again.

Also, thanks to everyone else who has been contributing to this thread.

---

### Post by sebbouckaert on 2009-01-25
First of all, thanks to all who contributed their hard work here!

I followed Federico's guide and everything went well up to playing a test wav after the configuring of ALSA. Card shows up, wav is being played: yes!!

But now i'm (kinda noobishly) wondering how to make the Tascam the default audio card in my setup. I mean so that all ALSA audio apps use the Tascam (banshee etc...)

I tried running asoundconf to set default but got kinda lost there ```
asoundconfig set default card PARAMETER
``` 

but what parameter? also running asoundconf-gtk gives following error:

```
You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~./asoundrc.asoundconf and must be indluded in ~/.asoundrc. Open this file to make sure it is!
```

I don't understand this really...I have both ./asoundrc and ./asoundrc.asoundconf in my home dir

So how do I make the the tascam default card under GNOME?

Thanks.

(Asus eee 900 PC - Ubuntu Intrepid)

---

### Post by Chromos on 2009-01-25
first check:
cat /proc/asound/cards

You should get something like this:
```

 0 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 005/004)
 1 [CMI8738        ]: CMI8738-MC6 - C-Media CMI8738
                      C-Media CMI8738 (model 55) at 0xe800, irq 16

```
Then you have to change the default number in .asoundrc Here it should be "0"
.asoundrc
```

# The usb_stream plugin configuration

pcm.!usb_stream {
	@args [ CARD ]
	@args.CARD {
		type string
		default "0"
	}

	type usb_stream

	card $CARD
}

```
Thats the way I get it. The problem I have is everytime Im rebooting the numbers are changing.
Ive alsa1.0.19 and kernel 2.6.27-9-generic. Dont know why.

---

### Post by sebbouckaert on 2009-01-25
I've now managed to install JACK and I am able to use audio apps such as Mixxx and Audacity with the Tascam US-122L. So for me issue is solved. Thanks again.

---

### Post by chilisenzacarne on 2009-02-11
> **federicobriata said:**
> Hi!

As probably you know linux 2.6.28 and alsa 1.0.18 there is support Tascam US-122L, that means Ubuntu Jaunty support our card. 

The following method is valid for Ubuntu Intrepid, and alternative would be upgrade to Ubuntu Jaunty.

Thanks to Philippe ([http://pagesperso-orange.fr/La-page-Web-of-Phil/](http://pagesperso-orange.fr/La-page-Web-of-Phil/)), I could patched and recompile binary for using us-122l on intrepid with linux_2.6.27 and alsa_1.0.17.

ehci-hcd + snd-usb-us122l -> [http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb](http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb)

usb_stream-plugin -> [http://pub.briata.org/us-122l/intrepid-2.6.27/linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb](http://pub.briata.org/us-122l/intrepid-2.6.27/linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb)

~/.asoundrc -> [http://pub.briata.org/us-122l/src/us122l-patches_2.6.25/.asoundrc](http://pub.briata.org/us-122l/src/us122l-patches_2.6.25/.asoundrc)

Source patch -> [http://pub.briata.org/us-122l/intrepid-2.6.27/src/](http://pub.briata.org/us-122l/intrepid-2.6.27/src/)

Please verify with md5sum before install them:

$ md5sum libasound2-plugins_1.0.17-0ubuntu5_i386.deb -> 1e3cf4b7ba62b22f82f7a36cdcf20e94

$ md5sum linux-image-2.6.27.2-us122l_2.6.27.2-us122l-10.00.Custom_i386.deb -> 3bb22bb6b6ecd15196f9327fddd121dc

step1 and step2 on [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux) are not necessary with files gives above.

Than see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa) for use with PCM

and/or see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime) for use with jackd.

For any problem see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#troubleshooting)
or mailme.

grazie,
federico

Hi Federico,

thanks from my side too, but I still have problems getting it to work. I did it on Ubuntu 8.10 with the deb-files on your Howto and followed step by step. I use no RT Kernel, as I read it doesn work now with 8.10.
The US122-L is well recognized as card O after reboot, but neither alsa / pulse / nor Jack are working with it. Actually in Pulse device chooser it is not listed. In Jack it is. When I use the first loop test command given in your Howto, I get:

peer@peer-desktop:~$ ARGS="-MDusb_stream:1 -fS24_3LE -r44100 -c2 --period-size=640" ; arecord $ARGS | aplay $ARGS
ALSA lib pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_usb_stream.so
aplay: main:583: Fehler beim Öffnen des Audiogerätes: No such file or directory
ALSA lib pcm.c:2156:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_usb_stream.so
arecord: main:583: Fehler beim Öffnen des Audiogerätes: No such file or directory

No sound at all. Jack shows the US122-L and  I tried all different latencys but it always closes immediately saying:

loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|2048|12|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
16:30:26.871 JACK was stopped successfully.
16:30:26.871 Post-shutdown script...
16:30:26.872 killall jackd
jackd: Kein Prozess beendet
16:30:27.280 Post-shutdown script terminated with exit status=256.
16:30:28.969 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Any ideas what I can try? Is the Jaunty stable enough to be used for recording, if there the card is supported natively?

Thanks for your support

chilli(senzacarne) :-)

---

### Post by federicobriata on 2009-02-11
Earl_Maroon & chilisenzacarne

Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_usb_stream.so

it means that you din't install my version libasound2-plugins or maybe, more probable, you let ubuntu to updates to the official version of that package which not include libasound_module_pcm_usb_stream.so, I think just reinstall back will resolve the problem.

usb_stream-plugin -> [http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb](http://pub.briata.org/us-122l/intrepid-2.6.27/libasound2-plugins_1.0.17-0ubuntu5_i386.deb)


Earl_Maroon

<OT>

about your wireless, yes the problem is the new kernel, because the drive which control your card is an external 3rd part module.
For example I've atheros wifi, I resolved by installing
madwifi-source than with

 sudo make-kpkg --append-to-version -us122l --initrd kernel_image modules_image

this command moreover create a new linux-kernel with tascam driver it creates also the packages with madwifi modules.

The same example is valid for every external modules, as wifi, video, webcam or any other.

</OT>

---

### Post by chilisenzacarne on 2009-02-11
Thanks for the fast reply Federico. You were right I applied the update which shows up immediately after installing your patch. Followed your instruction now and reinstalled your patch, did restart, but still not working. Doesn't show up in pulseaudio device chooser as option, but has green light and is listed as second soundcard; jackd closes as before. Only the first of the two testlines shows some activity now but no sound at all.
(ARGS="-MDusb_stream:1 -fS24_3LE -r44100 -c2 --period-size=640" ; arecord $ARGS | aplay $ARGS )
In audacity shows something like usb-stream to be chosen for record and playback. Once I choose this, audacity crashes. Is this maybe because I followed these instructions before to fix the other sound-issues in 8.10:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)   ???
And again: would you recommend updating to Jaunty already, to have it running?
Thanks a bunch 
chili

---

### Post by federicobriata on 2009-02-12
I never testd the card with pulseaudio, try alsa instead.

With alsa i tested the card with mixxx and audacious.

if is working than you can try audacious also with jackd plugin.

thanks,
federico

---

### Post by chilisenzacarne on 2009-02-13
> **federicobriata said:**
> I never testd the card with pulseaudio, try alsa instead.

With alsa i tested the card with mixxx and audacious.

if is working than you can try audacious also with jackd plugin.

thanks,
federico

Hi Federico!

The others must be magicians ...:) I've tried it now three ways. I set up one new Intrepid with the regular updates and applied your patches. Soundcard US122_L is recognized, but does not show up in alsa nor in pulseaudio. I have a third soundcard (Behringer U-Control UCA202), which works out of the box. Plugged it in and plugged it out to see if there are any problems btween the two usb - same results whatever. Result: Only mixx works with US122-L. When I want to use audacity and try to switch to usb-stream, it crashes. When I try to use jackd, it keeps closing and can't find sounddevice, though it is listed. No sound at all.
The other way: I read, that the newest alsa shall support US122-L and updated alsa. Result: I guess your patch is missing, soundcard not recognized any more, but the general sound is better ...
Third way: I upgrade to Jaunty. Result: System freezes during startUp.
I have got so many things working in Ubuntu, but this one leaves me dumb and dull.:confused:
I understand you saying, I should quit pulse and use alsa instead. But how? As far as I see it is closely interwoven with Ubuntu and might cause problems to deinstall. In fact it is as for now causing more problems then solving any - and I don't see the use for it. The only reason I found is pulseaudio is said to be the system of the future. But for the presence its just rubbish in Ubuntu. It is like somebody from windows is working to dicredit Ubuntu. 
Shall I always do pulseaudio -kk to close it?
I really appreciate your support and would be happy, if you could give me any idea, what to try or change to make it working as standard soundcard in my system.
Will it be working in Jaunty out of the box? 
Thank you

Chili:confused:

---

### Post by chilisenzacarne on 2009-02-13
I give you the output of 

lspci
lsusb
cat /proc/asound/cards
cat /proc/asound/modules
aplay -l
arecord -l

Maybe this helps. As far as I understand the card is recognized but not working for playback or record.

~$ **lspci**
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller (rev 20)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 91)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 91)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 91)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 91)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 7650 GS (rev a1)
04:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
04:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
07:09.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
07:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

~$ **lsusb**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 011: ID 2304:020f Pinnacle Systems, Inc. [hex] PCTV 400e BDA Device
Bus 005 Device 009: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 005 Device 008: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 005 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 005 Device 006: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
**Bus 005 Device 003: ID 0644:800e TEAC Corp. **
Bus 005 Device 002: ID 0424:2602 Standard Microsystems Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08bb:2902 Texas Instruments Japan 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


:~$ **cat /proc/asound/cards**
[B] 0 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 005/003)[/B]
 1 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xdfafc000 irq 17
 2 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:10.3-1, full s


~$ **cat /proc/asound/modules**
 **0 snd_usb_us122l**
 1 snd_hda_intel
 2 snd_usb_audio


~$ **aplay -l**
**** Liste von PLAYBACK Geräten ****
Karte 1: VT82xx [HDA VIA VT82xx], Gerät 0: ALC888 Analog [ALC888 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: VT82xx [HDA VIA VT82xx], Gerät 1: ALC888 Digital [ALC888 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 2: default [USB Audio CODEC ], Gerät 0: USB Audio [USB Audio]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0


~$ **arecord -l**
**** Liste von CAPTURE Geräten ****
Karte 1: VT82xx [HDA VIA VT82xx], Gerät 0: ALC888 Analog [ALC888 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: VT82xx [HDA VIA VT82xx], Gerät 1: ALC888 Digital [ALC888 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: VT82xx [HDA VIA VT82xx], Gerät 2: ALC888 Analog [ALC888 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 2: default [USB Audio CODEC ], Gerät 0: USB Audio [USB Audio]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

---

### Post by federicobriata on 2009-02-14
> **chilisenzacarne said:**
> Hi Federico!

The others must be magicians ...:) I've tried it now three ways. I set up one new Intrepid with the regular updates and applied your patches. Soundcard US122_L is recognized, but does not show up in alsa nor in pulseaudio. I have a third soundcard (Behringer U-Control UCA202), which works out of the box. Plugged it in and plugged it out to see if there are any problems btween the two usb - same results whatever. Result: Only mixx works with US122-L. When I want to use audacity and try to switch to usb-stream, it crashes. When I try to use jackd, it keeps closing and can't find sounddevice, though it is listed. No sound at all.
The other way: I read, that the newest alsa shall support US122-L and updated alsa. Result: I guess your patch is missing, soundcard not recognized any more, but the general sound is better ...
Third way: I upgrade to Jaunty. Result: System freezes during startUp.
I have got so many things working in Ubuntu, but this one leaves me dumb and dull.:confused:



On Intrepid, if mixxx work and audacity not it mean that alsa PCM is working, so problem is not related with kernel or alsa but can be some problem with audacity which don't like usb_stream.
What about jackd? can you give me the output of
jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
and
sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2


I've updated too to Jaunty (because, as you said, new alsa kernel and alsalib add support to the card). I did't get any significant problem during upgrading, I can say only that I made it from shell with apt tools, instead graphical ubuntu method.

We know that an update is always a critical moment, and if you are not familiar with apt and resolving packages dependence is better for you to download iso from
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/)

tanks,
federico

---

### Post by chilisenzacarne on 2009-02-14
> **federicobriata said:**
> On Intrepid, if mixxx work and audacity not it mean that alsa PCM is working, so problem is not related with kernel or alsa but can be some problem with audacity which don't like usb_stream.
What about jackd? can you give me the output of
jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
and
sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2

We know that an update is always a critical moment, and if you are not familiar with apt and resolving packages dependence is better for you to download iso from
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/)

tanks,
federico

Hi Federico,

I tried both ways: first download and didn't get it running. After that I tried with upgrade from an existing Ubuntu 8.10. Same result same point of installation: Both did not work and freezed after 2o seconds. But I guess that's normal for a beta :-)
Just could not trry for now, if this works.

Here is the output:

~$ jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209608528, from thread -1209608528] (1: Operation not permitted)
cannot create engine

$ sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2
[sudo] password for peer: 
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:0|usb_stream:0|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:0
control open "usb_stream:0" (No such file or directory)
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns

:guitar: :popcorn: I have enough windows lying around, which I kicked from my systems, to help me for now with dualboot, but I was so proud getting it all working in Ubuntu and want to stay with it; for recording too. So bad I don't know anything about coding :lolflag:

A big thank you!

Chili

---

### Post by federicobriata on 2009-02-14
> **chilisenzacarne said:**
> Hi Federico,


Here is the output:

~$ jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1209608528, from thread -1209608528] (1: Operation not permitted)
cannot create engine



this is because maybe you still have to enable realtime for jack, see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime)

> 

$ sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2
[sudo] password for peer: 
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:0|usb_stream:0|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:0
control open "usb_stream:0" (No such file or directory)
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns

Chili

Anyway jack in realtime is not strict necessary.
If you got that error maybe Have you applied all the update again?
Try this

$ ls /usr/lib/alsa-lib | grep pcm_usb_stream
libasound_module_pcm_usb_stream.a
libasound_module_pcm_usb_stream.la
libasound_module_pcm_usb_stream.so

and if you don't get any files install back a patched libasound, and if you get those file try to reinstall the 2.6.27 kernel from my url.

Remember that there is difference between plug the card before boot and after login into ubuntu, the order of audio device will change

On my laptop, if I plug the card after login

 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l

than I've to start the card with

sudo jackd -dalsa -dusb_stream:1 -r44100 -p64 -n2

So if you use usb_stream:0 you have are probably pluging the card before boot, remember to use a valid .asoundrc

for the error about usb_stream (No such file or directory), don't care I've too and jackd work:)

about jaunty alpha-4 there is still a problem with ehci_hcd, I uploaded the necessary patch for solve this issue.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329437)
A workaround could be 
$ sudo rmmod ehci_hcd
than you can plug the card.

Please focus on Intrepid, remember that you have to boot with 2.6.27-us122l and use alsa v1.0.17, so if you move to v1.0.18 try to move back.

please let me know, you progress.
federico

---

### Post by chilisenzacarne on 2009-02-15
Well, first I found out that the usb cable which came with the new device is broken ... Changed it. Applied your hints regarding Realtime and now I can start jackd via Console; also with ardour, but no sound in or out. Ardour doesn't seem to recognize the device. The Tascam device itself works fine, takes mike-sound in and I am able to monitor it, but don't get ardour to work with it. Ardour and Jack seem to be fine together, too, but Tasacam is not listed. Also I can only start jackd with Root (sudo) and cannot change interface anymore. It's greyed out and permanent set to 1

> **federicobriata said:**
> this is because maybe you still have to enable realtime for jack, see
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_4_-_jackd_in_realtime)
federico

Did the enabling now. Get this when I start jackd. Looks good I guess:

~$ sudo jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback

> **federicobriata said:**
> 
$ ls /usr/lib/alsa-lib | grep pcm_usb_stream
libasound_module_pcm_usb_stream.a
libasound_module_pcm_usb_stream.la
libasound_module_pcm_usb_stream.so federico

works fine.

> **federicobriata said:**
> 
 cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l

than I've to start the card with

sudo jackd -dalsa -dusb_stream:1 -r44100 -p64 -n2 

So if you use usb_stream:0 you have are probably pluging the card before boot, remember to use a valid .asoundrc federico

I always have to check in asoundrc and to check in this command before starting jackd.

> **federicobriata said:**
>  please let me know, you progress.
federico

Some progress but not yet working. Get me some popcorn :-)

Thanks again

chili

---

### Post by federicobriata on 2009-02-16
> **chilisenzacarne said:**
> Well, first I found out that the usb cable which came with the new device is broken ... Changed it. Applied your hints regarding Realtime and now I can start jackd via Console; also with ardour, but no sound in or out. Ardour doesn't seem to recognize the device. The Tascam device itself works fine, takes mike-sound in and I am able to monitor it, but don't get ardour to work with it. Ardour and Jack seem to be fine together, too, but Tasacam is not listed. Also I can only start jackd with Root (sudo) and cannot change interface anymore. It's greyed out and permanent set to 1



Did the enabling now. Get this when I start jackd. Looks good I guess:

~$ sudo jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback



works fine.



I always have to check in asoundrc and to check in this command before starting jackd.



Some progress but not yet working. Get me some popcorn :-)

Thanks again

chili

yes look like you jack is working.

see my last test
[http://article.gmane.org/gmane.linux.usb.general/14820](http://article.gmane.org/gmane.linux.usb.general/14820)

I still have to test Ardour, but i think that with running jackd and you set ardour to use jack driver it should work.

ciao,
federico

---

### Post by chilisenzacarne on 2009-02-16
> **federicobriata said:**
> yes look like you jack is working.

see my last test
[http://article.gmane.org/gmane.linux.usb.general/14820](http://article.gmane.org/gmane.linux.usb.general/14820)

I still have to test Ardour, but i think that with running jackd and you set ardour to use jack driver it should work.

ciao,
federico


Finally got it! Thank you so much! Just have to check everytime .asoundrc for the correct default. Jackd starts with nearly no xruns, and ardour works perfectly. Just had to download the most recent ardour directly, because the one in the repository has a bug with opening existing files. Actually I am running three soundcards at the same time now without any problems: Behringer U-Control UCA202 for playback, Tascam US122-L for record and playback via Jackd and the built in soundcard, Realtek something I think. 
And I am not able to open Jack with qjacktl and cannot change the default there; it's greyed out, but worked a few days ago. Do you like any output from konsole to check?
Will send you a short soundfile to your private mail.

Happy chili :D

---

### Post by phobikore on 2009-03-17
it may be answered above bu i didnt understand quite well...

im running ubuntu studio intrepid 8.10 and i bought a tascam us-144.can you tell me the steps to make it talk??

desperate and exhausted..#-o

thnx

---

### Post by Conq321 on 2009-04-20
I've upgraded to juanty, "asoundconf list" lists the tascam 122L card, but i can not set it as default (asoundconf set-default-card US122L), the list stays in the same order (tascam second).

Neither can i see the card in the drop-down list of my alsamixer. Any ideas on this?

EDIT: this works!

aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 ~/test.wav
Playing WAVE '~/test.wav' : Signed 24 bit Little Endian in 3bytes, Rate 44100 Hz, Stereo

So i gues it's just a matter of getting it listed in the mixer? How do i fix that?

---

### Post by sebbouckaert on 2009-04-20
> **Conq321 said:**
> 
Neither can i see the card in the drop-down list of my alsamixer. Any ideas on this?


So i gues it's just a matter of getting it listed in the mixer? How do i fix that?

I dont' know if there is much use listing the card in alsamixer, certainly not for level controls as you are supposed to mix the card's in and outputs directly with the sliders on the interface itself.

For me the thing seems to work well through jack for now. Recording and playback with Audacity works fine. 

Alsa apps can be routed to the card by using jack for the gstreamer output, as described in this guide:

[http://ubuntuforums.org/archive/index.php/t-554457.html](http://ubuntuforums.org/archive/index.php/t-554457.html)

(changing the 'audiosink' key keys in the gconf-editor only was enough here to play mp3's with Banshee on the Tascam.)

Then you have more or less system wide use of your Tascam. But what I cant't get working is sound from Firefox plugins in Flash (youtube etc...)

So it is true that a better or more permanent solution for using the card system wide as a default would be more than welcome.

(fyi i'm on Jaunty too)

---

### Post by Conq321 on 2009-04-20
I've been trying to get it working through jackd, but i get the following error:
```
$ jackd -d alsa -dhw:1
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
```
I found some bug reports regarding this, saying to delete (I renamed them) ~/.asoundrc , but that didn't work out for me.
Starting my onboard card with jackd (hw:0) works fine.

Btw, what exactly is jackd for? Low latency, i get it. But it still goes it's way through alsa?

Edit: trying to start jack via qjackctl makes the program hang

---

### Post by sebbouckaert on 2009-04-20
> **Conq321 said:**
> 

Btw, what exactly is jackd for? Low latency, i get it. But it still goes it's way through alsa?

Edit: trying to start jack via qjackctl makes the program hang

Alsa rather goes through jack. Jack is a low latency audio server with lots of features. This site explains it better than I do: [http://jackaudio.org/](http://jackaudio.org/)

Concerning your error: check what number the card has in ~/.asoundrc

Preferably use the ~/.asoundrc file Federico Briata put in the files of his howto. Then change the number if you like but make sure the number corresponds to the number in Jack settings/preferences as seen here:

[http://wiki.briata.org/lib/exe/detail.php?id=testing_us122l_under_linux&cache=cache&media=ok.png](http://wiki.briata.org/lib/exe/detail.php?id=testing_us122l_under_linux&cache=cache&media=ok.png)

i.e. if your card is listed as "2" in ~/.asoundrc the value under "interface" should be "usb_stream:2"

---

### Post by Conq321 on 2009-04-20
Done all that, but again i get an error.```
$ cat /proc/asound/cards
 0 [M5455          ]: ICH - ALi M5455
                      ALi M5455 with ALC655 at irq 23
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/006)

$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_us122l

$ cat ~/.asoundrc
# The usb_stream plugin configuration

pcm.!usb_stream {
	@args [ CARD ]
	@args.CARD {
		type string
		default "1"
	}

	type usb_stream

	card $CARD
}

$ jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
Bus error

```

---

### Post by Chromos on 2009-06-09
> **federicobriata said:**
> 

about jaunty alpha-4 there is still a problem with ehci_hcd, I uploaded the necessary patch for solve this issue.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/329437)
A workaround could be 
$ sudo rmmod ehci_hcd
than you can plug the card.



when I try to rmmod i get this:
ERROR: Module ehci_hcd does not exist in /proc/modules

What can I do?

---

### Post by federicobriata on 2009-06-10
> **Chromos said:**
> when I try to rmmod i get this:
ERROR: Module ehci_hcd does not exist in /proc/modules

What can I do?

that rmmod was necessary till jaunty alpha-4, now should not be necessary because the jaunty kernel support the 122l natively.

what the output of
cat /proc/asound/modules ?

start to do from step_3
[http://wiki.briata.org/doku.php#step_3_-_set_alsa](http://wiki.briata.org/doku.php#step_3_-_set_alsa)

and copy and paste ALL output

federico

---

### Post by fergrorke on 2009-06-14
I'm running Juanty and 144 is shown in *lsusb* but not in *asoundconf list*. I understand that Jaunty has kernel support for the US-122L and that should also work for the US-144. So how do you get the system to recognise the 144 as a 122L? Or, more generically, how do I get Jaunty to work with the 144?

/ferg

---

### Post by claudioaudio on 2009-06-17
> **Earl_Maroon said:**
> I recently bought the Tascam US-122l (USB sound card, not yet supported in ALSA), thinking that it was the same as the US-122 (which is supported by ALSA). I have found a walkthrough that has been claimed to work for this and it involves compiling and installing a patched kernel. The thing is, the walkthrough is for Debian, and while I know that Ubuntu is based on Debian I'm not sure quite how compatible the walkthrough is. I assume it would be pretty fatal for my current install if I broke the kernel. There is one particular line which mentions *amd64.deb, but I use an x86. If someone could take a look at this and let me know if this is safe and if there is anything that needs to be changed for my purposes I'd be very grateful.
 
The walkthrough is at:
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)
 
Hello, Im new to Ubuntu. I havent even finished the download yet. I have a question though. I've owned the Tascam US-122 for years and have never been able to get it to record without glichtes and pops on Windows XP or Vista (no matter what buffer setting/bitrate was used) does it work flawlessly on the Ubuntu version you mentioned?

---

### Post by drfunkeys on 2009-08-06
Hi, I'm running AVLinux (Debian) with the 2.6.30.1 low latency kernel. It seems like the us-122l is supported, but I haven't got it working yet. I'm new to Linux, so it might be something simple I've overlooked. Here's the output:  # cat /proc/asound/modules   0 snd_usb_audio   1 snd_usb_us122l   2 snd_hda_intel   3 snd_hda_intel   4 snd_hda_intel     # cat /proc/asound/cards  0 [PCR            ]: USB-Audio - PCR                       EDIROL PCR at usb-0000:00:0b.0-8, full speed  1 [US122L         ]: USB US-122L - TASCAM US-122L                       TASCAM US-122L (644:800e if 0 at 001/004)  2 [NVidia         ]: HDA-Intel - HDA NVidia                       HDA NVidia at 0xcfff4000 irq 22  3 [HDMI           ]: HDA-Intel - HDA ATI HDMI                       HDA ATI HDMI at 0xcfdfc000 irq 16  4 [HDMI_1         ]: HDA-Intel - HDA ATI HDMI                       HDA ATI HDMI at 0xcfcfc000 irq 16   # gedit ~/.asoundrc # The usb_stream plugin configuration  pcm.!usb_stream {     @args [ CARD ]     @args.CARD {         type string         default &quot;1&quot;     }      type usb_stream      card $CARD }   # ARGS=&quot;-MDusb_stream:1 -fS24_3LE -r44100 -c2 --period-size=640&quot; : arecrd $ARGS | aplay $ARGS ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave aplay: main:608: audio open error: No such file or directory   # aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 test.wav ALSA lib pcm.c:2171:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_usb_stream.so aplay: main:608: audio open error: No such file or directory    Arhg, this be a fine seaworthy vessel......psssssssst.. Arhg, I don't know what I'm doing.  edit: whoa, the forum took away all my nice formatting.. sorry if the output stuff is hard to read because of it.

---

### Post by daggedog on 2009-09-05
drfunkenkeys. I have tried AV Linux and us-122l. It worked with jack, and I used Briata's instructions [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)  Remember to install alsa-plugins  (libasound2-plugins) in debian. And it is easier if you use the jack GUI qjackctl. 
The reason I tried AV Linux is that it is impossible to install nvidia drivers with realtime kernel in Ubuntu Studio, [B]2.6.31-1-rt. I really liked AV Linux, but hmm.. LXDE or XFCE,  a bit strange, even though less resources are used. (LXDE, too primitive for my taste. XFCE, not able to single click by default on XFCE desktop, can do so with nautilus, but then some of the advanges of XFCE goes away, so I have to switch between thunar and nautilus. I am a KDE fan, and I really want to single click on my desktop!)
[/B]

---

### Post by MigBc on 2009-09-22
Hi,

I just submitted a patch that makes US-144 work when ehci-hcd is disabled:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-September/021363.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-September/021363.html)

If you can't rmmod ehci-hcd, that is because it is build into the kernel. You then have to recompile the kernel with ehci-hcd as a module.

Regards,
Tobias

EDIT: [Installation instructions for US-144 on Ubuntu]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144")

---

### Post by 90Brougham350 on 2010-02-13
I'm glad I found this thread! I bought the US-144l a few weeks ago. I'm running a dual-boot with Vista because my wife needs it for work every now and then. I had absolutely no luck getting the unit to work with Windows, the version of Cubase LE4 that came with the interface would not register, and crashed every time I used it. I found Briata's page and tried to follow the instructions but I am a total noob with linux, and couldn't really follow them or do what they were telling me to do. I've been using Ubuntu for years pretty much as a music and internet machine, but really want to get the unit to work with Ardour. Are there some very simple step-by-step instructions that a guy like me could use? I'm running Ubuntu Studio 9.10. Thanks!

Brian

---

### Post by kurt. on 2010-02-20
hi
i followed different instructions i found on the web for installing the us-144 under ubuntu. (i just posted the following somewhere else on this forum but cannot find it anymore)

i downloaded the us-122l firmware with the synaptic-packet-manager, upgraded alsa with the script i found [here]("http://ubuntuforums.org/showthread.php?p=6589810") and did

```
kurt@kurt-laptop:~$ sudo modprobe snd-usb-audio
kurt@kurt-laptop:~$ echo -n 0000:00:1d.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind
```after that (loading the module and disabling usb 2) i plugged the interface out and in again and the us-144 was recognized as us-122l under usb 1...

```
kurt@kurt-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7ff8000 irq 31
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800f if 0 at 008/008)
kurt@kurt-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l
```the problem is, that somehow still the thing doesn't work. 
i created the right .asoundrc file, but jackd seems not to be able to handle the us-144:

```
kurt@kurt-laptop:~$ sudo jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
Couldn't configure usb_stream
: Invalid argument
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
```the test with aplay is not working either, but thats maybe a different problem:

```
kurt@kurt-laptop:~$ aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 ~/testing.wav
Warning: format is changed to S16_LE
Playing WAVE '/home/kurt/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:990: Sample format non available
Available formats:
- S24_3LE

```i see the tascam in qjackctl ---> connections only under alsa as

20:TASCAM US-122L
---> 0:TASCAM US-122L MIDI 1

but i can't connect it.

qjackctl 'messages' output:
```

 p, li { white-space: pre-wrap; }  15:29:46.230 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2
 15:29:46.233 JACK was started with PID=2622.
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:1
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 cannot load driver module alsa
 15:29:46.279 JACK was stopped successfully.
 15:29:46.279 Post-shutdown script...
 15:29:46.279 killall jackd
 15:29:46.432 ALSA connection change.
 jackd: no process found
 15:29:46.688 Post-shutdown script terminated with exit status=256.
 15:29:48.438 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```auszug aus dmesg:
```
[  249.795296] ehci_hcd 0000:00:1d.7: remove, state 1
[  249.795310] usb usb2: USB disconnect, address 1
[  249.795313] usb 2-5: USB disconnect, address 2
[  249.877131] ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
[  249.877217] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  250.160090] usb 8-1: new full speed USB device using uhci_hcd and address 6
[  250.311865] usb 8-1: not running at top speed; connect to a high speed hub
[  250.436934] usb 8-1: configuration #1 chosen from 1 choice
[  250.445887] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[  250.469945] input: CNF7129 as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input10
[  250.592542] usb 8-2: new full speed USB device using uhci_hcd and address 7
[  265.710082] usb 8-2: device descriptor read/64, error -110
[  273.560148] hub 8-0:1.0: unable to enumerate USB device on port 2
[  277.070116] usb 8-2: new full speed USB device using uhci_hcd and address 8
[  277.216426] usb 8-2: not running at top speed; connect to a high speed hub
[  277.243535] usb 8-2: configuration #1 chosen from 1 choice
[  278.730661] usbcore: registered new interface driver snd-usb-us122l
[ 2216.940044] CE: hpet increasing min_delta_ns to 15000 nsec
[ 3876.029937] usbcore: registered new interface driver snd-usb-audio

```thanks for help with the next steps or ideas.

---

### Post by Radoka on 2010-02-28
Got exactly the same problem as Kurt. The card is found but not usable... Anyone..?

---

### Post by Radoka on 2010-03-01
Nvm, I solved it and told how in this thread: [http://ubuntuforums.org/showthread.php?p=8899319#post8899319](http://ubuntuforums.org/showthread.php?p=8899319#post8899319)

---

