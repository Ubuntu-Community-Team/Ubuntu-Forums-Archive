---
title: "slmodemd installed, but still can't connect to internet"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by AlaskaLass on 2005-07-16
Hi, 

I am a new Ubuntu user, the install on my laptop went well.  But I have one of those internal software modems, so I cannot connect to the internet.  Fortunately, I have access to another computer.  I searched around and found instructions to:

wget -c [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

Of course, I can't do apt-get from my laptop since I can't connect to the internet.   I downloaded the sl-modem-modules....deb from the recommended site.  Then I searched and found sl-modem-daemon_2.9.9-1_i386.deb.  I wrote both to a floppy and transfered to the laptop (directory /home/xxx/packages-new), then:

root@mylaptop:/home/xxx/packages-new # dir
sl-modem-daemon_2.9.9-1_i386.deb
sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb

root@mylaptop:/home/xxx/packages-new # dpkg -i sl-modem-modules-*.deb
Selecting previously deselected package sl-modem-modules-2.6.10-5-386.
(Reading database ... 58119 files and directories currently installed.)
Unpacking sl-modem-modules-2.6.10-5-386 (from sl-modem-modules-2.6.10-5-386_2.9. 9a-1ubuntu2+2.6.10-34_i386.deb) ...
Setting up sl-modem-modules-2.6.10-5-386 (2.9.9a-1ubuntu2+2.6.10-34) ...

root@mylaptop:/home/xxx/packages-new # dpkg -i sl-modem-daemon*.deb
Selecting previously deselected package sl-modem-daemon.
(Reading database ... 58126 files and directories currently installed.)
Unpacking sl-modem-daemon (from sl-modem-daemon_2.9.9-1_i386.deb) ...
Setting up sl-modem-daemon (2.9.9-1) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 column s wide.)
debconf: falling back to frontend: Readline
Starting SmartLink Modem driver for: hw:1.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

Then I went to the internet connection setup item in the system menu, and configured the modem with /dev/modem and my local dial-up information.  But when I try to connect, nothing happens.

How do I find out what's wrong?  Many, many thanks to any kind person who can help me.

---

### Post by s_p_a_r_k_y on 2005-07-18
try things from the command line. there is a program slmodemd I think, run that with --help and you get all types of information...I think 
Then set the country code from
slmodemd --countrylist

and once you found it replace val with it
slmodemd --country=VAL

I don't currently use my modem, so thats all I can help with.

---

### Post by AlaskaLass on 2005-07-18
Thanks for the tip, Sparky.  As much as I can tell, slmodemd is running with the correct country setting (default = USA).  The daemon is starting at boot, and the /dev/modem symlink to ttySL0 is in place.  

I think perhaps my problem lies somewhere in the gnome network configurations, but I can't seem to find out how to check on that.   The little panel applet for monitoring the network shows "lo" regardless of whether I've tried to connect through the modem or not.  The network tools program shows a "loopback" network connection, that I can't edit, and that seems to be running all the time.

Can anybody explain this loopback or "lo" network connection --why is it running all the time?  --could it be interfering with my modem dial-up connection?  

Also, is there some way of testing my modem configuration to make sure it is correct?

Many thanks!

---

### Post by s_p_a_r_k_y on 2005-07-20
[QUOTE=AlaskaLass]Thanks for the tip, Sparky.  As much as I can tell, slmodemd is running with the correct country setting (default = USA).  The daemon is starting at boot, and the /dev/modem symlink to ttySL0 is in place.  

I think perhaps my problem lies somewhere in the gnome network configurations, but I can't seem to find out how to check on that.   The little panel applet for monitoring the network shows "lo" regardless of whether I've tried to connect through the modem or not.  The network tools program shows a "loopback" network connection, that I can't edit, and that seems to be running all the time.

Can anybody explain this loopback or "lo" network connection --why is it running all the time?  --could it be interfering with my modem dial-up connection?  

Also, is there some way of testing my modem configuration to make sure it is correct?

Many thanks![/QUOTE]

The lo device is the loopback device. Try pinging 127.0.0.1
thats your loopback device as certain server (apache) need a device to serve on if there is no other connection.

if you type if ifconfig
do you see anything else like eth0? wlan? ppp0? I have ppp0 show up in my Network Settings, but its not configured as I have no use for it, does that show up in yours? System->Administration->Networking

I can't help much more as I have not used modems on Linux in ages as I've always had high speed connections at work and home. What program are you using to setup your connection?

In the network settings, do you have the correct modem port set? can you turn on the volume to see if the modem makes any noise at all?

---

### Post by AlaskaLass on 2005-07-21
HEY SPARKY, MY RESPONSES IN ALL CAPS...

The lo device is the loopback device. Try pinging 127.0.0.1
thats your loopback device as certain server (apache) need a device to serve on if there is no other connection.

I SENT PING REQUEST USING MENU>SYSTEM TOOLS>NETWORK TOOLS,[TAB]=PING, NETWORK ADDRESS=127.0.0.1, I GOT BACK 64 BYTES.  I ALSO NOTICED ON [TAB]=DEVICES, THAT ONLY THE LOOPBACK INTERFACE (LO) IS LISTED UNDER NETWORK DEVICES. IP INFORMATION FOR "LO" SHOWS IPv4---127.0.0.1---255.0.0.0 AND IPv6---::1---128, AND THE INTERFACE STATISTICS SHOW TRANSMITTED AND RECEIVED BYTES ACCRUING EVERY FEW SECONDS. PRESUMABLY ALL THIS IS AS IT SHOULD BE...?

if you type if ifconfig
do you see anything else like eth0? wlan? ppp0? 

TYPING "IF IFCONFIG" GAVE ME AN INPUT PROMPT; SEEMS IT WAS THE CONFIGURATION PROGRAM - NOT KNOWING WHAT TO ENTER, I USED CTRL-C TO EXIT.  AFTER READING A BIT ABOUT THE "IFCONFIG" COMMAND, I TYPED "IFCONFIG -A" AND GOT:

eth0      Link encap:Ethernet  HWaddr 00:A0:CC:DD:02:BE  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:541535 (528.8 KiB)  TX bytes:541535 (528.8 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

THERE'S THE LOOPBACK, AND THE ETHERNET PORT I'M NOT USING, BUT WHAT IS "SIT0"?  I GUESS ALL THOSE ERRORS LISTED UNDER "LO" ARE THE TRANSMISSIONS THAT HAPPEN EVERY FEW SECONDS AND ARE NORMAL?

I have ppp0 show up in my Network Settings, but its not configured as I have no use for it, does that show up in yours? System->Administration->Networking

UNDER MENU>SYSTEM>ADMINSTRATION>NETWORKING SETTINGS, I HAVE TWO CONNECTIONS:  MODEM-INTERFACE PPP0 AND ETHERNET-INTERFACE ETH0.  NEITHER WAS CONFIGURED TO START.  AFTER INSTALLING THE SLMODEM MODULES AND DAEMON, I CONFIGURED THE MODEM CONNECTION WITH MY LOCAL DIAL-UP AND ACCOUNT INFORMATION.  BUT WHEN I CLICK ON THE "ACTIVATE" BUTTON, NOTHING SEEMS TO HAPPEN.

I can't help much more as I have not used modems on Linux in ages as I've always had high speed connections at work and home. What program are you using to setup your connection?

I WISH I HAD HIGH-SPEED! BUT IT IS DIAL-UP FOR ME AT PRESENT.  I REALLY APPRECIATE YOUR HELP EVEN THOUGH YOU HAVEN'T USED A MODEM CONNECTION IN AWHILE.  I USED THE NETWORKING SETTINGS TOOL (ABOVE) TO SETUP THE CONNECTION.

In the network settings, do you have the correct modem port set? can you turn on the volume to see if the modem makes any noise at all?

I THINK IT IS THE CORRECT PORT, IT IS /DEV/MODEM AND WHEN I INSTALLED SLMODEMD I GOT THE MESSAGE THAT IT HAD CREATED THE SYMLINK FROM /DEV/MODEM TO DEV/TTYSL0.  I TURNED THE VOLUME TO HIGH AND GOT NO SOUND, AND STILL NO TRANSMISSION THROUGH THE PHONE, WHEN I ACTIVATED THE CONNECTION.

MORE INFO:  I'VE BEEN SEARCHING AROUND FOR TOOLS, AND I FOUND WVDIAL.  WHEN I RAN WVDIALCONF, IT FOUND THE MODEM ON /DEV/TTYSL0 AND CONFIGURED IT.  THE MAN PAGE FOR WVDIALCONF SAID I HAD TO FINISH THE CONFIGURATION BY GIVING THE DIAL-UP NUMBER AND ACCOUNT NAME/PASSWORD MYSELF.  I EDITED THE /ETC/WVDIAL.CONF FILE AND THEN:

root@laptop:/etc # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT1234567
--> Waiting for carrier.
ATDT1234567
CONNECT 50667
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT1234567
--> Waiting for carrier.
Welcome to 3Com Total Control HiPer ARC (TM)
Networks That Go The Distance (TM)
login:
ATDT1234567
Password:
--> Timed out while dialing.  Trying again.
--> Sending: ATDT1234567
--> Waiting for carrier.
ATDT1234567
Login Incorrect

AT THIS POINT IT SEEMED TO HANG FOREVER, SO I SENT CTRL-C TO EXIT THE PROGRAM.

login: Caught signal #2!  Attempting to exit gracefully...
--> Disconnecting at Wed Jul 20 22:29:00 2005

BUT IT DID NOT DISCONNECT, I HAD TO PHYSICALLY UNPLUG THE MODEM CORD TO GET IT TO QUIT TRYING.  RIGHT AWAY I DOUBLE CHECKED MY DIAL-UP PHONE NUMBER, USER NAME AND PASSWORD, AND THEY WERE ALL CORRECT.  (THE PHONE NUMBER ISN'T REALLY 123-4567, I JUST THOUGHT IT BEST NOT TO BROADCAST THE REAL NUMBER) 

I DON'T REALLY KNOW WHAT I'M DOING WITH WVDIAL, BUT IT SEEMS TO INDICATE THAT THE DEVICE EXISTS AND SLMODEMD CAN USE IT.  BUT SOMETHING GOES WRONG WITH THE REST OF THE WVDIAL CONFIGURATION.  AND THE MENU NETWORK TOOL CAN'T SEEM TO USE /DEV/MODEM AT ALL.

---

### Post by eeried on 2005-07-21
How did you install slmodemd? Did you copy the script somewhere?

What a vexing matter these winmodems are! ](*,)

---

### Post by AlaskaLass on 2005-07-22
Hi eeried,

First I tried searching the ubuntu FAQ and wiki/wikipedia first for "slmodemd", but didn't get any results back.  So I followed instructions I found on the unofficial ubuntu 5.04 starter guide (see first post above). 

There was some confusion on my part while trying to follow the instructions.  Since I can't connect to the internet yet, I can't do those automatic "get" commands that are recommended.  I am new to a debian-based system and was using the apt commands for the first time, but the install return messages seemed to indicate that things went OK (see first post).

---

