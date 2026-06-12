---
title: "Setting up my canon mx922 all-in-one"
date: 2022-05-16
forum: Hardware
---

### Post by jpjones55 on 2022-05-16
Hello all.  I'm trying to use Kubuntu 22.04. Now I've read and tried all the different setup scenarios on these forums and nothing is working.  Albeit that these setup scenarios are like 5 or 6 years old.  Does anyone have a more recent set of instructions to guide me along to set this printer up before I move on to another OS?  I really like ubuntu but if I can't use this printer, then what's the point? 

My machine is an older Samsung RC512, about 11-12 years old, but still runs fine, with a 600gb hd and maxed out at 8bg ram.

So, any advise or suggestions will be appreciated.

John Paul

---

### Post by brian_p on 2022-05-16
> **jpjones55 said:**
> Hello all.  I'm trying to use Kubuntu 22.04. Now I've read and tried all the different setup scenarios on these forums and nothing is working.  Albeit that these setup scenarios are like 5 or 6 years old.  Does anyone have a more recent set of instructions to guide me along to set this printer up before I move on to another OS?  I really like ubuntu but if I can't use this printer, then what's the point? 

My machine is an older Samsung RC512, about 11-12 years old, but still runs fine, with a 600gb hd and maxed out at 8bg ram.

So, any advise or suggestions will be appreciated.

John Paul

USB? Wireless?

Give ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
``` 
```
driverless
```
```
lpstat -t
```

---

### Post by jpjones55 on 2022-05-16
> USB? Wireless?

Wireless. 

[FONT=monospace][COLOR=#000000]avahi-browse -rt _ipp._tcp   returns:[/COLOR][/FONT]
> [FONT=monospace][COLOR=#54ff54]**ohn@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ avahi-browse -rt _ipp._tcp   [/COLOR]
+ wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
= wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
   hostname = [3DA251000000.local] 
   address = [192.168.1.162] 
   port = [631] 
   txt = ["mac=F4:A9:97:3D:A2:51" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "URF=V1.2,CP1,PQ4-5,RS600,SRGB24,W8,OB
9,OFU0,DM3,IS11-13" "UUID=00000000-0000-1000-8000-F4A9973DA251" "usb_CMD=URF" "usb_MDL=MX920 series" "usb_MFG=
Canon" "adminurl=http://3DA251000000.local./mainmenu.html" "pdl=application/octet-stream,image/urf,image/jpeg"
 "product=(Canon MX920 series)" "ty=Canon MX920 series" "priority=15" "qtotal=1" "note=" "rp=ipp/print" "txtve
rs=1"][/FONT]

avahi-browse -rt _uscan._tcp returns"
> [FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ avahi-browse -rt _uscan._tcp [/COLOR]
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT]


driverless returns:
> [FONT=monospace][FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ driverless [/COLOR]
ipp://Canon%20MX920%20series._ipp._tcp.local/
[/FONT][/FONT][FONT=monospace]

lpstat -t returns:
[/FONT][FONT=monospace][FONT=monospace]> [FONT=monospace][FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpstat -t [/COLOR]
scheduler is running 
no system default destination 
lpstat: No destinations added. 
lpstat: No destinations added. 
lpstat: No destinations added. 
lpstat: No destinations added.
[/FONT][/FONT]

So what were we checking here?

Thanks
john

[/FONT]

[/FONT]

---

### Post by brian_p on 2022-05-16
> **jpjones55 said:**
> Wireless. 

So what were we checking here?



The output for the first command shows the printer is v1.2 AirPrint-capable. It should be auto-setup but the foutth command shows that hasn't happened. Let's try a manual setup. Execute

```
lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere
```

Test printing with

```
lp -d mx922 /etc/nsswitch.conf
```

---

### Post by jpjones55 on 2022-05-17
Thanks Brian.  I was going to re-install kubuntu to have a clean slate to work on, but I put the xubuntu usb in, but It should be the same difference, right?  x wouldn't finish the installation correctly for some reason, so I just re-installed k.

I'll try all these commands again once it's installed.  Oh, and what about the drivers everyone says you have to install, like from the canon asia site and all?  or we're doing first things first?

John

---

### Post by jpjones55 on 2022-05-17
```
lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere 
```

no output


Test printing with

```
lp -d mx922 /etc/nsswitch.conf 
```

output: ```
[FONT=monospace][COLOR=#000000]request id is mx922-1 (1 file(s))[/COLOR][/FONT]
```

But no test print.
Printer is listed in printers - system setting, but has an error after trying to send a test print:
> MX922
in use - "unable to locate printer 3DA251000000.local"


John

---

### Post by brian_p on 2022-05-17
> **jpjones55 said:**
> ```
lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere 
```

no output

That's OK. The command completed successfully.


> MX922
in use - "unable to locate printer 3DA251000000.local" 

This looks like a network error. The previous avahi-browse command found the printer easily enough. Try ```
nmap 3DA251000000.local
```

---

### Post by jpjones55 on 2022-05-17
Here's the result of that:

> [FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ nmap 3DA251000000.local [/COLOR]
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2022-05-17 11:15 EDT 
Failed to resolve "3DA251000000.local". 
WARNING: No targets were specified, so 0 hosts scanned. 
Nmap done: 0 IP addresses (0 hosts up) scanned in 0.15 seconds
[/FONT]

---

### Post by jpjones55 on 2022-05-17
Brian, do I need to install any of those mx920 series drivers?

Thanks,
john

---

### Post by brian_p on 2022-05-17
Hello John,

You also reran ```
avahi-browse -rt _ipp._tcp
```

> Failed to resolve "3DA251000000.local"

Is libnss-mdns installed? ```
dpkg -l libnss-mdns
```

---

### Post by brian_p on 2022-05-17
> **jpjones55 said:**
> Brian, do I need to install any of those mx920 series drivers?

Thanks,
john

The Canon drivers are not needed with an AirPrint device.

---

### Post by jpjones55 on 2022-05-17
here's those results"

```
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ avahi-browse -rt _ipp._tcp [/COLOR]
+ wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
= wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
   hostname = [3DA251000000.local] 
   address = [192.168.1.162] 
   port = [631] 
   txt = ["mac=F4:A9:97:3D:A2:51" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "URF=V1.2,CP1,PQ4-5,RS600,SRGB24,W8,OB
9,OFU0,DM3,IS11-13" "UUID=00000000-0000-1000-8000-F4A9973DA251" "usb_CMD=URF" "usb_MDL=MX920 series" "usb_MFG=
Canon" "adminurl=http://3DA251000000.local./mainmenu.html" "pdl=application/octet-stream,image/urf,image/jpeg"
 "product=(Canon MX920 series)" "ty=Canon MX920 series" "priority=15" "qtotal=1" "note=" "rp=ipp/print" "txtve
rs=1"] 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dpkg -l libnss-mdns [/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name              Version         Architecture Description 
+++-=================-===============-============-============================================ 
ii  libnss-mdns:amd64 0.15.1-1ubuntu1 amd64        NSS module for Multicast DNS name resolution 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

---

### Post by brian_p on 2022-05-17
> **jpjones55 said:**
> here's those results"

```
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ avahi-browse -rt _ipp._tcp [/COLOR]
+ wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
= wlp1s0 IPv4 Canon MX920 series                            Internet Printer     local 
   hostname = [3DA251000000.local] 
   address = [192.168.1.162] 
   port = [631] 
   txt = ["mac=F4:A9:97:3D:A2:51" "Fax=F" "Scan=T" "Duplex=T" "Color=T" "URF=V1.2,CP1,PQ4-5,RS600,SRGB24,W8,OB
9,OFU0,DM3,IS11-13" "UUID=00000000-0000-1000-8000-F4A9973DA251" "usb_CMD=URF" "usb_MDL=MX920 series" "usb_MFG=
Canon" "adminurl=http://3DA251000000.local./mainmenu.html" "pdl=application/octet-stream,image/urf,image/jpeg"
 "product=(Canon MX920 series)" "ty=Canon MX920 series" "priority=15" "qtotal=1" "note=" "rp=ipp/print" "txtve
rs=1"] 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dpkg -l libnss-mdns [/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name              Version         Architecture Description 
+++-=================-===============-============-============================================ 
ii  libnss-mdns:amd64 0.15.1-1ubuntu1 amd64        NSS module for Multicast DNS name resolution 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

There you are: ```
 hostname = [3DA251000000.local] 
```

resolves to

```
address = [192.168.1.162]
```

In other words, 3DA251000000.local is equivalent to 192.168.1.162.

Let us change the lpadmin command to

```
lpadmin -p mx922 -v ipp://192.168.1.162/ipp/print -E -m everywhere
```

No resolution is involved because the IP address is given.

Print as before:

```
lp -d mx922 /etc/nsswitch.conf
```

---

### Post by jpjones55 on 2022-05-17
Brian it still won't print the test page

```
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpadmin -p mx922 -v ipp://192.168.1.162/ipp/print -E -m everywhere [/COLOR]
lpadmin: Success 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lp -d mx922 /etc/nsswitch.conf [/COLOR]
request id is mx922-6 (1 file(s)) 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]


[/FONT]
```

---

### Post by brian_p on 2022-05-17
Both commands complete.

Sorry, I have nothing more to give  to help easily towards a solution.

---

### Post by jpjones55 on 2022-05-18
ok, I thank you for your help

John

---

### Post by brian_p on 2022-05-18
> **jpjones55 said:**
> ok, I thank you for your help

John

The two commands we have used are as basic as it gets. Let's see if a debugging technique is of use:

```
sudo cupsfilter -p /etc/cups/ppd/mx922.ppd -m printer/foo -e /etc/nssitch > out.urf 2> log.txt
```

Post log.txt. You may view it with ```
less log.txt
```.

---

### Post by jpjones55 on 2022-05-18
Thanks Brian.  Well, I'm installing xubuntu right now.  Had to fix some stuff on my win10 machine so I could burn the iso.  I use poweriso and something corrupted it, had to uninstall reboot reinstall and finally it worked again correctly,.  Once xubuntu is installed I'll re run all the commands you listed and see what happens and definitely let you know what's happening.

john

---

### Post by jpjones55 on 2022-05-18
here's the contents of the log.txt file:

```
cupsfilter: Unable to open PPD file: Unable to open PPD file on line 0.
cupsfilter: Unable to determine MIME type of "/etc/nssitch".
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)



```

---

### Post by brian_p on 2022-05-18
> **jpjones55 said:**
> here's the contents of the log.txt file:

cupsfilter: Unable to open PPD file: Unable to open PPD file on line 0.
cupsfilter: Unable to determine MIME type of "/etc/nssitch".

Does  /etc/cups/ppd/mx922.ppd exist?

```
ls -l /etc/cups/ppd/mx922.ppd/
```

One of the previous lpadmin commands has to be used to create it.

I made a typo. nssitch should be nsswitch..

---

### Post by jpjones55 on 2022-05-19
Does  /etc/cups/ppd/mx922.ppd exist?

          ```
ls -l /etc/cups/ppd/mx922.ppd/
```

Returns:[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/mx922.ppd/ [/COLOR]
ls: cannot access '/etc/cups/ppd/mx922.ppd/': No such file or directory


[/FONT]

---

### Post by brian_p on 2022-05-19
I appear to have intoduced some typos :(. We'll start again.

Set up a print queue as before: ```
lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere
```

Test printing with
```
lp -d mx922 /etc/nsswitch.conf
```

If that does not work, do

```
sudo cupsfilter -p /etc/cups/ppd/mx922.ppd -m printer/foo -e /etc/nsswitch.conf > out.urf 2> log.txt
```

and post log.txt.

Check existance of the PPD with ```
ls -l /etc/cups/ppd/mx922.ppd
```

---

### Post by jpjones55 on 2022-05-19
Here's the output of those commands:
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere [/COLOR]
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lp -d mx922 /etc/nsswitch.conf [/COLOR]
request id is mx922-12 (1 file(s)) 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo cupsfilter -p /etc/cups/ppd/mx922.ppd -m printer/foo -e /etc/nsswitch.conf > out.urf 2[/COLOR]
> log.txt 
[sudo] password for john:  
Segmentation fault 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/mx922.ppd [/COLOR]
ls: cannot access '/etc/cups/ppd/mx922.ppd': No such file or directory 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

Thanks, man
john
[/FONT]

---

### Post by jpjones55 on 2022-05-19
I have to go to the dr's office.  be back in a couple of hours.

thanks,
john

---

### Post by brian_p on 2022-05-19
> **jpjones55 said:**
> Here's the output of those commands:
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere [/COLOR]
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lp -d mx922 /etc/nsswitch.conf [/COLOR]
request id is mx922-12 (1 file(s)) 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo cupsfilter -p /etc/cups/ppd/mx922.ppd -m printer/foo -e /etc/nsswitch.conf > out.urf 2[/COLOR]
> log.txt 
[sudo] password for john:  
Segmentation fault 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/mx922.ppd [/COLOR]
ls: cannot access '/etc/cups/ppd/mx922.ppd': No such file or directory 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

Thanks, man
john
[/FONT]

I am stumped! The lpadmin command completes without error so it should have generated mx922.ppd. What about ```
ls -l /etc/cups/ppd/
```

---

### Post by jpjones55 on 2022-05-19
[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/ [/COLOR]
total 0



[/FONT]

---

### Post by brian_p on 2022-05-19
> **jpjones55 said:**
> [FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/ [/COLOR]
total 0



[/FONT]

In the light of what we had before, this makes sense. But it should not happen.

Please run this command:

```
driverless cat  ipp://Canon%20MX920%20series._ipp._tcp.local/ > mx922.ppd
```

Give ```
ls -l mx922.ppd
```

I do not want to see the whole file (yet) but you can view it with ```
less mx922.ppd
```

Give the lines with ***NickName** and ***cupsFilter2**.

---

### Post by jpjones55 on 2022-05-19
Brian, here's the last few commands I've run.  This is a brand new install of kbuntu 22.04

[FONT=monospace][COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpadmin -p mx922 -v ipp://192.168.1.162/ipp/print -E -m everywhere [/COLOR]
lpadmin: Success 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lp -d mx922 /etc/nsswitch.conf [/COLOR]
lp: Error - The printer or class does not exist. 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/cups/ppd/mx922.ppd/ [/COLOR]
ls: cannot access '/etc/cups/ppd/mx922.ppd/': No such file or directory 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lpadmin -p mx922 -v ipp://Canon%20MX920%20series._ipp._tcp.local/ -E -m everywhere [/COLOR]
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lp -d mx922 /etc/nsswitch.conf [/COLOR]
request id is mx922-2 (1 file(s)) 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ driverless cat  ipp://Canon%20MX920%20series._ipp._tcp.local/ > mx922.ppd [/COLOR]
DEBUG2: get-printer-attributes: Cannot connect to printer with URI ipp://3DA251000000.local:631/ipp/print. 
DEBUG2:  
ERROR: Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Canon%20MX
920%20series._ipp._tcp.local/, ipp://3DA251000000.local:631/ipp/print) via IPP! 
[COLOR=#54ff54]**john@john-RC512**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ driverless cat ipp://Canon%20MX920%20series._ipp._tcp.local/ > mx922.ppd  [/COLOR]
DEBUG2: get-printer-attributes: Cannot connect to printer with URI ipp://3DA251000000.local:631/ipp/print. 
DEBUG2:  
ERROR: Unable to create PPD file: Could not poll sufficient capability info from the printer (ipp://Canon%20MX
920%20series._ipp._tcp.local/, ipp://3DA251000000.local:631/ipp/print) via IPP!


[/FONT]

---

### Post by jpjones55 on 2022-05-19
I got the printer where it says its ready, send a test print to it, it shows in the que and gone like it printed.  My printer woke up when I sent to first test, but no actual print took place.   hhhhmmmm.

thanks
john

---

### Post by jpjones55 on 2022-05-20
Brian I got it printing by changing the connection to this:
```
ipp://192.168.1.162:631/ipp/print
```
and changing the driver from auto to custom driver:
```
current - CanonMX920 series,driverless,cups-filters 1.28.15
```

BUT it's just printing from the 4x6 photopaper tray, not the 8.5x11 bottom tray where it should be printing from.  In the gui - system center - printers, under config, there's no option for regular paper, it's all photo paper choices.  At least we're making some hen way here...lol

thanks,
john

---

### Post by brian_p on 2022-05-20
> **jpjones55 said:**
> Brian I got it printing by changing the connection to this:
```
ipp://192.168.1.162:631/ipp/print
```

Hello John Paul,

Good. This is probably what got printing going.
> 
and changing the driver from auto to custom driver:
```
current - CanonMX920 series,driverless,cups-filters 1.28.15
```

BUT it's just printing from the 4x6 photopaper tray, not the 8.5x11 bottom tray where it should be printing from.  In the gui - system center - printers, under config, there's no option for regular paper, it's all photo paper choices.  At least we're making some hen way here...lol

thanks,
john

It seems to me you have multiple issues. The main one seems to have been worked round. Where you go from here is beyond my skills.

---

### Post by jpjones55 on 2022-05-20
Thanks for your help Brian.  But now I just did a fresh install of ubuntu 22.04.  Everytime I try something it just adds another mx922 to the printer list.  I'll try to start from scratch and use the command line like you were showing me.  Don't close this thread yet so I can let you know how it went.

JP

---

### Post by jpjones55 on 2022-05-21
Gooday Brian.  Good news on the mx922 issue(s).  I was down to trying my last distro (linux mint cinnamon) and dang if it didn't work right out the box?  mint had the gutenprint drivers as part of the distro.  So, I used that to configure kubuntu (which I really like) and viola! I got it printing in color AND scanning with xsane and GIMP, although there's a bug in the gimp-plugin.  but I found a guy on one of the forums that had re-engineered it for his own use and had it for a download to put in the gimp plugin folder.  

So now I got kbuntu 22.04 setup how I want it with the printing and scanning.  Now on the setup the network so I can access my win10 pro machine.  It has my whole life on it it seems!

Brian I don't know how to thank you enough for you time and effort. I've learned alot this past week about ubuntu printing and all.

Thanks and cheers,
jp

---

### Post by brian_p on 2022-05-21
John Paul,

After a long journey there is nothing more satisfying than to reach its end safely. I am glad to have assisted you along the way, hopefully without giving too many erroneous directions. You have been assiduous and persistent. Enjoy your OS and its printing and scanning.

---

### Post by TheFu on 2022-05-23
Would really help the community if you used the _Thread Tools_ button and marked the thread as "**SOLVED**" so people don't waste time.

Switching distros isn't something most people would do, though there is nothing wrong with the Mint desktops, provided that's what you want with the support you want.

---

