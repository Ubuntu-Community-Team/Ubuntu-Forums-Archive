---
title: "Internal modem not working"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by trav1085 on 2005-12-31
I have a Dell Inspiron 1150, with internal 56K modem, And, I can't get it to be detected on the System>>>Administarion>>Network, there is a modem option but won't be detected.

I really think this will help about what kind of modem I have, my computer doesn't have software CD for the modem, I think the driver is built in.

Oh, I have Windows XP Home as the first OS, the modem works fine with a built in driver.

This is the modem I have: Conexant D480 MDC V.9x Modem
                                    On Windows, attaached to COM3

I just need to know if there are any drivers needed for linux.

---

### Post by jml on 2005-12-31
In all likelyhood your laptop is using what is called a "Winmodem"  Its not a true modem, in that it simply consists of a connection between the phone line and the computer's motherboard.  The modem functions are emulated in software rather than in the hardware of a regular modem.  Here is a link to a huge resource for finding drivers for many different types of modems, especially winmodems.

[http://linmodems.org/](http://linmodems.org/)

Hope this helps.

Joe

---

### Post by towsonu2003 on 2005-12-31
more reading is also available in the wiki in my signature... good luck

---

### Post by ronb on 2005-12-31
[QUOTE=trav1085]

This is the modem I have: Conexant D480 MDC V.9x Modem
                                    On Windows, attaached to COM3

I just need to know if there are any drivers needed for linux.[/QUOTE]

You might be able to find a driver for your Conexant modem at this website: [http://www.linuxant.com/company/](http://www.linuxant.com/company/)

If you find the right driver for your modem there, the chances are that they will offer you a free version that runs at 14.4K and a full speed version for about $20.

I bought a nice external modem that works great using COM1 (/dev/ttyS0), but maybe you don't want an external modem if you have laptop.

Ron

---

### Post by trav1085 on 2006-01-01
So if I absolutly can't find a driver for my modem, I could buy a cheap USB external modem for my laptop, as I only have USB ports for connecting

---

### Post by ronb on 2006-01-01
[QUOTE=trav1085]So if I absolutly can't find a driver for my modem, I could buy a cheap USB external modem for my laptop, as I only have USB ports for connecting[/QUOTE]

I think that USB modems are similar to internal modems.  That is, they are software modems and that their hardware is incomplete somehow.  Because of this they need to use some of the computer's hardware.  If you go this route, you will need to read through the links provided above by towsonu2003 to make sure you get a modem that is compatible with Linux.

My external modem is a so-called 'real' modem, and I guess that means that it has all the hardware it needs built-in.  But, if you don't have a COM1 port, that option is not available.

However, I'm sure that there are several USB modems (and free drivers) that will work.

---

### Post by trav1085 on 2006-01-01
No conexant drivers are working, what about some free drivers for any internal modem, like SmartLink, or Generic Internal drivers. Becuase I looked at Staples for a USB modem and there cheapest (and only one) was $80

---

### Post by trav1085 on 2006-01-01
I downloaded a Generic Driver from linuxant.com, I hope that will work. And if it doesn't, I think I can find even more help in alt.computer or alt.linux

---

### Post by trav1085 on 2006-01-02
I'm pretty sure I have the driver installed right, when I restart or shut down to get into windows I see "Stopping Conexant HSF softmodem -- OK" So I know it's working and running, but how do I connect and test to get a dial tone?

---

### Post by John C on 2006-01-02
I also come from "A very small town in Canada"...  hence: dial-up connection is required.  Received a big package of "Ubuntu CDs" in the mail (nicely packaged) and proceeded to pop a "live" one in one of my computers to try it out.

Very disappointed that I couldn't get a dial-up connection in the first two computers I tried -- both had access to internal SmartLink modems and a serial modem on Com1 as well.  First of all it was not very easy at all to find the setup for a modem, until I went to this forum and learned of "Modem Monitor" -- not in Menus and only available back-clicking and +Add to the top Menu Bar.

OK.. owing to the extreme lack of utility (read: too simple), I never did get online as it appears Ubuntu doesn't like two modems attached to the computer at the same time -- it was impossible to configure anything :-(

To keep this short:  I ended up trying a computer with no modem inside, just an external Zoom modem (serial)...  No problem at all, other then the lack of a better modem conigurator utility.  I really was ready to give up, as I have several versions of Linux on my computers and have never run into so much trouble trying to connect a modem(s) that are supposed to be supported.

Guess what I'm saying is that there really needs to be an obvious way to get onto the internet right from go.  Less experienced users would have simply given up.
One of the first things I do when trying a new Distros is immediately fire up an internet connection.... if that doesn't happen, the CD goes into the re-cycle bin.

My first impressions of Ubuntu:  Nice clean interface -- very sweet!

But before I can hand out my big pile of Ubuntu CDs, I'll have to write and print a sheet explaining how to get a modem connected -- very bad oversite.

Gee I hate it when my first posting is not a little more positive.  I'm sure the second Post will be about something wonderful in Ubuntu.

---

### Post by towsonu2003 on 2006-01-02
> **John C]First of all it was not very easy at all to find the setup for a modem, until I went to this forum and learned of "Modem Monitor" -- not in Menus and only available back-clicking and +Add to the top Menu Bar. [/quote] but the modem monitor would be of no use to winmodem users who are trying to figure out whether the modem is supported
[QUOTE=John C]
it was impossible to configure anything :-( (...) No problem at all, other then the lack of a better modem conigurator utility.[/quote] once you got your modem up and running, try wvdial to configure your dial out. To me, it is much easier than the 'Administration>Networking tool and the Modem Monitor applet doesn said:**
> 
Less experienced users would have simply given up. I did give up about 5 times bc. of my winmodem before trying out 'once more', 'this the last try'. most people will try it once and quit. 
[QUOTE=John C]
But before I can hand out my big pile of Ubuntu CDs, I'll have to write and print a sheet explaining how to get a modem connected [/quote] Unfortunately, that would not help newcomers with winmodems at all. There are too many winmodems and too many specificthings to do for each winmodem to print out... You need to configure their winmodems for them, write a personalized howto for that machine, and hand the machine to the owner along with that howto...

The lack of winmodem support in linux is sad, and it clearly is the fault of the manufacturers who are too lazy to either give the community the specs of their winmodems or write the damn drivers themselves. 

However, cooperation of big distro makers (such as ubuntu, slackware, suse etc) with linmodems.org to come up with out-of-the-box winmodem support also seems unplausible, making linux a geek toy for those who are lucky enough to have a supported winmodem (like me) and stubborn enough to configure it, or for those who are rich enough to buy broadband.

**PS. did the OP (original post) run scanModem tool on his/her machine to see whether there are any drivers for his/her winmodem yet? see the wiki link in my signture for that.**

---

### Post by trav1085 on 2006-01-02
OK, I got my modem working know, I used the Debian HSF driver from linuxant.com, then used minicom to configure, also used scanModem to find the port, It turned out that my modem wasn't on /dev/modem or any of the pre-configured options but /dev/ttySHSF0

One more thing, how do I connect and set up a connection to work with Firefox on ubuntu

---

### Post by towsonu2003 on 2006-01-03
[QUOTE=trav1085]
One more thing, how do I connect and set up a connection to work with Firefox on ubuntu[/QUOTE]
Try using wvdial (wiki link here: [https://wiki.ubuntu.com/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb](https://wiki.ubuntu.com/DialupModemHowto#head-8f5dfcf07a408945df0dcd5a4eed9d5a8d20dacb) ). you may need to do ```
ln -s /dev/ttySHSF0 /dev/modem
``` before setting it up (i.e. configuring) though. That command will link your modem port to /dev/modem, thus making easier for the dialers (like wvdial) to find the modem...

Once you connect to your ISP, firefox and any other web-enabled program will just work as in Windows...

---

### Post by trav1085 on 2006-01-03
I did download wvdial once, but it was the source that I had to compile myself, I don't know how to compile source and want the binary (or installer), Is that the binary or source, if source, where can I find the binary. 

(I think learning to compile source should be next priority after internet's working! :)

---

### Post by trav1085 on 2006-01-03
wvdial is too hard to get to work, I need to have a c compiler which I don't have, but I have minicom, which connects then stays connected for a couple of minutes then says "NO CARRIER"

---

### Post by towsonu2003 on 2006-01-03
try this: put your install CD in your computer, then ```
sudo apt-get update
sudo apt-get install wvdial
```

This should install wvdial (from the CD)... Make sure you read the wiki link in my previous post while trying to set it up & dial.

---

### Post by John C on 2006-01-04
*PS. did the OP (original post) run scanModem tool on his/her machine to see whether there are any drivers for his/her winmodem yet? see the wiki link in my signture for that.* end quote

I think the point of my original Post was that there was no obvious/quick way of getting an internet connection with a modem -- when/if you do get a connection, there is almost NO information --  I like details about my connections!

Kppp comes to mind... and of what use is there, if you have to download something IF you can't get on the internet in the first place?

Most good Distros have the few (win)linmodem drivers that are available; most detect automatically, and some have a script or an install routine.

It is pretty much unforgiveable that you can't get a serial modem working if you have a win(lin)modem on the same computer -- first time I have come up against this.

All that being said, I have Ubuntu "live" running on a computer and I am enjoying it... it just might become part of the fleet of installed Distros.  And yes it is nicely surfing the web with an external serial Zoom modem that took about 2 minutes to get working (once you get the drift of it :)

In the Menus: a heading: "Internet/Modem connection ->"  But why make it easy?

---

### Post by towsonu2003 on 2006-01-04
[QUOTE=John C]
Most good Distros have the few (win)linmodem drivers that are available; most detect automatically, and some have a script or an install routine.
[/QUOTE]
I agree... hence the first link in my signature which refers to a thread in Dapper developers forum...

---

### Post by edemark on 2006-01-04
I just would have liked to point out that there is a really easy way to set up dial up connection put the following in a terminal:
sudo pppconfig
(it sould be made more easy to be found by newwbees like us)
then follow the steps. One more good think you can add directly /dev/ttySHSF0 as a modem and you can add user easyly. When you finish with the set up you just need to type:
pon MyConnection  
to connect and 
poff MyConnection
to disconnect. Of course you can set up launchers to make connectin easier 
Finnally I would like to indicate that I feel this issue injust like you as i have a winmodem in my nx9010. However this is not the fault of linux but of the providers in my case HP who does not supply linux driver.
for this reason
UBUNTU SHOULD SUPPORT WINMODEMS  OUT OF THE BOX

---

### Post by trav1085 on 2006-01-04
I have used pppconfig, I made a internet connection connected to it but any web-enabled services still won't work, I'm connected but Firefox doesn't seem to find the connection

(PS: Is there an Internet Explorer for linux)

---

### Post by ronb on 2006-01-05
[QUOTE=trav1085]I'm pretty sure I have the driver installed right, when I restart or shut down to get into windows I see "Stopping Conexant HSF softmodem -- OK" So I know it's working and running, but how do I connect and test to get a dial tone?[/QUOTE]

In your first post you said:
[QUOTE=trav1085]This is the modem I have: Conexant D480 MDC V.9x Modem
On Windows, attaached to COM3[/QUOTE]

I'm not sure that modem works with an HSF driver.  However, if you're sure that you have the correct driver and if you have not already do so, you can choose **System => Administration => Networking**.  

> Taken from **[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")**

_The Networking section of System => Administration will let you set up the ppp connection in a graphical interface. You have to know your device name, ISP phone number, username and password to set it up._ You can also use the Gnome Modem Monitor and Network Monitor panel applets if you want to stop, start and monitor modem connections without opening the Networking GUI every time. Some people have had a problem with the modem dialing during bootup. This may be related to setting the modem as default route to the internet on the Options tab of Interface properties.

Ron

---

### Post by GoodPanos on 2006-01-07
I use a Psion Dacom Gold Card Global (PCMCIA card).  Using wvdial I'm able to dial out successfully.  But I cannot browse the web no matter what.

I've enabled *Stupid mode = 0* in my /etc/wdial.conf file and also I have added the line *defaultroute* in the /etc/ppp/options file but still can't browse the Internet.

It also seems that I'm getting the same IP address everytime I'm connecting.

Any ideas?

---

### Post by GoodPanos on 2006-01-07
Correction.

I don't get the same IP address each time.  And I finally got it working.  A simple reboot is all it took.

Is there a way to make the dial tone heard?  Right now it's completely silent.

---

### Post by trav1085 on 2006-01-07
The modem is 100% correct, it's just any web-enabled application that won't work.

I guess there is no Internet Explorer for linux then?

---

### Post by trav1085 on 2006-01-07
I still know something is wrong, modem drivers and hardware are all good but it's the software, I use pppconfig to make a connection, then dial with "sudo pon MyConnection" (which works) it will stay on until I disconnect by typing "sudo poff". Just any web-enalbled application as I said won't work, in Firefox it says "Cannot find google.ca check the name" I know that means firefox can't find an internet connection or is not configured properly

---

### Post by wanger123 on 2006-01-08
```
I guess there is no Internet Explorer for linux then?
``` I sincerely hope not!!!:D

Do you just mean, is there another web browser for linux? If so, there are heaps of them (opera, firefox, mozilla, konqueror, etc)

wanger

---

### Post by trav1085 on 2006-01-08
It's working know! I'm using Mozilla Firefox in Ubuntu to post this post, I got it working using gnome-ppp, not just the terminal ppp, I don't know what made the diference but what matters is it works

-Thanks for your help

---

### Post by Finncannon on 2006-01-30
I am VERY new to linux/Ubuntu and am reluctant to do things that I don't understand.  I've been reading til my eyes are about to fall out!  But I still have a question.  I've read the dialupHowto wiki.

I've just installed Ubuntu 5.1 in a dual boot mode with XP on a Dell Inspiron 8200.  ListModem log is:
=====================================================================
=              SYSTEM INFORMATION                                   =
=====================================================================
Date         : 1/26/2006
ListMdm Ver  : 1.6
Windows OS   : Microsoft Windows XP
Build Number : 2600

=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
 PCI CONFIGURATION INFORMATION READ:
    VENDOR ID              : 8086
    DEVICE ID              : 2486
    SUBVENDOR ID           : 14F1
    SUBDEVICE ID           : 5421
    REVISION ID            : 02

 DEDUCED INFORMATION:
    VENDOR NAME            : ICH
    DEVICE NAME            : ICH3 (AC '97 MODEM)
    SUBVENDOR NAME         : ACTIONTEC                   -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/)
    MODEM TYPE             : HSF
    WINXP INBUILD SUPPORT  : NO

Do I need to follow steps 1 thru 4 of the Conexant driver install procedure if I use the driver you uploaded to the ftp site?  And which file would I use?  I assume <conexant_192-1ubuntu-1_i386.deb>.  Simple is good.  Cookbook steps would be great.

Thanks

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=Finncannon]
I've just installed Ubuntu 5.1 in a dual boot mode with XP on a Dell Inspiron 8200.  ListModem log is:
[/QUOTE]
I don't think the listmodem tool (first time I heard it) will be very helpful for you? you might want to go back to [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) and follow the instructions for "using scanmodem tool" at the top of the page.

---

### Post by Finncannon on 2006-01-30
ok, done.  Here's the text of the scanModem results:

 [COLOR="Blue"]DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_Jan_25
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:2486   Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
  SubSystem 14f1:5421  Conexant MD56ORD V.92 MDC Modem
	Flags: medium devsel, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  Intel 82801CA-ICH3

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:2486 14f1:5421 ubuntu 2.6.12-9-386  3.4.5 none    i686
              From records, 14f1:5421 has soft modem codec type CXT
 The hsfmodem drivers from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) are the ONLY support of ConeXanT codec modems under Linux!!

       
 The controller: 8086:2486 82801CA/CAM ICH3 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id identifies a ConeXanT CXTnm codec.
 Support is ONLY available the hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers)
 Low speed test drivers are free, but full speed drivers have a one time fee.
 Support is NOT available through ALSA or Smartlink modem drivers.

Checking for autoloaded ALSA modem drivers

  Driver snd-intel8x0m  may enable codec acquisition [/COLOR]

Do I correctly understand that the <conexant_192-1ubuntu-1_i386.deb> driver on the ftp site will NOT work?  I've been to the Linuxant site and there isn't a low speed test driver available to see if things work. At least I couldn't find it.  I'd like to try before I buy and I'd rather use the <conexant_192-1ubuntu-1_i386.deb> driver if possible.

Thanks.

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=Finncannon]
  SubSystem 14f1:5421  Conexant MD56ORD V.92 MDC Modem
      XT-PIC  Intel 82801CA-ICH3
              From records, 14f1:5421 has soft modem codec type CXT
 The hsfmodem drivers from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) are the ONLY support of ConeXanT codec modems under Linux!![/QUOTE]
I quoted the stuff that matters in the document AFAIK. your next step will be either to
a. go to the wiki again (link in my signature) and refer to the section called "Modems supported by the Conexant drivers" (section 7 when I was writing this); 
or
b. research to buy a smartlink chipset softmodem (or a serially connectable hard modem). I do not know how to find one as I was one of the lucky ones having an slmodem (although it only works with ubuntu). 
I think I would do the second one rather than buying the same s*** from that [bleeep] company annually... or stick with very slow dial up?

---

### Post by Finncannon on 2006-01-30
Thanks for your time.  I'll keep working!

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=Finncannon]Thanks for your time.  I'll keep working![/QUOTE]
you're most welcome. good luck, I hope you'll solve the issue as soon as possible.

---

