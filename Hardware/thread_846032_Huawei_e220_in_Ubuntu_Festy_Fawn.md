---
title: "Huawei e220 in Ubuntu Festy Fawn"
date: 2008-07-01
forum: Hardware
---

### Post by Belthazor on 2008-07-01
I have seen a lot of instructions about how to install this modem in linux. I've tried almost all (I think), but they didn't work. So, I saw the modem information and it said that my modem was in dev/ttyUSB0, dev/ttyUSB1 and dev/ttyUSB2 ](*,). What have I got to do?

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Hello Belthazor,

 We'll need some more info, can you post the contents of /etc/wvdial?

---

### Post by Fingers &amp; Thumbs on 2008-07-01
I'm sorry belyhazor, just realised you are a brand new user, so my previous post probably is not very clear.

  Have you read my HOWTO [***[COLOR="Blue"]here[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=843973")

---

### Post by Belthazor on 2008-07-01
the content of my wvdial.conf is :

# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem



But the modem is not only /dev/ttyUSB0, it is in 1 and 2, too.

What must I do?

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Much as I admire tazz_tux for his generosity in setting up his comprehensive guide, it is a little unclear for beginners, I made the same mistake as you did after reading his pages.

  Copying someone elses /etc/wvdial.conf in it's entirety will not work, which wasn't clear in his thread. Although they are useful for gaining some info and a greater understanding of what's going on.

  In terminal type:

```
sudo gedit /etc/wvdial.conf
```

Now make a copy of that file on your desktop.

Once you have backed it up to your desktop, delete everything in the origional /etc/wvdial.conf, Save and close.

Back to terminal and type sudo wvdialconf (be sure that this is wvdialconf and not wvdial.conf. wvdialconf is a command whereas wvdial.conf is a filename.

What this will do is collect the correct information from your modem and write it to wvdial.conf (/etc/wvdial.conf) although some info will be missing. (Phone, Username, and Password) You can then refer to the copy of the old one on your desktop to complete these missing lines.

What you put is password/username really isn't that important, but your Phone number must be correct, in tazz's example it says *99***1#, It's quite possible that this is correct, but this will differ depending on your provider, you could obtain this from your provider, from google, or by plugging your modem into a windows machine.

Once you're satisfied that your file is complete, check what it says in the first line after [Dialer, save and exit.

Now in terminal type:

```
wvdial [COLOR="RoyalBlue"]"followed by whatever came after [Dialer (if this was Defaults you can leave this blank and just type wvdial) "[/COLOR]
```

Your modem should now work, let me know how you get on, also, if you would like help setting up a GUI to interface with your connection, please refer to my howto from the link in the previous post.

---

### Post by Belthazor on 2008-07-01
it all worked well until the sudo wvdialconf.
It showed this message:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
______________________________________________________________

What about now?

---

### Post by Fingers &amp; Thumbs on 2008-07-01
OK, there two possible reasons for this that I am aware of.

   1. Sometimes, if you have previously tried other methods to connect, these can still be hanging on to the modem, despite not successfuly connecting it.

   2. There is a virtual CD drive on the modem that some users have reported can prevent a proper connection to your modem, although I have never found this to be a problem. As you mentioned earlier you appear to have numerous usb connections to your modem, (tty/USB0,1,2 etc) One of these is that VirtualCD.

  To give your modem exclusive rights to your connection after previous efforts, all I would do, as I have done in the past is to simply reboot.

  Regarding the virtual CD, do you have a link to it on your desktop? or does it show up in computer:///? (>Places >Computer) If so right clicking and unmounting it before you connect via wvdial should prevent it blocking

Be patient, we'll get this working I am confident of that, and I'm more than happy to assist.

---

### Post by Sealbhach on 2008-07-01
Just looking at [this page]("http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/"), it seems normal:

> When in modem state, the box offers three serial USB devices:
/dev/ttyUSB0, /dev/ttyUSB1, /dev/ttyUSB2
Use /dev/ttyUSB0 to examine modem settings using minicom or go online via PPP.

> You have to provide the options vendor=0x12d1 and product=0x1003 when loading the usbserial module, e.g via 

```
sudo modprobe usbserial vendor=0x12d1 product=0x1003
```

Try that.

I have an E220 working in Hardy, I use Gnome-PPP to configure it and it works fine. Make sure you always have the modem plugged in before you boot up - otherwise it doesn't find it.

Try this anyway, it might help.

EDIT: Some good info here too!

[http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)


. 

.

---

### Post by Belthazor on 2008-07-01
1. Sometimes, if you have previously tried other methods to connect, these can still be hanging on to the modem, despite not successfuly connecting it.

I think this is the problem. I've tried to install a lot of things to work with my modem. To erase them what should do?

---

### Post by Fingers &amp; Thumbs on 2008-07-01
If you can remember what they were, then use synaptic manager and select them using the completely remove option. 

In the meantime rebooting should get your modem working, unless any of these other programs are set to load at startup. To check this go to >System >Preferences >Sessions and de-select them.

But before you do, what programs are they? Even though wvdial can work on it's own, it has no GUI, some of these programs may be GUI's that work as frontends for wvdial, in which case I can help you to configure them.

---

### Post by Belthazor on 2008-07-01
these programs were oozie's and vodafone's official ones.

---

### Post by Fingers &amp; Thumbs on 2008-07-01
ok, which network are you on?
  
   Unless you are with vodafone then I suggest you uninstall this package as it is very resource hungry with loads of features that only work with vodafone. It will connect but all of the features are useless.

   I am not familiar with oozie, but I do know that you do not need it and it is possible that it is getting in your way. So I would suggest uninstalling this too.
  
Open synaptic package manage and select the packages with a right click and select completely remove.

---

### Post by Sealbhach on 2008-07-01
> **Belthazor said:**
> these programs were oozie's and vodafone's official ones.

Yes, the Vodafone driver killed my modem, didn't work at all with that installed.

Someone advised me to do this and it solved the problem:

```
sudo dpkg -r vodafone-mobile-connect-card-driver-for-linux
```


.

---

### Post by Belthazor on 2008-07-01
I've instaled oozie's program and vodafone mobile connect card driver for linux, but I couldn't find any of them in the synaptic package manager

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Ok, as sealbhach pointed out:

```
sudo dpkg -r vodafone-mobile-connect-card-driver-for-linux
```

To remove (-r) using the deb package manager (dpkg), I'm also assuming that oozie was installed by the same means, I'm not sure oozie is a problem as a quick search tells me that it does nothing for your connection, it is just a tool to give you statistical feedback. But as it's not officially supported in the repos, I would remove it anyway. (Generally speaking it is advised only to install software from synaptic or via apt-get particularly for a beginner, an advanced user with experience in debugging may feel that the benefits of non supported software may outweigh the risks, but with no knowledge of debugging the risks are much greater,)

Try:

```
sudo dpkg -r oozie
```

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Yeah the vodafone package requires lots of python dependencies, and as you have to compile them independently rather than leting syn(apt)ic take care of it, there are many troubles, especially as developement is rapid often leaving the links within threads out of date. I'm pretty sure this is why vodafone hung your modem. It can work with the correnct and up to date dependencies for your distro, but IMHO is unnecessarily flabby.

---

### Post by Belthazor on 2008-07-01
well, I've removed everything and it works! I still have one doubt: the Target Phone number. What should I put there?

---

### Post by Sealbhach on 2008-07-01
> **Belthazor said:**
> well, I've removed everything and it works! I still have one doubt: the Target Phone number. What should I put there?

I would use the phone number that's in your /etc/wvdial.conf



[Dialer Defaults]
**[COLOR="Indigo"]Phone = *99***1#[/COLOR]**
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT


I'm assuming your ISP is Vodafone UK? 


.

---

### Post by Fingers &amp; Thumbs on 2008-07-01
What network and country are you needing settings for?

---

### Post by Belthazor on 2008-07-01
> **Sealbhach said:**
> 
I'm assuming your ISP is Vodafone UK? 
.

nope... vodafone P (Portugal)---lol

I putted the number *99# and the following appeared:

line 2: [Dialer: command not found
Init2: command not found
line 3: C1: command not found
line 3: D2: command not found
line 4: Modem: command not found
line 5: syntax error near unexpected token `;'
wvdial.conf: line 5: `; Phone = <*99#>'

What about now?

---

### Post by Sealbhach on 2008-07-01
Do

```
sudo wvdialconf 
```

then

```
cat /etc/wvdial.conf
```

Use the phone number from that.


.

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Post your /etc/wvdial.conf, it should be different to the one you posted at the beginning.

---

### Post by Belthazor on 2008-07-01
my /etc/wvdialconf is:

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <*99#>
ISDN = 0
; Username = <hello>
Init1 = ATZ
; Password = <hello>
Modem = /dev/ttyUSB0
Baud = 460800

---

### Post by Fingers &amp; Thumbs on 2008-07-01
no problem, 

```
sudo gedit /etc/wvdial.conf
```

then replace with this (for your own understanding, please observe the changes I have made.

```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = hello
Init1 = ATZ
Password = hello
Modem = /dev/ttyUSB0
Baud = 460800 
```

Now, in a terminal just type

```
wvdial Defaults
```

I'm not sure if *99# is correct for your network, but the <,>, and ; will prevent all of those lines being read correctly.

If this works and you would like to know how to make a launcher for this or have it load automatically at startup, just let me know

---

### Post by Belthazor on 2008-07-01
how can I execute wvdial.conf? I forgot

---

### Post by Belthazor on 2008-07-01
the following appeared:

2: [Dialer: not found
3: Init2: not found
3: C1: not found
3: D2: not found
4: Modem: not found
5: Phone: not found
6: ISDN: not found
7: Username: not found
8: Init1: not found
9: Password: not found
10: Modem: not found
11: Baud: not found

---

### Post by Fingers &amp; Thumbs on 2008-07-02
It looks like the file didn't save, or at least not to the correct location,

```
sudo gedit /etc/wvdial.conf
```

I'm pretty sure you will find it is empty,

Copy/paste

```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = hello
Init1 = ATZ
Password = hello
Modem = /dev/ttyUSB0
Baud = 460800
```

be sure to click Save, this will write the file to /etc/wvdial.conf

---

### Post by dragonknight1212 on 2008-07-16
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Jul 16 23:24:18 2008
--> Pid of pppd: 21872
--> Disconnecting at Wed Jul 16 23:24:19 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

```

[B][SIZE="3"]can anyone help me out with this? i keep on getting the exit code 2.
thanks.. 


~Jay[/SIZE][/B]

---

