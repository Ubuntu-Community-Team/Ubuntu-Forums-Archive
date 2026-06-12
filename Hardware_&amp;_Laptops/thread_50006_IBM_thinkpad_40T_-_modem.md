---
title: "IBM thinkpad 40T - modem??"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by eeried on 2005-07-18
Hello,
I'm new to ubuntu but not to Linux (Libranet 2.8.1), though I'm far from being an expert as you'll see in the rest of this post..

I installed Ubuntu this morning on IBM Thinkpad40T (dual-boot WinXP, as this computer is only lent to me). The dial-up connexion doesn't work -- the only one I have here.

This is the result of the lspci command:
```

tux@ubuntu:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 81)


```

Do the following lines mean the modem is a winmodem? Please let me know -- I have the feeling it's the case since the audio controller and the modem controller are the same (AC'97)

> 0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 

Windows says it's CXT Bus PCI0 56K Modem.

I 've read quite a lot of posts on the subject of modems and drivers, and even tried installing sl-modem-daemon and sl-modem-source from the ubuntu repository, but though the installation was successful, still the connection doesn't work (in fact sl-modem-daemon doesn't seem to get installed. I tried pppconfig which I find much more pleasant than GUI utilities, and set the modem to /dev/ttyS2 (COM 3 in Windoze).

I also failed using Knoppix Live CD.

PS. This isn't my computer so i can't buy another modem. I could try and plug in my own Olitec external  serial modem but the modem plug and the only serial-looking plug on the IBM laptop are exactly the same -- so impossible to plug in!!

I do need some help -- I'd hate to be stuck with Winxp for the rest of the summer.... :roll:

---

### Post by Skrewdriver on 2005-07-19
Thinkpads generally have winmodems installed.
Have a look at Linux Winmodem Support:
[http://walbran.org/sean/linux/linmodem-howto.html](http://walbran.org/sean/linux/linmodem-howto.html) ?

I have an old Thinkpad, and there is no linux driver for the internal modem, so I hook up an external modem via the seial port. I know you said you couldn't do this, but I didn't understand what your problem was. Could you rephrase it so it is a bit clearer?

---

### Post by eeried on 2005-07-19
Many thanks for your reply, Skrewdriver.

I downloaded  scanmodem from Ubuntu wiki as others have done.

This confirms the laptop modem is a winmodem. The file inside the scanmodem archive, Modemdata.txt isn't encouraging at all (conexant and linuxant aren't quite satisfactory unless you pay for the driver) but your link looks more promising -- though the page won't load (timeout)  (overloaded server?, too many visitors ?)

It could be expected Thinkpad laptop would be shipped with some decent hardware modem not a softmodem... All the less decent from IBM since the pride themselves on being kind to Linux users.

Now let me rephrase my difficulty with the external modem. The only plug that looks like a serial one on the laptop has holes. Now the serial plug at the back of my destop computer has pins, and has the plug at the back of the modem. So what I mean is  you can't plug in a cord that has a "hole" plug on another "hole" plug. And what's more the pins on my serial plug are bigger than the holes in the laptop plug. I can't even plug in the modem directly into the laptop serial plug (which would be impossible any way because of the various cords and switch at the back of the modem).

Maybe I can find an adaptor to plug in between the laptop hole plug and the the modem cord.

cheers

---

### Post by odix on 2005-07-19
maybe the socket on your notebook is the monitor connector not the serial port, if it is a serial port it must have pins, otherwise it isnt a serial port...

I've looked at a picture of a T40, the only connector which could look like a serial port is the VGA monitor connector, which is on the right side of the T40

regards

---

### Post by eeried on 2005-07-19
Many thanks for looking at this serial business.

The conclusion is that Thinkpad T 40 has a winmodem and no serial port! Fair enough ](*,)  -- someone mislaid the laptop manual so I wasn't able to check the specs easily.

But I think I have managed to install the modem drivers. Though ModemData.txt seemed to point to hsfmodem drivers  I finally hit upon a detailed thread on ls-modem, and thought I'd better try that.

[http://ubuntuforums.org/showthread.php?t=49503](http://ubuntuforums.org/showthread.php?t=49503)

I also installed gnome-ppp. It detected the modem once, initialized the connection, sent the password and then noting -- there's absolutely no sound, but then this may be due to the soft modem which if I understand right is controlled by the sound software?

I also configured the connection through pppconfig which I'm familiar with, and set the modem to /dev/modem since it doesn't like /dev/ttySLO (which was set by the sl-modem-daemon)

The modem is detected by wvdial, but wvdial complains there's no phone number, nor login, nor password.

I created a wvdial config file /etc/wvdialconf but of course it only recorded the modem and I don't know what syntax I should use.

pon doesn't produce any message but doesn't manage to connect.

Do I need linux-headers -- is the package  on unbuntuCD-rom? (it's online anyway and fits into a floppy).

Thanks for putting up with me! :^o

---

### Post by eeried on 2005-07-19
Here  is the output for the wvdial command:

user@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

=========

I don't know how to configure the phone number the login and the password.

The wvdialconf file in /etc/ I created via wvdialconf had the right phone number and login; only the password is missing -- for security reasons?

Could this be a case of permissions?

Can you help me out?

---

### Post by eeried on 2005-07-20
Hello everyone,

From what I read in an oldish thread on the subject of winmodem (for Warty), there seems to be a confusion between Smartlink, Conexant, and Lucent.

Now is there a difference between installing ls-modem* .deb files and hfsmodem ones?

In that long thread I read (can't find the link again just now), the user installed hsfmodem files then ls-modem ones and finally was told to uninstall the hsf * package. His modem finally worked but unfortunately he never said how he finally succeeded.

I suppose everybody"s fed up to their backteeth with this nagging winmodem hitch, and so am I. But it'd be nice if the darned thing could work. 
Otherwise I'll have to install mepis which according to a member on this forum has all the drives for winmodem -- Mepis seems rather full of proprietray stuff which isn't quite my idea of Linux but well, it'll have to do for the present being.

So my question is should I install hfs files (modem controller Ac'97, codec CXT=connexant, according to scanmodem)?

A good day to you all,

eeried

---

### Post by eeried on 2005-07-21
I'm still in the same fix.

I managed to get as as far as this once with gnome-ppp:
```

GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATX3
GNOME PPP: STDERR: ATX3
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT0860888080
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT0860888080
GNOME PPP: STDERR: NO ANSWER
GNOME PPP: STDERR: --> Unknown dial response string.
GNOME PPP: STDERR: --> Disconnecting at Thu Jul 21 17:31:02 2005

```

This is hopeless I believe.

The problem is the modem seems to be a mixture of Smartlink and Conexant (Conexant being the codec: AC'97) though I don't understand any of that.

Plug and Play in the bios might also be a problem but I don't how to access the bios on this laptop (Access IBM demands a password).

There doesn't seem any place where things are explained in detail and clearly. The linmodem maling list will be as much confusing as all the rest, and the howtos are usually outdated, or not adapted to your distro. 

I can understand that nobody here has the patience to go over all that stupid problem again as it has been dealt with quite often on the forum.

 ](*,)

---

### Post by eeried on 2005-07-21
PS: scamodem says slamr is missing -- I installed the whole module package though.

---

### Post by centremco on 2005-07-21
I have a T40, I can have a look in my bios for you if you like, the only thing is, I don't really understand what you are looking for in the bios... Tell me what to look for and I'll see what I can find.
I'm a real newbie at linux.
But I do have some hardware and *indo*s knowledge.
I remember that, when I was running *indo*s, it recognized my modem as an HSFmodem.

And yes it's a VGA connector.
The T40 has an LPT, if you do go oldschool using an external modem, like a box with the nice lights...  :?   You could use a convertor from LPT to COM...  ;-)

grtz

---

### Post by eeried on 2005-07-22
Hello Centremco, and thank you 
About the bios: I mentioned this because someone mentioned Plug and Play playing mischief with their modem -- but I doubt this is the real problem.

Now if the modem is hsfmodem, I'll give up because the free conexant driver gives you a very limited bandwidth.

> The T40 has an LPT, if you do go oldschool using an external modem, like a box with the nice lights...  You could use a convertor from LPT to COM...

Now this sounds good.

I have a serial modem which works fine on Linux (Libranet) on my desktop.

But what's an LPT?

And how can I convert LPT to COM?

---

### Post by zagor on 2005-07-22
Hi all,

same problem of dialing here.
I've succeded in having the modem recognized by both gnome-ppp and the networking settings ([http://www.ubuntuforums.org/showthread.php?t=24736)](http://www.ubuntuforums.org/showthread.php?t=24736)).
I still can't dial the number, though.
When I enable the modem in the network settings, I just hear a sound (the phone line) for a couple of seconds and then nothing happens.
If I use gnome-ppp, the modem is contacted and after the ATZ it askd for a password.
Which password?
I've tried to sudo gnome-ppp but it still asks for psw.

The SimplyMepis liveCD works perfectly, out of the box. There should be a way to let it work in Ubuntu, then!

Another question: how is generally handled a modem connection on Ubuntu?
gnome-ppp doesn't come with Ubuntu, therefore I'm expecting that I should just use the networking application and just activate the connection, then it should dial without prompting. Am I correct?

---

### Post by eeried on 2005-07-24
> If I use gnome-ppp, the modem is contacted and after the ATZ it askd for a password. 
 Should be your connection pwd. But it seems either it isn't echoed back (so no sign appears) or in fact you can't type in anything

What I did was check "remember password" in the gnome-ppp dialog box.

On Simply Mepis the modem was detected as smarlink but never got a response after dialling. There was no dial-tone so I uncheked "wait for the dialtone) but it didn't work either. The phone line crackled, and all that but the connection failed.

However I copied a Mepis module that might help in ubuntu. I'll post the result. Mepis works better with such winmodem because it has proprietary modules and drivers. However some I've read on this forum that ubuntu isn't absolutely top-class on dial-up connection -- perhaps they simply meant the default Ubuntu networking app isn't up to scratch.

The gnome-ppp app is apparently more effective than the default networking  app, and in fact it's more pleasant to use. But you need to configure that default app, and then you can click on the "activate" button (a funny way of saying "connect" or "dial out").

Never say "die".

---

### Post by eeried on 2005-07-24
Wel I've tried many things, following the thread you mentioned earlier, and the linmodem pages.

The problem may be as follows:

the modem is Smartlink but there's a subsystem, says ModemData.txt, which is a conexant codec CTX (as Windows shows BTW).

Okay now I was'nt even able to find the free version oc that conexant driver. 

Is it possible to have both smartlink and conexant files (drivers or modules?) (doesn't look like it from the thread [http://www.ubuntuforums.org/showthread.php?t=24736](http://www.ubuntuforums.org/showthread.php?t=24736) and following pages.

 :---)

---

### Post by eeried on 2005-07-25
I've finally succeded.

I wasted much time over this issue because the scamdem results was not very clear to me. It seemed to pint to both smartlink and conexant.

So in fact what was important was the subsystem and the codec detected as conexant.

So it was a matter of downloading the ubuntu on this linuxant page:
[http://www.linuxant.com/drivers/hsf/full/downloads.php?PHPSESSID=da255767521799855fc3d17f5a4454ca](http://www.linuxant.com/drivers/hsf/full/downloads.php?PHPSESSID=da255767521799855fc3d17f5a4454ca)

(a zipped deb file) -- called full doesn't matter; at install you choose your llicence free or full (and not free=

unzip it, and install the package. The hsfmodem was configured.

I only had to config the pppconfig, and the gnome-ppp (as prrecaution) and typing wvdial started the connection.

Of course it's awfully slow.

As a reminder if you buy the driver you'll have to buy it again when your kernel version changes -- at least this was said on this forum). So I'm not going to buy it.

In fact you're better off with a smartlink winmodem...

The sound has gone though...

---

### Post by eeried on 2005-07-26
[quote]The T40 has an LPT, if you do go oldschool using an external modem, like a box with the nice lights...  You could use a convertor from LPT to COM...[quote]

Now I know that LPT means the printer port, and I'm not using a printer anyway.

 What does a convertor look like? is it a kind of plug, or some piece of software or both? :-?  Could be a good idea, centremco, thanks!

---

### Post by plasmatonic on 2005-08-05
My T40p's modem works flawlessly via [Ubuntu Starter Guide Directions](http://ubuntuguide.org/#installsmartlinkdriver)

---

### Post by eeried on 2005-08-07
You're lucky, plasmatonic!

n my case the modem works with the Linuxant (conexant) driver which in its free edition is very slow (14.4kbps). :-x 

I've read here and there that T40 have a Smartlink type of modem -- not in my case unfortunately.

---

