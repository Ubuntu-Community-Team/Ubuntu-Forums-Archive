---
title: "Ubuntu 24.04. Scanner Brother DCP-135C driver not working?!"
date: 2024-07-01
forum: Hardware
---

### Post by upsetti on 2024-07-01
Guys (and girls etc.).
I am a Computer Scientist etc. pp. have loads of experience BUT...
I just installed for my mother a new Ubuntu 24.04. because the old one was not updateable.

As much as I love the Linux/OpenSource idea etc.pp. if you/it want to be successful it can't be that simple things such as installing/using a scanner
(which even does have a driver provided by the manufacturer) is not(!?) working?!

So, to make a long story short:
System: Ubuntu 24.04.
Printer/Scanner: Brother DCP-135C (USB)

Printer: Works (mostly; cuts off top of each page, but that is fixable).
Scanner: Does not work?! (was working beforehand on the older Ubuntu)
Default program says: 'Install driver software' (which is a link, but klicking the link does nothing?!)

However, I went to the brothers homepage, downloaded the driver ([https://support.brother.com/g/b/downloadlist.aspx?c=de&lang=de&prod=dcp135c_eu_as&os=128&flang=English](https://support.brother.com/g/b/downloadlist.aspx?c=de&lang=de&prod=dcp135c_eu_as&os=128&flang=English))

Tried to install the driver but it fails at the the scanner section because of an unresolved dependency.
Iirc it was the sane lib? The interwebz tells me that the libsane was renamed to libsane1 at one point?

Anyways. Does anyone have the same problem and maybe a (in the best case simple) solution to it?
It would be highly appreciated.

Thanks a lot!

---

### Post by him610 on 2024-07-01
@upsetti,
Welcome to the Forums.

Maybe we can get your Brother DCP-135C scanner capability working. I have Brother MFC-7360N software installed on Xubuntu 24.04, and it works. 
Please run this command and post the results within the code brackets.
```
dpkg -l libsane*
```

---

### Post by upsetti on 2024-07-03
Hey.
Thanks for the reply, and sorry for my late answer.
Yesterday (and today) were long days and when I wanted to post my answer yesterday the forum itself wasn't working!
Sorry.

Anyways, here is the output:
```

|/ Name                Version                Architektur  Beschreibung
+++-===================-======================-============-===========================================================
ii  libsane-common      1.2.1-7build4          all          API library for scanners -- documentation and support files
ii  libsane-hpaio:amd64 3.23.12+dfsg0-0ubuntu5 amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64      1.2.1-7build4          amd64        API library for scanners

```

---

### Post by theotherothermatt on 2024-07-04
I have the same problem. The standard install script installs brscan-skey but that has a control file dependency on libsane where as Ubuntu 24.04 has libsane1; so I unpacked the deb file edited the control file dependency to be libsane1 and reinstalled the deb package.

But, as I suspected it still isn't working. I've disabled all other drivers in /etc/sane.d/dll.conf apart from brother4 and still no joy.

I've checked the strace(1) output of the scanimage binary as it runs and it seems to give up after is reads /sys/bus/usb/devices/{busID}-{deviceID}/descriptors and then seems to check if it matches any of the supported scanners in either /etc/opt/brother/scanner/brscan4/Brsane4.ini or any of the extended definitions in /etc/opt/brother/scanner/brscan4//models4/ext_*.ini

I have a DCP-L8410CDW and it is in ext_18.ini but I suspect whatever info it is getting from the descriptors file isn't matching what is in the ext_*.ini file.

This may have to do with the fact that there might be changes in either libsane or libusb compared to older versions.

---

### Post by him610 on 2024-07-04
I get the same with *dpkg -l libsane**
however, I get this also,
```
$ dpkg -l *sane*
.....
ii  libsane-common      1.2.1-7build4          all          API library for scanners -- documentation and support files
ii  libsane-hpaio:amd64 3.23.12+dfsg0-0ubuntu5 amd64        HP SANE backend for multi-function peripherals
ii  libsane1:amd64      1.2.1-7build4          amd64        API library for scanners
ii  sane-airscan        0.99.29-0ubuntu4       amd64        SANE backend for AirScan (eSCL) and WSD document scanner
ii  sane-utils          1.2.1-7build4          amd64        API library for scanners -- utilities
hugh@ma90x:~$ 

```
 and 
```

dpkg -l br*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  brotli         <none>       <none>       (no description available)
un  brscan         <none>       <none>       (no description available)
ii  brscan4        0.4.11-1     amd64        Brother Scanner Driver

```
```

$ apt policy brscan4
brscan4:
  Installed: 0.4.11-1
  Candidate: 0.4.11-1
  Version table:
 *** 0.4.11-1 100
        100 /var/lib/dpkg/status

```
I don't know of any other advice to give you.

---

### Post by him610 on 2024-07-04
Does your *Brsane4.ini *have your particular DCP model listed? Mine does not show your model, DCP-135C.

```
$ cat /etc/opt/brother/scanner/brscan4/Brsane4.ini
[Support Model]

0x0246,116,1,"MFC-9970CDW",133,4
0x0245,116,1,"MFC-9560CDW",133,4
0x0244,116,1,"MFC-9465CDN",133,4
0x0243, 16,1,"MFC-9460CDN",133,4
0x0242,116,2,"DCP-9270CDN",133,4
0x0241, 16,2,"DCP-9055CDN",133,4

0x0262,13,1,"MFC-J6510DW"
0x0263,13,1,"MFC-J6710DW"
0x0266,13,1,"MFC-J6710CDW"
0x0267,113,1,"MFC-J6910DW"
0x0268,113,1,"MFC-J6910CDW"

0x028b,13,1,"MFC-7362N",133,4
0x0277,14,2,"DCP-7070DW",133,4
0x0275,13,1,"FAX-7860DW",133,4
0x0273,14,2,"DCP-7057",133,4
0x0272,14,2,"HL-2280DW",133,4
0x0271,13,1,"MFC-7470D",133,4
0x0270,13,1,"MFC-7360N",133,4
0x024f,13,1,"MFC-7860DW",133,4
0x024e,13,1,"MFC-7460DN",133,4
0x024d,13,1,"MFC-7360",133,4
0x024c,13,1,"MFC-7860DN",133,4
0x024a,13,2,"DCP-7065DN",133,4
0x0249,14,2,"DCP-7060D",133,4
0x0248,14,2,"DCP-7055",133,4

[ModelTypeName]
1=MFC Scanner
2=DCP Scanner

[Driver]
scanfast24=0
NoUseCM=0
compression=1
Inqueue=32000
LogFile=0
xshift_c=0
timeout=60000
minpid=582
EnableFBMultiPage=1
EnableSKeyDuplex=0

```

---

### Post by upsetti on 2024-07-05
Interestingly enough(?) I do not even have a Brsane4.ini nor a brother folder at /etc/opt/brother?

However dpkg -l br*
leads to:

```

+++-==========================-============-============-==========================================================
un  brasero                    <keine>      <keine>      (keine Beschreibung vorhanden)
ii  brltty                     6.6-4ubuntu5 amd64        Access software for a blind person using a braille display
un  brltty-speechd             <keine>      <keine>      (keine Beschreibung vorhanden)
un  brltty-x11                 <keine>      <keine>      (keine Beschreibung vorhanden)
un  broffice                   <keine>      <keine>      (keine Beschreibung vorhanden)
un  browser-plugin-libreoffice <keine>      <keine>      (keine Beschreibung vorhanden)
un  brscan                     <keine>      <keine>      (keine Beschreibung vorhanden)
ii  brscan2                    0.2.5-1      amd64        Brother Scanner Driver

```

Could that be of any help?

And thanks a lot for your engagement and also good to know that I am not the only one.
Even though it is a really old printer/scanner it is still working flawlessly (theoretically).
So being able to continue to use it would be awesome.

Thanks a lot!

---

### Post by him610 on 2024-07-06
I see that you have *brscan2  0.2.5-1* while I have *brscan4  0.4.11-1* installed; although, yours was released about five years earlier than mine. 

Wonder if that is due to yours being an inkjet while mine is a laser device. Mine is also a commercial grade office machine.

---

### Post by oldfred on 2024-07-06
Have you tried different scanner software.
I use Kubuntu, so my defaults may be different.

I think with 22.04, I found Skanlite worked or worked better.
With 24.04 both Skanlite & Skanpage worked.

I have not installed any software directly from Brother, and with 24.04 Brother printer just worked for both printing & scanning.

My printer is both USB & WiFi. I think when I first installed it, it seemed like WiFi was the working mode.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ scanimage -L [/COLOR]
device `escl:http://192.168.1.6:80' is a Brother HL-L2390DW adf scanner 
device `escl:http://localhost:60000' is a Brother HL-L2390DW (USB) platen scanner 
device `airscan:e0:Brother HL-L2390DW' is a eSCL Brother HL-L2390DW ip=192.168.1.6 
device `airscan:e1:Brother HL-L2390DW (USB)' is a eSCL Brother HL-L2390DW (USB) ip=127.0.0.1, ::1 
[COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ airscan-discover [/COLOR]
[devices] 
  Brother HL-L2390DW = http://192.168.1.6:80/eSCL/, eSCL 
  Brother HL-L2390DW = http://[fe80::4223:43ff:fe9c:afd6%252]:80/eSCL/, eSCL 
  Brother HL-L2390DW = http://192.168.1.6:80/WebServices/ScannerService, WSD 
  Brother HL-L2390DW = http://[FE80::4223:43FF:FE9C:AFD6%252]:80/WebServices/ScannerService, WSD 
  Brother HL-L2390DW (USB) = http://[::1]:60000/eSCL/, eSCL 
  Brother HL-L2390DW (USB) = http://127.0.0.1:60000/eSCL/, eSCL


[/FONT]
```

---

### Post by him610 on 2024-07-06
Well, I downloaded the software for DCP-135C and went so far in the install process as this...
```
bash linux-brprinter-installer-2.2.4-1
Input model name ->DCP-135C

You are going to install following packages.
   dcp135clpr-1.0.1-1.i386.deb
   dcp135ccupswrapper-1.0.1-1.i386.deb
   brscan2-0.2.5-1.amd64.deb
   brscan-skey-0.3.2-0.amd64.deb
OK? [y/N] ->

```
Of course, I chose "no" as I did not want to spoil my own Brother software.

One more question for you, when you ran this command...
```
bash linux-brprinter-installer-2.2.4-1 DCP-135C
```
Did you do it as root (*sudo su*)?

---

### Post by clydestereo on 2024-08-30
I have a Brother MFC-7440N - Same Issue. (Linux Mint 22)

Here is what I did to get it working

Add this PPA to your system (Ubuntu SANE packages from SANE Stable Source)

You can update your system with unsupported packages from this untrusted PPA by adding ppa:sane-project/sane-release to your system's Software Sources. 

---
sudo add-apt-repository ppa:sane-project/sane-release
sudo apt update
---

Open Update Manager-->Refresh-->Install updates (libsane-common)

Install Brother Driver as per Brother website

ie: sudo bash linux-brprinter-installer-2.2.4-1 MFC-7440N

---

