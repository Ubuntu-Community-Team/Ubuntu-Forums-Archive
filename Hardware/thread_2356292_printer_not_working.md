---
title: "printer not working"
date: 2017-03-21
forum: Hardware
---

### Post by jarp53 on 2017-03-21
i had problems with my printer before with not being able to scan but that was fix two weeks ago <  [https://ubuntuforums.org/showthread.php?t=2355175](https://ubuntuforums.org/showthread.php?t=2355175)  > and now i went to print and i get error that said " the queue is not enable " so i open the settings >printer and that menu enable is check but is faded , in fact everything is faded except " view print queue'; i try "find printer" but system can not find it  ; i'm able to scan so i know the connection is ok .  So any ideas as to what to do ?

---

### Post by pdc on 2017-03-22
1) please open your **PRINTERS** folder;         ...... use your DASH function to find it if you can't ............

2) tell us how many printers icons there are in that folder please

3) If only one, please RIGHT-CLICK on it, and select **PROPERTIES**           (we are talking about a Brother MFC-5890CN, is that correct?)

4) The window should say **SETTINGS** so come down to the third line to **Device URI**: and please copy what is there; and paste it back here

5) Go one line down to **MAKE & MODEL** and please copy that line; in its entirety and paste it also back here for us to read;

thank you

---

### Post by jarp53 on 2017-03-22
Device URI --usb://Brother/MFC-5890CN?serial=BROE0F358610
MAKE & MODEL---Brother MFC-5890CN CUPS v1.1
Printer State---Idle - File "/usr/lib/cups/backend/usb" not available: No such file or directory

---

### Post by pdc on 2017-03-22
tell us what version of Ubuntu you are using: I see ```
Brother MFC-5890CN CUPS v1.1
``` and I am wondering what that refers to: for example, our version of cups is cups 2.1.3-4

____________

from such posts as this [https://bbs.archlinux.org/viewtopic.php?id=202925](https://bbs.archlinux.org/viewtopic.php?id=202925) where the same error message as yours was quoted ```
File "/usr/lib/cups/backend/usb" not available: No such file or directory 
```, it was commented that "*/usr/lib/cups/backend/usb is owned by libcups which is a dependency of cups and many softwares. Without this file cups cannot acces USB printer*."

so you need to check if you have libcups installed; on our system, if I run ```
dpkg -l libcups*
```. which is asking debian package manager to LIST all versions of libcups on the system ........ I get quite a few .... all version 2.1.3-4 ....... what about you?

---

### Post by jarp53 on 2017-03-22
i have Ubuntu 16.04 LTS;  
jr@jr-Z68X-UD3H-B3:~$ dpkg -l libcups*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libcups2:amd64 2.1.3-4      amd64        Common UNIX Printing System(tm) -
ii  libcupscgi1:am 2.1.3-4      amd64        Common UNIX Printing System(tm) -
ii  libcupsfilters 1.8.3-2ubunt amd64        OpenPrinting CUPS Filters - Share
ii  libcupsimage2: 2.1.3-4      amd64        Common UNIX Printing System(tm) -
ii  libcupsmime1:a 2.1.3-4      amd64        Common UNIX Printing System(tm) -
ii  libcupsppdc1:a 2.1.3-4      amd64        Common UNIX Printing System(tm) -
jr@jr-Z68X-UD3H-B3:~$

---

### Post by jarp53 on 2017-03-23
i try to reinstall my drivers that had work a couple of weeks ago , but i think that the changing of all those files when i try to install the scanner drivers mess something up ; so now as i'm reinstalling i get this 
lpinfo: cups-devicedfailed to execute.
lpadmin: Baddevice-uri scheme "usb".
################################
lpinfo: cups-devicedfailed to execute.


0 (I): Specify IPaddress.
1 (A): Auto.(usb://dev/usblp0)


select the number ofdestination Device URI. ->1


lpadmin -p MFC5890CN-v usb://dev/usblp0 -E -P /usr/share/cups/model/brmfc5890cn.ppd
lpadmin: Baddevice-uri scheme "usb".

 i try both options, i specify from my printer which was 000.000.000 but that turn out to be an invalid address ; and option 1- is giving me this error

---

### Post by pdc on 2017-03-23
there is a lot of badness about ............... on your computer ........ eg ...........

```
File "/usr/lib/cups/backend/usb" not available: No such file or directory
``` /usr/lib/cups/backend/usb is owned by libcups which is a dependency of cups and many softwares. **Without this file cups cannot access USB printer.**

```
lpadmin: Baddevice-uri scheme "usb".
```

I suspect if libcups was doing all the right things, that /usr/lib/cups/backend/usb would be available; and things might work; some might suggest deleting and reinstalling libcups; but I will keep away from recommending such; as I fear the long journey to get you out of any further swamps you fall in; some reading the thread must wonder how /usr/lib/cups/backend/usb ended up disappearing; do you remember deleting and reinstalling cups at some stage? Just curious what journeys your computer may have been on

---

### Post by jarp53 on 2017-03-24
good news problem solved ; i uninstall cups and install  2 packages of " cupswrapp " that came in the downloads from brothers , then i reinstall cups , then ion printer i added new printer and deleted the old one ; and now i have both scanner and printer working , but i don't know how because at the drivers installation i was always getting the uri errors , so idont know unless there was a fix after all the reports being send automatically  what ever the case PROBLEM SOLVED !!!!!!!!!  THANKS FOR ALL YOUR HELP

---

### Post by pdc on 2017-03-24
that's great; glad you got ahead and did that; we learn too from what worked for you; 

as it is your thread, you can mark it as solved in the thread tools; top right; glad that the Brother printer and scanner drivers are working well; (Brother will be relieved too!)

"and now i have both scanner and printer working , but i don't know how" one would suspect libcups now has ownership of the files it needs; to send messages to and from your usb ports to the printer/scanner

---

