---
title: "Cannot get any printers to work ubuntu 12.04 lts"
date: 2013-05-15
forum: Hardware
---

### Post by poahrr on 2013-05-15
Don't know much about this... so hopefully this isn't an extremely basic question but everytime i try to install a driver for a canon mf4500


generic driver gies CUPS server error

There was an error during the CUPS operation: 'client-error-document-format-not-supported

I had it working at one time but had to reinstall OS for other reasons and can't get anything to go now.

---

### Post by plucky on 2013-05-15
> **poahrr said:**
> Don't know much about this... so hopefully this isn't an extremely basic question but everytime i try to install a driver for a canon mf4500


generic driver gies CUPS server error

There was an error during the CUPS operation: 'client-error-document-format-not-supported

I had it working at one time but had to reinstall OS for other reasons and can't get anything to go now.


I don't have your printer,but the best place to administer a printer is the CUPS interface which you can find in your browser at localhost:631.

Open your browser and type **localhost:631** into the address bar of your browser.

The CUPS interface should then open.

That error could be your printer is set to letter format and it requires A4 instead.

Good Luck

---

### Post by pdc on 2013-05-15
Hi Poarr

all these types of Canon printers use the ubiquituous Canon UFR driver; it is at version 2.6

you can get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

it comes down as Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz

you need to install that; to get the laser working; you don't tell us if you have 32bit or 64bit installed; please tell us that and I can give you further help after that

---

### Post by poahrr on 2013-05-15
thanks guys


I have 32 bit

---

### Post by pdc on 2013-05-15
If you go to post number 9 here (also called #9)

[http://ubuntuforums.org/showthread.php?t=2141925](http://ubuntuforums.org/showthread.php?t=2141925)

I gave a description to Clement as to how to install the Canon UFR driver ........if you follow those instructions and see how you do please?

---

### Post by poahrr on 2013-05-15
i did everything, the printer shows up... i click print and nothing happens...?

---

### Post by poahrr on 2013-05-15
in system settings, printers -  the tab to click print test page is grayed out

---

### Post by pdc on 2013-05-15
> [COLOR="#EE82EE"]the printer shows up[/COLOR]

what do you see?

............I don't have one of these printers ......but when I read the guide I see it talks of registering the printer

what does 

> [COLOR="#FF0000"]sudo /usr/sbin/lpinfo -v[/COLOR] give you?

To register the printer the command is 

> [COLOR="#0000FF"]sudo /usr/sbin/lpadmin -p [printer name for registration] -P [PPD file path] -v lpd:[device URI] -E[/COLOR]

.........we need to fill in some of the details so it would be 

> [COLOR="#0000FF"]sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd[/COLOR] [COLOR="#0000FF"]-v[/COLOR] [COLOR="#EE82EE"]lpd:[device URI] -E[/COLOR]

You would replace the

> lpd:[device URI] -E

with the result of the command sudo /usr/sbin/lpinfo -v .................eg if you got something like ....         [COLOR="#A52A2A"]usb://Canon/MF4500%20Series%20(UFRII%20LT)
[/COLOR]
you paste that in so it looks like sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd -v usb://Canon/MF4500%20Series%20(UFRII%20LT) -E

then restart cups with 

> [COLOR="#FF0000"]sudo service cups restart[/COLOR]

any joy?

---

### Post by poahrr on 2013-05-15
> **pdc said:**
> what do you see?

............I don't have one of these printers ......but when I read the guide I see it talks of registering the printer

what does 

 give you?

To register the printer the command is 



.........we need to fill in some of the details so it would be 



You would replace the



with the result of the command sudo /usr/sbin/lpinfo -v .................eg if you got something like ....         [COLOR=#A52A2A]usb://Canon/MF4500%20Series%20(UFRII%20LT)
[/COLOR]
you paste that in so it looks like sudo /usr/sbin/lpadmin -p MF4500_USB  -P CNCUPSMF4500ZK.ppd -v usb://Canon/MF4500%20Series%20(UFRII%20LT) -E

then restart cups with 



any joy?


it shows up as 

[CENTER]```
Canon-Canon-MF4500-Series-(UFRII-LT)
```
[/CENTER]


```
[CENTER][sudo] password for phr: 
network beh
network socket
network ipp14
network http
network https
network ipps
network lpd
network ipp
direct parallel:/dev/lp0
network smb
direct hp
direct hpfax
network dnssd://PS-4BA44B-U1._printer._tcp.local/
network socket://192.168.1.70
[/CENTER]

```



I put in[CENTER]```

sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd -v lpd:[Canon-Canon-MF4500-Series-(UFRII-LT)] -E
```

[/CENTER]
and got

[CENTER]```
bash: syntax error near unexpected token `('
```
[/CENTER]

---

### Post by pdc on 2013-05-15
help us understand a little about your system:

most folks who post here have a standalone home computer with a printer attached by a USB cable ...................tell us about your system

because I see such things as this

> network dnssd://PS-4BA44B-U1._printer._tcp.local/

to register the printer; have a read at my earlier post:

---

### Post by poahrr on 2013-05-16
> **pdc said:**
> help us understand a little about your system:

most folks who post here have a standalone home computer with a printer attached by a USB cable ...................tell us about your system

because I see such things as this



to register the printer; have a read at my earlier post:

its connected on a lan

---

### Post by pdc on 2013-05-16
>  its connected on a lan 

I struggle a little to help you: I assume the printer is connected by a USB cable................is that right........please tell us this as only you can see the printer .......Canon says it has "[COLOR="#008000"]USB 2.0 Hi-Speed, 10/100 Base-T Ethernet (Network)[/COLOR]"

when your results of the command sudo /usr/sbin/lpinfo -v give the results

> network dnssd://[COLOR="#0000FF"]PS-4BA44B-U1._printer[/COLOR]._tcp.local/ I am wondering if the printer is powered up and connected; as in other posts eg

[http://ubuntuforums.org/showthread.php?t=2059138&page=2](http://ubuntuforums.org/showthread.php?t=2059138&page=2)

in post #13, the system has a Samsung and HP connected and so gives results like

> network dnssd://[COLOR="#0000FF"]HP%20Color%20LaserJet%20CP3525%20%5B872E19%5D[/COLOR]._ipp._tcp.local/ for the HP and 

> network dnssd://[COLOR="#0000FF"]Samsung%20CLP-620%20Series%20(SEC001599484A46)[/COLOR]._ipp._tcp.local/ for the Samsung

and your results is > network dnssd://[COLOR="#0000FF"]PS-4BA44B-U1._printer[/COLOR]._tcp.local/

_______________________________________________________________________________________________________________________________________________

I am thinking that .............to register the printer with the command ................

> sudo /usr/sbin/lpadmin -p [printer name for registration] -P [PPD file path] -v lpd:[device URI] -E

that it ***should*** have something like 

> sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd -v dnssd://Samsung%20CLP-620%20Series%20(SEC001599484A46)._ipp._tcp.local/

.........where I have substituted the Samsung from the previous post

............ what I notice is the system does not seem to recognise your MF4500 and describe it as an MF4500 .....and I think it should ....... you could............... if you feel all is connected well....................try registering with 

> [COLOR="#EE82EE"]sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd -v dnssd://PS-4BA44B-U1._printer._tcp.local/ -E[/COLOR]

---

### Post by poahrr on 2013-05-17
> **poahrr said:**
> its connected on a lan

Sorry for the late reply, been busy.... I appreciate the help.

the results to /usr/sbin/lpinfo are;

[CENTER]```
network socket
network ipp14
network ipps
network https
network http
network lpd
network ipp
network beh
direct parallel:/dev/lp0
direct hp
network dnssd://PS-4BA44B-U1._printer._tcp.local/
network smb
direct hpfax
network socket://192.168.1.70
```
[/CENTER]




[COLOR=#EE82EE]sudo /usr/sbin/lpadmin -p MF4500_USB -P CNCUPSMF4500ZK.ppd -v dnssd://PS-4BA44B-U1._printer._tcp.local/ -E       [/COLOR]gave me;[CENTER]```

lpadmin: Unable to open PPD file "CNCUPSMF4500ZK.ppd" - No such file or directory
```



[/CENTER]
I know the printer is connected properly, ive printed to it before with linux mint before with no changes to the printer or how its hooked up.. the printer is on during these tests and attempts to get it to work. other linux computers on the same wifi can print to it.

---

### Post by pdc on 2013-05-18
all I can suggest when you get 

> Unable to open PPD file "CNCUPSMF4500ZK.ppd" - No such file or directory

is that ppd files are usually in [COLOR="#008000"]/usr/share/cups/model/[/COLOR] so one could spell out the full pathway

 ie sudo /usr/sbin/lpadmin -p MF4500_USB -P /usr/share/cups/model/CNCUPSMF4500ZK.ppd -v dnssd://PS-4BA44B-U1._printer._tcp.local/ -E

........but perhaps best look in [COLOR="#008000"]/usr/share/cups/model/[/COLOR] to see that is there

do you feel able to describe your setup in more detail so we can attempt to understand what might be going on

---

