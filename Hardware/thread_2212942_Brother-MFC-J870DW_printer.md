---
title: "Brother-MFC-J870DW printer"
date: 2014-03-23
forum: Hardware
---

### Post by Muahdib on 2014-03-23
im running 12.04. I have a shinny new mfc-j8700 printer. I have the cups wrapper and the debian driver installed. I cant log into the web cups web interface and add the printer [http://localhost:631/](http://localhost:631/). however
when I print a test page, as far as I can tell the page looks like it is sent to the printer. the display on the printer lights up, but nothing prints. cups shows job as "completed".. 

I suspect this has something to do with 64bit Ubuntu and a 32 bit driver? 

I have gone through all the brother per-installs and read countless threads but no joy. 

any help is appreciated, thanks

---

### Post by Muahdib on 2014-03-23
more info

lpstat -p -d=
printer Brother-MFC-J870DW is idle.  enabled since Sun 23 Mar 2014 06:33:45 PM MST
	Ready to print.
printer Brother_MFC-J870DW is idle.  enabled since Sun 23 Mar 2014 05:41:38 PM MST
system default destination: Brother-MFC-J870DW

---

### Post by gifford on 2014-03-23
Are you using usb or network for printing?
As far as the 32 bit driver, if you followed the installation instructions on the Brother site, it should have installed correctly in your 64 bit system.
Did you create the **mkdir /var/spool/lpd ?**

---

### Post by Muahdib on 2014-03-23
so yes i did make a /var/spool/lpd... but in that dir is a dir called
drwx------ 2 lp lp 4096 2014-03-23 16:50 mfcj825dw 

I have a MFC-870DW, looks like it uses the same lpr driver as the 825dw

---

### Post by Muahdib on 2014-03-23
cups access log from the last print job. i tried to print the google home page..

localhost - - [23/Mar/2014:20:07:03 -0700] "POST /printers/Brother-MFC-J870DW HTTP/1.1" 200 146812 Print-Job successful-ok

---

### Post by pdc on 2014-03-24
please explain your system; ie is it a home computer; with the brother printer being the only printer; and it being connected by usb cable to the standalone computer?

also .....what does > [COLOR="#FF0000"]uname -a[/COLOR] give in a terminal and can you paste the result back here please: 

also what does 

> [COLOR="#FF0000"]lpinfo -v[/COLOR]

and 

> [COLOR="#FF0000"]dpkg -l | grep Brother[/COLOR]

if you copy and paste these commands into a terminal; and if you paste the results back please

---

### Post by Muahdib on 2014-03-24
sorry.. yes its a home computer running ubuntu12.04. it has a software raid running a 3 disk raid 5. the printer is a network printer. it is connected wireless. other computers and smart devices on the network are able to see and print to this printer. i have 3 other linux computers on this network that I want to set up to see and print to this printer. this computer i am having trouble with is just the first one I tried. no other linux system is currently using this printer. I also dont want to use any of the linux systems as a print server as I dont like to leave any one of them running.  


uname -a
Linux morganland 2.6.32-57-server #119-Ubuntu SMP Wed Feb 19 01:11:15 UTC 2014 x86_64 GNU/Linux

lpinfo -v

network smb
network socket
network beh
network http
direct scsi
network ipp
network lpd
serial serial:/dev/ttyS0?baud=115200
network dnssd://Brother%20MFC-J870DW._pdl-datastream._tcp.local/
network dnssd://Brother%20MFC-J870DW._printer._tcp.local/
network dnssd://Brother%20MFC-J870DW._ipp._tcp.local/
direct hp
direct hpfax
network lpd://BRN30055C1CCFA8/BINARY_P1

dpkg -l | grep Brother
ii  mfcj825dwlpr                                 3.0.1-1                                         Brother lpr Inkjet Printer Definitions
ii  mfcj870dwcupswrapper                  3.0.0-1                                         Brother CUPS Inkjet Printer Definitions

---

### Post by pdc on 2014-03-24
you have slightly more than most folks' definition of a home computer! well done for all the complexity

you seem to have a 64bit system; and the brother drivers seem to be installed;

and this instruction page from Brother

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

in **_[COLOR="#0000FF"]Step 5b. (for Network Connection)[/COLOR]_** [COLOR="#EE82EE"]Configure your printer on the cups web interface[/COLOR]

>     5b-1. Open a web browser and go to "http://localhost:631/printers". 
    5b-2. Click "Modify Printer" and set following parameters.

    - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect" 	     	for Device
    - lpd://(Your printer's IP address)/binary_p1 	     	for Device URI
    - Brother 	     	for Make/Manufacturer Selection
    - Your printer's name 	     	for Model/Driver Selection

I wonder if you feel you have done all that; they give examples to help you

___________________________

as you seem a very organised person, here is the Ubuntu debug printer issues page, 

[https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer)

why don't you work through this and let us know how it helps you: a series of commands to issue and test

---

### Post by Muahdib on 2014-03-24
Thanks pdc, the complexity was or is just because i was, or am curious by nature. This was meant to be a server for everyone on the network to do backups, proxy, proxy cache, stream music, and videos from. I only stopped because I ran out of money :(. if you remember a few years back, there was a flood at one of the western digital hard drive manufacturing plants that drove all the hard drive prices way up. They have now in the last few months come back down. I needed between 6 and 8 TB of space for all this to work and when i built the machine all I had laying around was 3 340 GB drives. I used them but decided the home server could wait till the prices of drives came back down.. ... ... waiting... ... waiting... ... 

now Im working on some other stuff in the evenings. now this machine is just my desktop I use 80% of the time for "My computer" that none of the kids or even my wife has the password for so they can&#8217;t mess it up:) I may still get back to it. But even with a 80% efficient power supply and all green components, idle servers still eat lots of power.. 

anyway.. no one asked for that brain dump... back to the printer. 

I will try these steps after work. I did skim over this document however I did not stop to think about it being Wi-Fi vs. wired. I think i will wire it in tonight as well and turn off the Wi-Fi on the printer. I once watched my instructor gain access to a network through a Wi-Fi printer ip address using ssh. of course it was a windows network.. sooo.. yeah. 

thanks for the reply.

I will report back any results.

---

### Post by Muahdib on 2014-03-31
after going through many many threads, trying all kinds of advice. i am still not able to get this printer to work. 

here is some more information.

ron@morganland:~$ ping 192.168.0.41 (printers IP address)
PING 192.168.0.41 (192.168.0.41) 56(84) bytes of data.
64 bytes from 192.168.0.41: icmp_seq=1 ttl=255 time=0.290 ms
64 bytes from 192.168.0.41: icmp_seq=2 ttl=255 time=0.275 ms
64 bytes from 192.168.0.41: icmp_seq=3 ttl=255 time=0.279 ms
64 bytes from 192.168.0.41: icmp_seq=4 ttl=255 time=12.9 ms
64 bytes from 192.168.0.41: icmp_seq=5 ttl=255 time=0.276 ms
64 bytes from 192.168.0.41: icmp_seq=6 ttl=255 time=0.261 ms
64 bytes from 192.168.0.41: icmp_seq=7 ttl=255 time=0.271 ms
^C
--- 192.168.0.41 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5997ms
rtt min/avg/max/mdev = 0.261/2.089/12.974/4.443 ms

ron@morganland:~$ nmap 192.168.0.41

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2014-03-30 20:54 MST
Interesting ports on 192.168.0.41:
Not shown: 993 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
443/tcp  open  https
515/tcp  open  printer
631/tcp  open  ipp
9100/tcp open  jetdirect

Nmap done: 1 IP address (1 host up) scanned in 0.31 seconds

ron@morganland:~$ /usr/lib/cups/backend/snmp
network lpd://BRN30055C1CCFA8/BINARY_P1 "Brother MFC-J870DW" "Brother MFC-J870DW" "MFG:Brother;CMD:HBP,BRPJL,URF;MDL:MFC-J870DW;CLS:PRINTER;CID:Brother IJ Type2;URF:SRGB24,W8,CP1,IS1,MT1-8-11,OB9,PQ4-5,RS300,OFU0,V1.2,DM3;" ""
ron@morganland:~$ sudo /usr/lib/cups/backend/dnssd
[sudo] password for ron: 
DEBUG: Found "Brother MFC-J870DW._ipp._tcplocal"...
DEBUG: Found "Brother MFC-J870DW._pdl-datastream._tcplocal"...
DEBUG: Found "Brother MFC-J870DW._printer._tcplocal"...
network dnssd://Brother%20MFC-J870DW._pdl-datastream._tcp.local/ "Brother MFC-J870DW" "Brother MFC-J870DW" "MFG:Brother;MDL:MFC-J870DW;CMD:HBP,BRPJL,URF;" ""
network dnssd://Brother%20MFC-J870DW._printer._tcp.local/ "Brother MFC-J870DW" "Brother MFC-J870DW" "MFG:Brother;MDL:MFC-J870DW;CMD:HBP,BRPJL,URF;" ""
network dnssd://Brother%20MFC-J870DW._ipp._tcp.local/ "Brother MFC-J870DW" "Brother MFC-J870DW" "MFG:Brother;MDL:MFC-J870DW;CMD:HBP,BRPJL,URF;" ""


ron@morganland:~$ lpinfo -v
network http
network smb
network ipp
direct scsi
network socket
network lpd
network beh
serial serial:/dev/ttyS0?baud=115200
network dnssd://Brother%20MFC-J870DW._ipp._tcp.local/
network dnssd://Brother%20MFC-J870DW._pdl-datastream._tcp.local/
network dnssd://Brother%20MFC-J870DW._printer._tcp.local/
direct hp
direct hpfax
network lpd://BRN30055C1CCFA8/BINARY_P1

ron@morganland:~$ avahi-browse -a -v -t -v
Server version: avahi 0.6.25; Host name: morganland.local
E Ifce Prot Name                                          Type                 Domain
+ virbr0 IPv4 morganland [ce:96:e8:61:ce:f1]                Workstation          local
+ eth0 IPv4 morganland [8c:89:a5:31:52:63]                Workstation          local
+ virbr0 IPv4 Virtualization Host morganland                _libvirt._tcp        local
+ eth0 IPv4 Virtualization Host morganland                _libvirt._tcp        local
+ eth0 IPv4 Brother MFC-J870DW                            Web Site             local
+ eth0 IPv4 Brother MFC-J870DW                            _scanner._tcp        local
+ eth0 IPv4 Brother MFC-J870DW                            Internet Printer     local
+ eth0 IPv4 Brother MFC-J870DW                            UNIX Printer         local
+ eth0 IPv4 Brother MFC-J870DW                            PDL Printer          local
: Cache exhausted
: All for now

---

### Post by Muahdib on 2014-03-31
im not to sure about posting this next bit as its kind of a log bit of text. im going to its just i feel bad.. but at the end of my rope here. Im not as smart as some of you. 
this is the log file from trying to print a test page from the cups localhost:631

D [30/Mar/2014:21:08:05 -0700] cupsdAcceptClient: 162 from localhost:631 (IPv6)
D [30/Mar/2014:21:08:05 -0700] Report: clients=3
D [30/Mar/2014:21:08:05 -0700] Report: jobs=25
D [30/Mar/2014:21:08:05 -0700] Report: jobs-active=0
D [30/Mar/2014:21:08:05 -0700] Report: printers=1
D [30/Mar/2014:21:08:05 -0700] Report: printers-implicit=0
D [30/Mar/2014:21:08:05 -0700] Report: stringpool-string-count=2476
D [30/Mar/2014:21:08:05 -0700] Report: stringpool-alloc-bytes=8712
D [30/Mar/2014:21:08:05 -0700] Report: stringpool-total-bytes=53312
D [30/Mar/2014:21:08:05 -0700] cupsdAcceptClient: 1133 from localhost:631 (IPv6)
D [30/Mar/2014:21:08:05 -0700] cupsdAcceptClient: 1166 from localhost:631 (IPv6)
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 162 GET /printers/? HTTP/1.1
D [30/Mar/2014:21:08:07 -0700] cupsdSetBusyState: Active clients
D [30/Mar/2014:21:08:07 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:07 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[26] = "SCRIPT_NAME=/printers/"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[28] = "PATH_INFO=/"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[29] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[30] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[31] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[32] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[33] = "HTTP_REFERER=http://localhost:631/admin"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[34] = "REQUEST_METHOD=GET"
D [30/Mar/2014:21:08:07 -0700] [CGI] envp[35] = "QUERY_STRING="
D [30/Mar/2014:21:08:07 -0700] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 8124)
I [30/Mar/2014:21:08:07 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=8124)
D [30/Mar/2014:21:08:07 -0700] cupsdSendCommand: 162 file=1584
D [30/Mar/2014:21:08:07 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:07 -0700] cupsdAcceptClient: 1585 from localhost (Domain)
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 1585 POST / HTTP/1.1
D [30/Mar/2014:21:08:07 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 1585 1.1 CUPS-Get-Default 1
D [30/Mar/2014:21:08:07 -0700] CUPS-Get-Default
D [30/Mar/2014:21:08:07 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [30/Mar/2014:21:08:07 -0700] [CGI] show_all_printers(http=0x7f21cb34d3c0, user="ron")
D [30/Mar/2014:21:08:07 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:07 -0700] Script header: 
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 1585 POST / HTTP/1.1
D [30/Mar/2014:21:08:07 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 1585 1.1 CUPS-Get-Printers 1
D [30/Mar/2014:21:08:07 -0700] CUPS-Get-Printers
D [30/Mar/2014:21:08:07 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [30/Mar/2014:21:08:07 -0700] cupsdReadClient: 1585 WAITING Closing on EOF
D [30/Mar/2014:21:08:07 -0700] cupsdCloseClient: 1585
D [30/Mar/2014:21:08:07 -0700] PID 8124 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [30/Mar/2014:21:08:07 -0700] cupsdSetBusyState: Not busy
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 162 GET /printers/Brother-MFC-J870DW HTTP/1.1
D [30/Mar/2014:21:08:09 -0700] cupsdSetBusyState: Active clients
D [30/Mar/2014:21:08:09 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:09 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[26] = "SCRIPT_NAME=/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[28] = "PATH_INFO=/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[29] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[30] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[31] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[32] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[33] = "HTTP_REFERER=http://localhost:631/printers/?"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[34] = "REQUEST_METHOD=GET"
D [30/Mar/2014:21:08:09 -0700] [CGI] envp[35] = "QUERY_STRING="
D [30/Mar/2014:21:08:09 -0700] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 8125)
I [30/Mar/2014:21:08:09 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=8125)
D [30/Mar/2014:21:08:09 -0700] cupsdSendCommand: 162 file=1590
D [30/Mar/2014:21:08:09 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:09 -0700] cupsdAcceptClient: 1591 from localhost (Domain)
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 POST / HTTP/1.1
D [30/Mar/2014:21:08:09 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 1.1 CUPS-Get-Default 1
D [30/Mar/2014:21:08:09 -0700] CUPS-Get-Default
D [30/Mar/2014:21:08:09 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [30/Mar/2014:21:08:09 -0700] [CGI] show_printer(http=0x7fef0d562430, printer="Brother-MFC-J870DW")
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 POST / HTTP/1.1
D [30/Mar/2014:21:08:09 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 1.1 Get-Printer-Attributes 1
D [30/Mar/2014:21:08:09 -0700] Get-Printer-Attributes ipp://localhost/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:09 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:09 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:09 -0700] Script header: 
D [30/Mar/2014:21:08:09 -0700] [CGI] Regular expression ".*Clean.*"
D [30/Mar/2014:21:08:09 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:09 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:09 -0700] [CGI] Regular expression ".*PrintSelfTestPage.*"
D [30/Mar/2014:21:08:09 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:09 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 POST / HTTP/1.1
D [30/Mar/2014:21:08:09 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 1.1 Get-Jobs 1
D [30/Mar/2014:21:08:09 -0700] Get-Jobs ipp://localhost:631/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:09 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost:631/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:09 -0700] cupsdReadClient: 1591 WAITING Closing on EOF
D [30/Mar/2014:21:08:09 -0700] cupsdCloseClient: 1591
D [30/Mar/2014:21:08:09 -0700] PID 8125 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [30/Mar/2014:21:08:09 -0700] cupsdSetBusyState: Not busy
D [30/Mar/2014:21:08:17 -0700] cupsdReadClient: 1133 WAITING Closing on EOF
D [30/Mar/2014:21:08:17 -0700] cupsdCloseClient: 1133
D [30/Mar/2014:21:08:17 -0700] cupsdReadClient: 1166 WAITING Closing on EOF
D [30/Mar/2014:21:08:17 -0700] cupsdCloseClient: 1166
D [30/Mar/2014:21:08:20 -0700] cupsdReadClient: 162 POST /printers/Brother-MFC-J870DW HTTP/1.1
D [30/Mar/2014:21:08:20 -0700] cupsdSetBusyState: Active clients
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:21 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[26] = "SCRIPT_NAME=/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[28] = "PATH_INFO=/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[29] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[30] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[31] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[32] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[33] = "HTTP_REFERER=http://localhost:631/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[34] = "REQUEST_METHOD=POST"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[35] = "CONTENT_LENGTH=64"
D [30/Mar/2014:21:08:21 -0700] [CGI] envp[36] = "CONTENT_TYPE=application/x-www-form-urlencoded"
D [30/Mar/2014:21:08:21 -0700] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 8126)
I [30/Mar/2014:21:08:21 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=8126)
D [30/Mar/2014:21:08:21 -0700] cupsdSendCommand: 162 file=1595
D [30/Mar/2014:21:08:21 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:21 -0700] cupsdAcceptClient: 1594 from localhost (Domain)
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 POST /printers/Brother-MFC-J870DW HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 1.1 Print-Job 1
D [30/Mar/2014:21:08:21 -0700] Print-Job ipp://localhost:631/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:21 -0700] [Job ???] Auto-typing file...
I [30/Mar/2014:21:08:21 -0700] [Job ???] Request file type is application/vnd.cups-banner.
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(----J-)
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [30/Mar/2014:21:08:21 -0700] add_job: requesting-user-name="ron"
D [30/Mar/2014:21:08:21 -0700] Adding default job-sheets values "none,none"...
I [30/Mar/2014:21:08:21 -0700] [Job 27] Adding start banner page "none".
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(----J-)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Adding end banner page "none".
I [30/Mar/2014:21:08:21 -0700] [Job 27] File of type application/vnd.cups-banner queued by "ron".
D [30/Mar/2014:21:08:21 -0700] [Job 27] hold_until=0
I [30/Mar/2014:21:08:21 -0700] [Job 27] Queued on "Brother-MFC-J870DW" by "ron".
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(----J-)
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] job-sheets=none,none
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[0]="Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[1]="27"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[2]="ron"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[3]="Test Page"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[4]="1"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[5]="job-uuid=urn:uuid:c8224477-0a92-30a0-5412-4a09a0f36128 job-originating-host-name=localhost"
D [30/Mar/2014:21:08:21 -0700] [Job 27] argv[6]="/var/spool/cups/d00027-001"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[8]="HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[10]="SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[11]="SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[13]="TZ=America/Phoenix"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[14]="USER=root"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[17]="IPP_PORT=631"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[18]="CHARSET=utf-8"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[19]="LANG=en_US.UTF-8"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[20]="PPD=/etc/cups/ppd/Brother-MFC-J870DW.ppd"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[21]="RIP_MAX_CACHE=2041418k"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[23]="DEVICE_URI=lpd://BRN30055C1CCFA8/BINARY_P1"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[24]="PRINTER_INFO=Brother MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[25]="PRINTER_LOCATION=desk"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[26]="PRINTER=Brother-MFC-J870DW"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[27]="CUPS_FILETYPE=document"
D [30/Mar/2014:21:08:21 -0700] [Job 27] envp[28]="FINAL_CONTENT_TYPE=printer/Brother-MFC-J870DW"
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started filter /usr/lib/cups/filter/bannertops (PID 8127)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started filter /usr/lib/cups/filter/pstopdf (PID 8128)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started filter /usr/lib/cups/filter/pdftopdf (PID 8129)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started filter /usr/lib/cups/filter/cpdftocps (PID 8130)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started filter /usr/lib/cups/filter/brother_lpdwrapper_mfcj870dw (PID 8132)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Started backend /usr/lib/cups/backend/lpd (PID 8134)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost:631/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:21 -0700] [Job 27] load_banner(filename="/var/spool/cups/d00027-001")
D [30/Mar/2014:21:08:21 -0700] [Job 27] pstopdf 5 args: 27 ron Test Page 1 job-uuid=urn:uuid:c8224477-0a92-30a0-5412-4a09a0f36128 job-originating-host-name=localhost
D [30/Mar/2014:21:08:21 -0700] [Job 27] PPD: /etc/cups/ppd/Brother-MFC-J870DW.ppd
D [30/Mar/2014:21:08:21 -0700] [Job 27] Page = 612x792; 9,9 to 603,783
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 WAITING Closing on EOF
D [30/Mar/2014:21:08:21 -0700] cupsdCloseClient: 1594
D [30/Mar/2014:21:08:21 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:21 -0700] Script header: 
D [30/Mar/2014:21:08:21 -0700] PID 8126 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: +connecting-to-device
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] Looking up "BRN30055C1CCFA8"...
D [30/Mar/2014:21:08:21 -0700] [Job 27] pdftops argv[5] = 27 ron Test Page 1 job-uuid=urn:uuid:c8224477-0a92-30a0-5412-4a09a0f36128 job-originating-host-name=localhost
D [30/Mar/2014:21:08:21 -0700] [Job 27] PPD: /etc/cups/ppd/Brother-MFC-J870DW.ppd
D [30/Mar/2014:21:08:21 -0700] [Job 27] /usr/bin/pdftops supports '-origpagesizes': yes
D [30/Mar/2014:21:08:21 -0700] [Job 27] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [30/Mar/2014:21:08:21 -0700] [Job 27] PNG image: 192x128x8, color_type=2 (RGB)
D [30/Mar/2014:21:08:21 -0700] [Job 27] PostScript Level: 2
D [30/Mar/2014:21:08:21 -0700] [Job 27] cp: cannot stat `/opt/brother/Printers/mfcj870dw/inf/brmfcj870dwrc': No such file or directory
D [30/Mar/2014:21:08:21 -0700] PID 8127 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] [Job 27] chmod: cannot access `/tmp/brmfcj870dwrc_8132': No such file or directory
D [30/Mar/2014:21:08:21 -0700] [Job 27] Resolution: 
D [30/Mar/2014:21:08:21 -0700] [Job 27] Duplex: no
D [30/Mar/2014:21:08:21 -0700] [Job 27] Resolution: 
D [30/Mar/2014:21:08:21 -0700] [Job 27] Page size: Letter
I [30/Mar/2014:21:08:21 -0700] [Job 27] Copying print data...
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] backendRunLoop(print_fd=-1, device_fd=6, snmp_fd=5, addr=0x7fa3e6bb6488, use_bc=0, side_cb=0x7fa3e505aa20)
D [30/Mar/2014:21:08:21 -0700] [Job 27] Page size: Letter
D [30/Mar/2014:21:08:21 -0700] [Job 27] Width: 612, height: 792, absolute margins: 9, 9, 603, 783
D [30/Mar/2014:21:08:21 -0700] [Job 27] Relative margins: 9, 9, 9, 9
D [30/Mar/2014:21:08:21 -0700] [Job 27] PPD options: -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [30/Mar/2014:21:08:21 -0700] [Job 27] PostScript to be injected: 
D [30/Mar/2014:21:08:21 -0700] [Job 27] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [30/Mar/2014:21:08:21 -0700] [Job 27] Width: 612, height: 792, absolute margins: 9, 9, 603, 783
D [30/Mar/2014:21:08:21 -0700] [Job 27] Relative margins: 9, 9, 9, 9
D [30/Mar/2014:21:08:21 -0700] [Job 27] PPD options: -level2 -origpagesizes
D [30/Mar/2014:21:08:21 -0700] [Job 27] PostScript to be injected: 
D [30/Mar/2014:21:08:21 -0700] cupsdAcceptClient: 1594 from localhost (Domain)
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 POST / HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 1.1 Get-Jobs 1
D [30/Mar/2014:21:08:21 -0700] Get-Jobs ipp://localhost/printers/
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 WAITING Closing on EOF
D [30/Mar/2014:21:08:21 -0700] cupsdCloseClient: 1594
D [30/Mar/2014:21:08:21 -0700] cupsdAcceptClient: 1594 from localhost (Domain)
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 POST / HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 1.1 Get-Notifications 1
D [30/Mar/2014:21:08:21 -0700] Get-Notifications /
D [30/Mar/2014:21:08:21 -0700] cupsdIsAuthorized: requesting-user-name="ron"
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 POST / HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 1.1 Get-Job-Attributes 1
D [30/Mar/2014:21:08:21 -0700] Get-Job-Attributes ipp://localhost/jobs/27
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/27) from localhost
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] PID 8128 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] PID 8129 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] [Job 27] Device copies: 1; device collate: 
D [30/Mar/2014:21:08:21 -0700] [Job 27] Running /usr/bin/pdftops  -level2 -origpagesizes /tmp/pdftops.isLwqF -
D [30/Mar/2014:21:08:21 -0700] [Job 27] Running pstops '27' 'ron' 'Test Page' '1' ' job-uuid=urn:uuid:c8224477-0a92-30a0-5412-4a09a0f36128 job-originating-host-name=localhost'
D [30/Mar/2014:21:08:21 -0700] [Job 27] Page = 612x792; 9,9 to 603,783
D [30/Mar/2014:21:08:21 -0700] [Job 27] slow_collate=0, slow_duplex=0, slow_order=0
D [30/Mar/2014:21:08:21 -0700] [Job 27] Before copy_comments - %!PS-Adobe-3.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] %!PS-Adobe-3.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%LanguageLevel: 2
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%DocumentSuppliedResources: (atend)
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%DocumentMedia: plain 612 792 0 () ()
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%BoundingBox: 0 0 612 792
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%Pages: 1
D [30/Mar/2014:21:08:21 -0700] [Job 27] %%EndComments
D [30/Mar/2014:21:08:21 -0700] [Job 27] Before copy_prolog - %%BeginDefaults
D [30/Mar/2014:21:08:21 -0700] [Job 27] Before copy_setup - %%BeginSetup
D [30/Mar/2014:21:08:21 -0700] [Job 27] Before page loop - %%Page: 1 1
D [30/Mar/2014:21:08:21 -0700] [Job 27] Copying page 1...
D [30/Mar/2014:21:08:21 -0700] [Job 27] pagew = 594.0, pagel = 774.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [30/Mar/2014:21:08:21 -0700] [Job 27] PageLeft = 9.0, PageRight = 603.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] PageTop = 783.0, PageBottom = 9.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] PageWidth = 612.0, PageLength = 792.0
D [30/Mar/2014:21:08:21 -0700] [Job 27] Wrote 1 pages...
D [30/Mar/2014:21:08:21 -0700] PID 8130 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] PID 8132 (/usr/lib/cups/filter/brother_lpdwrapper_mfcj870dw) exited with no errors.
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: +connecting-to-device
D [30/Mar/2014:21:08:21 -0700] [Job 27] Looking up "BRN30055C1CCFA8"...
D [30/Mar/2014:21:08:21 -0700] [Job 27] Connecting to BRN30055C1CCFA8:515 for printer BINARY_P1
I [30/Mar/2014:21:08:21 -0700] [Job 27] Connecting to printer...
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -connecting-to-device
I [30/Mar/2014:21:08:21 -0700] [Job 27] Connected to printer...
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] Connected to 192.168.0.41:515 (IPv4) (local port 1023)...
D [30/Mar/2014:21:08:21 -0700] [Job 27] ATTR: marker-colors=#000000,#FFFF00,#00FFFF,#FF00FF,none
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(P-----)
D [30/Mar/2014:21:08:21 -0700] [Job 27] ATTR: marker-names="Black Ink Cartridge","Yellow Ink Cartridge","Cyan Ink Cartridge","Magenta Ink Cartridge","Ink Absorber"
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(P-----)
D [30/Mar/2014:21:08:21 -0700] [Job 27] ATTR: marker-types=inkCartridge,inkCartridge,inkCartridge,inkCartridge,wasteInk
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(P-----)
D [30/Mar/2014:21:08:21 -0700] [Job 27] ATTR: marker-levels=-1,-1,-1,-1,-1
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(P-----)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -media-low-report
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -media-empty-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -toner-low-report
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -toner-empty-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -door-open-report
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -media-jam-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -input-tray-missing-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -output-tray-missing-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -marker-supply-missing-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -output-area-almost-full-report
D [30/Mar/2014:21:08:21 -0700] [Job 27] STATE: -output-area-full-warning
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command 02 BINARY_P1
D [30/Mar/2014:21:08:21 -0700] [Job 27] Sending command string (11 bytes)...
D [30/Mar/2014:21:08:21 -0700] [Job 27] Reading command status...
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command returning 0
D [30/Mar/2014:21:08:21 -0700] [Job 27] Control file is:
D [30/Mar/2014:21:08:21 -0700] [Job 27] Hmorganland.hsd1.az.comcast.net
D [30/Mar/2014:21:08:21 -0700] [Job 27] Pron
D [30/Mar/2014:21:08:21 -0700] [Job 27] JTest Page
D [30/Mar/2014:21:08:21 -0700] [Job 27] ldfA134morganland.hsd1
D [30/Mar/2014:21:08:21 -0700] [Job 27] UdfA134morganland.hsd1
D [30/Mar/2014:21:08:21 -0700] [Job 27] NTest Page
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command 02 105 cfA134morganland.hsd1
D [30/Mar/2014:21:08:21 -0700] [Job 27] Sending command string (27 bytes)...
D [30/Mar/2014:21:08:21 -0700] [Job 27] Reading command status...
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command returning 0
I [30/Mar/2014:21:08:21 -0700] [Job 27] Sending control file (105 bytes)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
I [30/Mar/2014:21:08:21 -0700] [Job 27] Control file sent successfully
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command 03 0 dfA134morganland.hsd1
D [30/Mar/2014:21:08:21 -0700] [Job 27] Sending command string (25 bytes)...
D [30/Mar/2014:21:08:21 -0700] [Job 27] Reading command status...
D [30/Mar/2014:21:08:21 -0700] [Job 27] lpd_command returning 0
I [30/Mar/2014:21:08:21 -0700] [Job 27] Sending data file (0 bytes)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdMarkDirty(-----S)
D [30/Mar/2014:21:08:21 -0700] cupsdAcceptClient: 1595 from localhost (Domain)
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 POST / HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 1.1 Get-Jobs 1
D [30/Mar/2014:21:08:21 -0700] Get-Jobs ipp://localhost/printers/
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 WAITING Closing on EOF
D [30/Mar/2014:21:08:21 -0700] cupsdCloseClient: 1595
D [30/Mar/2014:21:08:21 -0700] cupsdAcceptClient: 1595 from localhost (Domain)
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 POST / HTTP/1.1
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 1.1 Get-Notifications 1
D [30/Mar/2014:21:08:21 -0700] Get-Notifications /
D [30/Mar/2014:21:08:21 -0700] cupsdIsAuthorized: requesting-user-name="ron"
D [30/Mar/2014:21:08:21 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [30/Mar/2014:21:08:21 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1594 WAITING Closing on EOF
D [30/Mar/2014:21:08:21 -0700] cupsdCloseClient: 1594
D [30/Mar/2014:21:08:21 -0700] cupsdReadClient: 1595 WAITING Closing on EOF
D [30/Mar/2014:21:08:21 -0700] cupsdCloseClient: 1595
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 162 GET /printers/Brother-MFC-J870DW HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:23 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[26] = "SCRIPT_NAME=/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[28] = "PATH_INFO=/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[29] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[30] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[31] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[32] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[33] = "HTTP_REFERER=http://localhost:631/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[34] = "REQUEST_METHOD=GET"
D [30/Mar/2014:21:08:23 -0700] [CGI] envp[35] = "QUERY_STRING="
D [30/Mar/2014:21:08:23 -0700] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 8224)
I [30/Mar/2014:21:08:23 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=8224)
D [30/Mar/2014:21:08:23 -0700] cupsdSendCommand: 162 file=1601
D [30/Mar/2014:21:08:23 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:23 -0700] cupsdAcceptClient: 1602 from localhost (Domain)
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 POST / HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 1.1 CUPS-Get-Default 1
D [30/Mar/2014:21:08:23 -0700] CUPS-Get-Default
D [30/Mar/2014:21:08:23 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [30/Mar/2014:21:08:23 -0700] [CGI] show_printer(http=0x7fcb2ffa9430, printer="Brother-MFC-J870DW")
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 POST / HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 1.1 Get-Printer-Attributes 1
D [30/Mar/2014:21:08:23 -0700] Get-Printer-Attributes ipp://localhost/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:23 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:23 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:23 -0700] Script header: 
D [30/Mar/2014:21:08:23 -0700] [CGI] Regular expression ".*Clean.*"
D [30/Mar/2014:21:08:23 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:23 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:23 -0700] [CGI] Regular expression ".*PrintSelfTestPage.*"
D [30/Mar/2014:21:08:23 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:23 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 POST / HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 1.1 Get-Jobs 1
D [30/Mar/2014:21:08:23 -0700] Get-Jobs ipp://localhost:631/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:23 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost:631/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:23 -0700] PID 8224 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1602 WAITING Closing on EOF
D [30/Mar/2014:21:08:23 -0700] cupsdCloseClient: 1602
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAcceptClient: 1601 from localhost:631 (IPv6)
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1601 GET /cups.css HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 162 GET /images/left.gif HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAcceptClient: 1614 from localhost:631 (IPv6)
D [30/Mar/2014:21:08:23 -0700] cupsdReadClient: 1614 GET /images/right.gif HTTP/1.1
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:23 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:23 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1614 GET /printers/Brother-MFC-J870DW HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:33 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/printers.cgi"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[26] = "SCRIPT_NAME=/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[28] = "PATH_INFO=/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[29] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[30] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[31] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[32] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[33] = "HTTP_REFERER=http://localhost:631/printers/Brother-MFC-J870DW"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[34] = "REQUEST_METHOD=GET"
D [30/Mar/2014:21:08:33 -0700] [CGI] envp[35] = "QUERY_STRING="
D [30/Mar/2014:21:08:33 -0700] [CGI] Started /usr/lib/cups/cgi-bin/printers.cgi (PID 8225)
I [30/Mar/2014:21:08:33 -0700] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=8225)
D [30/Mar/2014:21:08:33 -0700] cupsdSendCommand: 1614 file=1627
D [30/Mar/2014:21:08:33 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:33 -0700] cupsdAcceptClient: 1628 from localhost (Domain)
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 POST / HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 1.1 CUPS-Get-Default 1
D [30/Mar/2014:21:08:33 -0700] CUPS-Get-Default
D [30/Mar/2014:21:08:33 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [30/Mar/2014:21:08:33 -0700] [CGI] show_printer(http=0x7fb3dfb2c430, printer="Brother-MFC-J870DW")
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 POST / HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 1.1 Get-Printer-Attributes 1
D [30/Mar/2014:21:08:33 -0700] Get-Printer-Attributes ipp://localhost/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:33 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:33 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:33 -0700] Script header: 
D [30/Mar/2014:21:08:33 -0700] [CGI] Regular expression ".*Clean.*"
D [30/Mar/2014:21:08:33 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:33 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:33 -0700] [CGI] Regular expression ".*PrintSelfTestPage.*"
D [30/Mar/2014:21:08:33 -0700] [CGI] matches[0].rm_so=0
D [30/Mar/2014:21:08:33 -0700] [CGI] matches[1].rm_so=-1
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 POST / HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 1.1 Get-Jobs 1
D [30/Mar/2014:21:08:33 -0700] Get-Jobs ipp://localhost:631/printers/Brother-MFC-J870DW
D [30/Mar/2014:21:08:33 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost:631/printers/Brother-MFC-J870DW) from localhost
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1628 WAITING Closing on EOF
D [30/Mar/2014:21:08:33 -0700] cupsdCloseClient: 1628
D [30/Mar/2014:21:08:33 -0700] PID 8225 (/usr/lib/cups/cgi-bin/printers.cgi) exited with no errors.
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1614 GET /cups.css HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 162 GET /images/left.gif HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdReadClient: 1601 GET /images/right.gif HTTP/1.1
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:33 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:33 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:41 -0700] cupsdReadClient: 1601 GET /admin HTTP/1.1
D [30/Mar/2014:21:08:41 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:41 -0700] cupsdAuthorize: Authorized as ron using Basic
D [30/Mar/2014:21:08:41 -0700] [CGI] argv[0] = "/usr/lib/cups/cgi-bin/admin.cgi"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@morganland"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[14] = "USER=root"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Basic"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[26] = "SCRIPT_NAME=/admin"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/admin"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[28] = "REMOTE_USER=ron"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[30] = "HTTP_COOKIE=sessiontest=1; org.cups.sid=b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[31] = "HTTP_USER_AGENT=Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.22 (KHTML, like Gecko) Ubuntu Chromium/25.0.1364.160 Chrome/25.0.1364.160 Safari/537.22"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[32] = "HTTP_REFERER=http://localhost:631/"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[33] = "REQUEST_METHOD=GET"
D [30/Mar/2014:21:08:41 -0700] [CGI] envp[34] = "QUERY_STRING="
D [30/Mar/2014:21:08:41 -0700] [CGI] Started /usr/lib/cups/cgi-bin/admin.cgi (PID 8226)
I [30/Mar/2014:21:08:41 -0700] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=8226)
D [30/Mar/2014:21:08:41 -0700] cupsdSendCommand: 1601 file=1651
D [30/Mar/2014:21:08:41 -0700] [CGI] admin.cgi started...
D [30/Mar/2014:21:08:41 -0700] cupsdAcceptClient: 1652 from localhost (Domain)
D [30/Mar/2014:21:08:41 -0700] [CGI] http=0x7f624cbd8880
D [30/Mar/2014:21:08:41 -0700] [CGI] org.cups.sid cookie is "b0585b9b895c8d2aece3c05cf1d44811"
D [30/Mar/2014:21:08:41 -0700] [CGI] No form data, showing main menu...
D [30/Mar/2014:21:08:41 -0700] [CGI] /usr/share/cups/drivers/pscript5.dll: No such file or directory
D [30/Mar/2014:21:08:41 -0700] cupsdReadClient: 1652 POST / HTTP/1.1
D [30/Mar/2014:21:08:41 -0700] cupsdAuthorize: No authentication data provided.
D [30/Mar/2014:21:08:41 -0700] cupsdReadClient: 1652 1.1 Get-Subscriptions 1
D [30/Mar/2014:21:08:41 -0700] Get-Subscriptions ipp://localhost/
D [30/Mar/2014:21:08:41 -0700] Returning IPP successful-ok for Get-Subscriptions (ipp://localhost/) from localhost
D [30/Mar/2014:21:08:41 -0700] Script header: Content-Type: text/html;charset=utf-8
D [30/Mar/2014:21:08:41 -0700] Script header: 
D [30/Mar/2014:21:08:41 -0700] cupsdReadClient: 1652 WAITING Closing on EOF
D [30/Mar/2014:21:08:41 -0700] cupsdCloseClient: 1652
D [30/Mar/2014:21:08:41 -0700] PID 8226 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [30/Mar/2014:21:08:41 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [30/Mar/2014:21:08:43 -0700] cupsdReadClient: 1601 GET /admin/log/error_log? HTTP/1.1
D [30/Mar/2014:21:08:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [30/Mar/2014:21:08:43 -0700] cupsdAuthorize: Authorized as ron using Basic

---

### Post by Muahdib on 2014-03-31
again.. when I print anything.. the printers display lights up and show the icon for recieving data.

---

### Post by wagb278 on 2014-07-18
Muahdib, Did you ever get the Brother MFC-J870DW working over the network?

I have the same printer model and all I get after installing the drivers is a notice that the "Printer may not be connected".  I can ping the printer, so I have physical connectivity via the network, but any attempt to print a test page just reports the printer is not connected. 

Thanks

---

### Post by Muahdib on 2014-07-18
I have not found an answer to this problem yet. I thought I was being carful when I selected a brother printer wtih "linux" drivers. I did a few searches and did not find anyone complaining about the drivers.. and it was on sale.. so 

I am still running 12.04, I have found no solution to the problem. I have not spent lots of time on it either.

---

### Post by wagb278 on 2014-07-19
Muahdib, 

I got my (actually a friends) Brother MFC-J870DW printer to print under Linux Mint (derived from Ubuntu) and thouhgt I would pass on what I did in the hopes that you, or someone else will find this useful. 

I discovered a post [https://wiki.archlinux.org/index.php/CUPS#All_jobs_are_.22The_printer_is_not_responding.22]("https://wiki.archlinux.org/index.php/CUPS#All_jobs_are_.22The_printer_is_not_responding.22") that gave me the clue I needed.  My problem was that Linux reported the printer was not connected - "the pinter is not responding" and that on network printers - mine is using the wired network configuration with a static IP.  When the connection string in CUPS is of the form: [COLOR="#0000FF"]lpd://BRN_mac-address_of_printer/BINARY_P1[/COLOR] that mac-address string must resolve to the device being connected via DNS.  

The fix is to add an entry into the /etc/hosts file with the IP address of the printer and the name is the BRN_mac-address_of_printer.  After editing the /etc/hosts file adding that entry for my printer I restarted the computer to ensure the hosts file was re-loaded (not sure that was necessary).  Printing now works. 

I installed the Brother drivers on my Linux system using the relatively new driver install tool for Linux available on the Brother site.  If you need to reinstall drivers for the printer I suggest you use that tool.  Word of caution - make sure the directory you place that tool in does not have spaces in the directory name (the Brother script can't handle spaces in the directory name).

I also found newer versions of the firmware for this printer model on the Brother site.  I installed the updated firmware - but that didn't help solve my connection problem.  The Brother firmware update tool requires a Windows or Macintosh computer to run the tool.  I did not find how to update the firmware via a Linux box.  But again, the recent firmware updates don't address any connection issues.  

Hope this is of some help

---

### Post by Muahdib on 2014-07-22
wagb278,

you are the man... unless you'ur a gril, I didn't check your profile:) but even if your not a man... you are the MAN!! while this phrase is not in the sprit of  political correctness strangle-hold that is killing American.. and so on... you'ur still the man :)

this is the best lead/bit of information I have got. I don't know when I will get to try this as I am so stacked with work by the time I get home and deal with family/kids/broken stuff/homework/bugs(no one else at home will squesh on them!!)... i know im forgetting something, OH yeah, my wife. im lucky to get to my home office/computer desk. 

but... im really thankful you wrote this. I will give it a try ASAP.. and report back when I can.

---

