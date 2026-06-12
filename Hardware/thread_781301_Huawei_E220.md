---
title: "Huawei E220"
date: 2008-05-04
forum: Hardware
---

### Post by danne123 on 2008-05-04
I cant connect to internet with my huawei E220. The modem is blinking in blue.
Now I use ubuntu 8.04 but the same problem happens with knoppix.

And is it normal that I don´t get a popup window when Huawei modem is plugged in? If I connect my friends USB memory-stick, then a popup window appears.

ANYWAY I made some progress by reinstalling ubuntu.

And if you look at these lines:

```
[  822.835710] usb 2-1: USB disconnect, address 3
[  822.836443] airprime ttyUSB0: airprime converter now disconnected from ttyUSB0
[  822.836768] airprime ttyUSB1: airprime converter now disconnected from ttyUSB1
[  822.837086] airprime ttyUSB2: airprime converter now disconnected from ttyUSB2
[  822.837117] airprime 2-1:1.0: device disconnected
[  822.837648] airprime ttyUSB3: airprime converter now disconnected from ttyUSB3
[  822.837968] airprime ttyUSB4: airprime converter now disconnected from ttyUSB4
[  822.838284] airprime ttyUSB5: airprime converter now disconnected from ttyUSB5
``` 

Is this normal?


```

[ 1623.463569] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  648.659856] sr1: scsi-1 drive
[  648.659932] sr 10:0:0:0: Attached scsi CD-ROM sr1
[  648.659985] sr 10:0:0:0: Attached scsi generic sg2 type 5
[ 1717.105050] usb 2-2: USB disconnect, address 4
[ 1717.107240] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1717.107281] airprime 2-2:1.0: device disconnected
[ 1717.107834] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1717.107868] airprime 2-2:1.1: device disconnected
[  728.828430] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Why does it connect to both ttyUSB0 and ttyUSB1?

---

### Post by babam on 2008-05-04
don't plug modem after OS coming up, please plug the modem before OS coming up.
I can connect to the Modem after upgrade from 7.10 to 8.0.4

msg log:

root@pegelinux-laptop:~# . ./.huawei-config &
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.[1] 6651
root@pegelinux-laptop:~# 
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun May  4 17:06:24 2008
--> Pid of pppd: 6653
--> pppd: &#554;[06][08]
--> Using interface ppp0
--> pppd: &#554;[06][08]
--> pppd: &#554;[06][08]
--> pppd: &#554;[06][08]
--> pppd: &#554;[06][08]
--> pppd: &#554;[06][08]
--> pppd: &#554;[06][08]
--> local  IP address 124.81.192.78
--> pppd: &#554;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#554;[06][08]
--> primary   DNS address 202.155.0.10
--> pppd: &#554;[06][08]
--> secondary DNS address 202.155.0.15
--> pppd: &#554;[06][08]

/me:
Babam.

---

### Post by danne123 on 2008-05-04
Forgot to say that I am a noob. 

How did you open msg log?

I have plugged in the modem before and after the computer starts, nothing happens. The same thing with OS, plugged in before and after the OS started. Nothing there either.

---

### Post by danne123 on 2008-05-04
When shall you actually plug in the modem? Before the computer starts, after bios, grub startup or during OS-boot?

---

### Post by danne123 on 2008-05-04
bump

---

### Post by dastasha on 2008-05-04
Plug it in before the computer starts.

I still have no success with 8.04.
The modem worked once after I installed VMC then has frozen at the startup screen ever since.

I went back to 7.10 and VMC is happy.

---

### Post by danne123 on 2008-05-05
What is VMC?

---

### Post by dastasha on 2008-05-05
VMC is vodafone mobile connect. Its program I use to connect with the huawei e220.

Available from here
[https://forge.vodafonebetavine.net/](https://forge.vodafonebetavine.net/)

However I suspect it&#347; not working too well with hardy.
Looking around on these forums, some guys have workarounds sorted.
No such luck for me though - bit of a noob myself.

It works great in gutsy though.
I staying tuned to the vodafoneBV forums for a hardy solution I think we are not the only ones waiting to find a solution

---

### Post by danne123 on 2008-05-05
Does this say anything that could help solve my problem?

 ```
tail -f /var/log/messages
May  5 20:56:48 diablo chat[5657]: expect (OK)
May  5 20:56:48 diablo chat[5657]: ATZ^M^M
May  5 20:56:48 diablo chat[5657]: OK
May  5 20:56:48 diablo chat[5657]:  -- got it 
May  5 20:56:48 diablo chat[5657]: send (ATDT*99#W*99#^M)
May  5 20:56:48 diablo chat[5657]: timeout set to 75 seconds
May  5 20:56:48 diablo chat[5657]: expect (CONNECT)
May  5 20:56:48 diablo chat[5657]: ^M
May  5 20:56:48 diablo chat[5657]: ATDT*99#W*99#^M^M
May  5 20:56:48 diablo chat[5657]: COMMAND NOT SUPPORT^M
May  5 20:58:03 diablo chat[5657]: alarm
May  5 20:58:03 diablo chat[5657]: Failed
May  5 20:58:35 diablo chat[6078]: timeout set to 60 seconds
May  5 20:58:35 diablo chat[6078]: abort on (ERROR)
May  5 20:58:35 diablo chat[6078]: abort on (BUSY)
May  5 20:58:35 diablo chat[6078]: abort on (VOICE)
May  5 20:58:35 diablo chat[6078]: abort on (NO CARRIER)
May  5 20:58:35 diablo chat[6078]: abort on (NO DIALTONE)
May  5 20:58:35 diablo chat[6078]: abort on (NO DIAL TONE)
May  5 20:58:35 diablo chat[6078]: abort on (NO ANSWER)
May  5 20:58:35 diablo chat[6078]: send (ATZ^M)
May  5 20:58:35 diablo chat[6078]: send (AT&FH0M0^M)
May  5 20:58:35 diablo chat[6078]: expect (OK)
May  5 20:58:35 diablo chat[6078]: ATZ^M^M
May  5 20:58:35 diablo chat[6078]: OK
May  5 20:58:35 diablo chat[6078]:  -- got it 
May  5 20:58:35 diablo chat[6078]: send (ATDT*99#W*99#^M)
May  5 20:58:35 diablo chat[6078]: timeout set to 75 seconds
May  5 20:58:35 diablo chat[6078]: expect (CONNECT)
May  5 20:58:35 diablo chat[6078]: ^M
May  5 20:58:35 diablo chat[6078]: ATDT*99#W*99#^M^M
May  5 20:58:35 diablo chat[6078]: NO CARRIER
May  5 20:58:35 diablo chat[6078]:  -- failed
May  5 20:58:35 diablo chat[6078]: Failed (NO CARRIER)
```

---

### Post by danne123 on 2008-05-06
AHHHHH, I managed to get everything working yesterday! But now, NOTHING again!!!!!

---

### Post by MathSWE on 2008-05-06
Im using the E220 with my laptop that is reinstalled with 8.04, but I have /home on a separate partition and didnt reformat it so all my settings stayed put.

Vodafone Mobile Connect didnt work after 8.04 BUT then I removed the .vmc2 folder in my home folder and then it worked again.

Im running VMC 1.99.something because I found 2.0 Beta 1 to be very buggy in the graphical interface, havent tried beta 2 yet but Im sticking with 1.99 since it works very fine.

Danne, if you havent tried VMC I suggest that you do! Great tool to get connected! Im switching my surf account to vodafone just because their application is so great!

---

### Post by danne123 on 2008-05-08
My modem is a 3Turbo. It comes with a program that is similar to VMC and called 3Connect.

But I found a strange thing that maybe can help you too:

If I first start windows XP and start internet connection surf around for a moment and after that reboot the computer to start linux. Then the internet connection actually works? Why is that?

---

