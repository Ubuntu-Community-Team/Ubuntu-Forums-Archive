---
title: "HSP 56 PCTel Modem driver for Linux?"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by Zonkle on 2005-05-05
Hi there ;)

I'm really enjoying Ubuntu .... but the problem is that it is not recognizing my modem.

In the Device Manager I see AC'97 modem controller ... but in Winxp it was like HSP 56 PCTel.

When I try to auto detect the port .. Ubuntu doesn't find anything.

But when I attached my external Modem (U.S. Robotics) it worked great.

So now how can I make my built in Laptop modem works?

Thank you for this great community and support.

---

### Post by ajt3nc on 2005-05-14
This worked for me on my inspiron 1100 with a AC97 modem

uname -r (must be 2.6.10-5-386)
wget -c [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

---

### Post by Zonkle on 2005-05-21
It didn' work for me :(

I think the wget thingy needs to connect to the net man ?

Please somebody help me ?

I tried the web site the says something like linmodem.....il ..... but this site is blocked in my country !!

Thanks.

---

### Post by Chrissie on 2005-08-07
I have a PCTel HSP56 Micromodem, running on Ubunto 5.04 + gnome 2.10 with kernel 2.6.10.
Modem PCI ID is 134d:7891 (to find which is yours, download and run scanModem - available at [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/))

I got Ubuntu to recognize it by installing the driver **pctel-0.9.7-9-rht-4.tar.gz** available at [http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html).

Good luck
Christel

---

### Post by az on 2005-08-07
Try downloading those two debs onto floppies or a usb stick.  You will have to do the same for that pctel driver.  If the sl-modem driver does not work (I give it about a 80 percent chance since you have an ac97 modem), try the pctel driver.  To compile it, you will need to install the build-essential and linux-headers-2.6.10-5-386 packages which are found on your cd.  Just use synaptic for them.

Read the readme once you decompress the driver

tar xvzf pctel*


If vendors better supported modems in linux, it would not be such a pain.

---

### Post by Zonkle on 2005-08-08
[QUOTE=Chrissie]I have a PCTel HSP56 Micromodem, running on Ubunto 5.04 + gnome 2.10 with kernel 2.6.10.
Modem PCI ID is 134d:7891 (to find which is yours, download and run scanModem - available at [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/))

I got Ubuntu to recognize it by installing the driver **pctel-0.9.7-9-rht-4.tar.gz** available at [http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html).

Good luck
Christel[/QUOTE]
 Thank you very much guys.

Chrissie, I knew about that web site, but the problem is that I can't access it :( it is forbidden in here to access that web site!! proxy thingy :( ...... so I would really really appreciate it if some body can send it to my email please ? the scan tool and the driver? pleaaaaase :'( ?

My email address is: hbazerbashi (at) yahoo.com

And azz, I think I did install header packages ... but what is "tar xvzf pctel*" ? I think in Linux there is a normal visual uncompression tool if that is what you meant.
I will come back to you please as soon as I get the driver.

Thank you very much.

---

### Post by Zonkle on 2005-08-08
I managed to download the scanModem tool from other site however they say I have to download it from the original web site, ,, but there is nothing I can do.

I did run the tool, and this is the results from the "Modemdata.txt" file .. i think it is the need one right ?:
```



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.04 kernel 2.6.10-5-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2005_April_19
------------ --------------  System information ------------------------
Ubuntu 5.04 "Hoary Hedgehog" 
 on System with processor: i686
 currently under kernel:   2.6.10-5-386

There are emerging complications under 2.6.10 kernels.  Concerning code for:
Smartlink slmodem :
   slmodem-2.9.9b.tar.gz at http://linmodems.technion.ac.il/packages/smartlink/
      has the current fixes.  Related messages are:
   http://www.datiku.com/documents/2610_migration.php
   http://www.ussg.iu.edu/hypermail/linux/kernel/0409.3/0345.html 
   http://linmodems.technion.ac.il/archive-fourth/msg03736.html . 
Lucent/Agere DSP/ltmodem:
  http://linmodems.technion.ac.il/archive-fourth/msg03733.html 
Concerning Intel-536ep and 537
   http://linmodems.technion.ac.il/archive-fifth/msg00280.html
   http://linmodems.technion.ac.il/archive-fifth/msg00881.html
   
 The kernel was assembled with compiler:  3.3.5
 with current System compiler GCC=3.3.5
    /usr/bin/gcc -> gcc-3.3

Checking for kernel-headers needed for compiling.
 kernel-headers have base folder /lib/modules/2.6.10-5-386/build
 kernel-headers have base folder /usr/src/linux-headers-2.6.10-5-386

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:01.6
    
Providing detail for device at PCI_bus 0000:00:01.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 1039:7013   Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
  SubSystem 1043:1457   Asustek Computer, Inc.: Unknown device 1457
0000:00:01.6 0703: 1039:7013 (rev a0)
	Flags: medium devsel, IRQ 5
	I/O ports at b800 [size=256]
	I/O ports at b400 [size=128]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1039:7013 1043:1457 debian 2.6.10-5-386 3.3.5 3.3.5    i686

       
 The soft modem Subsystem operates under a controller
   1039:7013  SIS 630 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
  Driver snd-intel8x0m  may enable codec acquisition 

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Checking through information gathered from LinModem ARCHIVES
 Modem codec information on Subsystem 1043:1457 is not in the records.
 There are the following routes toward support:
	Follow instructions in Modem/SoftModem.txt for identifying the modem under a Microsoft boot.
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
  Test the effectiveness of the hsfmodem package from http://www.linuxant.com/drivers/hsf/index.php.

 The debian Linux includes sl-modem packages with Smartlink drivers
   Install the kernel-headers-2.6.10-5-386.deb
   If necessary, set a symbolic link needed for slmodem compiling:
     # ln -s /usr/src/kernel-headers-2.6.10-5-386 /lib/modules/2.6.10-5-386/build
     as described in Modem/DriverCompiling.txt
   Then install the two sl-modem/slmodem packages and follow their directions.
   Thereafter the above slamr diagnositic can be run.

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  http://www.agere.com/client/modem_dsp.html. Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 
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
   http://www-3.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52698
 The SmartLink slmodem-2.9.9 may serve for modems not served by this AgereSystems software.
 
 If may be necessary to add -DMODVERSIONS to the compile flags, 
 depending on whether your kernel was thus compiled. See
 http://linmodems.technion.ac.il/archive-fourth/msg01408.html


 Under the controller 1039:7013  SIS 630 ,
 with modem subSystem 1043:1457     
 Alternative supporting packages are the SmartLink slmodem-2.9.N using its proprietary slamr driver, 
 OR the Open Source snd-intel8x0m.ko driver included with recent 2.6.n kernel installations,
    complemented by the daemon, slmodemd,  of the slmodem-2.9.9-alsa.tar.gz package available at:
            http://linmodems.technion.ac.il/packages/smartlink/
    A major advantage is that driver compiling is not necessary upon kernel updates
.  The command sequence is:
    # modprobe snd-intel8x0m
    # slmodemd --alsa --country=YOURCOUNTRY hw:1 
   with the slmodemd providing for dynamic port creation:
         /dev/ttySL0 --> /dev/pts/N    
   and higher level functions.
 Read the slmodem package readme, Modem/Slmodem.txt and Modem/SoftModem.txt for details.
 
 For SuSE 9.2 users, there is an update  for driver slamr.ko loading during bootup. 
 To find it easily, search for "slamr" within  http://www.novell.com/linux/download/updates/92_i386.html
     

 SmartLink at http://www.smlink.com/ owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  http://www.smlink.com/main/index1.php?ln=en&main_id=40 ,
  but http://linmodems.technion.ac.il/packages/smartlink/ has older packages and new fixes.
      For the emerging 2.6.10 kernels, use the slmodem-2.9.9b.tar.gz  therefrom.
 Read Slmodem.txt  for details.
   
 == Checking PCI IDs through modem chip suppliers ==
 Vendor 1039 is SiS, Silicon Integrated System, producing  soft modem controllers and subsystems.

  ======= PCI_ID checking completed ====== 
 Update=2005_April_19

Analyzing information for PCMCIA device at PCI Bus 00:0a.0
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:0a.1
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31a9.tar.gz at  http://ltmodem.heby.de/
   
For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt
DEVPPP=crw------- 1 root root 108, 0 2005-08-08 15:31 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
  debian is not yet providing pre-compiled drivers for WinModems

``` 


What should I do now ?

Thanks a lot.

---

### Post by az on 2005-08-08
It is saying that it may work with the sl-modem drivers.

Try them here:  
wiki.ubuntu.com/forum/hardware
If it does not work, just remove the two packages.

---

### Post by Zonkle on 2005-08-09
[QUOTE=azz]It is saying that it may work with the sl-modem drivers.

Try them here:  
wiki.ubuntu.com/forum/hardware
If it does not work, just remove the two packages.[/QUOTE]
 Thanks a lot,

I downloaded the two debian files in the SL Modems section and I installed them using "sudo dpkg -i" but one of them looks like didn't install probably ... the one with the "daemon" word.

After I installed them I tried to Auto Detect Modem but I got nothing :( it said couldn't detect modem.

What should I do :( ?

Please look here for a screen shot: [http://img.photobucket.com/albums/v254/hasanbb/Misc/Screenshot.png](http://img.photobucket.com/albums/v254/hasanbb/Misc/Screenshot.png)

Thanks for your time a lot.

---

### Post by az on 2005-08-09
Do 

sudo apt-get -f install

from a terminal.  I think that should solve any problem you have with the packages.

Then try to configure your modem with the netwokring tool.

---

### Post by Zonkle on 2005-08-10
[QUOTE=azz]Do 

sudo apt-get -f install

from a terminal.  I think that should solve any problem you have with the packages.

Then try to configure your modem with the netwokring tool.[/QUOTE]
 What do you mean configure my modem? I tried to autodetect .. and tried the command u told me but it didn't work ... it said something about no such a directory or list.

What should I do now ? is there any other driver or something ?

Thank you very much.

---

