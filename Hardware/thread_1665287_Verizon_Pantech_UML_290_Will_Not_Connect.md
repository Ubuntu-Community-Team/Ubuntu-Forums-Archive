---
title: "Verizon Pantech UML 290 Will Not Connect"
date: 2011-01-12
forum: Hardware
---

### Post by raywjohnson on 2011-01-12
I searched around a bit before committing to upgrading to the Pantech UML 290. All indications were that it would work on Ubuntu out of the box.

I found and followed the instructions here: 

[http://www.pagey.info/2011/01/using-pantech-uml290-on-ubuntu-linux.html](http://www.pagey.info/2011/01/using-pantech-uml290-on-ubuntu-linux.html)

All went well. Accept.... it will not connect.

I tested the modem on Windoz XP/VZAcess, worked perfect. 

I have tried a number of different settings (like: *99***3# - setting the username/password). No connection. 

I shows up in the Network Manager (Verizon 4G LTE) and the "Enable Mobile Broadband" is checked.

Has anyone else found the missing element to make this work?

Using Ubuntu 10.04 LTS - the Lucid Lynx. Must I upgrade to 10.10?

--RayJ

---

### Post by raywjohnson on 2011-01-12
UPDATE:

Still no connection via Network Manager.

However, I did get wvdial to make a connection. Posting here so that it may help someone else.

I gathered data from these posts/threads:
[http://ubuntuforums.org/showthread.php?p=10298982](http://ubuntuforums.org/showthread.php?p=10298982)
and
[http://ubuntuforums.org/showthread.php?p=10220571](http://ubuntuforums.org/showthread.php?p=10220571)

Here is my config:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
Init4 = ATE0V1
Init5 = AT+CPIN?
Init6 = AAT+CLCK="SC",2
Init7 = AT+GCAP?
Init8 = AT+CMEE=1
Modem Type = USB Modem 
Stupid Mode = 3
New PPPD = yes
Dial Command = atdt
Carrier Check = no
ISDN = 0

[Dialer Verizon4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########@vzw4g.com
Password = vzw
```

(########## = your modems phone number)

command: sudo wvdial Verizon4G

(note: wvdial has permissions issue if not running as root)

```
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
```Over and over.

Here is the terminal output:

```
PROMPT:$ sudo wvdial Verizon4G
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
OK
--> Sending: ATE0V1
ATE0V1
OK
--> Sending: AT+CPIN?
+CPIN: READY
OK
--> Sending: AAT+CLCK="SC",2
+CLCK: 0
OK
--> Sending: AT+GCAP?
+GCAP: +CIS707-A, CIS-856, CIS-856-A, +CGSM, +CLTE1
OK
--> Sending: AT+CMEE=1
OK
--> Modem initialized.
--> Sending: atdt*99***3#
--> Waiting for carrier.
CONNECT 100000000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Jan 12 16:43:59 2011
--> Pid of pppd: 6334
--> pppd: &#65533;&#65533;a 
--> Using interface ppp0
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> pppd: &#65533;&#65533;a 
--> local  IP address xx.xx.xx.xx
--> pppd: &#65533;&#65533;a 
--> remote IP address xx.xx.xx.xx
--> pppd: &#65533;&#65533;a 
--> primary   DNS address xx.xx.xx.xx
--> pppd: &#65533;&#65533;a 
--> secondary DNS address xx.xx.xx.xx
--> pppd: &#65533;&#65533;a 
```

I am looking for a means of running pppd as a normal user.

--RayJ

---

### Post by raywjohnson on 2011-01-15
> **raywjohnson said:**
> I am looking for a means of running pppd as a normal user.

Finally found the answer to this.

Found this: [Re: [SOLVED] GNOME PPP Check permissions]("http://ubuntuforums.org/showpost.php?p=8854531&postcount=11")

So, I set /usr/sbin/pppd to allow anyone to run/execute it.

```
sudo chmod +x /usr/sbin/pppd
```

Then, to fix the "Warning: Could not modify /etc/ppp/chap-secrets: Permission denied" issue. I set it to group rw and changed the group to dip.


```

sudo chmod 660 /etc/ppp/chap-secrets

sudo chgrp dip /etc/ppp/chap-secrets

```

If you are not already in the dip group, then:

```
sudo adduser YOUR_USERNAME dip
```

Now I can wvdial as a regular user!

Next project: GUI for wvdial.

--RayJ

---

### Post by raywjohnson on 2011-01-16
> **raywjohnson said:**
> Next project: GUI for wvdial.

Alrighty then!

The following code is, at best, a crude effort. It works on my machine and takes a few things for granted. It has no real error checking. I created it so that I could enable and disable my Verizon connection via wvdial without having a terminal window open the whole time. 

As happened the every time I have upgraded to a new Verizon device/modem. Network Manager is behind the curve. Once they catch up, the unit will connect via Network Manager and I will no longer need the use of wvdial.

Anyway, here is the Bash script: guiwvdial
```
#!/bin/bash

usage="Usage: guiwvdial CONNECTION_NAME";

if [ -z "$1" ]; then
 echo "$usage";
 exit 1;
fi

#name the var
connect_to="$1"

#to prevent more that one instance
LOCKFILE=~/wvdial_$connect_to.connect.lock
[ -f $LOCKFILE ] && exit 0
trap "{ rm -f $LOCKFILE ; exit 255; }" EXIT
touch $LOCKFILE

#Get active connection
test_cnnct=$(ps -eo command,pid | grep "^wvdial $connect_to")

#PID
xpid_cnnct=${test_cnnct/wvdial $connect_to/}

#Name
xconnected=${test_cnnct/wvdial /}
xconnected=${xconnected/$xpid_cnnct/}

if [ "$test_cnnct" == "" ]; then
  zenity --question --text "[$connect_to] not connected.\nConnect?"
  ans=$?
  if [ "$ans" == 1 ]; then
    #no-do nothing
    exit 1
  fi
  exec wvdial $connect_to &

  TEST=""
  (
    while [ ! "$TEST" ]; do
      TEST=`ifconfig -s | grep ^ppp`
      echo ""
      sleep 1
    done
  ) | tee >(zenity --progress --pulsate --auto-close --text="Connecting..." --title="wvdial $connect_to")

  zenity --info --text "[$connect_to] Connected!"

  exit 0
else
  zenity --question --text "[$connect_to] onnected.\nDisconnect?"
  ans=$?
  if [ "$ans" == 1 ]; then
    #no-do nothing
    exit 1
  fi
  kill -INT $xpid_cnnct
  zenity --info --text "[$connect_to] Disconnected"
  exit 1
fi

exit 0

```

You should use it only as a basis for your own system. USE AT YOUR OWN RISK.

Enjoy!

--RayJ

---

### Post by mdurham on 2011-02-03
Hi Ray, I see that you had a conversation bit only with yourself so I thought I'd say thanks for the info and all your effort. I discovered these problems myself as my cable stopped working and I had to use dial-up. I wonder why these things are in such disarray?
Cheers, Mike

---

### Post by NYCeyes on 2011-03-30
Hi Friends:

Thank you Ray for you very helpful posts. Network Manager on Fedora 14 does not work for me (despite it working for others). So I found your posts here and tried them. I am able to connect with success (albeit sometimes having to unplug and reconnect the UML290 device).

The problem I'm having is that after I connect and a "ppp0" interface is created (see below), and entries are added to the routing table (again see below), and with no entries made to /etc/resolv.conf (again see below), I cannot actually connect to the internet.

See the following outputs ...
#############################################
nmvega@e6510$ ifconfig ppp0
ppp0   Link encap:Point-to-Point Protocol  
          inet addr:10.171.182.101  P-t-P:69.83.13.52  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 b)  TX bytes:9798 (9.5 KiB)

nmvega@e6510$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
69.83.13.52     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
0.0.0.0            0.0.0.0         0.0.0.0                U         0 0          0 ppp0

nmvega@e6510$ cat /etc/resolv.conf
# Generated by NetworkManager
# No nameservers found; try putting DNS servers into your
# ifcfg files in /etc/sysconfig/network-scripts like so:
#
# DNS1=xxx.xxx.xxx.xxx
# DNS2=xxx.xxx.xxx.xxx
# DOMAIN=lab.foo.com bar.foo.com

nmvega@e6510$ grep hosts /etc/nsswitch.conf
hosts:      files dns

... [ snippet of wvdial session ] ...
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Mar 30 21:49:05 2011
--> Pid of pppd: 2600
--> Using interface ppp0
--> local  IP address 10.171.182.101
--> remote IP address 69.83.13.52
--> primary   DNS address 69.78.134.231
--> secondary DNS address 69.78.80.231
##########################################


So, in review, I can't ping the remote IP address "69.83.13.52". I can only ping the local
IP address. I must say the routing table looks strange, but maybe P-t-P works this
way in routing tables. Also, why no entry into resolv.conf? Hmm.

Do you get similar output in your working case? And any ideas?

Thanks,
Noel

---

### Post by raywjohnson on 2011-04-14
> **mdurham said:**
> Hi Ray, I see that you had a conversation bit only with yourself so I thought I'd say thanks for the info and all your effort. I discovered these problems myself as my cable stopped working and I had to use dial-up. I wonder why these things are in such disarray?
Cheers, Mike

Thanks Mike! 

Sorry for the late reply. 

I know for a fact that Verizon has a version of VZAccess for Linux. It comes with Red Hat Enterprise. The problem could easily be solved if Verizon would release it for the rest of us.

--RayJ

---

### Post by raywjohnson on 2011-04-14
> **NYCeyes said:**
> Hi Friends:

Thank you Ray for you very helpful posts. Network Manager on Fedora 14 does not work for me (despite it working for others). So I found your posts here and tried them. I am able to connect with success (albeit sometimes having to unplug and reconnect the UML290 device).

The problem I'm having is that after I connect and a "ppp0" interface is created (see below), and entries are added to the routing table (again see below), and with no entries made to /etc/resolv.conf (again see below), I cannot actually connect to the internet.

See the following outputs ...
#############################################
nmvega@e6510$ ifconfig ppp0
ppp0   Link encap:Point-to-Point Protocol  
          inet addr:10.171.182.101  P-t-P:69.83.13.52  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 b)  TX bytes:9798 (9.5 KiB)

nmvega@e6510$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
69.83.13.52     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
0.0.0.0            0.0.0.0         0.0.0.0                U         0 0          0 ppp0

nmvega@e6510$ cat /etc/resolv.conf
# Generated by NetworkManager
# No nameservers found; try putting DNS servers into your
# ifcfg files in /etc/sysconfig/network-scripts like so:
#
# DNS1=xxx.xxx.xxx.xxx
# DNS2=xxx.xxx.xxx.xxx
# DOMAIN=lab.foo.com bar.foo.com

nmvega@e6510$ grep hosts /etc/nsswitch.conf
hosts:      files dns

... [ snippet of wvdial session ] ...
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Mar 30 21:49:05 2011
--> Pid of pppd: 2600
--> Using interface ppp0
--> local  IP address 10.171.182.101
--> remote IP address 69.83.13.52
--> primary   DNS address 69.78.134.231
--> secondary DNS address 69.78.80.231
##########################################


So, in review, I can't ping the remote IP address "69.83.13.52". I can only ping the local
IP address. I must say the routing table looks strange, but maybe P-t-P works this
way in routing tables. Also, why no entry into resolv.conf? Hmm.

Do you get similar output in your working case? And any ideas?

Thanks,
Noel

Hi Noel,

Not sure what is preventing your connection. On my system, /etc/resolv.conf is not used for PPP. This file is: /etc/ppp/resolv.conf

--RayJ

PS: I made the mistake of pluging my UML290 into an XP box and letting it upgrade the firmware. Now my script fails to connect, back to the drawing board!

Here is the output:
```
./guiwvdial Verizon4G
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.

--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0

AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
ERROR
--> Bad init string.
```

---

### Post by raywjohnson on 2011-04-14
Alrighty then!

Got connected again. Here is the updated /etc/wvdial.conf

```
[Dialer Defaults]
Init1 = ATZ
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem 
Stupid Mode = 3
New PPPD = yes
Dial Command = atdt
Carrier Check = no
ISDN = 0

[Dialer Verizon4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########@vzw4g.com
Password = vzw

```

I removed all the Init# entries from 3-8 and fixed Init 2: (Was ATQ0 / Now: AT Q0)

Connected and tested:

[http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)
Last Result:
Download Speed: 12502 kbps (1562.8 KB/sec transfer rate)
Upload Speed: 3663 kbps (457.9 KB/sec transfer rate)

--RayJ

---

### Post by NYCeyes on 2011-04-18
Hi RayJ...

Thanks. When I connect, no /etc/ppp/resolv.conf gets generated, so I created one
manually (using DNS servers outputted after a connect). Still cannot communicate
with the external world - or even ping the default router, which is likely the core
issue. :confused:

Perhaps I need to accidentally, like you, upgrade the device firmware under windows. :)
Maybe that will change something. Will see.

Btw... sorry, too, for the late reply. This forum is not emailing me when someone
replies. I'll have to see how to subscribe to the thread.

Thanks,
Noel

---

### Post by raywjohnson on 2011-04-18
I forgot to subscribe! Which is why I did not get the notices. ;)

No worries. I am sure we can get this to work. Just to be thorough, do you have ppp
(Point-to-Point Protocol daemon) and  pppoe (PPP over Ethernet driver) installed?

--RayJ

---

### Post by dotnetbrett on 2011-04-19
> **raywjohnson said:**
> I searched around a bit before committing to upgrading to the Pantech UML 290. All indications were that it would work on Ubuntu out of the box.
 
I found and followed the instructions here: 
 
[http://www.pagey.info/2011/01/using-pantech-uml290-on-ubuntu-linux.html](http://www.pagey.info/2011/01/using-pantech-uml290-on-ubuntu-linux.html)
 
All went well. Accept.... it will not connect.
 
I tested the modem on Windoz XP/VZAcess, worked perfect. 
 
I have tried a number of different settings (like: *99***3# - setting the username/password). No connection. 
 
I shows up in the Network Manager (Verizon 4G LTE) and the "Enable Mobile Broadband" is checked.
 
Has anyone else found the missing element to make this work?
 
Using Ubuntu 10.04 LTS - the Lucid Lynx. Must I upgrade to 10.10?
 
--RayJ
 OK, So here is what I have. I had Ubuntu 10.04 and could not connect my pantech to my notebook. I upgraded to the 10.10 release which took a while. After I upgraded, I plugged in the Pantech and my wireless saw it. I added it by typing in Verizon 4G LTE in the name and making vzwinternet my network name. I then skipped all of the rest of the details and it just worked. I think that most folks are overthinking it.od luck

---

### Post by raywjohnson on 2011-11-20
Alrighty then! 

Just bought a Sony VAIO Laptop E Series VPCEB. (Yes, with windoze)

I installed Ubuntu 11.10 dual boot. Working well.

Again, no love for the Pantech UML290 VW. However, using the same info I have already posted here. I am back online with Verizon.

--RayJ

---

### Post by cnull2 on 2011-12-18
Ray you seam to have a better handle on this than most. I hope i can throw something your way and see if you can help.

I am also running Ubuntu 11.10 but on a Lenovo w510 
I tried your method until I realized I don't get 4G where I am at and your instructions are specific to 4G. 
My goal is to get 3G when I am at a location without 4G


wcdial.conf
```

[Dialer Defaults]
Init1 = ATZ
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem 
Stupid Mode = 3
New PPPD = yes
Dial Command = atdt
Carrier Check = no
ISDN = 0

[ Dialer Verizon3G ]
Modem = /dev/ttyACM0
Baud = 3100000
Phone = *99***3#
Username = ##########@vzw4g.com
Password = vzw

[ Dialer Verizon4G ]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########@vzw4g.com
Password = vzw

```

When I connect I get the following output.
```
root@name:/etc# wvdial Verizon3G
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: atdt*99***3#
--> Waiting for carrier.
atdt*99***3#
CONNECT 3100000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Dec 17 23:31:15 2011
--> Pid of pppd: 4320
--> Using interface ppp0
--> local  IP address xx.xx.xx.xx
--> remote IP address xx.xx.xx.xx
--> primary   DNS address xx.xx.xx.xx
--> secondary DNS address xx.xx.xx.xx

```

It looks like I am connected, but I don't get any Internet. 

Do you have any suggestions?
Thanks!!

---

### Post by raywjohnson on 2011-12-18
> **cnull2 said:**
> It looks like I am connected, but I don't get any Internet. 

Do you have any suggestions?I did change one setting in my config, I set Stupid Mode = 1 

Also, I do not have an @ sign in the username: ##########vzw4g.com

--RayJ

---

### Post by raywjohnson on 2011-12-18
Uploading my current configuration:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Stupid Mode = 1
New PPPD = yes
Dial Command = ATDT
Carrier Check = no
ISDN = 0

[Dialer Verizon4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########vzw4g.com
Password = vzw
```

This seems to connect very quickly now. The old config would give me the 

```
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
```

lines after 30 seconds or so. Now it connects after detecting the "prompt" in about 10 seconds.

--RayJ

---

### Post by cnull2 on 2011-12-27
Sorry it has been a while. 

I have made the changes that you mentioned but no luck. Of course I am still only trying to 3G. 

I am traveling to a location that will definitely have 4G this week. Maybe my luck will change at that location. 

Any other suggestions are accepted. 

Many thanks!
cnull2

---

### Post by raywjohnson on 2011-12-27
> **cnull2 said:**
> Sorry it has been a while.No worries. That is what make a forum great! The conversation will wait for you. ;)

This one is for 4G:
```
[Dialer Verizon4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########vzw4g.com
Password = vzw
```

Try adding this to your config:
```
[Dialer Verizon3G]
Modem = /dev/ttyACM0
Baud = 3100000
Phone = #777
Username = ##########@vzw3g.com
Password = vzw
```

If you are using my GUI script: guiwvdial Verizon3G
Or just WVDial: wvdial Verizon3G

--RayJ

---

### Post by jayk_s4 on 2012-04-12
This is a slightly different problem, but since everybody seems knowledgeable here I thought I'd try posting in this thread.  It's kind of an emergency.

I am working with Ubuntu 11.10 that I have upgraded to kernel 3.2 and a Pantech UML 290 (also a LG vl600 but forget about that for now).

I created a wvdial.conf based on the advice given in this thread.

It looks something like :

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0
Modem Type = USB Modem
Stupid Mode = 1
New PPPD = yes
Dial Command = atdt
Carrer Check = no
ISDN = 0

[Dialer Verizon3G]
Modem = /dev/ttyACM0
Baud = 3100000
Phone = #777
Username = [EMAIL="2023029617@vzw3g.com"]xxxxxxxxxx@vzw3g.com[/EMAIL]
Password = vzw

[Dialer Verizon 4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = _xxxxxxxxxxx_[EMAIL="2023029617@vzw4g.com"]@vzw4g.com[/EMAIL]
Password = vzw

I started it up with

wvdial Verizon 4G

Didn't work the first time, but I unplugged the modem and tried it again right away and it connected.  Then all I needed was some iptables work and I was sharing a lightning-fast 4G connection all around my house.  Everything was great over night.

Then this morning I logged in and it worked for about 15 minutes.  And then BOOM!  The modem disconnected.  My linux server froze.  After forcing a reboot, the server no longer sees the modem.  When I plug it in there is no activity in the syslog or dmesg.  It's like it isn't even plugged in.  wvdial complains that the tty does not exist, which makes sense.

Here's where it gets really ugly.  I take the pantech modem and plug it into my windows box, and still nothing.  Blue light blinks, but it doesn't seem aware of 1x, 3G, or 4G using vzam.  So I move my sim card back to my LG VL600 modem and plug it into my windows box, and luckily here 3G works at least.  No 4G and no 1x.

What could have happened to my SIM card?  Or my modems (though one was disconnected entirely so that seems unlikely)?  Or to my verizon account?

Thanks in advance for any help!  And to those looking to experiment with this, I'd be very careful.  I didn't do anything abnormal (other than maybe switching my SIM) and now have no access to 4G.

---

### Post by raywjohnson on 2012-04-12
Greetings jayk_s4,

The first thing I would do is change the [Dialer Verizon 4G] to [Dialer Verizon4G] (remove the space). Then use wvdial Verizon4G to start the connection. 

Did you activate the device via windows before you tried to connect via Linux? 

You should have received a new SIM card with the UML 290 modem. Every time I have upgraded or had a modem replaced, Verizon always sent a new SIM.

It might also be a problem with the Verizon service. I get this problem about once week now. I cannot connect to 4G for whole day.

Also, I no longer use this line: Init3 = AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0

I cannot connect with that line in the config, here is my current configuration:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Stupid Mode = 1
New PPPD = yes
Dial Command = ATDT
Carrier Check = no
ISDN = 0

[Dialer Verizon3G]
Modem = /dev/ttyACM0
Baud = 3100000
Phone = #777
Username = ##########@vzw3g.com
Password = vzw

[Dialer Verizon4G]
Modem = /dev/ttyACM0
Baud = 100000000
Phone = *99***3#
Username = ##########@vzw4g.com
Password = vzw

```

--RayJ

---

### Post by jayk_s4 on 2012-04-13
> **raywjohnson said:**
> Greetings jayk_s4,

The first thing I would do is change the [Dialer Verizon 4G] to [Dialer Verizon4G] (remove the space). Then use wvdial Verizon4G to start the connection. 

Did you activate the device via windows before you tried to connect via Linux? 

You should have received a new SIM card with the UML 290 modem. Every time I have upgraded or had a modem replaced, Verizon always sent a new SIM.

It might also be a problem with the Verizon service. I get this problem about once week now. I cannot connect to 4G for whole day.

Also, I no longer use this line: Init3 = AT+CGDCONT=3,"IPV4V6","vzwinternet","0.0.0.0",0,0

I cannot connect with that line in the config, here is my current configuration:
--RayJ

OK, thanks I will modify my script.  At the moment I can't even run the script though because linux won't recognize the modem at all.  I don't even have a /dev/ttyACM0.

If 4G service is down and the modem isn't forced into 3G mode, does linux just ignore the device?   It is possible 4G is down in the area, it's been over 24 hours now, but maybe I just didn't notice outages before because it automatically switched to 3G.

The Pantech modem was originally activated on a windows box about a year ago.  I used it in a cradlepoint router for most of that time but got lots of disconnects from the router.  Then I bought a LG VL600 from ebay with no SIM card and moved my SIM card into the LG modem and then updated the IMEI or MEID at verizonwireless.  This worked a little better but still disconnected.  I had to throttle it to lower than 3G speeds to keep it connected.  Apparently the USB device on the cradlepoint can't handle high speeds very well. That is why I decided to put it in my linux box and use that as the router.

I couldn't get the LG device to connect so I moved the SIM card back into the Pantech.  And you know the rest of the story after that.  The only difference is that i didn't update verizonwireless this time with the correct device ID that is being used with the SIM card.  Verizon still thinks I have a LG modem rather than the Pantech.  Maybe they detected that and turned off my 4G access?

Thanks for the help!

---

### Post by raywjohnson on 2012-04-13
> **jayk_s4 said:**
> OK, thanks I will modify my script.  At the moment I can't even run the script though because linux won't recognize the modem at all.  I don't even have a /dev/ttyACM0.Check for any /dev/ttyACM (sometimes mine shows up as /dev/ttyACM1). If you not getting any listing, then I would say the modem is the problem.

Try: (without the modem plugged in)
dmesg | grep -i tty

then plugin and wait a few seconds, and run again:
dmesg | grep -i tty

You should see:
cdc_acm 2-1.1:1.0: ttyACM0: USB ACM device

Also, does the light on the modem ever flash blue? If not, then it is not able to communicate with the Verizon hight speed node (cell tower).


> If 4G service is down and the modem isn't forced into 3G mode, does linux just ignore the device?It will simply not connect. That is why I have both a [Dialer Verizon3G] and a [Dialer Verizon4G] in the config. 

> It is possible 4G is down in the area, it's been over 24 hours now, but maybe I just didn't notice outages before because it automatically switched to 3G.When I have called Verizon about suspected outages, they never admit to that problem. They always blame the modem.

> The Pantech modem was originally activated on a windows box about a year ago.  I used it in a cradlepoint router for most of that time but got lots of disconnects from the router.  Then I bought a LG VL600 from ebay with no SIM card and moved my SIM card into the LG modem and then updated the IMEI or MEID at verizonwireless.  This worked a little better but still disconnected.  I had to throttle it to lower than 3G speeds to keep it connected.  Apparently the USB device on the cradlepoint can't handle high speeds very well. That is why I decided to put it in my linux box and use that as the router.

I couldn't get the LG device to connect so I moved the SIM card back into the Pantech.  And you know the rest of the story after that.  The only difference is that i didn't update verizonwireless this time with the correct device ID that is being used with the SIM card.  Verizon still thinks I have a LG modem rather than the Pantech.  Maybe they detected that and turned off my 4G access?What I suspect is the SIM card is messed up. You may need to call Verizon and have them send you a new one.

> Thanks for the help!No problem. ;)

--RayJ

---

### Post by jayk_s4 on 2012-04-27
Just thought I'd give an update...  I went on vacation for a week and tried to put all this behind me, when I got back 4G still wasn't working.  So I called Verizon and they had me go through some diagnostic stuff and then said they thought it was something wrong with the tower, so they're sending somebody out to check on it.

In the meantime, I was messing around tonight and decided to re-install the latest vzam and firmware for the Pantech modem, and voila!  4G was back using access manager.  I then updated my dial-up connection to use 4G settings (still on windows) and that worked for 4G as well.

So I guess it's possible that Verizon just now fixed their tower or whatever was wrong with 4G, but I suspect it was the fresh firmware that fixed whatever was wrong with it.

So that's the good news.  The bad news is that on Linux it still doesn't work.  When I plug in the modem I don't get a ttyACM0 or ttyUSB0.  I get a bunch of messages in dmesg about disconnecting it immediately after it is connected the first time.  After that nothing happens.

I even downgraded back to the 3.0.0-17 kernel and it is even worse.  Sometimes it will recognize the modem once, but if remove it and re-insert it the linux box will crash or hang.

To finish the loop, I plugged the modem back into my windows vista box, and it still works.

---

### Post by raywjohnson on 2012-04-27
Did you check to make sure your Network Manager is not trying to create a connection? 

Right click on the Network Manager and click Edit Connections. The select the Mobile Broadband tab. Delete any entries. Or edit them to not auto connect.

Also, look for other ID numbers for the modem in /dev (when mine acts flaky, it is usually because it got assigned ttyACM1 instead of ttyACM0).

--RayJ

---

### Post by ahsscott77 on 2012-10-12
Hello, 

I have been trying to use your instructions to connect with the UML 290. 

I'm running 12.04. 

The output from pppd is below. Is says that it connects but I am never able to actually connect to the internet.

Any help is very much appreciated.


--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: atdt*99***3#
--> Waiting for carrier.
atdt*99***3#
CONNECT 100000000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Feb 15 17:15:53 2001
--> Pid of pppd: 21640
--> Using interface ppp0
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> local  IP address 10.186.95.1
--> pppd: 
--> [7f]
--> remote IP address 10.64.64.64
--> pppd: 
--> [7f]
--> primary   DNS address 66.174.95.44
--> pppd: 
--> [7f]
--> secondary DNS address 66.174.71.33
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> Connect time 10.0 minutes.
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> pppd: 
--> [7f]
--> Disconnecting at Thu Feb 15 17:26:00 2001
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)

---

### Post by raywjohnson on 2012-10-12
I will do what I can to help!

I get that sometimes as well. I usually figure it is just Verizon.

Did you setup the device via Windowz? Make sure its firmware is updated?

Is the light on your Pantech UML 290 flashing blue or red?

If red, then the device is not talking to the Verizon network. 

If blue, try unplugging it, wait a few seconds, the plug in again. Wait for the light to flash blue. Then try to connect.

--RayJ

---

### Post by raywjohnson on 2013-01-15
Final Update...

I found the best solution: cancel Verizon and go with Clear. They have a wireless "hot spot" device that does not require any connection software. It is just a secure router.

Got my device today. Connected my Ubuntu laptop and Android phone, no problem. Same speed and cost as Verizon, but no annal contract and no bandwidth limits. :D

--RayJ

---

### Post by raywjohnson on 2013-01-15
Of note: I plugged the device (Voyager) in (via USB) to keep it powered. What I did not know is that it is detected as a USB "wired" wifi device! Network Manager connected to it without me having to do a thing. Nice...


--RayJ

---

