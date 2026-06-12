---
title: "Moden help"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by readitsideways on 2007-06-18
Hi

I'm trying to set up a dialup modem.

Ive done 
```
wget -c http://linmodems.technion.ac.il/packages/scanModem.gz 
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt
```

which tells me 

```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-16-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007
 scanModem update of:  2007_June_16


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	103c:30a5	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:       1256          0   IO-APIC-fasteoi   HDA Intel

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   31.820000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   31.820000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:27d8 is a High Definition Audio card, possibly hosting a soft modem.
```

What now? I don't know from this what my modem is... 

I followed the [following tutorial]("http://ubuntuforums.org/showthread.php?t=458228&highlight=Corporation+82801G+modem"), but it didn't work: 

When I run : sudo slmodemd -c SOUTHAFRICA --alsa hw:0,6
I get:
error: mixer setup: Off-hook switch not found for card hw:0
error: alsa setup: cannot open playback device 'hw:0,6': No such file or directory
error: cannot setup device `hw:0,6'

Can any one help?

Also, when I set up a modem connection by clicking on my wireless notification icon and going to "Manual Connection" I now have an option to connect to a ppp0 connection under Dial up connections - but this does nothing.

Pleeeease can someone help me

Duncan

---

### Post by readitsideways on 2007-06-18
Hi

On the HP website the windows driver it is :
 sp34557.exe  

on this page: 
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-46783-1&lc=en&cc=us&dlc=en&product=3352171&os=2093&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-46783-1&lc=en&cc=us&dlc=en&product=3352171&os=2093&lang=en)

Who would think a modem could be so difficult??

---

### Post by timcredible on 2007-06-18
if at all possible, use an external modem, they work with no setup or problems at all.

---

### Post by readitsideways on 2007-06-20
Nuts

---

