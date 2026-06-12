---
title: "Brother DCP-J315W - usb and wireless - 11.10"
date: 2012-02-07
forum: Hardware
---

### Post by JaxBoy67 on 2012-02-07
After many attempts; I have successfully enabled my DCP-J315W Brother printer - hope the following method will be helpful to others

                                    
Brother Printer DCP-J315W  install on 64 bit 11.10    usb & wireless
 
It is best to Set up in Unity
1    Install ia32-libs from Software centre
2    sudo apt-get install tcsh from terminal
3 Copy or download lpr and cupswrapper drivers onto 'desktop' &#8211; ie;
     dcpj315wlpr-1.1.3-1.i386.deb
     dcpj315wcupswrapper-1.1.3-1.i386.deb
cd Desktop     in terminal  (' cd Desktop ' )
5    sudo mkdir /var/spool/lpd    in terminal
6    sudo dpkg -i &#8211;force-all dcpj315wlpr-1.1.3-1.i386.deb    in terminal
7    sudo mkdir /usr/share/cups/model        in terminal
8`    sudo dpkg -i &#8211;force-all dcpj315wcupswrapper-1.1.3-1.i386.deb        in terminal
9    [http://localhost:631]("http://localhost:631/")    in firefox to see printer & check it shows a driver. (ie 'Brother DCP-J315W CUPS (color, 2-sided printing)')
10    Reboot PC
10    System ---- Administration ---- Printing
11    For usb connection;-
 
     'Add' &#8211; ' ' &#8211; 'select Brother printer shown ie DCPJ315W' &#8211; follow 'forward ' &#8211; 'Apply'&#8211;         print test page.
 
12    For wireless connection:-
     'Add' &#8211; 'Find Network Printer -enter the ip address (ie192.168.1.50 in my case) &#8211; click 'find'  &#8211; 'select 'jet     direct' and 'LPD/LPR PASSTHROUGH' &#8211; follow 'forward' &#8211; 'Apply'
 
     print test page
     
 
 Scanner Install
1    Copy or download drivers onto desktop (must be 64amd drivers) ie;brscan3-0.2.11-4.amd64.deb (this installs [B]/usr/lib64/ needed later)[    brscan-skey-0.2.1-3.amd64.deb
 2    Instal drivers through Software Centre (make sure any 386 drivers removed first)
3    lsusb    in terminal to get printer id -ie  04f9  ; 0254 Brother Industries......
  
4    sudo gedit /lib/udev/rules.d/40-libsane.rules    in terminal (or use 'sudo nautilus' in terminal to access file through file system)
5    Add at end of printer list ( just before line  &#8220;# The following rule...&#8221;)  the following;-
 # Brother scanners
 ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
6    sudo dpkg -l | grep Brother to check drivers installed

7    Copy files from     /usr/lib64/    to     /usr/lib/.  
     Copy one line at a time using    in terminal**:-**
     sudo cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
    sudo cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
    sudo cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
    sudo cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
    sudo cp /usr/lib64/libbrscandec3.so /usr/lib
    sudo cp /usr/lib64/libbrscandec3.so.1 /usr/lib
8reboot PC.
9     Test scan with **Simplescan** and/or X[B]sane


I also found this procedure is likely to be required to install other DCP printers -ie DCP 153C which I got working on 64 bit
[/B]

---

### Post by mörgæs on 2012-02-07
Thanks, moved to the hardware forum.

---

### Post by k.mooijman on 2012-02-14
Did you mannage to get the scanner working via Wlan ??

---

### Post by JaxBoy67 on 2012-03-02
Hi
Yes - printing and scanning all worked correctly -(a little slow before printing or scanning starts but it did work fine both with simplscan and xsane).
I have also found that the procedure I used is needed on 64 bit for other dcp printers ie dcp 153c which I also got working correctly. 
You must add the additional lines of text [  # Brother scanners
 ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"  ] in /lib/udev/rules.d/40-libsane.rules. 
You can also access the file using 'sudo nautilus' in a terminal. Dont forget to save changes. If this line is not added; nothing will happen at all when trying to scan.
Apologies for late reply.

---

### Post by bml on 2012-09-22
Hi,

"3    lsusb    in terminal to get printer id -ie  04f9  ; 0254 Brother Industries......"

I don't have the printer listed... the printer is working fine, the scanner is not, but I can't go any further because I don't have the printer id...

any ideas?

Thank you,

Bruno

---

### Post by pdc on 2012-09-25
........not sure if you are still out there Bruno.......

but to get the printer ID;

enter the command

> lsusb

in a terminal, and hit the enter key

eg my scanner shows as

> Bus 004 Device 002: **[COLOR="Red"]ID 04a9:2206[/COLOR]** Canon, Inc. CanoScan N650U/N656U

---

### Post by okkietje on 2013-06-06
**For Dutch people:**
Instellen van de Brother DCP-J315W

Na alle fori afgezocht te hebben naar een makkelijke protocol om een printer als de Brother DCP-J315W in te stellen ben ik ten einde raad de Brother Solution Center Nederland gaan bellen. Dit gesprek verliep uiterst teleurstellend. Als Linux gebruiker werd ik in staat geacht zelf een oplossing te vinden. Dus wij Linuxers zijn slimmer dan de Mac gebruikers en nog slimmer dan de Windowers.  Dus heb ik mij wat meer verdiept in de materie. Allereerst bedank ik [http://ubuntuforums.org/showthread.php?t=1921644](http://ubuntuforums.org/showthread.php?t=1921644) vor hun inbreng. Het meeste van mij is met behulp van hen.

We moeten het volgende doen. De drivers installeren en daarna CUPS via de browser gebruiken. Klinkt ingewikkeld maar is het niet.
De &#8594; verwijzen naar de volgende keus.
Daar gaat ie:

1. Ga via de rowser naar Brother Solution Center.
    &#8594; DCP &#8594; DCP-J3 serie &#8594; DCP-J315W &#8594; linux &#8594; printer-driver &#8594; DCP-J315W
	&#8594; lpr-driver.deb download &#8594; accept &#8594; install.
2.	cupswrapper.driver.deb download &#8594; accept &#8594; install
3.	Nu je er toch bent, installeer dan ook de brscan3-32bit of 64bit
4	en de scan-key-tool 32bit of 64 bit.
5.	ga met de browser naar [http://localhost:6631](http://localhost:6631) en log in
6,	 dit ziet DCP-J315W (color, 2 sided printer)
7.	herstart de computer.

Systeemmenu &#8594; afdrukbeheer Er staat nu een printer klaar met als eigenschappen:
	Omschrijving	DCPJ315W
	Locatie 	thuis (mijn visie)
	apparaat URI:	usb:/dev/usb/lp0
	merk en model	Brother DCP-J315W CUPS
	printer status	inactief

Nu de WIFI
Ga weer naar CUPS
Add printer en log in
Kies Dicovered networkprinter Brother DCP-J315W (Brother DCPJ315W)
&#8594; continue en kies uit de database Brother DCP-J315W (eng)
We zien:
	Name	Brother DCP-J315W
	Description	lan (mijn visie)
	connection	lpd:////BINARY_P1
	continue
Herstart computer
Systeemmenu &#8594; Instellingbeheerder &#8594; Afdrukbeheer
9.	Verander lpd:///BINARY_P1 in lpd://192,168,001,226 (maar dan die van uw printer)/BINARY_P1
10.Druk testpagina af

SUCCES.

---

