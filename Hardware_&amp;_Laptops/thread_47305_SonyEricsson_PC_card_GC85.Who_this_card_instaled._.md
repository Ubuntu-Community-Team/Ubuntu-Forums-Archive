---
title: "SonyEricsson PC card GC85.Who this card instaled. PLease answer."
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by Vitalij on 2005-07-08
Good afternoon!
I`m with LIthuania. I have PC card modem SonyEricsson PC Card GC85.
For Win OS i have driver, worked fine, but linux, i don`t now.......
Who have business with instaled this card  to linux, or Ubuntu.......
Please, answer.....
Thanks, Vitalij
Writing my e-mail, [email]vitalijz@user.harvista.lt[/email]

---

### Post by t3r0 on 2005-07-08
[QUOTE=Vitalij]Good afternoon!
I`m with LIthuania. I have PC card modem SonyEricsson PC Card GC85.
For Win OS i have driver, worked fine, but linux, i don`t now.......
Who have business with instaled this card  to linux, or Ubuntu.......
Please, answer.....
Thanks, Vitalij
Writing my e-mail, [email]vitalijz@user.harvista.lt[/email][/QUOTE]


Hi,

I just got the GC75E 5mins ago.... i'll let you know if (how!) i get it to work...  :wink: 

- tero

---

### Post by t3r0 on 2005-07-10
Hi,

atleast my card works just fine under linux....

first ensure that you have pcmcia modules loaded etc...

Open a Root terminal. 

And check that the card is detected correctly:
```

t3r0# cardctl info
PRODID_1="Sony Ericsson"
PRODID_2="GC75 PC Card"
PRODID_3="ML2029"
PRODID_4=""
MANFID=0221,2000
FUNCID=2

```

Then check that you have a sym link from /dev/modem => /dev/ttyS0
```

t3r0# ls -l /dev/modem
lrwxrwxrwx  1 root root 10 Jul 10 00:47 /dev/modem -> /dev/ttyS0

```

then install minicom:
```

$ aptitude install minicom

```

create the file /etc/chatscripts/<name> Where <name> is a name for the connection, for example the name of your ISP.

Then put the following lines to that file:
```

# abortstring
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
# modeminit
"" AT+CGDCONT=1,"IP","internet"
# ispnumber
OK-AT-OK ATDT*99***1#
# ispconnect
CONNECT ''
# postlogin

```
NOTE: this works with my isp, so you need to edit at least the lines
```

"" AT+CGDCONT=1,"IP","internet"

OK-AT-OK ATDT*99***1#

```
To match the settings of your ISP.. Then just save the file...

Then set the pin code for your SIM card using minicom...

```

$ minicom --noinit /dev/modem

```

And in that screen type following:
```

AT+CFUN=1,1
AT+CPIN=1234

```
Where 1234 is the PIN code for your SIM card.. 

NOTE: you need to set the pin code after every reboot..

TIP: for complete list of supported AT commands check the pdf file in sonyEricssons support page ;) 

Then close minicom, i dont remember the key command for that but just open a new console and type: killall minicom


OK, Thats ALL  \\:D/ 


Then just test:

```

$ pon <name> &

```

here is a example output:
```

t3r0# pon dna &
[1] 8728
t3r0# Serial connection established.
using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/modem
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe43ef6ac> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xe43ef6ac> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe43ef6ac> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xe43ef6ac> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x4d <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x3573ac1> <pcomp> <accomp>]
sent [LCP ConfAck id=0x4d <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x3573ac1> <pcomp> <accomp>]
sent [PAP AuthReq id=0x1 user="t3r0" password=<hidden>]
rcvd [PAP AuthAck id=0x1 "PAP access OK"]
Remote message: PAP access OK
PAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x4d <addr 62.78.105.0>]
sent [IPCP ConfNak id=0x4d <addr 10.0.0.1>]
rcvd [IPCP ConfNak id=0x1 <addr 62.78.105.166> <ms-dns1 217.78.192.22> <ms-dns3 217.78.192.78>]
sent [IPCP ConfReq id=0x2 <addr 62.78.105.166> <ms-dns1 217.78.192.22> <ms-dns3 217.78.192.78>]
rcvd [IPCP ConfNak id=0x1 <addr 62.78.105.166> <ms-dns1 217.78.192.22> <ms-dns3 217.78.192.78>]
rcvd [IPCP ConfReq id=0x4e <addr 10.0.0.1>]
sent [IPCP ConfAck id=0x4e <addr 10.0.0.1>]
rcvd [IPCP ConfAck id=0x2 <addr 62.78.105.166> <ms-dns1 217.78.192.22> <ms-dns3 217.78.192.78>]
not replacing default route to eth0 [192.168.0.3]
local  IP address 62.78.105.166
remote IP address 10.0.0.1
primary   DNS address 217.78.192.22
secondary DNS address 217.78.192.78
[B]Script /etc/ppp/ip-up started (pid 8741)
Script /etc/ppp/ip-up finished (pid 8741), status = 0x0[/B]

```

If you dont get any errors then just test the connection... :)

Now to close the connection type:
```

$ poff <name>

```


-- Tero :)

---

### Post by dgh on 2006-07-11
When I did```
pon <name> &
```, I got this:

```
The file /etc/ppp/peers/<name> does not exist. Please create it or use
a command line argument to use another file in the /etc/ppp/peers/ directory.
```

Then I created that script in /etc/ppp/peers/<name>. The I did ```
pon <name> &
``` again and got this:

```
/usr/sbin/pppd: In file /etc/ppp/peers/<name>: unrecognized option 'ABORT'
```

What should I do now?

---

### Post by t3r0 on 2006-07-17
Hi,

I don't know about that error, but here is my /etc/ppp/peers/provider file (provider == <name>)


```

# This optionfile was generated by pppconfig 2.3.5.
#
#
# hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/provider"
# disconnect "/usr/sbin/chat -v -f /etc/chatscripts/provider"
#debug
/dev/ttyS0
115200
defaultroute
#nodefaultroute
replacedefaultroute
# noipdefault
# user ""
# remotename tmobile
# ipparam tmobile
crtscts
lock
local
nodetach

usepeerdns

lcp-echo-failure 0
lcp-echo-interval 65535


```

no ABORT line there, so that might be the issue... 


- Tero

---

### Post by ]SiB[ on 2008-01-01
Hello, I have Ubuntu 7.10 and SE GC85 PCMCIA.

Download on the M$_OS this file:
[http://pl.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.2-5_i386.deb]("http://pl.archive.ubuntu.com/ubuntu/pool/main/m/minicom/minicom_2.2-5_i386.deb")

$
$ [COLOR="YellowGreen"]**sudo su**[/COLOR]
[sudo] password for user:*********************Enter**
root@localmachine[COLOR="Red"]#[/COLOR]
[COLOR="Red"]#[/COLOR] # - from only root
# [COLOR="YellowGreen"]$[/COLOR] - from user
# [COLOR="YellowGreen"]**user_command**[/COLOR]
# [COLOR="YellowGreen"]**sudo root_command**[/COLOR]
[COLOR="Red"]# **root_command**[/COLOR]
# [COLOR="Red"]**logout**[/COLOR] ;# Or simple exit
$
$ [COLOR="YellowGreen"]**apropos pcmcia**[/COLOR]
lspcmcia (8)         - PCMCIA card control utility
pccardctl (8)        - PCMCIA card control utility
$
$ [COLOR="YellowGreen"]**pccardctl info**[/COLOR]
PRODID_1="Sony Ericsson"
PRODID_2="GC85 PC Card"
PRODID_3="ML2022"
PRODID_4=""
MANFID=0221,2000
FUNCID=2
$
$ [COLOR="YellowGreen"]**ls -l /dev/modem**[/COLOR]
ls: /dev/modem: No such file or directory
$
$ [COLOR="YellowGreen"]**hal-device |grep ttyS**[/COLOR] ;# In short way
  linux.device_file = '**/dev/ttyS2**'  (string)
  serial.device = '**/dev/ttyS2**'  (string)
  linux.sysfs_path = '/sys/class/tty/ttyS2'  (string)
$
$ [COLOR="YellowGreen"]**hal-device**[/COLOR] ;# Only info for pcmcia
27: udi = '/org/freedesktop/Hal/devices/pcmcia__1__1_serial_platform_2'
  linux.device_file = '**/dev/ttyS2**'  (string)
  serial.device = '**/dev/ttyS2**'  (string)
  serial.physical_device = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.capabilities = { 'serial' } (string list)
  info.udi = '/org/freedesktop/Hal/devices/pcmcia__1__1_serial_platform_2'  (string)
  linux.subsystem = 'tty'  (string)
  info.product = '**GC85 PC Card**'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.sysfs_path = '/sys/class/tty/ttyS2'  (string)
  serial.type = 'platform'  (string)
  info.category = 'serial'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  serial.port = 2  (0x2)  (int)

85: udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'
  pcmcia.card_id = 8192  (0x2000)  (int)
  info.bus = 'pcmcia'  (string)
  pcmcia.prod_id1 = '**Sony Ericsson**'  (string)
  pcmcia.manf_id = 545  (0x221)  (int)
  pcmcia.func_id = 2  (0x2)  (int)
  pcmcia.vendor = '**Sony Ericsson**'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pcmcia__1__1'  (string)
  pcmcia.prod_id2 = '**GC85 PC Card**'  (string)
  linux.subsystem = 'pcmcia'  (string)
  pcmcia.prod_id3 = 'ML2022'  (string)
  info.vendor = '**Sony Ericsson**'  (string)
  info.subsystem = 'pcmcia'  (string)
  info.product = '**GC85 PC Card**'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/0.0'  (string)
  pcmcia.product = '**Sony Ericsson**'  (string)
  pcmcia.socket_number = 0  (0x0)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_476'  (string)
  info.linux.driver = 'serial_cs'  (string)
#
# # By root user from hire
# [COLOR="Red"]**ln -s /dev/ttyS2 /dev/modem**[/COLOR]
#
$ [COLOR="YellowGreen"]**ls -l /dev/ttyS2**[/COLOR]
crw-rw---- 1 root dialout 4, 66 2008-01-01 16:31 /dev/ttyS2
$
$ [COLOR="YellowGreen"]**ls -l /dev/modem**[/COLOR]
lrwxrwxrwx 1 root root 10 2008-01-01 16:54 /dev/modem -> /dev/ttyS2
#
# [COLOR="Red"]**touch /etc/chatscripts/gprs-c**[/COLOR]
#
# [COLOR="Red"]**vim /etc/chatscripts/gprs-c**[/COLOR] ;# mcedit, joe, vi, kwrite or other editors
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
"" AT+CGDCONT=1,"IP","**[www.plusgsm.pl](www.plusgsm.pl)**"
OK-AT-OK ATDT***99***1#**
CONNECT ''

# # [www.plusgsm.pl](www.plusgsm.pl) is APN for POLAND_ISP
#
# [COLOR="Red"]**vim /etc/chatscripts/gprs-disc**[/COLOR] 
"" "\K"
"" "+++ATH0"

#
# [COLOR="Red"]**vim /etc/ppp/peers/gprs**[/COLOR] 
noauth
connect "/usr/sbin/chat -v -f **/etc/chatscripts/gprs-c**"
disconnect "/usr/sbin/chat -v -f **/etc/chatscripts/gprs-disc**"
**/dev/ttyS2**
115200
defaultroute
replacedefaultroute
crtscts
lock
local
nodetach
usepeerdns
lcp-echo-failure 0
lcp-echo-interval 65535
 
# # /dev/ttyS2 is my serial.device
$
$ [COLOR="YellowGreen"]**minicom --noinit /dev/modem**[/COLOR]
minicom: OSTRZEúENIE: plik konfiguracyjny nie znaleziony, uúywam
		      ustawieî standardowych.

#//clear screen

Witaj w minicom-ie 2.2

OPCJE: I18n 
Skomilowany dnia Apr 27 2007, 15:50:20.
Port /dev/tty8

              Wci#nij CTRL-A Z po pomoc na temat specjalnych klawiszy

[COLOR="YellowGreen"]**CTRL-A Q Enter**[/COLOR]
$
$ [COLOR="YellowGreen"]**minicom**[/COLOR] 
$ # the same error
$
$ [COLOR="YellowGreen"]**minicom -o /dev/modem**[/COLOR]
//the same error
//clear screen

[COLOR="YellowGreen"][B]CTRL+A Z O 3position(settings serial port) A /dev/ttyS2 Enter Enter 6pos(save by _dev_modem) 8pos(exit)
CTRL+A Q Yes=Enter[/B][/COLOR]
$
$ [COLOR="YellowGreen"]**minicom -o /dev/modem**[/COLOR]
//without start error
[COLOR="YellowGreen"][B]CTRL+A A Enter
AT+CFUN=1,1[/B][/COLOR]
OK
[COLOR="YellowGreen"]**AT+CPIN=_5647_**[/COLOR]
OK
[COLOR="YellowGreen"]**CTRL+A Q Yes=Enter**[/COLOR]
 
$ # 5647 is PIN from ISP
$ 
$ [COLOR="YellowGreen"]**pon gprs &**[/COLOR]
[1] 6159
$
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyS2
appear to have received our own echo-reply!
Remote message: PAP access OK
PAP authentication succeeded
replacing old default route to eth0 [192.168.1.1]
Cannot determine ethernet address for proxy ARP
local  IP address 77.113.112.149
remote IP address 77.113.112.0
primary   DNS address 212.2.96.51
secondary DNS address 212.2.96.52

$
$ [COLOR="YellowGreen"]**plog**[/COLOR]
Jan  1 21:43:24 sib-laptop pppd[6313]: Remote message: PAP access OK
Jan  1 21:43:24 sib-laptop pppd[6313]: PAP authentication succeeded
Jan  1 21:43:26 sib-laptop pppd[6313]: replacing old default route to eth0 [192.168.1.1]
Jan  1 21:43:26 sib-laptop pppd[6313]: Cannot determine ethernet address for proxy ARP
Jan  1 21:43:26 sib-laptop pppd[6313]: local  IP address 77.113.112.149
Jan  1 21:43:26 sib-laptop pppd[6313]: remote IP address 77.113.112.0
Jan  1 21:43:26 sib-laptop pppd[6313]: primary   DNS address 212.2.96.51
Jan  1 21:43:26 sib-laptop pppd[6313]: secondary DNS address 212.2.96.52

$
$  [COLOR="YellowGreen"]**ifconfig ppp0**[/COLOR]
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:77.113.112.149  P-t-P:77.113.112.0  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:3 
          RX bytes:18837 (18.3 KB)  TX bytes:5708 (5.5 KB)

$
$ [COLOR="YellowGreen"]**ping [www.plusgsm.pl](www.plusgsm.pl) -c 4**[/COLOR]
PING [www.plusgsm.pl](www.plusgsm.pl) (212.2.96.31) 56(84) bytes of data.
64 bytes from w3.plusgsm.pl (212.2.96.31): icmp_seq=1 ttl=124 time=999 ms
64 bytes from w3.plusgsm.pl (212.2.96.31): icmp_seq=2 ttl=124 time=759 ms
64 bytes from w3.plusgsm.pl (212.2.96.31): icmp_seq=3 ttl=124 time=783 ms
64 bytes from w3.plusgsm.pl (212.2.96.31): icmp_seq=4 ttl=124 time=679 ms

--- [www.plusgsm.pl](www.plusgsm.pl) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 4039ms
rtt min/avg/max/mdev = 679.919/805.923/999.801/118.385 ms, pipe 2

#
# [COLOR="Red"]**apt-get install links**[/COLOR]
...
Pob: 1 [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) gutsy/universe links 0.99+1.00pre12-1.2 [368kB]
Pobrano 368kB w 1m26s (**4264B/s**)
...
$ # GPRS is 805ms and 4,5kB/s
$
$ 
# [COLOR="Red"]**shutdown -r now**[/COLOR]

$
$
# [COLOR="Red"]**ln -l /dev/ttyS2 /dev/modem**[/COLOR]
$ [COLOR="YellowGreen"]**pon gprs &**[/COLOR]
[1] 6175
$
Connect script failed
$  [COLOR="YellowGreen"]**plog**[/COLOR]
Jan  1 23:27:13 sib-laptop chat[6171]: send (AT^M)
Jan  1 23:27:13 sib-laptop chat[6171]: expect (OK)
Jan  1 23:27:13 sib-laptop chat[6171]: AT^M^M
Jan  1 23:27:13 sib-laptop chat[6171]: OK
Jan  1 23:27:13 sib-laptop chat[6171]:  -- got it 
Jan  1 23:27:13 sib-laptop chat[6171]: send (ATDT*99***1#^M)
Jan  1 23:27:13 sib-laptop chat[6171]: expect (CONNECT)
Jan  1 23:27:13 sib-laptop chat[6171]: ^M
Jan  1 23:27:13 sib-laptop chat[6171]: ATDT*99***1#^M^M
Jan  1 23:27:13 sib-laptop chat[6171]: ERROR^M
Jan  1 23:28:58 sib-laptop chat[6178]: alarm
Jan  1 23:28:58 sib-laptop chat[6178]: Failed
Jan  1 23:28:58 sib-laptop pppd[6175]: Connect script failed
Jan  1 23:28:58 sib-laptop pppd[6175]: Exit.

$
$ [COLOR="YellowGreen"]**minicom -o /dev/modem**[/COLOR]
//without start error
[COLOR="YellowGreen"][B]CTRL+A A Enter
AT+CFUN=1,1[/B][/COLOR]
OK
[COLOR="YellowGreen"]**AT+CPIN=5647**[/COLOR]
OK
[COLOR="YellowGreen"]**CTRL+A Q Yes=Enter**[/COLOR]

$
$ [COLOR="YellowGreen"]**pon gprs &**[/COLOR]
 Serial connection established.
 ...
$
$  [COLOR="YellowGreen"]**poff gprs &**[/COLOR]
[2] 6293
$ Terminating on signal 15
Connect time 0.2 minutes.
Sent 0 bytes, received 0 bytes.
restoring old default route to eth0 [192.168.1.1]
Connection terminated.
Serial link disconnected.

$
$ # To not use ln and minicom after any reboot edit this file:
#
# [COLOR="Red"]**vim /etc/chatscripts/gprs-c**[/COLOR] ;# mcedit, joe, vi, kwrite or other editors
ABORT BUSY
ABORT 'NO CARRIER'
ABORT VOICE
ABORT 'NO DIALTONE'
ABORT 'NO DIAL TONE'
ABORT 'NO ANSWER'
ABORT DELAYED
[B]"" 'AT+CFUN=1,1'
"" 'AT+CPIN=5647'[/B]
"" AT+CGDCONT=1,"IP","www.plusgsm.pl"
OK-AT-OK ATDT*99***1#
CONNECT ''

$
$ # after reboot simply use:
$ [COLOR="YellowGreen"]**pon gprs &**[/COLOR]
...
$ [COLOR="YellowGreen"]**poff**[/COLOR]
# [COLOR="Red"]**shutdown -h now**[/COLOR] # Bye

---

### Post by ]SiB[ on 2008-01-09
It works for 'Option Globetrotter EDGE' too.

$ [COLOR="YellowGreen"]**pccardctl info**[/COLOR]
PRODID_1="GlobeTrotter"
PRODID_2="EDGE"
PRODID_3="ML2132C2"
PRODID_4=""
MANFID=0314,0007
FUNCID=2

---

