---
title: "facing triplex problem Feisty usb ML-1610 cups"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by ronny_d on 2007-08-11
Hi,

Does anyone in pc mode Feisty Fawn desktop version have good experience with usb#1 installed Samsung ML 1610 and on a sole pc (no laptop) as local printer (no network), even with manual feed and papersize folio, options in the simple CUPS-tool? 


.... 

There is, since manual feed, 1 folio sized clean sheet of paper waiting in the printer. 

I installed the printer rightaway, no problem via the CUPS tool and immediate detection, but the testpage is not printed, even: i cannot print anything, not even a testpage from the printer itself and a static red light is "On Line / Error".  Also the manual of this printer, does not give me a clear clue on this; i have never worked with this printer before. 



So i am here in a for me unfamiliar situation: i don't know the printer (it is brandnew and i have never worked with this printer before, so i do not know its behaviour at all) and i do not know whether it may be due to usb suspend in my pc that my usb-printer is not working... or whether it somehow is due to... CUPS... or all three.


I am clueless. I do not know this sort of stuff.  


I do 

 lpstat -p -d
printer ML-1610 now printing ML-1610-39.  enabled since za 11 aug 2007 23:48:10 CEST
        USB printer is busy; will retry in 5 seconds...
system default destination: ML-1610


Well: the command to print a testpage from the cupstool was about an hour ago...


What is wrong here? 

Is it a usb-bug in pc-version Feisty? 

Is it this printer Samsung that is not well, maybe internal fault? 

Is it CUPS?


Is it all three of them?  


I am really clueless. Please somebody who knows more about this printer and pc usb Feisty plus CUPS...: enlighten me in this.. 

 lsusb
Bus 001 Device 005: ID 04e8:3268 Samsung Electronics Co., Ltd 

There it is (the printer)

 lpinfo -v
network socket
network beh
network bluetooth
direct hpfax
direct hp
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
direct scsi
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
network smb

There it is not.  But it was there, before i gave command for printing  testpage from the CUPS tool, the Samsung printer was inthere stated as:

direct usb://Samsung/ML-1610


Worst may be is that i do not know anything about this printer, despite the manual i read. That is: it does not say much about the red light on "On Line / Error" than that a green (!) light means the printer is ready for printing...  :confused: But since i plugged in the printer's electricity cable, i have not seen any other light then this red one. 

All is plugged in: electricity cable and usb cable, all is connected and the printer is installed succesfully... but no printing at all yet. 


Is there anyone outthere familiar with all this to help me with this  for me "triplex" ... triple unfamiliar stuff in Feisty Fawn to at least indicate what might be the cause of the problem?

---

### Post by ronny_d on 2007-08-13
I cannot change the title into 'triple' instead of 'triplex'... :popcorn:


Anway: so far i found out this brandnew Samsung ML1610 printer has itself an internal error, a mistake, a fault, so the printer itself is the first cause.


driver functioning is o.k. 

(checked)


O.K., one third of this problem is solved. I have to wait for some time to receive a new same printer and hope the internal printer error is not in that one. 

If then all would work fine, it would have nothing to do with usb suspend in my pc either; but for now i cannot tell yet. I know: the printer type should work on Feisty Fawn in pc mode.

---

### Post by ronny_d on 2007-08-20
Sigh... I have another Samsung ML-1610; the first one was indeed broken. This one at least shows a green light and nowhere to be seen is the red light (like the first one only had). 

I have not installed the driver yet (though that should be done automatically without effort, this driver is in the list with the CUPS-tool via system/administration/printers). 


If i would have done so (would have installed the driver) i could test whether the usb_suspend function on pc would have any effect at all (though i hope this will not be the case).

---

### Post by ronny_d on 2007-08-21
So far, for now, i have installed the driver via system/administration/printers in the sort of automated cups and no localhost:631 issues at all necessary as for the somewhat "piece of cake"-advanced Linux-geek, and this easy cups-tool found the usb printer Samsung ML1610 without effort and the driver ML1610 for Feisty with 'gdi' language is set automatically, no need to specify any information as what this cups-program automatically sets is correct and the printer is working fine, printing well as far as i have tested in the various programs; simply set OpenOffice for example to the printer and printmode (like paper size) and OpenOffice prints out fine. It is truly very simple.

I however have now not connected my usb scanner Canon Lide 25 simultaneously, which was effected by the usb_suspend/resume-bug, but this seemed to be solved with 'scanbutond' via apt-get with sudo and then execute scanbuttond from commandline in "ordinary" usermode (pwd then so is your homedirectory, not in sudo mode).


So for now it seems that i can take a little rest and at least i have reduced the "triplex" problem with this usb printer as follows: 1) get another printer of the same brand and so i concluded the other one had an internal printer error 2) try to print testpage and print pages from other programs to see in case of this usb printer there seems to be no trace of usb_suspend/resume failure and printtasks until sofar were executed successfully  and 3) i can conclude safely that the "ultimately easy" cups-tool is working very well and in case of at least this printer choosing papersize 'folio' is possible (which i need) as too is 'manual feed'.



So for now i can really state that i am content and feeling well about Feisty Fawn about the issues above. 


I am not talking on other issues yet, because i have not yet tested or tried out this Feisty Fawn system too extensively, since i am only new to it just a couple of weeks.


For example -though then this could be something for another thread- i am not yet sure how the usb_suspend function in the scanner connected to xsane without scanbuttond could have effected some of the screensaver themes pre-installed in Feisty where it comes to black screen, or that disappearing of a particular theme screensaver is due to another cause like changing the desktop theme "look and feel" appearance or else maybe due to a hardware computer brand issue which i am not familiar with, else even due to failure in lock screensaver and via password enter again the workspace on the desktop, which kills the screensaver rather literally so it can no more be found anywhere as far as i have seen and has disappeared from the list or else is just black.


Despite all this for now, i feel content about Feisty on pc (but i do not mean to say that there may not be necessary "fixings" on deeper level because as i said: i have not yet tried out Feisty Fawn extensively yet as an "ordinary" user).   


But i am really pleased and happy for now because i can do the things i need this computer for and can pick up my work again. :KS   


Most of all i now feel relaxed with this computersystem :KS which in my opinion is an elementary necessary state for a computersystem, that is: a computersystem should not give a user any stress. I feel this computersystem, Linux Feisty Fawn Ubuntu 7.04 can invite a user to become more like a geek, but it is not necessary for a user to be a geek and all this is making me feel very relaxed towards 'my' computersystem. :KS The several Ubuntu-forums are a good initiative and very helpful as well as a place for learning on one's own computer, or can function as some "step up" in coming to know more on one's own computersystem when one is absolutely non-technical. 


This is why i feel Ubuntu could become really very powerful and build up and grow into many users from all walks of life using some flavour of Ubuntu and that all those users feel :KSrelaxed :KSwhen they are using their computer.


So the coming time i am going to try out this Feisty Fawn in as many ways as i can.

---

