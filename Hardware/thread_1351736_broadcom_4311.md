---
title: "broadcom 4311"
date: 2009-12-10
forum: Hardware
---

### Post by caltabellotta on 2009-12-10
im trying to configure ndiswrapper to recognize my wifi adapter, dreaded broadcom 4311. i tried using this guide
    [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
    but got stuck at step 3 before realizing the guide was a year old and probably wouldn't help.
    any experience with this certain driver+9.10?

---

### Post by KommaH on 2009-12-10
I'm having the same problem as well, however, you might have more luck than I have.

This is a little more up-to-date: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by caltabellotta on 2009-12-10
i went into system > administration > hardware drivers

and activated the broadcom STA wireless driver.  that fixes the problem, but once i restart i have to re activate it. 

is there any way i can get around this? and keep the drivers activated permanently?

edit: not to mention the computer freezes if i click on the wifi icon............

---

### Post by Jeffrey Green on 2009-12-11
When I go into System > Administration > Hardware Drivers, I get a message stating "No proprietary drivers are in use on this system". Which is peculiar since before when I was running my HP Pavillion dv9600 laptop from the Ubuntu Live CD, I would find at least 2 WLAN drivers and 2 NVIDIA graphics adapter drivers displayed. Then after that I could select one and after jumping through some Rings login and providing my WPA2 password, I would be able to connect to my WLAN.
However I had managed to find a link to the Broadcom website somewhere in this forum that had a Linux hybrid driver download and some README instructions which did not help me because the make command was not properly constructed. After some searching I finally stumbled upon some well-constructed make command that was able to produce the wl.ko file. 
But when the makefile got to the formatting part it threw an error which I interpret as meaning that the error was caused by my assumption that I could use the 64-bit version as I have a 64-bit machine. Wrong! Is that what happened? Should I have downloaded the 32-bit version package to use to install the driver. Or should I really be using teh 64-bit version of Ubuntu? I know that the Vista Home Premium OS that I am dual-booting on this laptop is the 32-bit version.
Anyway I am going to add the make commands output and the lspci command output for reference. Can I get someone to confirm or not confirm my suspicions?

Here it is:
   jeffrey@linux-laptop:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
  make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
    CLEAN   /home/jeffrey/hybrid_wl/.tmp_versions
  make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
  jeffrey@linux-laptop:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=`pwd`
  make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
    LD      /home/jeffrey/hybrid_wl/built-in.o
    CC [M]  /home/jeffrey/hybrid_wl/src/wl/sys/wl_linux.o
    CC [M]  /home/jeffrey/hybrid_wl/src/wl/sys/wl_iw.o
    CC [M]  /home/jeffrey/hybrid_wl/src/shared/linux_osl.o
    LD [M]  /home/jeffrey/hybrid_wl/wl.o
  ld: Relocatable linking with relocations from format elf64-x86-64 (/home/jeffrey/hybrid_wl/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/home/jeffrey/hybrid_wl/wl.o) is not supported
  make[1]: *** [/home/jeffrey/hybrid_wl/wl.o] Error 1
  make: *** [_module_/home/jeffrey/hybrid_wl] Error 2
  make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
  jeffrey@linux-laptop:~/hybrid_wl$ clear
  
  jeffrey@linux-laptop:~/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=`pwd`
  make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
    LD [M]  /home/jeffrey/hybrid_wl/wl.o
  ld: Relocatable linking with relocations from format elf64-x86-64 (/home/jeffrey/hybrid_wl/lib/wlc_hybrid.o_shipped) to format elf32-i386 (/home/jeffrey/hybrid_wl/wl.o) is not supported
  make[1]: *** [/home/jeffrey/hybrid_wl/wl.o] Error 1
  make: *** [_module_/home/jeffrey/hybrid_wl] Error 2
  make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
  jeffrey@linux-laptop:~/hybrid_wl$ ls -a
  .  ..  built-in.o  .built-in.o.cmd  lib  Makefile  src  .tmp_versions
  jeffrey@linux-laptop:~/hybrid_wl$ lspci
  00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
  00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
  00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
  00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
  00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
  00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
  00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
  00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
  00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
  00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
  00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
  00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
  00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
  00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
  00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
  00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
  00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
  00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
  02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
  02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
  02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
  02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
  02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
  03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
  jeffrey@linux-laptop:~/hybrid_wl$

---

### Post by caltabellotta on 2009-12-11
is there any way to save the settings in hardware drivers? so i dont have to re activate every start up????

---

### Post by Jeffrey Green on 2009-12-11
> **KommaH said:**
> I'm having the same problem as well, however, you might have more luck than I have.

This is a little more up-to-date: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

So here is what I did so far to solve the No Wireless Driver to be activated problem that I had after fresh install of Karmic Ubuntu [9.10]. First of all, there are numerous update packages to be added to the repositories via Synaptics after the install.  So I did the reload in Synaptics which downloaded the 157 updates and restored any missing packages. then I did the bcm43xx driver installation by following the instructions from the Ubuntu Community Help Webpage above. 

So when I went into System > Administration > Hardware Drivers and tried to activate the broadcom STA wireless driver that was fixed by the aforementioned procedure, I hit another snag. I was asked to authenticate this activation with a password. Aargh. Did you have to do the authentication thing? How?

---

### Post by caltabellotta on 2009-12-11
now whenever i activate the broadcom drivers ubuntu freezes.

would switching to 9.04 solve this? because it doesnt seem like there are solutions:-\"

---

### Post by IcarusR on 2009-12-12
Don't know if this will help, it is a recent (26/11/09) post, sucessfully used on 9.04. 
Maybe worth trying.

[http://prashchopra.blogspot.com/2009/11/setting-up-wireless-lan-on-ubuntu-904.html]("http://prashchopra.blogspot.com/2009/11/setting-up-wireless-lan-on-ubuntu-904.html")

---

### Post by Jeffrey Green on 2009-12-12
> im trying to configure ndiswrapper to recognize my wifi adapter, dreaded broadcom 4311. i tried using this guide
    [https://help.ubuntu.com/community/Wi...eisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
    but got stuck at step 3 before realizing the guide was a year old and probably wouldn't help.
    any experience with this certain driver+9.10? 	   	  	     		 	   

AFAICT, there is no need to use an ndiswrapper, because a firmware update exists that resolves the issue. I found the solution here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx). I've only got one other issue (hopefully) to solve. Now that I have activated the Broadcom STA Wireless driver in Hardware Drivers window, "This driver is activated but not currently in use" appears as the status in the bottom portion of the window. It also appears to not have fixed the issue of the inoperative hard-wired Wireless switch as it still indicates a red "inactive" led status in either the on or off position. So when I click on the wireless/wired symbol in the upper right-hand portion of my ubuntu 9.10/GNOME Desktop GUI, all I get to see is that the wired network status. So hopefully I can get this problem resolved. Anyone have any ideas?

---

### Post by Jeffrey Green on 2009-12-12
Just to let you know that I had neglected to note one sentence in the aforereferenced url link above. 
> If it fails to work after a restart try 'sudo modprobe b43'. Then add the line 'b43' to 'sudo gedit /etc/modules'. 
Then after a restart with my ethernet cable unplugged, my screen suddenly informed me that "Wireless networks are available. Click here to connect to a network." [paraphrased] A few more steps and I was connected.

So now I can truly say, "No worries, mate." Ubuntu just works [,  if you work it right.] Kind of like self-help and recovery. "It works if you work it."

---

### Post by JosephBus on 2010-07-05
**Re: The Definitive Broadcom Solution Guide** 			
 			 			 		   		 		 		Thx 4 Ur advice  on loading broadcom driver...
My problem: 
      Network Manager displays only Desktop & "Windows Network" (Is  that x11?)...
      LAPTOP DOES NOT APPEAR...Wireless is disabled...Wired Networking  'Auto eth0'   active...
 
My laptop  (Hp Pavilion dv7 w/ Broadcom STA Network Ctrlr BCM 4312  802.11b/g is ACTIVATED & in use...)

Thank You for Ur consideration...ANY Thoughts  appreciated...JosephBus@gmail.com

---

