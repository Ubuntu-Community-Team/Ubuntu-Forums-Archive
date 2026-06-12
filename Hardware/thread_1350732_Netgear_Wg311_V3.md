---
title: "Netgear Wg311 V3"
date: 2009-12-09
forum: Hardware
---

### Post by janthomasebeling on 2009-12-09
Hello

It is the first time I use Ubuntu or any other linux dirived program. I would want to know if there was any idiot proof way to install the netgear WG311 V3 on Ubuntu 9.10. I'm running ubuntu on a Packard Bell Imedia x2802.

Thanks for your time

---

### Post by Trent T on 2009-12-31
I managed to get the Marvell Netgear WG311V3 wireless card running with ndiswrapper--  Here's a link to the discussion of that installation, posted Oct 18 2009;

[http://ubuntuforums.org/showthread.php?t=1293176&highlight=netgear+wg311](http://ubuntuforums.org/showthread.php?t=1293176&highlight=netgear+wg311)

NOTE: You will be running a lot of commands in the terminal window;
When you see commands listed in a thread, you can copy them by highlighting the text to copy, then pressing Control C
--
Switch to the terminal window, and past the command in, using the key combination 
Shift Insert

Then hit the Enter key, and your command will execute.

Best of luck activating your driver!

---

### Post by tmattson on 2010-05-27
[FONT=Times New Roman][SIZE=2]Please help: Just downloaded Ubuntu 10.04 and installed a **[COLOR=#ff0000]Netgear[/COLOR]** **[COLOR=#ff0000]wg311[/COLOR]** **[COLOR=#ff0000]v3[/COLOR]** wireless card. I have been successful (I think) in downloading the ndiswrapper. I have not been able to download the driver however, even though I have tried multiple sites. Here is an error reading I received when following a script in the terminal:[/SIZE][/FONT][FONT=Times New Roman][SIZE=3] 

[/SIZE][/FONT][FONT=Nimbus Mono L, monospace]tlm@tlm:~$ ifconfig -a [/FONT]
[FONT=Nimbus Mono L, monospace]eth0 Link encap:Ethernet HWaddr 00:0f:fe:4d:0d:6b [/FONT]
[FONT=Nimbus Mono L, monospace]inet addr:192.168.1.35 Bcast:192.168.1.255 Mask:255.255.255.0 [/FONT]
[FONT=Nimbus Mono L, monospace]inet6 addr: fe80::20f:feff:fe4d:d6b/64 Scope:Link [/FONT]
[FONT=Nimbus Mono L, monospace]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 [/FONT]
[FONT=Nimbus Mono L, monospace]RX packets:3338 errors:0 dropped:0 overruns:0 frame:0 [/FONT]
[FONT=Nimbus Mono L, monospace]TX packets:3065 errors:0 dropped:0 overruns:0 carrier:0 [/FONT]
[FONT=Nimbus Mono L, monospace]collisions:0 txqueuelen:100 [/FONT]
[FONT=Nimbus Mono L, monospace]RX bytes:2907875 (2.9 MB) TX bytes:443102 (443.1 KB) [/FONT]
[FONT=Nimbus Mono L, monospace]Memory:f0500000-f0520000 [/FONT]


[FONT=Nimbus Mono L, monospace]lo Link encap:Local Loopback [/FONT]
[FONT=Nimbus Mono L, monospace]inet addr:127.0.0.1 Mask:255.0.0.0 [/FONT]
[FONT=Nimbus Mono L, monospace]inet6 addr: ::1/128 Scope:Host [/FONT]
[FONT=Nimbus Mono L, monospace]UP LOOPBACK RUNNING MTU:16436 Metric:1 [/FONT]
[FONT=Nimbus Mono L, monospace]RX packets:12 errors:0 dropped:0 overruns:0 frame:0 [/FONT]
[FONT=Nimbus Mono L, monospace]TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 [/FONT]
[FONT=Nimbus Mono L, monospace]collisions:0 txqueuelen:0 [/FONT]
[FONT=Nimbus Mono L, monospace]RX bytes:720 (720.0 B) TX bytes:720 (720.0 B) [/FONT]


[FONT=Nimbus Mono L, monospace]tlm@tlm:~$ cd /tmp/ [/FONT]
[FONT=Nimbus Mono L, monospace]tlm@tlm:/tmp$ wget [[COLOR=#444444]ftp://downloads.netgear.com/files/wg311v3_1_0.zip[/COLOR]]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") [/FONT]
[FONT=Nimbus Mono L, monospace]--2010-05-18 22:51:38-- [[COLOR=#444444]ftp://downloads.netgear.com/files/wg311v3_1_0.zip[/COLOR]]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") [/FONT]
[FONT=Nimbus Mono L, monospace]=> `wg311v3_1_0.zip.1' [/FONT]
[FONT=Nimbus Mono L, monospace]Resolving downloads.netgear.com... 207.211.82.170 [/FONT]
[FONT=Nimbus Mono L, monospace]Connecting to downloads.netgear.com|207.211.82.170|:21... connected. [/FONT]
[FONT=Nimbus Mono L, monospace]Logging in as anonymous ... Logged in! [/FONT]
[FONT=Nimbus Mono L, monospace]==> SYST ... done. ==> PWD ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]==> TYPE I ... done. ==> CWD (1) /files ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]==> SIZE wg311v3_1_0.zip ... 6502117 [/FONT]
[FONT=Nimbus Mono L, monospace]==> PASV ... done. ==> RETR wg311v3_1_0.zip ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]Length: 6502117 (6.2M) (unauthoritative) [/FONT]


[FONT=Nimbus Mono L, monospace]100%[================================================== ===================>] 6,502,117 1.09K/s in 96m 53s [/FONT]


[FONT=Nimbus Mono L, monospace]2010-05-19 00:28:33 (1.09 KB/s) - Data transfer aborted. [/FONT]
[FONT=Nimbus Mono L, monospace]Retrying. [/FONT]


[FONT=Nimbus Mono L, monospace]--2010-05-19 00:28:34-- [[COLOR=#444444]ftp://downloads.netgear.com/files/wg311v3_1_0.zip[/COLOR]]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") [/FONT]
[FONT=Nimbus Mono L, monospace](try: 2) => `wg311v3_1_0.zip.1' [/FONT]
[FONT=Nimbus Mono L, monospace]==> CWD not required. [/FONT]
[FONT=Nimbus Mono L, monospace]==> SIZE wg311v3_1_0.zip ... [/FONT]
[FONT=Nimbus Mono L, monospace]Error in server response, closing control connection. [/FONT]
[FONT=Nimbus Mono L, monospace]Retrying. [/FONT]


[FONT=Nimbus Mono L, monospace]--2010-05-19 00:28:36-- [[COLOR=#444444]ftp://downloads.netgear.com/files/wg311v3_1_0.zip[/COLOR]]("ftp://downloads.netgear.com/files/wg311v3_1_0.zip") [/FONT]
[FONT=Nimbus Mono L, monospace](try: 3) => `wg311v3_1_0.zip.1' [/FONT]
[FONT=Nimbus Mono L, monospace]Connecting to downloads.netgear.com|207.211.82.170|:21... connected. [/FONT]
[FONT=Nimbus Mono L, monospace]Logging in as anonymous ... Logged in! [/FONT]
[FONT=Nimbus Mono L, monospace]==> SYST ... done. ==> PWD ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]==> TYPE I ... done. ==> CWD (1) /files ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]==> SIZE wg311v3_1_0.zip ... 6502117 [/FONT]
[FONT=Nimbus Mono L, monospace]==> PASV ... done. ==> REST 6502117 ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]==> RETR wg311v3_1_0.zip ... done. [/FONT]
[FONT=Nimbus Mono L, monospace]Length: 6502117 (6.2M), 0 remaining (unauthoritative) [/FONT]


[FONT=Nimbus Mono L, monospace]100%[++++++++++++++++++++++++++++++++++++++++++++++++++ ++++++++++++++++++++] 6,502,117 --.-K/s in 0s [/FONT]


[FONT=Nimbus Mono L, monospace]2010-05-19 00:28:37 (0.00 B/s) - `wg311v3_1_0.zip.1' saved [6502117] [/FONT]


[FONT=Nimbus Mono L, monospace]tlm@tlm:/tmp$ unzip wg311v3_1_0.zi [/FONT]
[FONT=Nimbus Mono L, monospace]unzip: cannot find or open wg311v3_1_0.zi, wg311v3_1_0.zi.zip or wg311v3_1_0.zi.ZIP. [/FONT]
[FONT=Nimbus Mono L, monospace]tlm@tlm:/tmp$ unzip wg311v3_1_0.zip [/FONT]
[FONT=Nimbus Mono L, monospace]Archive: wg311v3_1_0.zip [/FONT]
[FONT=Nimbus Mono L, monospace]End-of-central-directory signature not found. Either this file is not [/FONT]
[FONT=Nimbus Mono L, monospace]a zipfile, or it constitutes one disk of a multi-part archive. In the [/FONT]
[FONT=Nimbus Mono L, monospace]latter case the central directory and zipfile comment will be found on [/FONT]
[FONT=Nimbus Mono L, monospace]the last disk(s) of this archive. [/FONT]
[FONT=Nimbus Mono L, monospace]unzip: cannot find zipfile directory in one of wg311v3_1_0.zip or [/FONT]
[FONT=Nimbus Mono L, monospace]wg311v3_1_0.zip.zip, and cannot find wg311v3_1_0.zip.ZIP, period. [/FONT]
[FONT=Nimbus Mono L, monospace]tlm@tlm:/tmp$ cd "/tmp/WG311v3 V1.0/Driver/Windows XP/" [/FONT]
[FONT=Nimbus Mono L, monospace]bash: cd: /tmp/WG311v3 V1.0/Driver/Windows XP/: No such file or directory 
[/FONT]


[FONT=Times New Roman][SIZE=2][SIZE=2]Every time I try to download the driver, it seems not to work. I have the following files in my downloads folder[/SIZE]: 

/home/tlm/Downloads/driverfetch_setup.exe
/home/tlm/Downloads/driverfetch_setup(2).exe
/home/tlm/Downloads/driverfetch_setup(3).exe
/home/tlm/Downloads/driverfetch_setup(4).exe
/home/tlm/Downloads/driverfetch_setup(5).exe
/home/tlm/Downloads/driverfetch_setup(6).exe
/home/tlm/Downloads/driverfetch_setup(7).exe
/home/tlm/Downloads/mrv8335x64.inf
/home/tlm/Downloads/MRV8335x64.sys
/home/tlm/Downloads/WinX64.zip[/SIZE][/FONT][SIZE=2]

[FONT=Times New Roman][SIZE=3]When I double click on the [/SIZE][/FONT][/SIZE][FONT=Times New Roman][SIZE=2][SIZE=3]/home/tlm/Downloads/MRV8335x64.sys I get the following error message: [/SIZE]

[FONT=Courier New][SIZE=1]Archive: /home/tlm/Downloads/MRV8335x64.sys
[/home/tlm/Downloads/MRV8335x64.sys]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
zipinfo: cannot find zipfile directory in one of /home/tlm/Downloads/MRV8335x64.sys or
/home/tlm/Downloads/MRV8335x64.sys.zip, and cannot find /home/tlm/Downloads/MRV8335x64.sys.ZIP, period.
[SIZE=3]
[/SIZE][FONT=Times New Roman][SIZE=2][SIZE=2]This is the same error message I get when I click the .exe files.[/SIZE] 

[SIZE=3]I hope this makes more sense to someone out there than it makes to me. If anyone could point me in the right direction, I would appreciate it. I am trying to follow the scripts that are provided, but none have seemed to work for me. Please help![/SIZE]
[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by joshedmonds on 2010-05-28
Please try installing package linux-firmware-nonfree

System -> Administration -> Synaptic Package Manager

A reboot may be required after installation. If this is successful NDISWrapper will not be necessary.

---

### Post by tmattson on 2010-05-29
Not sure what was different this time, but this page helped get me up and running.  

[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

---

