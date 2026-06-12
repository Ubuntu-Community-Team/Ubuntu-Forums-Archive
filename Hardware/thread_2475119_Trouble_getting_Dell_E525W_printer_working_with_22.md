---
title: "Trouble getting Dell E525W printer working with 22.04"
date: 2022-05-17
forum: Hardware
---

### Post by floofenstein on 2022-05-17
Hi all, Been digging around trying to get my dell E525W working on 22.04. I've pulled and installed the ubuntu drivers from the dell website (released Mey 2015) [https://www.dell.com/support/home/en-us/product-support/product/dell-e525w-printer/drivers](https://www.dell.com/support/home/en-us/product-support/product/dell-e525w-printer/drivers)

There was also a similar thread with someone having troubles with ubuntu 16 but wasn't any help.
[https://ubuntuforums.org/showthread.php?t=2341397&highlight=e525w](https://ubuntuforums.org/showthread.php?t=2341397&highlight=e525w)

It appears to be installed and recognized in the print queue but any prints get stuck in "Pending" in the active jobs queue. I had seen that some printers can get Disabled under policies which was my case. When I check the "Enabled" box in Printer Properties>Policies the Enabled box unchecks.  
[URL="https://askubuntu.com/questions/519401/printer-in-pending-mode-only-not-printing"]https://askubuntu.com/questions/519401/printer-in-pending-mode-only-not-printing
[/URL]
Current Settings:
Device URI: implicitclass://Dell_Color_MFP_E525w_E0_7D_93/
Make and Model: ell Color MFP E525w, driverless, cups-filters 1.28.15
Printer State: Stopped

Policies:
Enabled: <unchecked>
Accepting Jobs: <Checked>
Shared: <unchecked>
Error Policy: Retry Job
Operation Policy: Default

Access Control: Allow All

Ink/Toner Levels: Printer 'Dell_Color_MFP_E525w_E0_7D-93':'cups-pki-expired'

The cups-pki-expired note was mentioned in this thread. I tried adding AllowExpiredCerts under Job Options which added another instance of the printer but that version of the printer is stuck in Stopped state and doesn't do anything after you restart it.: 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1886653](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1886653)

I've futzed around a bit more but haven't made any more progress. Any hints or suggestions?

---

### Post by brian_p on 2022-05-18
Provide ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```  ```
driverless
``` ```
lpstat -t
```

---

### Post by floofenstein on 2022-05-19
> **brian_p said:**
> Provide ```
avahi-browse -rt _ipp._tcp
``` 
:~$ avahi-browse -rt _ipp._tcp
+ enxcc483aa52797 IPv6 Dell Color MFP E525w (E0:7D:93)               Internet Printer     local
+ enxcc483aa52797 IPv4 Dell Color MFP E525w (E0:7D:93)               Internet Printer     local
= enxcc483aa52797 IPv6 Dell Color MFP E525w (E0:7D:93)               Internet Printer     local
   hostname = [DELLE07D93.local]
   address = [xxx.xxx.xxx.xxx]
   port = [xxx]
   txt = ["rfo=ipp/faxout" "kind=document,envelope" "PaperMax=legal-A4" "air=none" "TLS=1.2" "Scan=T" "Fax=T" "Duplex=F" "Color=T" "URF=W8,SRGB24,RS200-600,PQ3-4-5,IS1-4-20,MT1-3-4-5,CP1,OB10,IFU0,V1.4" "UUID=00000001-0000-1000-8000-080037e07d93" "TBCP=T" "Binary=T" "usb_MDL=Dell Color MFP E525w" "usb_MFG=Dell" "adminurl=http://DELLE07D93.local./setting/setairprint.asp" "pdl=application/postscript,application/pdf,image/urf,image/jpeg,application/vnd.hp-PCLXL,application/vnd.hp-PCL" "product=(Dell Color MFP E525w)" "ty=Dell Color MFP E525w" "priority=40" "qtotal=1" "rp=ipp/print" "note=" "txtvers=1"]
= enxcc483aa52797 IPv4 Dell Color MFP E525w (E0:7D:93)               Internet Printer     local
   hostname = [DELLE07D93.local]
   address = [xxx.xxx.xxx.xxx]
   port = [xxx]
   txt = ["rfo=ipp/faxout" "kind=document,envelope" "PaperMax=legal-A4" "air=none" "TLS=1.2" "Scan=T" "Fax=T" "Duplex=F" "Color=T" "URF=W8,SRGB24,RS200-600,PQ3-4-5,IS1-4-20,MT1-3-4-5,CP1,OB10,IFU0,V1.4" "UUID=00000001-0000-1000-8000-080037e07d93" "TBCP=T" "Binary=T" "usb_MDL=Dell Color MFP E525w" "usb_MFG=Dell" "adminurl=http://DELLE07D93.local./setting/setairprint.asp" "pdl=application/postscript,application/pdf,image/urf,image/jpeg,application/vnd.hp-PCLXL,application/vnd.hp-PCL" "product=(Dell Color MFP E525w)" "ty=Dell Color MFP E525w" "priority=40" "qtotal=1" "rp=ipp/print" "note=" "txtvers=1"]


```
avahi-browse -rt _uscan._tcp
```

:~$ avahi-browse -rt _uscan._tcp
+ enxcc483aa52797 IPv4 Dell Color MFP E525w (E0:7D:93)               _uscan._tcp          local
= enxcc483aa52797 IPv4 Dell Color MFP E525w (E0:7D:93)               _uscan._tcp          local
   hostname = [DELLE07D93.local]
   address = [xxx.xxx.xxx.xxx]
   port = [xxx]
   txt = ["duplex=F" "is=platen,adf" "cs=color,grayscale" "UUID=00000001-0000-1000-8000-080037e07d93" "pdl=application/pdf,image/jpeg" "note=" "ty=Dell Color MFP E525w" "rs=eSCL" "representation=http://DELLE07D93.local./images/pr_icon128.png" "adminurl=http://DELLE07D93.local./setting/setairprint.asp" "vers=2.5" "txtvers=1"]
+ enxcc483aa52797 IPv6 Dell Color MFP E525w (E0:7D:93)               _uscan._tcp          local
= enxcc483aa52797 IPv6 Dell Color MFP E525w (E0:7D:93)               _uscan._tcp          local
   hostname = [DELLE07D93.local]
   address = [xxx,xxx,xxx,xxx]
   port = [xxx]
   txt = ["duplex=F" "is=platen,adf" "cs=color,grayscale" "UUID=00000001-0000-1000-8000-080037e07d93" "pdl=application/pdf,image/jpeg" "note=" "ty=Dell Color MFP E525w" "rs=eSCL" "representation=http://DELLE07D93.local./images/pr_icon128.png" "adminurl=http://DELLE07D93.local./setting/setairprint.asp" "vers=2.5" "txtvers=1"]



  ```
driverless
``` 

:~$ driverless
ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps._tcp.local/


```
lpstat -t
```

:~$ lpstat -t
scheduler is running
system default destination: Dell_Color_MFP_E525w_E0_7D_93
device for Dell_Color_MFP_E525w_E0_7D_93: implicitclass://Dell_Color_MFP_E525w_E0_7D_93/
device for [EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL]: implicitclass://Dell_Color_MFP_E525w_E0_7D_93%40DELLE07D93.local/
Dell_Color_MFP_E525w_E0_7D_93 accepting requests since Tue 17 May 2022 09:21:33 AM MDT
[EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL] accepting requests since Thu 19 May 2022 08:42:29 AM MDT
printer Dell_Color_MFP_E525w_E0_7D_93 disabled since Tue 17 May 2022 09:21:33 AM MDT -
    No destination host name supplied by cups-browsed for printer "Dell_Color_MFP_E525w_E0_7D_93", is cups-browsed running?
printer [EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL] is idle.  enabled since Thu 19 May 2022 08:42:29 AM MDT

---

### Post by floofenstein on 2022-05-19
```
lpstat -t
```[/QUOTE]

:~$ lpstat -t
scheduler is running
system default destination: Dell_Color_MFP_E525w_E0_7D_93
device for Dell_Color_MFP_E525w_E0_7D_93: implicitclass://Dell_Color_MFP_E525w_E0_7D_93/
device for [EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL]: implicitclass://Dell_Color_MFP_E525w_E0_7D_93%40DELLE07D93.local/
Dell_Color_MFP_E525w_E0_7D_93 accepting requests since Tue 17 May 2022 09:21:33 AM MDT
[EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL] accepting requests since Thu 19 May 2022 08:42:29 AM MDT
printer Dell_Color_MFP_E525w_E0_7D_93 disabled since Tue 17 May 2022 09:21:33 AM MDT -
    No destination host name supplied by cups-browsed for printer "Dell_Color_MFP_E525w_E0_7D_93", is cups-browsed running?
printer [EMAIL="Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local"]Dell_Color_MFP_E525w_E0_7D_93@DELLE07D93.local[/EMAIL] is idle.  enabled since Thu 19 May 2022 08:42:29 AM MDT

---

### Post by brian_p on 2022-05-19
The problem here is

> printer Dell_Color_MFP_E525w_E0_7D_93 disabled since Tue 17 May 2022 09:21:33 AM MDT -
No destination host name supplied by cups-browsed for printer "Dell_Color_MFP_E525w_E0_7D_93", is cups-browsed running?

For some reason, cups-browsed is not behaving itself . I am not prepared to debug it. It is easier (and just as good) to set up a print queue manually.

Execute
```
lpadmin -p E525W -v "ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps. _tcp.local/" -E -m everywhere
```

Test printing with ```
lp -d E525W /etc/nsswitch.conf
```

How's that?

---

### Post by floofenstein on 2022-05-23
Kicking out lpadmin: Bad device-uri

:/# lpadmin -p E525W -v "ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps. _tcp.local/" -E -m everywhere
lpadmin: Bad device-uri "ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps. _tcp.local/".

---

### Post by brian_p on 2022-05-23
> **floofenstein said:**
> Kicking out lpadmin: Bad device-uri

:/# lpadmin -p E525W -v "ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps. _tcp.local/" -E -m everywhere
lpadmin: Bad device-uri "ipps://Dell%20Color%20MFP%20E525w%20(E0%3A7D%3A93)._ipps. _tcp.local/".

You provided the URI. Try ```
ipp://xxx.xxx.xxx.xxx/ipp/print
``` or ```
ipp://DELLE07D93.local/ipp/print
```

---

### Post by floofenstein on 2022-05-23
Really weird, I hand jammed the command you gave me with the output from driverless and it worked, copying and pasting your code above gave the error.

It added E525Q to the print devices gui, says "Stopped please restart when the problem is resolved." Tried restarting
Status Messages:
Printer 'E525W':'cups-pki-expired'
Printer 'E525W':'paused'

I did try adding AllowExpiredCerts true to the config

journalctl | grep "cups"
May 23 08:46:44 xxxx systemd[1]: cups-browsed.service: Deactivated successfully.
May 23 08:46:44 xxxx systemd[1]: cups.service: Deactivated successfully.
May 23 08:46:44 xxxx systemd[1]: cups.path: Deactivated successfully.
May 23 08:46:44 xxxx systemd[1]: cups.socket: Deactivated successfully.
May 23 08:46:44 xxxx gsd-color[5614]: failed to connect to device: Failed to connect to missing device /org/freedesktop/ColorManager/devices/cups_Dell_Color_MFP_E525w_E0_7D_93
May 23 08:46:44 xxxx audit[641055]: AVC apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=641055 comm="cupsd" capability=12  capname="net_admin"
May 23 08:46:44 xxxx kernel: audit: type=1400 audit(1653317204.184:3806): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=641055 comm="cupsd" capability=12  capname="net_admin"
May 23 08:46:44 xxxx audit[641071]: AVC apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=641071 comm="cups-browsed" capability=23  capname="sys_nice"
May 23 08:46:44 xxxx kernel: audit: type=1400 audit(1653317204.200:3807): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=641071 comm="cups-browsed" capability=23  capname="sys_nice"
May 23 17:24:46 xxxx hpfax[962732]: [962732]: error: Failed to create /var/spool/cups/tmp/.hplip

---

### Post by floofenstein on 2022-05-23
installed apparmor-utils
aa-complain cupsd
tried another print and still stuck

May 23 17:38:28 xxxx audit[973038]: AVC apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=973038 comm="apparmor_parser"
May 23 17:38:28 xxxx kernel: audit: type=1400 audit(1653349108.974:4006): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=973038 comm="apparmor_parser"
May 23 17:38:28 xxxx audit[973038]: AVC apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=973038 comm="apparmor_parser"
May 23 17:38:28 xxxx kernel: audit: type=1400 audit(1653349108.978:4007): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=973038 comm="apparmor_parser"
May 23 17:38:29 xxxx audit[973038]: AVC apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=973038 comm="apparmor_parser"
May 23 17:38:29 xxxx kernel: audit: type=1400 audit(1653349109.002:4008): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=973038 comm="apparmor_parser"

---

