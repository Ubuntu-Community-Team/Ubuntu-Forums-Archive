---
title: "Using Nokia E51 as a modem"
date: 2009-03-08
forum: Hardware
---

### Post by xardas on 2009-03-08
I have Ubuntu 8.10 and a Nokia E51 smartphone. I use it as modem on Window XP using Nokia PC Suite. Is there any way to use internet on my Ubuntu installation by connecting the phone to the computer using a USB data cable?

---

### Post by mister_tea on 2009-03-15
connect Nokia to USB & select "PC Suite" mode

ubuntu@ubuntu:~$ lsusb
Bus 003 Device 008: ID 0AAA:00BB Nokia Mobile Phones 
ubuntu@ubuntu:~$ 

--> vendor id = 0xAAA
--> device id = 0xBB

sudo /sbin/modprobe usbserial vendor=0xAAA product=0xBB
wvdialconf create
sudo gedit /etc/wvdial.conf

below adapt Baud & Init3 depending on modem & cell Internet Provider APN
you can find world APN lists on internet or ask your cell operator
Phone field maybe adapt too

[Dialer Defaults]
Modem = /dev/ttyACM0
0Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
init3 = AT+CGDCONT=1,"IP","your_APN","",0,0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = find it for your APN
Password = find it for your APN
Stupid Mode = 1

then type :
sudo wvdial

ubuntu@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> local  IP address bla.bla.bla.bla

NOW you should have the internet link working
test with ping to any web site you want
in FireFox you might need to uncheck the File-OfflineMode

when this works you can also use BlueTooth to connect if your Nokia has it
BlueTooth Class2 is fast
it is easy check the forums
you will have to replace in wvdial the Modem field with rfcomm0 (bluetooth instead of usb link)

enjoy :)

---

### Post by impact on 2009-03-15
> **xardas said:**
> I have Ubuntu 8.10 and a Nokia E51 smartphone. I use it as modem on Window XP using Nokia PC Suite. Is there any way to use internet on my Ubuntu installation by connecting the phone to the computer using a USB data cable?

I can connect an E50 with the USB cable to my Ubuntu machine and then use the Network manager to connect to the net. Try it, it's probably the simplest method - the network manger just asks a few questions (what country are you in, what carrier do you have, what data plan) and then sets everything for you.

---

### Post by mister_tea on 2009-03-19
yes impact is right

the commands i gave can be usefull in cases like mine , where the country and operator i was using was not in the list

but maybe there is another way of adding settings of an operator i did not check this

---

### Post by xardas on 2009-05-04
I tried this approach. But I'm getting these error messages. Something about 'LCP terminated by peer'.
My wvdial.conf looks like this.

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
New PPPD = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","pinternet"
ISDN = 0
Modem Type = USB Modem
Phone = *99#
Username = "blank"
Password = "blank"
Stupid Mode = 1

And then I try sudo wvdial and I get this output

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","pinternet","",0,0
AT+CGDCONT=1,"IP","pinternet","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon May  4 13:40:43 2009
--> Pid of pppd: 9454
--> Using interface ppp0
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#1063;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Mon May  4 13:40:47 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

I go and look at /var/log/messages and I see this: Something about 'LCP terminated by peer'.

May  4 13:40:43 POPO pppd[9454]: pppd 2.4.4 started by root, uid 0
May  4 13:40:43 POPO pppd[9454]: Using interface ppp0
May  4 13:40:43 POPO pppd[9454]: Connect: ppp0 <--> /dev/ttyACM0
May  4 13:40:43 POPO pppd[9454]: PAP authentication succeeded
May  4 13:40:44 POPO pppd[9454]: LCP terminated by peer
May  4 13:40:47 POPO pppd[9454]: Connection terminated.
May  4 13:40:47 POPO pppd[9454]: Modem hangup
May  4 13:40:47 POPO pppd[9454]: Exit.

Any ideas?

---

### Post by dave66 on 2009-06-16
Hi,

I just wanted to confirm that this also works with:

Nokia 5130
Nokia 7310
Samsung J700

However, I must mention that for ease of connection I have found Sony Ericsson W910i and K800i to be really superb. With the Sony's all I had to do was connect the phone to the PC with a USB cable, Network Manager detected the connection as an ethernet connection, grabbed an IP address and I was ready rock and roll - 5 to 10 seconds is all it took.

Has anyone come up with a more user (non-technical user) friendly solution for handling the Nokia connections.

I have to oversee the rollout of a LOT of netbook computers running 8.04LTS, the users (95-98%) are non technical / IT literate and will from time to time use their mobile/cell phone to upload data. Any of those with a Sony (the minority) will be fine, however I see us having a battle with those who have Nokia/Samsung, haven't tested with Motorola yet.

Any suggestions/solutions would be most welcome/appreciated.

David

---

### Post by jamsh on 2009-06-17
I have a Nokia N95 with a T-Mobile PAYG sim card and I was online in a few seconds using the little connection wizard.  I use it regularly when I visit a friend who has no internet. My only problem is that I also have a Virgin PAYG sim card(internet is cheaper - 30p per day )and this does not connect at all.  The only option in the wizard is for Virgin Mobile, which is connecting via their dongle. I would like to configure my phone to connect to Virgin PAYG.

---

