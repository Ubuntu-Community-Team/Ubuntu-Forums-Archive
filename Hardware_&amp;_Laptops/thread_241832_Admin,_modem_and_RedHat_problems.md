---
title: "Admin, modem and RedHat problems"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by CovekNaFrezi on 2006-08-22
Ok, didn't know how to exactlly put them all together.

Here is my first problem, which starts with a modem:
[This]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html") link tells me how to configure a modem (scroll down to "Modems"), but writing the text to indentify the chipset 

This one:
```
wget -c http://linmodems.techion.ac.il/packages/scanModem.gz
gunzip -c scanModem.gz > scanModem
chmod +x scanModem
sudo ./scanModem
gedit Modem/ModemData.txt
```

does nothing. Then I realised that it CAN'T do nothing since I don't have a connection yet. ](*,) 

Ok. I go to the Linmodems site and download "scanModem.gz" tool with my desktop computer running RedHat. I thought I would burn it and transfer it via CD onto my laptop. 

It wasn't like that though.

I burned a CD with Gnome Toaster (Multisesion btw) and tried to run it on my laptop but it wouldn't recognise. Its like CD doesn't even exist. 



The other problem concerns the admin and everything that has to do with root, or being God of your little Ubuntu universe. 

In Terminal, when I type in command **su** it asks me for password. I give it a password (correct one) but it says "Authentication Failure". Now I know that Red Hat has the same command if you want to access "root"...what am I doing wrong?


So, to summarise it. :D

Can't find modem on my laptop, which leads to burning "scanModem" tool to CDROM with GnomeToaster, which leads to "I can't find your CD" problem...and then there is that admin/root crap...

Help is much appreciated. 

PS,
USB 'could' work but RedHat doesn't recognize it for some reason (even though it makes a sound like it "found" it) so I can't transfer from RH to Ubu.

[COLOR="Red"]**EDIT:** Problem about burning and reading CDs is solved. Looks like it was a bad burn. The rest exist.[/COLOR]

---

### Post by mariner09 on 2006-08-23
Your best sanity will be achieved if you just remember to use sudo in front of every command you want to run with root priveleges.  Ubuntu is not the same as Red Hat in regards to switching to root, however, I think you can make it function that way.  I prefer the way Ubuntu does things.

ScanModem should detect your modem whether it's turned on or off.

When I try your wget string it tells me it can't resolve the name, so I probably can't be of much more help.

Fire up the Ubuntu Device DB and see if it shows there.

---

### Post by CovekNaFrezi on 2006-08-23
I fired up Device DB (Device Manager?) and it DOES show there as M5457 AC'97 Modem Controller by ALi Corporation. Bus Type is PCI. Device Type and Capabilities are UNKNOWN. OEM Vendor is Sony Corporation.

---

### Post by CovekNaFrezi on 2006-08-23
Here is the text file that scanModem produced:

```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06.1 LTS  kernel 2.6.15-26-386 
 This will alert cogent experts, and  distinguish cases in the Archives 
 YourCounry is not essential, but will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_August_22

	Checking for ALSA (Advanced Linux Sound Architecture) 
compatible modem cards with:  aplay -l | grep -i modem
---------------------------



Checking /proc/asound/  folders for modem support.
	/proc/asound/pcm
-------------------------
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1

               The node for modem setup is:    modem:


=======================================================
 For candidate modem in PCI bus 0000:00:03.0, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 10b9:5457 104d:8158 Ubuntu 2.6.15-26-386 4.0.3 none i686 
 ------------------------------
 Chipset or support type: Smart

 With modem hardware:
   Modem: ALi Corporation M5457 AC'97 Modem Controller
   with Primary PCI_id  10b9:5457
    and a SubSystem_id  104d:8158
   using interrupt (IRQ) 11 , with sharing reported from /proc/interrupts:
         1:       1111          XT-PIC  i8042
 11:       1969          XT-PIC  uhci_hcd:usb1, yenta, ALI 5451, sonypi

There is DISagreement of diagnostics and hardware prediction.
Pausing for 10 seconds.
----------------------
There was a failure to acquire mc97 codec information, suggesting either
a Conexant modem chip, not supported by the ALSA modem driver snd-intel8x0m,
of that snd-intel8x0m may require reloading. Please with Root permission do:
	sudo modprobe -r snd-intel8x0m 
	sudo modprobe snd-intel8x0m  
Then rerun
	./scanModem
If displayed, Ignore his message on the next run.

 Lacking a dsp (digital signal processing) chip, the modem is a software intensive
 or "softmodem" type. Its primary controller manages the traffic with the CPU. But
 the software needed is specified in the Subsystem, not in the primary host controller.

 Information acquired by the scanModem analysis is:

 implying that the modem hardware:
 	Modem: ALi Corporation M5457 AC'97 Modem Controller
 with Subsystem 104d:8158 needs support type: SMART 
  Rather than an ALSA driver, the ALI5457 card requires the Smartlink driver:  slamr

 For more common kernels, some compiled SmartLink drivers are available. 
 The modem should setup with:
    sudo modprobe ungrab-winmodem
    sudo modprobe slamr
    sudo  slmodemd -c YOUR_COUNTRY /dev/slamr0
 Read Smartlink.txt for and Testing.txt  for details.


=======================================================
 For candidate modem in PCI bus 0000:00:04.0, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 10b9:5451 104d:8158 Ubuntu 2.6.15-26-386 4.0.3 none i686 
 ------------------------------
 Chipset or support type: Smart

 With modem hardware:
   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
   with Primary PCI_id  10b9:5451
    and a SubSystem_id  104d:8158
   using interrupt (IRQ) 11 , with sharing reported from /proc/interrupts:
         1:       1111          XT-PIC  i8042
 11:       1969          XT-PIC  uhci_hcd:usb1, yenta, ALI 5451, sonypi

There is DISagreement of diagnostics and hardware prediction.
Pausing for 10 seconds.
----------------------
There was a failure to acquire mc97 codec information, suggesting either
a Conexant modem chip, not supported by the ALSA modem driver snd-ali5451,
of that snd-ali5451 may require reloading. Please with Root permission do:
	sudo modprobe -r snd-ali5451 
	sudo modprobe snd-ali5451  
Then rerun
	./scanModem
If displayed, Ignore his message on the next run.

 The candidate ALSA modem driver on your System is:  snd-ali5451
 Lacking a dsp (digital signal processing) chip, the modem is a software intensive
 or "softmodem" type. Its primary controller manages the traffic with the CPU. But
 the software needed is specified in the Subsystem, not in the primary host controller.

 Information acquired by the scanModem analysis is:

 implying that the modem hardware:
 	Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device 
 with Subsystem 104d:8158 needs support type: Smart 
 

 Driver snd-ali5451 has modem in addition to audio support, for non-Conexant modems.
 An ALSA (Advanced Linux Sound Architecture} modem driver snd-ali5451 
  provides ONLY a low level access to the hardware. The complementing HIGH 
 level support for ALSA  modem drivers is through a Smartlink utility:  slmodemd
 Download from http://linmodems.technion.ac.il/packages/smartlink/ the SLMODEMD.gcc4.tar.gz 
 Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.tar.gz
 and read instructions therein. But briefly, the modem should setup with command:
 >>>	sudo slmodemd -c YOUR_COUNTRY --alsa -s hw:0,1     <<<

 A dialer utility such as wvdial (perferable) is still needed for dialout.
 slmodemd MUST be kept running throughout a dialout session.
 Read Modem/YourModem.txt and Modem/SmartLink.txt for furthere details.

 Already added to the kernel is snd-ali5451 and audio drivers it depends on, displayed by:
	lsmod | grep snd_ali5451
Module                  Size  Used by
-------------------------------------
snd_ali5451            24460  1 
snd_ac97_codec         93088  2 snd_intel8x0m,snd_ali5451
snd_pcm                89864  4 snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    55268  9 snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
-------------------------------------
 Note that mere loading does NOT establish that snd-ali5451 is the correct driver, rather
 than hsfmodem drivers.  But snd-ali5451 may still support readout of Subsystem information.

====== Writing residual advice ========
 The Major.Minor versions differ for the 
	the compiler used in kernel assembly:  4.0
	and the designated compiler:           none
 But there must be a match on the target for driver installation, 
 of gcc Major.Minor versions or kernel and drivers!!
 Otherwise the drivers will fail to load with warning:
	Invalid module format!!"
	See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 

If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-26-386 must be downloaded.  
Go to http://packages.ubuntu.com/  and search for linux-headers-2.6.15-26-386 
After downloading, it can be installed with:
$ sudo dpkg -i linux-header*.deb

Or alternatively if online through Ethernet do:
$ sudo apt-get update
$ sudo apt-get install build-essential
will do all the necessary installations mentioned above.

In either installation case, set a symbolic link which will be expected later:
$ sudo ln -s /usr/bin/gcc-4.0  /usr/bin/gcc
After check with:
$ ls -l /usr/bin/gcc*
which should display:
lrwxrwxrwx 1 root root    16 2006-07-09 21:53 /usr/bin/gcc -> /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 93584 2006-04-20 18:22 /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 16245 2006-04-20 18:13 /usr/bin/gccbug-4.0

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	make linux-headers-


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 08:00 /usr/sbin/pppd
To enable dialout without Root permission do:
	$ su - root
        # chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	$ SUDO chmod a+x /usr/sbin/pppd
Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```

---

### Post by CovekNaFrezi on 2006-08-23
nobody?

---

