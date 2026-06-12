---
title: "Newbie Modem Installation Woes"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by Bunkai on 2006-05-08
Been trying to install modem for-f---ing-ever. Different instructions everywhere I look and none (I repeat, NONE) that match up to the facts on the ground.

My latest attempt: I go to the Ubuntu wiki and find a page called [DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29") and find the following instructions:> You need sl-modem-daemon. 

...[snipped for brevity and to show pertainent text]...

If you cannot go online with your Ubuntu, search for the package using  [http://packages.ubuntu.com/](http://packages.ubuntu.com/) in another network-enabled computer, download and transfer the package for your version of Ubuntu to your Desktop. After making sure you do not have any other .deb files in your Desktop, open a terminal (alt+f2, type gnome-desktop -Ubuntu- or konsole -Kubuntu, hit enter), and type/copy-paste the following commands: 

[QUOTE]cd ~/Desktop
sudo dpkg -i *.deb[/QUOTE]
So I go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and do you think I find a deb package there for the  sl-modem-daemon? No. There's a tar.gz and a diff.gz. So the instruction given are as good as the south-bound output of a north bound horse.

I'm simply frustrated trying to get the modem working so that I can have more than a $1600 paperweight. Linmodem discussion instructions on the scan report have resulted in no help from anybody (not even so much as a "We got your message and are looking for an answer for you.")

I'm sorry about the tone of this post.](*,)  Please, any help appreciated. 

Thanks.
Bunkai

---

### Post by Bunkai on 2006-05-08
Oh, yea. In case it would help, here's the Linmodems scanner report:

> 

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 6.06 "Dapper Drake" Development Branch  kernel 2.6.15-21-686  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_April_26
------------ --------------  System information ------------------------
 Ubuntu 6.06 "Dapper Drake" Development Branch 
 on System with processor: i686
 currently under kernel:   2.6.15-21-686

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-04-19 05:48 /dev/ppp
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Reading /proc/asound/pcm 
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1
 The potentially supporting drivers now loaded on this System are:
0 snd_ali5451


 The kernel was assembled with compiler:  4.0.3
 with current System compiler GCC=4.0.3
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:06.0
0000:00:08.0
    
Providing detail for device at  0000:00:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0401: 10b9:5451   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
  SubSystem 103c:002a  Hewlett-Packard Company: Unknown device 002a
	Flags: bus master, medium devsel, latency 64, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  ALI 5451
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5451 103c:002a debian_version 2.6.15-21-686  4.0.3 4.0.3    i686
The audio card 10b9:5451 may carry a soft modem chip.
The audio/modem driver is not competent to write soft modem information to /proc/asound/pcm 
 For snd-ali5451.ko compiling instructions, see [http://phep2.technion.ac.il/linmodems/archive/msg04955.html](http://phep2.technion.ac.il/linmodems/archive/msg04955.html).
[COLOR="Purple"]Modem support within the snd-ali5451 driver is included in some 2.6.12 and later kernels
The following two Root commands should set up the modem.
	sudo modprobe snd-ali5451
	sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
Get the SLMODEMD.gcc4.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)[/COLOR]
       
 The controller: 10b9:5451  ALI 5451 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	AgereSystems
	Conexant
	Smartlink

 Archive records show that 103c:???? Subsystems from HP with the exception of  103c:006b and 103c:3081
 have a Conexant chip.  Thus first test hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers)
 Should that support fail, the alternate route is described in Modem/Slmodem-ALSA.txt
 
Checking for autoloaded ALSA modem drivers
snd_ali5451            26828  1 
snd_ac97_codec         99808  1 snd_ali5451
snd_pcm                96644  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    60004  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

  Driver snd-ali5451  may enable codec acquisition 
  === Begin mc97 codec query  ===
	   
 Files under /proc/asound/ do not include  modem codec information. 
 If more decisive information is not given below,
 this is a tentative signature of a Conexant hsfmodem.  Download a hsfmodem package from
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) or your installation CDs.  For SuSE/Novell, install both
 km_hsfmodem and hsfmodem packages,  for drivers and configuration tools respectively.
 
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 
 AgereSoftModem drivers only support AC97 or MC97 modem controllers with codecs charcterized by one of:
   SIL_id = 39 
   mc97 codec is SIL27 
   0x27 , as output by modem diagnostics under Microsoft Windows
 If uncertain, identity the softmodem codec through tests described in Modem/SoftModem.txt
 Support is currently ONLY for 2.4.n kernels and the following modem controllers:
   8086:(2416 2426 2446 7196 2486 24C6)  , with 8086 == Intel
   1039:7013  SIS
   1106:3068  VIA
 Access the soft modem software through code sponsor IBM at:
   [http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698](http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698)
 The SmartLink slmodem-2.9.9 may serve for modems not served by this AgereSystems software.
 
 If may be necessary to add -DMODVERSIONS to the compile flags, 
 depending on whether your kernel was thus compiled. See
 [http://linmodems.technion.ac.il/archive-fourth/msg01408.html](http://linmodems.technion.ac.il/archive-fourth/msg01408.html)


 Under the controller 10b9:5451  ALI 5451 ,
 with modem subSystem 103c:002a     
 Alternative supporting packages are the SmartLink slmodem-2.9.n using its proprietary slamr driver, 
 or dependent on  10b9:5451  ALI 5451 , an  Open Source driver from the  ALSA package.
 See Modem/Slmodem-ALSA.txt for details.
 A sample compilation is shown in: [http://linmodems.technion.ac.il/archive-fifth/msg02567.html](http://linmodems.technion.ac.il/archive-fifth/msg02567.html)
  
 For SuSE 9.2 users, there is an update  for driver slamr.ko loading during bootup. 
 To find it easily, search for "slamr" within  [http://www.novell.com/linux/download/updates/92_i386.html](http://www.novell.com/linux/download/updates/92_i386.html)
     

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc4 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 

    
Providing detail for device at  0000:00:08.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:5457   Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
  SubSystem 103c:002a  Hewlett-Packard Company: Unknown device 002a
	Flags: medium devsel, IRQ 10
 Checking for IRQ 10 sharing with modem.
      XT-PIC  ohci_hcd:usb1, eth0, radeon@pci:0000:01:05.0

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5457 103c:002a debian_version 2.6.15-21-686  4.0.3 4.0.3    i686
The following two Root commands should set up the modem.
	sudo modprobe snd-intel8x0m
	sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
Get the SLMODEMD.gcc4.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
       
 The controller: 10b9:5457  ALI 5457 AC-Link 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	Conexant
	Intel
	Smartlink

 Archive records show that 103c:???? Subsystems from HP with the exception of  103c:006b and 103c:3081
 have a Conexant chip.  Thus first test hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers)
 Should that support fail, the alternate route is described in Modem/Slmodem-ALSA.txt
 
Checking for autoloaded ALSA modem drivers
snd_ali5451            26828  1 
snd_ac97_codec         99808  1 snd_ali5451
snd_pcm                96644  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    60004  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

  Driver snd-intel8x0m  may enable codec acquisition 


---

### Post by towsonu2003 on 2006-05-08
nm

---

### Post by towsonu2003 on 2006-05-08
nm (slow server)

---

### Post by towsonu2003 on 2006-05-08
you're almost there (hopefully)... in packages.ubuntu.com result page, click on "i386" below "Architecture" to download the .deb

PS. fixed the wiki for more clarity

---

### Post by Bunkai on 2006-05-08
Yes! That looks like the file I need to follow the instructions. Downloading it now. Will let you know how it goes here.

Thanx AH-ton!

---

### Post by Bunkai on 2006-05-08
It tried to do it.

Got FATAL: Module slamr not found.

Trying to figure out what that means now.

---

### Post by Bunkai on 2006-05-08
[A thread]("http://www.ubuntuforums.org/showthread.php?t=170414") says> But there is Ubuntu Pacakges - sl-modem-source, which you need to compile. This creates a module which you can insert/'modprobe' into the kernel.
 because poster said > FATAL: Module slamr not found.
SmartLink modem driver not available for this Kernel. Please read README.Debian
or try to install the package sl-modem-modules-2.6.15-20-686. Exiting...
invoke-rc.d: initscript sl-modem-daemon, action "start" failed.


The is no sl-modem-modules-2.6.15-20-686 or sl-modem-modules-* . What can I do?

Nothing I have seen says that sl-modem-daemon __[COLOR="DarkOrange"]depends[/COLOR]__ on sl-modem-modules or sl-modem-source.

Besides I don't know what is meant by insert/modprobe into kernel.

---

### Post by Bunkai on 2006-05-08
I found out that I needed module-assistant to install source. I found it at [http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.10.2_all.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.10.2_all.deb"), put it on my desktop and went to the terminal window and typed ```
sudo dpkg -i module-assistant_0.10.2_all.deb
``` It looks to me like that part went well it ended with a setting up module-assistant message.

So then I typed ```
sudo dpkg -i sl-modem-source*.deb
``` (because I now have more than one deb pkg. on my desktop.) It also seems to have worked out all right -- again ending with a setting up sl-modem-source message.

So, now I think I have to do the modprobe and I info that and end up entering ```
modprobe slamr
``` in the terminal. It replies with FATAL: Module slamr not found.

So...the question is did I use incorrect syntax for the modprobe statement or is there even a need to modprobe now?

---

### Post by towsonu2003 on 2006-05-08
Excellent documentation of the steps and sources :) nice nice nice
[QUOTE=Bunkai]
Besides I don't know what is meant by insert/modprobe into kernel.[/QUOTE]
that means you need to load a driver. for example, if you were using a broadcom wireless device, you would do
sudo modprobe bcm43xx
which would load the driver. (more steps are needed for that particular driver in real life, this was just an example)
[QUOTE=Bunkai]
So, now I think I have to do the modprobe and I info that and end up entering ```
modprobe slamr
``` in the terminal. It replies with FATAL: Module slamr not found.
So...the question is did I use incorrect syntax for the modprobe statement or is there even a need to modprobe now?[/QUOTE]
You need to compile the driver first. sl-modem-source gives you the source of the driver file for you to compile. 
The steps are here in the wiki:
[https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4)

A user reported some problems with compiling the driver here: [https://launchpad.net/distros/ubuntu/+bug/43633](https://launchpad.net/distros/ubuntu/+bug/43633) so if you receive his/her errors, put a confirming message to that bug for it to be confirmed... I'm hoping you will not have any problems compiling... 

I'll fix the wiki to include what to do when you get that message. 

Also, check your modemdata.txt to see if it is recommending any alternative ways to configure. For example, one user's output was saying s/he should also try hsfmodem (just example, not for you), though I don't know if s/he succeded or not :(

Note: The reason sl-modem-daemon doesn't depend on sl-modem-source, imo, is bc some users' (like me) modems work with sl-modem-daemon without the driver...

---

### Post by Bunkai on 2006-05-08
OK, so I need to resolve the module slamr thing.

Hoping for the best I typed ```
sudo dpkg -i sl-modem-daemon*.deb
``` into the terminal and it looked like it really wanted to do it but it again eneded with > FATAL: Module slamr not found.

So, any ideas on what I need to do to install/modprobe the slamr module? The info on modprobe sounds like so much Esperanto;)  to me.

---

### Post by towsonu2003 on 2006-05-08
I think you missed my last post :)

---

### Post by Bunkai on 2006-05-08
[QUOTE=towsonu2003]I think you missed my last post :)[/QUOTE]

Yea, we crossed there. I found it and went to link and typed ```
sudo module-assistant auto-install sl-modem 
```and got a window that says > Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use.

In process of tryting to figure out how to do that.

I really appreciate your efforts, I at least feel like I could be making some progress here.

---

### Post by Bunkai on 2006-05-08
A following message said to ```
sudo module-assistant prepare
``` but this failed because it wanted to connect to repository and it can't.

So, I guess the next step would be to go through the manual process of finding and transferring the files it wants.

---

### Post by towsonu2003 on 2006-05-08
> **Bunkai]...Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use...[/QUOTE]
you have all these, right?>    1.

      build-essential
   2.

      linux-headers-`uname -r`
   3.

      fakeroot
   4.

      gcc-3.4

You also need to install the source of the Smartlink driver itself:

   1.

      sl-modem-source
   2.

      sl-modem-daemon

What's the outputs of```
[b]uname -r
ls -l /usr/src/[/b]
```? (copy paste  said:**
>    1.

      $ sudo module-assistant auto-install sl-modem
   2.

      $ sudo depmod -a (this updates the list of available modules)


---

### Post by Bunkai on 2006-05-08
[QUOTE=towsonu2003]you have all these, right?
What's the outputs of```
[b]uname -r
ls -l /usr/src/[/b]
```? (copy paste ;) )

[/QUOTE]

uname -r gives me 2.6.15-21-686

and ls -l /usr/src/ gives me:
flgrx-kernel-source.tar.gz
linux -> linux-headers.2.6.15-21-686
sl-modem.tar.bz2

---

### Post by Bunkai on 2006-05-08
These linux headers are also what it was trying to get from the repo.

---

### Post by towsonu2003 on 2006-05-08
[QUOTE=Bunkai]uname -r gives me **2.6.15-21-686**

and ls -l /usr/src/ gives me:
flgrx-kernel-source.tar.gz
linux -> linux-headers.**2.6.15-21-686**
sl-modem.tar.bz2[/QUOTE]
that's the correct output that negates what module-assistant says here: 
> Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use
You have the **correct** kernel headers. Most frustrating... Try the Microsoft way: reboot and try the command again (sudo module-assistant auto-install sl-modem). I really doubt it will work, but worth the try... 

Do you have the 2.6.15-21-**386** in your grub (the screen you when right when you boot the pc)? Try once after booting with that kernel in case this is a seriously stupid bug. **edit: you will need the linux-headers-2.6.15-21-386 bf doing the module thingy**

From your kernel version, I'm guessing you have Dapper... I would wonder whether the same occurs with Breezy, but I'm not gonna recommend you to install breezy (no guarantee that it will work in Breezy)... 

If these don't help, can you copy paste all your commands starting with "sudo module-assistant auto-install sl-modem" and including the sudo module-assistant prepare *and* all the outputs you get?

---

### Post by Bunkai on 2006-05-08
What's fakeroot and how can I tell if I have it?

If I understand the Synaptic search results right, it's in there (the box is gray.)

---

### Post by Bunkai on 2006-05-08
OK, rebooting...

---

### Post by towsonu2003 on 2006-05-08
[QUOTE=Bunkai]What's fakeroot and how can I tell if I have it?[/QUOTE]
not sure what it is, never works for me :) it should be "checked" in synaptic -if it is, it means it is installed. if there is a weird arrow along with the check mark (I assume that's what you refer to as "grey"), than it means it is marked to be installed, but not installed yet. I don't think it is the case for you though (you're using dpkg instead of apt-get/synaptic)...  

I'm hoping the 2.6.15-21-**386** will work... Link to its own linux headers: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-headers-2.6.15-21-386_2.6.15-21.32_i386.deb&md5sum=c84c7542f25f3c71c86fa8b08e12e04d&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-headers-2.6.15-21-386_2.6.15-21.32_i386.deb&md5sum=c84c7542f25f3c71c86fa8b08e12e04d&arch=i386&type=main)

you could also check for its md5sum if you know how to. md5sum seems to be c84c7542f25f3c71c86fa8b08e12e04d for this file (I may be wrong). to check md5sums, the command is:
```
md5sum /path/to/file
```

---

### Post by Bunkai on 2006-05-08
The stuff in the box doesn't show in the terminal, but it was the same as last time.

dan@ubuntu:~$ cd Desktop
dan@ubuntu:~/Desktop$ sudo module-assistant auto-install sl-modem
Password:
Reading package lists... Done
Building dependency tree... Done
sl-modem-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
dan@ubuntu:~/Desktop$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-21-686
apt-get install linux-headers-2.6.15-21-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-21
The following NEW packages will be installed
  linux-headers-2.6.15-21 linux-headers-2.6.15-21-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7726kB of archives.
After unpacking 79.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Errhttp://archive.ubuntu.com dapper/main linux-headers-2.6.15-21 2.6.15-21.32
  Temporary failure resolving `archive.ubuntu.com`
Errhttp://archive.ubuntu.com dapper/main linux-headers-2.6.15-21-686 2.6.15-21.32
  Temporary failure resolving `archive.ubuntu.com`
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21_2.6.15-21.32_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21_2.6.15-21.32_i386.deb)  Temporary failure resolving `archive.ubuntu.com`
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb)  Temporary failure resolving `archive.ubuntu.com`
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Done!
dan@ubuntu:~/Desktop$

---

### Post by Bunkai on 2006-05-08
I'm going to have to give up on this for tonight.

---

### Post by towsonu2003 on 2006-05-08
[QUOTE=Bunkai]The stuff in the box doesn't show in the terminal, but it was the same as last time.

dan@ubuntu:~$ cd Desktop
dan@ubuntu:~/Desktop$ sudo module-assistant auto-install sl-modem
Password:
Reading package lists... Done
Building dependency tree... Done
sl-modem-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
dan@ubuntu:~/Desktop$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-21-686
apt-get install linux-headers-2.6.15-21-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-21
The following NEW packages will be installed
  linux-headers-2.6.15-21 linux-headers-2.6.15-21-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7726kB of archives.
After unpacking 79.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Errhttp://archive.ubuntu.com dapper/main linux-headers-2.6.15-21 2.6.15-21.32
  Temporary failure resolving `archive.ubuntu.com`
Errhttp://archive.ubuntu.com dapper/main linux-headers-2.6.15-21-686 2.6.15-21.32
  Temporary failure resolving `archive.ubuntu.com`
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21_2.6.15-21.32_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21_2.6.15-21.32_i386.deb)  Temporary failure resolving `archive.ubuntu.com`
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb)  Temporary failure resolving `archive.ubuntu.com`
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Done!
dan@ubuntu:~/Desktop$[/QUOTE]
Let's try kicking apt-get around a little bit. Try this:

Download these files and put them to your desktop:
[linux-headers-2.6.15-21]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-headers-2.6.15-21_2.6.15-21.32_i386.deb&md5sum=4d8a4e75bc4488fb4022a3c50c866475&arch=i386&type=main")
[linux-headers-2.6.15-21-686]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.15%2Flinux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb&md5sum=7cf6c10662891b8b8818f28aa943e356&arch=i386&type=main")
I think you have already downloaded... 

Make a new folder on your desktop and move these files in that folder. Name the folder "temp" (no quotes)

Now:
```

cd
cd Desktop
sudo cp temp/* /var/cache/apt/archives/
ls /var/cache/apt/archives
```
The last command is for you to check that correct stuff went into the /var/cache/apt/archives/ directory. it should now have at least these two deb files you downloaded. Be extremely careful with those commands, playing around like this may be dangerous. 
Now try:
```

sudo module-assistant auto-install sl-modem

```
If it asks you to do "sudo module-assistant prepare", do that as well. If it doesn't ask you that, do
```
sudo depmod -a
```
Than do
```
sudo modprobe slamr
```
and pray at the same time. 

If it tells you it couldn't load the module, boot with your kernel 2.6.15-21-**386** and try the steps described in the wiki again. Don't forget that you'll need the linux-headers-2.6.15-21-**386** this time installed, instead of linux-headers-2.6.15-21-**686**.

if you get errors, copy paste all the commands you used prior to the error, their output, and the error-causing command and the error itself... 

If that doesn't work either, I'm truly clueless. post your ModemData.txt here s a last resort (if above does not work) and there is a minimal chance that I will make sense of it and let you know of an alternative. again, minimal chance... 

:(

> 
I'm going to have to give up on this for tonight

ok :)

---

### Post by Bunkai on 2006-05-10
[QUOTE=towsonu2003]post your ModemData.txt here[/QUOTE]
ModemData.txt is first reply to originally posted text.:)

Followed your instructions. Terminal output:> dan@ubuntu:~/Desktop/temp$ sudo module-assistant auto-install sl-modem
Reading package lists... Done
Building dependency tree... Done
sl-modem-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
dan@ubuntu:~/Desktop/temp$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-21-686
apt-get install linux-headers-2.6.15-21-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-21
The following NEW packages will be installed
  linux-headers-2.6.15-21 linux-headers-2.6.15-21-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7726kB of archives.
After unpacking 79.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-headers-2.6.15-21.
(Reading database ... 90257 files and directories currently installed.)
Unpacking linux-headers-2.6.15-21 (from .../linux-headers-2.6.15-21_2.6.15-21.32_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-21-686.
Unpacking linux-headers-2.6.15-21-686 (from .../linux-headers-2.6.15-21-686_2.6.15-21.32_i386.deb) ...
Setting up linux-headers-2.6.15-21 (2.6.15-21.32) ...

Setting up linux-headers-2.6.15-21-686 (2.6.15-21.32) ...

Done!
dan@ubuntu:~/Desktop/temp$ sudo module-assistant auto-install sl-modem
Reading package lists... Done
Building dependency tree... Done
sl-modem-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/sl-modem.tar.bz2, please wait...
Done with /usr/src/sl-modem-modules-2.6.15-21-686_2.9.10+2.9.9d-6ubuntu1+2.6.15-21.32_i386.deb .
Selecting previously deselected package sl-modem-modules-2.6.15-21-686.
(Reading database ... 105427 files and directories currently installed.)
Unpacking sl-modem-modules-2.6.15-21-686 (from .../sl-modem-modules-2.6.15-21-686_2.9.10+2.9.9d-6ubuntu1+2.6.15-21.32_i386.deb) ...
Setting up sl-modem-modules-2.6.15-21-686 (2.9.10+2.9.9d-6ubuntu1+2.6.15-21.32) ...
FATAL: Module slamr not found.
SmartLink modem driver not available for this Kernel. Please read README.Debian
or try to install the package sl-modem-modules-2.6.15-21-686. Exiting...

dan@ubuntu:~/Desktop/temp$ sudo modprobe slamr
FATAL: Module slamr not found.
dan@ubuntu:~/Desktop/temp$ sudo depmod -a
dan@ubuntu:~/Desktop/temp$ sudo modprobe slamr
FATAL: Error inserting slamr (/lib/modules/2.6.15-21-686/misc/slamr.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dan@ubuntu:~/Desktop/temp$ info dmesg

Looks like it went well up until the slamr insert. Here's what (I think is) the pertinent part of the dmesg:> ...
[4294698.022000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294698.022000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[4294698.855000] AC'97 1 does not respond - RESET
[4294698.855000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294698.855000] ali mixer 1 creating error.
...
[4363404.549000] slamr: module license 'Smart Link Ltd.' taints kernel.
[4363404.549000] slamr: Unknown symbol class_simple_device_add
[4363404.550000] slamr: Unknown symbol class_simple_destroy
[4363404.550000] slamr: Unknown symbol class_simple_device_remove
[4363404.550000] slamr: Unknown symbol class_simple_create

I can post the whole thing if needed, but it really makes little sense to me.

---

### Post by towsonu2003 on 2006-05-10
Absolute frustration... See this: [https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640](https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640)

Just found that (was using wrong keywords)... That means your modem won't work in Dapper until that bug is fixed... It should work in Breezy (same steps, adjusted for Breezy's kernel). 

Sorry... I should have found that bug earlier.

Note: you could try out the packages linked in that bug report (tar.gz or debian)... not sure it will work.

PS. Here is the crucial bit: 
```

[4363404.549000] slamr: module license 'Smart Link Ltd.' taints kernel.
[4363404.549000] slamr: Unknown symbol class_simple_device_add
[4363404.550000] slamr: Unknown symbol class_simple_destroy
[4363404.550000] slamr: Unknown symbol class_simple_device_remove
[4363404.550000] slamr: Unknown symbol class_simple_create

``` which says the module cannot be compiled bc of the module, not bc of any user fault.

---

### Post by Bunkai on 2006-05-10
Thanks. I'll go look at that bug report and see what I can try. Worse comes to worse I may go back to Breezy, though I didn't have it on long and never got it working either. I can get the install CD back off of deathbyswiftwind I think. You have been so helpful and I want you to know that its appreciated.

---

### Post by Matchless on 2006-05-13
Okay,
      Here is what I did to get Smartlink working in dapper. Uninstalled everything related to SL-modem using Synaptic. Deleted all files found on a search for sl-modem by Krusader. Then did the following:

Howto get Smartlink winmodem working in dapper

1.Read the ubuntu wiki dialupmodemhowto, the steps below only compliment the wiki and you should have all the preliminaries done as described for the Smartlink modem, but you can omit installing gcc-3.4 as this is not required for dapper. Basically the sl-modem driver has to be installed first and then the sl-modem-daemon. The daemon in the repositories will work after an installation, but the /dev/ttySL0  will not be rewritten and the symlink to /dev/modem will not exist after a reboot. The new daemon found in the debian repos solve this. There was a mention that the daemon now looks for ungrab-winmodem and if you get an error message refering to this, you may need to install as well.
2.Download sl-modem-daemon2.9.9d+e-pre2-5.deb and sl-modem_2.9.9d+e-pre2.orig.tar.gz from the debian website [http://packages.debian.org/unstable/misc/sl-modem-daemon](http://packages.debian.org/unstable/misc/sl-modem-daemon).  I have found that the slmodem-2.9.11-20051101.tar.gz works better in dapper and this can also be downloaded from the linmodem website [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/).
3.It may also be required that you download and install the ungrab-winmodem from the linmodem website as well.
4.Copy the sl-modem-daemon file to your local repository and update your Packages.gz file, this will allow you to install with Synaptic etc. Or use your favourite way to install a .deb file.
5.Copy the sl-modem_2.9.9+e-pre2.orig.tar.gz ( or preferably the slmodem-2.9.11-20051101.tar.gz) file to your Desktop and right click on it and select &#8220;Extract here&#8221; and a folder wth the same name will be created with the extracted files on your desktop.
6.Now rename the folder to an easier name such as &#8220;slmodem&#8221;
7.Open a terminal and cd in to the slmodem folder
8.Type make
9.Type sudo make install
10.Type sudo modprobe slamr
11.Type dmesg | grep slamr
12.Now install sl-modem-daemon2.9.9d+e-pre2-5.deb with Synaptic or in your own favourite way.
13.Use Kppp to query the modem, if this works you are there!
14.Edit /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= USA to i.e SOUTHAFRICA or your country
15.Type sudo /etc/init.d/sl-modem-daemon restart to restart the daemon.
16.If you do a &#8220;Query modem&#8221; in Kppp and you will see that your country has changed.
17.It seems as if the Smartlink modems with Netodragon chip MDV92XP does not work, but the ND92XPA chip works.

---

### Post by Bunkai on 2006-05-14
Thanks, but I already went back to Breezy. But this may help others or when I upgrade if there is a problem.

---

### Post by towsonu2003 on 2006-05-15
thanks for the steps. I added your post to the wiki as well as the bug report on this issue. Hopefully they will fix this bf Dapper comes out...

---

### Post by m.h.shams on 2006-06-30
[QUOTE=Matchless]
4.Copy the sl-modem-daemon file to your local repository and update your Packages.gz file, this will allow you to install with Synaptic etc. Or use your favourite way to install a .deb file.
[/QUOTE]

dear friends, 

im new in ubuntu, and i don't know where is my local repository in ubuntu and
how can i add a package in this repository and update packages.gz file.


please help me to find my answers.


regards.
shams

---

