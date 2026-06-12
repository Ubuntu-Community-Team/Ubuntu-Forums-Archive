---
title: "Can't install HP printer on Ubuntu 22.04"
date: 2022-08-16
forum: Hardware
---

### Post by cmalfet on 2022-08-16
[COLOR=#232629][FONT=-apple-system]I have a network HP printer at work. Recently, it dissappeared from the list of printers after some random update on Ubuntu 20.04. I decided that's it's time to upgrade to 22.04, the upgrade went very smooth, but again the printer can not be installed. hp-setup can detect the printer when I enter the IP address manually, but then either open a list of drivers which is empty and never give me any option to choose from or every few seconds give a message "hp-toolbox is not responding".[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Any ideas please??[/FONT][/COLOR]

---

### Post by Claus7 on 2022-08-16
Hello and welcome to the forums,

the recent policy of ubuntu is driverless printers: you should not install any driver for your printer to work. During my upgrade, in order for the printer to work, I had to switch it on. By doing so, then it appeared under System Settings->Printers having in its name the word localhost. When I switch off my printer, the printer disappears from that list. I have also the same printer named as usb one: this one is always in that list, yet if I try to send any documents to that one, they won't be printed. So, check out if your printer appears when you have it turned on, without attempting to search it and install it.

Regards!

---

### Post by cmalfet on 2022-08-16
Thanks for the reply. The printer is ON, however the thing is that the printer is not connected via USB, it's a network printer and it's connected to the same Ethernet network. The Printers section has no printers, it's absolutely empty. I can only press the button "Add printer". Once I click that button, I can find the printer by typing the IP address, but it can not be installed with either standard Ubuntu tools or HP tools. How do I print without drivers if Ubuntu starts to search for the drivers the very moment I choose the printer by IP address??

---

### Post by patspiper on 2022-08-16
Did you include sudo in the hp-setup command?

---

### Post by cmalfet on 2022-08-16
> **patspiper said:**
> Did you include sudo in the hp-setup command?

Yes. hp-setup windows freezes the moment it shows the printer found by the IP address and then I can only select between "Wait" or use "Force quit" :(

---

### Post by slickymaster on 2022-08-16
*Thread moved to **Hardware**.*

---

### Post by Claus7 on 2022-08-16
Hello,

I would advice you then to press Add Printer and wait, without you typing the IP address of the printer. Does it show up on its own? Normally ubuntu should find the printer itself providing you also the name of the printer. Then you could add it to your printers.

Regards!

---

### Post by brian_p on 2022-08-16
Give what you get for ```
avahi-browse -rt _ipp._tcp 
``` ```
avahi-browse -rt _uscan._tcp 
``` ```
driverless
```

---

### Post by cmalfet on 2022-08-17
> **Claus7 said:**
> Hello,

I would advice you then to press Add Printer and wait, without you typing the IP address of the printer. Does it show up on its own? 

Nope, nothing shows up. "No printers found"

---

### Post by cmalfet on 2022-08-17
> **brian_p said:**
> Give what you get for ```
avahi-browse -rt _ipp._tcp 
``` ```
avahi-browse -rt _uscan._tcp 
``` ```
driverless
```

All 3 commands gave no output :(

---

### Post by brian_p on 2022-08-17
Either the printer is not providing mDNS multcasts (Bonjour) or there isn't any connection between printer and computer. You could try ```
lpinfo -v
```

---

### Post by brian_p on 2022-08-17
Also, knowing the IP address of the printer you coud give ```
nmap ADDRESS
```

---

### Post by cmalfet on 2022-08-17
Hi Brian, thanks for the tips. Printer and computer can communicate, because I can ping the printer and because I used it for years until some recent random upgrade of Ubuntu. I know this is 100% about Ubuntu upgrade, because the same thing happened for a collegue who used the same Ubuntu version as me, but did not affect anyone else. 

lpinfo -v output was

> lpinfo: Success

nmap I already did before and it shows that printer can be detected and jetdirect port seems to be open.

> map 141.80.196.31
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2022-08-17 16:06 CEST
Nmap scan report for HP0C4C54.mdc-berlin.net (141.80.196.31)
Host is up (0.011s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
8080/tcp open  http-proxy
9100/tcp open  jetdirect


Nmap done: 1 IP address (1 host up) scanned in 0.44 seconds


---

### Post by cmalfet on 2022-08-17
Hi Brian, thanks for the tips. Printer and computer can communicate, because I can ping the printer and because I used it for years until some recent random upgrade of Ubuntu. I know this is 100% about Ubuntu upgrade, because the same thing happened for a collegue who used the same Ubuntu version as me, but did not affect anyone else. 

lpinfo -v output was

> lpinfo: Success

nmap I already did before and it shows that printer can be detected and jetdirect port seems to be open.

> 
Host is up (0.011s latency).
Not shown: 994 closed ports
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
8080/tcp open  http-proxy
9100/tcp open  jetdirect


Nmap done: 1 IP address (1 host up) scanned in 0.44 seconds


---

### Post by brian_p on 2022-08-17
I'd have expected a  bit more from the lpinfo -v output. For example, a socket (jetdirect) device.

nmap output is ok. Any firewall? Any blocking of port 5353?

---

### Post by brian_p on 2022-08-17
I am going to do a bit of guessing because the avahi-browse outputs are not available. ```
lpadmin -p testq -v ipp://IP_ADDRESS:631/ipp/print -E -m everywhere
``` can be used to set up a print queue. Does it complete without error?

---

### Post by cmalfet on 2022-08-17
> **brian_p said:**
> I'd have expected a  bit more from the lpinfo -v output. For example, a socket (jetdirect) device.
nmap output is ok. Any firewall? Any blocking of port 5353?

Hmm... I did not install any firewall or change any default network settings, that's all I can say. What does 5353 do? Is it essential for printers detection?

---

### Post by cmalfet on 2022-08-17
> **brian_p said:**
> I am going to do a bit of guessing because the avahi-browse outputs are not available. ```
lpadmin -p testq -v ipp://IP_ADDRESS:631/ipp/print -E -m everywhere
``` can be used to set up a print queue. Does it complete without error?

It says ```
lpadmin: Success
``` :) Did you expect just that or something more?

---

### Post by brian_p on 2022-08-17
> **cmalfet said:**
> Hmm... I did not install any firewall or change any default network settings, that's all I can say. What does 5353 do? Is it essential for printers detection?

Port 5353 is for mDNS/DNS-SD (Bonjur). It is used with AirPrint-capable printers, which AFAICT is on your printer.

---

### Post by brian_p on 2022-08-17
> **cmalfet said:**
> It says ```
lpadmin: Success
``` :) Did you expect just that or something more?

That was expected if the printer can be contacted to get its attributes. It looks like you should be able to print. Please try ```
lp -d testq /etc/nsswitch.conf
```

---

### Post by cmalfet on 2022-08-17
> **brian_p said:**
> Please try lp -d testq /etc/nsswitch.conf

Thank you again for the help, but this time it did not work :(

```
lp: Error - The printer or class does not exist.
```

---

### Post by brian_p on 2022-08-17
> **cmalfet said:**
> Thank you again for the help, but this time it did not work :(

```
lp: Error - The printer or class does not exist.
```

But testq has just been set up with lpadmin using the printer's known ADDRESS without any apparent error! It should be shown as installed with ```
lpstat -t
```

I am becoming even more flummoxed :confused:. There shuld be a PPD for it in /etc/cups/ppd. Is there? Give ```
grep PCFileName  /etc/cups/ppd/YOUR_PPD
```

---

### Post by cmalfet on 2022-08-17
> **brian_p said:**
> It should be shown as installed with lpstat -t

Yea, it would make sense, but... here are all outputs one after another. Hope this can help! Thank you!

```
$ lpadmin -p testq -v ipp://141.80.196.31:631/ipp/print -E -m everywhere
lpadmin: Success
$ lp -d testq /etc/nsswitch.conf
lp: Error - The printer or class does not exist.
$ lpstat -t
scheduler is running
no system default destination
lpstat: Connection reset by peer
lpstat: Bad file descriptor
lpstat: Bad file descriptor
lpstat: Success
lpstat: Connection reset by peer

```

There are lots of files in /etc/cups/ppd from 2019,2021 and 2022. One of them has correct printer name, but it's from 2021. I can open the file with sudo, but do not know what to do with it.

---

### Post by brian_p on 2022-08-17
> **cmalfet said:**
> Yea, it would make sense, but... here are all outputs one after another. Hope this can help! Thank you!

```
$ lpadmin -p testq -v ipp://141.80.196.31:631/ipp/print -E -m everywhere
lpadmin: Success
$ lp -d testq /etc/nsswitch.conf
lp: Error - The printer or class does not exist.
$ lpstat -t
scheduler is running
no system default destination
lpstat: Connection reset by peer
lpstat: Bad file descriptor
lpstat: Bad file descriptor
lpstat: Success
lpstat: Connection reset by peer

```

There are lots of files in /etc/cups/ppd from 2019,2021 and 2022. One of them has correct printer name, but it's from 2021. I can open the file with sudo, but do not know what to do with it.

I do not know what *Connection reset by peer* indicates. *Bad file descriptor* often means that the cups daemon is not running. Check with ```
systemctl status cups
```

The file you want in /etc/cups/ppd is **testq.ppd**.

---

### Post by cmalfet on 2022-08-18
> **brian_p said:**
> Check with systemctl status cups

Hi Brian, The [COLOR=#000000]cups daemon seems to be running[/COLOR]

```
$ systemctl status cups
&#9679; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: activating (start) since Thu 2022-08-18 10:36:03 CEST; 50s ago
TriggeredBy: &#9679; cups.socket
             &#9679; cups.path
       Docs: man:cupsd(8)
   Main PID: 130545 (cupsd)
      Tasks: 1 (limit: 57567)
     Memory: 16.8M
        CPU: 50.465s
     CGroup: /system.slice/cups.service
             &#9492;&#9472;130545 /usr/sbin/cupsd -l


Aug 18 10:36:03 malfet-ubuntupc systemd[1]: Starting CUPS Scheduler...
```


Unfortunately, there is no testq.ppd file in /etc/cups/ppd  It does not appear there even after I rerun lpadmin command. It reports Success, but no testq.ppd appears in /etc/cups/ppd :(

---

### Post by brian_p on 2022-08-18
> **cmalfet said:**
> 
Unfortunately, there is no testq.ppd file in /etc/cups/ppd  It does not appear there even after I rerun lpadmin command. It reports Success, but no testq.ppd appears in /etc/cups/ppd :(

Hello cmalfet,

In spite of reporting *Success* it appears lpadmin is unable to contact the printer to get a PPD. This returns us to the failure of the avahi-browse commands. You could check what the printer is providing with ```
http://141.80.196.31
``` from a browser. Look for AirPrint, Bonjour, IPP etc in the menus. 

I suppose avahi-daemon is installed? ```
dpkg -l avahi-daemon
``` The file /etc/nsswitch.conf should also have the line ```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```

---

### Post by cmalfet on 2022-08-18
Hi Brian,

Thanks so much for your time! The printer is providing Bonjour (the service is on), AirPrint (also on), WiFi Direct is active, IPP protocol appears active in Bonjour section... from the printer side everything should work just fine. In fact the printer is used by many people and works fine from Mac computers, as it used to work with Ubuntu too.[COLOR=#000000]

[/COLOR][COLOR=#000000]avahi-daemon is installed. [/COLOR][COLOR=#000000]/etc/nsswitch.conf has slightly longer line 

[/COLOR]```
hosts:          files mdns4_minimal [NOTFOUND=return] dns myhostname
```

---

### Post by brian_p on 2022-08-18
Thanks for the info, cmalfet. I haven't really any more ideas regarding your driverless printing situation. All I can say is that I have found it to work for me and other users on 22.04. Anyway, all you want to do is print! So, let's try the legacy route.

Install printer-driver-postscript-hp and get the PPD for your printer from ```
lpinfo -m | grep -i m178
``` It begins with *postscript* and ends with *ppd*. Now we need a URI. Your **lpinfo -v** from previously didn't give one. For jetdirect it should be ```
socket://141.80.196.31:9100
```. Then substitute for URI and PPD in ```
lpadmin -p testq -v URI -E -m PPD
``` and print to testq.

I has just passed through my mind to wonder whether your computer is on the same network as the printer. What does ```
ip a
``` say?

---

### Post by cmalfet on 2022-08-18
> **brian_p said:**
> I has just passed through my mind to wonder whether your computer is on the same network as the printer. 

Well, you are actually right, the printer and PC are not in the same subnet! PC's IP address is 141.80.218.32, while printer IP address 141.80.196.31. Probably this explains why the printer is invisible, but I do not understand why this was never an issue before. The printer's IP address is static and did not change over a year or more. Do you know if there is any way to force Ubuntu to look at other subnets for the printers?

---

### Post by brian_p on 2022-08-18
> **cmalfet said:**
> Well, you are actually right, the printer and PC are not in the same subnet! PC's IP address is 141.80.218.32, while printer IP address 141.80.196.31. Probably this explains why the printer is invisible, but I do not understand why this was never an issue before. The printer's IP address is static and did not change over a year or more. Do you know if there is any way to force Ubuntu to look at other subnets for the printers?

mDNS/DNS-SD will not work across subnets; therefore, no driverless printing for you. I'm glad we sorted that. However, you can ping and nmap the printer so the socket URI should work. The PC will produce a PostScript file and just shovel it to the printer. Worth a try.

---

### Post by cmalfet on 2022-08-18
Hi Brian,

Ok, thanks so much for your help and time!! I really appreciate this!

---

### Post by jeremylon on 2022-09-06
This post really helped me get mine...thx

---

