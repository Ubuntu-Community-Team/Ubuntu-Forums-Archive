---
title: "Brother MFC-7460 Scanner Stopped Working"
date: 2014-09-22
forum: Hardware
---

### Post by webmanoffesto on 2014-09-22
In the past I managed to get my Brother MFC-7460 Printer and Scanner working. Right now the printer works but not the scanner. Brother seems to have done an excellent job providing drivers, documentation, and even a Driver Install Tool you run from the command line. I reinstalled the drivers, that didn't help. I ran their Driver Install Tool, still not working. Neither **Simple Scan** or **XSane** work. 
Error Message from XSane:
"Failed to start scanner: Invalid argument"

XSane says
xsane 0.998 MFC-7460DN:bus2:dev1
on it's top menu bar. Maybe that's relevant.

My earlier struggles with the scanner can be found here: [http://ubuntuforums.org/showthread.php?t=2235276&p=13080547#post13080547](http://ubuntuforums.org/showthread.php?t=2235276&p=13080547#post13080547)

I tried following the instructions I posted back then but I don't think "brscan3" installed correctly
[FONT=courier new]
[/FONT][FONT=courier new][FONT=times new roman][FONT=courier new]"1. For the Scanner
2. Download the 64-bit brscan3 drivers ([http://welcome.solutions.brother.com...nload_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html"))
3. Install them (we don't need to force this time!) (dpkg -i [driver])
4. Check to make sure it worked [dpkg -l | grep Brother]
5. Use the brother tool for adding a new scanner (brsaneconfig3 -a   name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE   ip=xxx.xxx.xxx.xxx)
6. Open your favorite scanning program and try it out!" 
([http://ubuntuforums.org/showthread.php?t=1601221&page=2](http://ubuntuforums.org/showthread.php?t=1601221&page=2))

From the terminal:
[/FONT][/FONT][/FONT][FONT=times new roman]<code>
[SIZE=3]tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Drivers$ sudo dpkg -i brscan4-0.4.2-3.amd64.deb
[sudo] password for tom: 
(Reading database ... 415640 files and directories currently installed.)
Preparing to unpack brscan4-0.4.2-3.amd64.deb ...
Unpacking brscan4 (0.4.2-3) over (0.4.2-1) ...
Setting up brscan4 (0.4.2-3) ...
This software is based in part on the work of the Independent JPEG Group.
[EMAIL="tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver"]tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver[/EMAIL]s$ dpkg -l grep Brother
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  grep           2.16-1       amd64        GNU grep, egrep and fgrep
dpkg-query: no packages found matching Brother
[EMAIL="tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver"]tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver[/EMAIL]s$ 
[EMAIL="tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver"]tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver[/EMAIL]s$ brsaneconfig3 -a name=Brother model=MFC-7460
brsaneconfig3: command not found
[EMAIL="tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver"]tom@Toms-Laptop-K55A:~/Downloads/Brother.MFC.7460.Driver[/EMAIL]s$ [/SIZE]
[/FONT][FONT=courier new][FONT=times new roman][FONT=courier new][FONT=times new roman]</code>[/FONT]                                                                                                                                                             
                                                                                                                                                             
I tried again via Gimp:
Error: "Failed to open device 'brother4:bus2;dev3':Invalid argument."

A related post?
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/578620](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/578620)


                                                                                                                                                             
                                                                                                                                                             
                                                                                                      

[/FONT]
[/FONT][/FONT]

---

