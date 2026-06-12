---
title: "3 Mobile Broadband E160G"
date: 2008-08-11
forum: General Help
---

### Post by tom.hill on 2008-08-11
Hello,

I'm trying to convert over to Ubuntu but am VERY new to it at the moment. I'm trying to install the Huawei E160G USB mobile broadband dongle provided by the 3 network. I've seen elsewhere that its possible to get the dongles to work but I've not found anything that clearly describes how to use the E160G. I noticed that something about having to install Network Manager v0.07 but as I can access the internet via Ubuntu I'd have to download it onto windows first? When I looked at the NW o.7 pages I couldn't clearly what links I had to download. 

Sorry to sound like an oaf but it takes a bit of time to adjust to a post windows lifestyle....

Cheers,

Tom

---

### Post by tom.hill on 2008-08-12
Has anybody got any suggestions where I might find out? :s

T

---

### Post by brunogirin on 2008-08-14
Tom,

I found this howto on the subject: [http://tensixtyone.com/perma/howto-debian-lenny-huawei-e160g]("http://tensixtyone.com/perma/howto-debian-lenny-huawei-e160g"). It is for Debian but it may work for Ubuntu.

However, it assumes that you can connect to the net through another method than the modem in order to download what's required. If you can't do that but you can connect in Windows, you will need to download one of the packages available here: [http://debs.michaelbiebl.de/network-manager/]("http://debs.michaelbiebl.de/network-manager/"), either the one called network-manager_0.7.0~svn3758-1_i386.deb or network-manager-gnome_0.7.0~svn759-1_i386.deb.

Then, move over those files where you can have access to them under Ubuntu and run the following in a terminal window to install them:

sudo dpkg -i network-manager_0.7.0~svn3758-1_i386.deb

You have more info on installing packages from file in the Ubuntu docs: [https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html").

**Disclaimer:** I haven't tried this so it may not work! I intend to try to install an E160G on Ubuntu in the next few days though. I'll keep you posted about the results.

---

### Post by tom.hill on 2008-08-16
Thanks Bruno,

Thats really helpful. I'll give it ago.

The servers at my work broke down this week because of a windows glitch. Me and the IT guy are trying to get everyone else to consider using Linux now ... :o)

Tom

---

### Post by andrew.mckevitt on 2008-08-21
I've been using the Huawei e169 under ubuntu heron for 2 months now. I just couldn't resist the £5 month deal. It is my secondary internet connection, but was nearly never to be. While i was waiting for my dongle to arrive, I browsed the forums etc. They told me it will work. I installed the software, the drivers etc and nothing. My E169 (works the same as an E220) refused to work, even with the 'Vodafone' drivers. Although it worked on the wife's macbook and my old 'windoze' box. I was going to give up and send it back when I had a flash of inspiration. I searched synaptic for 'PPP'
It found Gnome PPP. I installed this little gem and have never looked back.
Now get this. I have working mobile broadband with no CLI. Yes, I got it to work with absolutely no command line nonesense.
Here are the details which were published in a computer weekly mag.


    I am writing this in response to John Goldspink's letter from issue
1013. He seem'd to have fallen into the same trap as I had. Mobile
broadband has now become a cheap 'secondary' internet connection and I
was tempted by the free dongle and half price contract from my mobile
phone supplier which was 3 mobile. I had seen a couple of
letters/replies about mobile broadband and linux (one of which was in
this magazine) and theoretically it should all work, I was prepared for
a few teething problems and was  sure that I would be able to work them
out.
  
    So here we are, I have a working mobile broadband connection from 3
using the Huawei E169 dongle in a few steps and no command line
nonesense. It should also work with the E220. I shall outline my set up
and explain the steps necessary to get it working.
    First, my laptop is my secondary computer (my toy), and mobile
broadband is my secondary internet connection (a toy for my toy).
Second, I'm using the great Ubuntu 8.04 LTS fully updated

1.     Forget about all the forums on mobile broadband, they are mostly
out of date with the latest kernal release
2.     Start with a 'fresh install'. Like me, you've probably been
playing and 'messed' a few things up. Install all updates.
3.     From synaptic, install 'Gnome PPP'
4.     Switch off PC, plug in dongle, 
5.     Switch on PC, disable wireless while booting, this step is
important (funtion F2 on my dell)
6.     Once booted, 'Applications' 'Internet' 'Gnome PPP'
7.     Click 'setup'
8.     Click 'detect' on the modem page, it'll come up with
'/dev/ttyUSB0' or similar.
9.     Choose 'USB Modem' in 'Type'
10.   Then choose '460800' in 'speed' and then click 'close'
11.   This is where there seems to be a lot of confusion, Username and
Password, these do not seem necessary for a login to mobile networks but
the software needs an entry. I just use two single quotes for both ''.
12.   Tick 'remember password'
13.   Phone number - this is *99#. I believe this is the same for all UK
networks.
14.   Finally, at last, click 'connect' and click 'log' to check
progress
15.   Be patient, it is a dial-up modem
16.   You should  see the last entries in the log as primary DNS 4.2.2.3
and secondary DNS 4.2.2.4 This is with 3, other networks may vary.
Ocassionally, I get primary DNS 10.11.12.13 and secondary 10.11.12.14.
This is a failed connection, usually when i'm in a poor signal area.
Disconnect, move your PC and connect again, this has always worked for
me.
17.    All  your configurations will be saved for when you next use
mobile broadband, meaning that you just need to click 'connect' in Gnome
PPP next time you use it.
18.   PPP and Ubuntu. After 2 years of dismissing windows and embracing
linux, I still consider myself a 'noob'. I'd rather click 10 times than
resort to the command line. So, those of you like me, don't be put off,
linux isn't all 'CLI'. Oh yes, PPP! As I said I'm a 'noob'. PPP isn't
recognised as a 'network connection', therefore, you need to untick the
'work offline' bit in firefox under 'file' and if you use Pidgin, change
status to 'offline' first and then back to 'available'. I'm sure there
is a fix for this PPP issue and I'm sure that someone will let me know.

    As mobile broadband is set to revolutionise the way we connect to
the internet on the move, it'd be a shame if the linux community felt
left out, or should I say the linux noobie community. As I said earlier,
mobile  broadband is my secondary internet connection, so I have to swap
between the two, this is easy, enable your wireless when booting up for
your normal connection, or disable it if you want mobile broadband.
    I hope this helps and gives you(us) 'noobies' hope in the community,
they are hard at work, but because progress is so fast, communication
can sometimes be overlooked and the 'oldies' can be too quick to assume
that we know the basics. But don't despair, or even worse, go back to
windows, there is usually a solution out there.


I hope this helps you out.

---

### Post by Tom--d on 2008-08-21
> **brunogirin said:**
> Tom,

I found this howto on the subject: [http://tensixtyone.com/perma/howto-debian-lenny-huawei-e160g]("http://tensixtyone.com/perma/howto-debian-lenny-huawei-e160g"). It is for Debian but it may work for Ubuntu.

However, it assumes that you can connect to the net through another method than the modem in order to download what's required. If you can't do that but you can connect in Windows, you will need to download one of the packages available here: [http://debs.michaelbiebl.de/network-manager/]("http://debs.michaelbiebl.de/network-manager/"), either the one called network-manager_0.7.0~svn3758-1_i386.deb or network-manager-gnome_0.7.0~svn759-1_i386.deb.

Then, move over those files where you can have access to them under Ubuntu and run the following in a terminal window to install them:

sudo dpkg -i network-manager_0.7.0~svn3758-1_i386.deb

You have more info on installing packages from file in the Ubuntu docs: [https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html").

**Disclaimer:** I haven't tried this so it may not work! I intend to try to install an E160G on Ubuntu in the next few days though. I'll keep you posted about the results.


Install BOTH
Network-manager is the backend for it.
Network-Manager-gnome is the GUI of Network-Manager!

---

### Post by Weird Al on 2008-08-29
***** FIXED *****

The following goes in /etc/wvdial.conf

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT^SYSCFG=2,2,3FFFFFFF,1,2
Init5 = AT+CGDCONT=1,"IP","3internet"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Stupid Mode=1
Phone = *99#
Password = three
Username = three

[Dialer 3g]
Init4 = AT^SYSCFG=14,1,3FFFFFFF,2,4

[Dialer gprs]
Init4 = AT^SYSCFG=13,1,3FFFFFFF,2,4

```

and simply run wvdial as root.

Note that I got a similar problem to below a few times, but I sort of let it cool off for a while (read: I gave up) and when I came back to it it just worked...

Unfortunately I didn't get any sort of useful DNS or routing. To solve this I have a script to edit /etc/resolv.conf every time I connect to the wireless. 

Routing was solved with the output from wvdial. You only need to do this if you can't ping something by IP - that is, if this happens:

```
$ ping 212.23.6.100
connect: Network is unreachable

```

Look for the following:

```
--> local  IP address num.num.num.num
```

And then run (as root or with sudo)

```
# route add default gw num.num.num.num
```


** ------ Original issue **


> **andrew.mckevitt said:**
> 

*snip* 

14.   Finally, at last, click 'connect' and click 'log' to check
progress
15.   Be patient, it is a dial-up modem
*snip*


This is the only method that's worked so far for me but it doesn't go all the way. The modem hangs up. I may be missing packages, so here is the log.

Note that I didn't start from a completely clean system, but it's fairly clean...

Thanks in advance!

A

```
--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri Aug 29 20:47:52 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 10420
--> Using interface ppp0
--> Disconnecting at Fri Aug 29 20:47:55 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

```

---

### Post by Jeztastic on 2008-09-14
> **andrew.mckevitt said:**
>  

<<snip>>

PPP isn't
recognised as a 'network connection', therefore, you need to untick the
'work offline' bit in firefox under 'file' and if you use Pidgin, change
status to 'offline' first and then back to 'available'. I'm sure there
is a fix for this PPP issue and I'm sure that someone will let me know.

I hope this helps you out.

This totally did help me out. Thanks! By far the quickest and easiest way to get on with the E106G.

I totally concur, there are loads of good, useful applications out there which people have dedicated time to writing. Then you come here for help and get told to edit .conf files. Crazy! Linux never going to take off that way.

I would also like to know a fix for the 'work offline' problem. It's a pain in the ****.

---

### Post by caue.rego on 2008-11-24
> **Weird Al said:**
> ***** FIXED *****
To solve this I have a script to edit /etc/resolv.conf every time I connect to the wireless. 


C'mon, there must already exist some kind of script from NM itself that do edit resolv.conf! I just want to find THAT script and make it right instead of comming with a Microsoft solution for this.

---

### Post by caue.rego on 2008-11-26
> **caue.rego said:**
> C'mon, there must already exist some kind of script from NM itself that do edit resolv.conf! I just want to find THAT script and make it right instead of comming with a Microsoft solution for this.

well, not quite what i was expecting, but still nice enough: [http://ubuntuforums.org/showthread.php?p=6254989](http://ubuntuforums.org/showthread.php?p=6254989)

---

### Post by andrew.mckevitt on 2008-11-27
Just an update from my previous reply, 

I managed to pluck up the courage to update network manager in September, I'm so glad I did. The E169G works a treat under NM 0.7, 

Here's the [howto]("http://ubuntuforums.org/showthread.php?t=797059")

This howto is for Hardy, 

I think I'll stick with Hardy a while longer, got it just how I like it and it all runs like a dream.

---

### Post by coffeecups on 2008-12-08
Hello all,
The Huawei E220 is not behaving well for me either, have looked at lots of the posts on subject and getting closer all the time wvdial conf looks different for me I get

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0 S1 S2 S3
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- OK
ttyUSB0<*1>: Max speed is 460800; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<Info>: Device or resource busy
Killed
sue@sue-desktop:~$
Message from syslogd@sue-desktop at Mon Dec 8 19:36:55 2008 ...
sue-desktop kernel: [ 3290.650583] Oops: 0002 [2] SMP

Message from syslogd@sue-desktop at Mon Dec 8 19:36:55 2008 ...
sue-desktop kernel: [ 3290.650803] CR2: 0000000000000030

not sure what this means? any help please!

I tried Andrew McKevitt's solution and it seemed the best but it connected then disconnected straight away, got this on my dialler log

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L1DT*99#
--> Waiting for carrier.
ATM1L1DT*99#
CONNECT
--> Carrier detected. Waiting for prompt.
--> Don't know what to do! Starting pppd and hoping for the best.
--> Starting pppd at Mon Dec 8 20:42:01 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6143
--> Using interface ppp0
--> Disconnecting at Mon Dec 8 20:42:04 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.


The pppd error codes didn't make me any the wiser, feel like i'm close but not quite there
thanks for any help
__________________

---

### Post by Sgt.Schultz on 2008-12-17
Hello there! ):P

I'm completely new to Ubuntu, and have been a Windows user for many years now. A few days ago I decided that I was very tired of Vista, and wanted a new experience, so I decided to give Linux a try. 

However now I realise that I have next to no knowledge when it comes to Linux, and am having no luck with my mobile broadband device, the huawei E160G.
I've followed the steps andrew.mckevitt provided, and I'm starting to think I'm getting close to operational. When I run Gnome-PPP I get the following in my connection log.

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.

This message goes on and on....

---

### Post by Geebird on 2009-01-24
> **andrew.mckevitt said:**
> I've been using the Huawei e169 under ubuntu heron for 2 months now. I just couldn't resist the £5 month deal. It is my secondary internet connection, but was nearly never to be. While i was waiting for my dongle to arrive, I browsed the forums etc. They told me it will work. I installed the software, the drivers etc and nothing. My E169 (works the same as an E220) refused to work, even with the 'Vodafone' drivers. Although it worked on the wife's macbook and my old 'windoze' box. I was going to give up and send it back when I had a flash of inspiration. I searched synaptic for 'PPP'
It found Gnome PPP. I installed this little gem and have never looked back.
Now get this. I have working mobile broadband with no CLI. Yes, I got it to work with absolutely no command line nonesense.
Here are the details which were published in a computer weekly mag.


    I am writing this in response to John Goldspink's letter from issue
1013. He seem'd to have fallen into the same trap as I had. Mobile
broadband has now become a cheap 'secondary' internet connection and I
was tempted by the free dongle and half price contract from my mobile
phone supplier which was 3 mobile. I had seen a couple of
letters/replies about mobile broadband and linux (one of which was in
this magazine) and theoretically it should all work, I was prepared for
a few teething problems and was  sure that I would be able to work them
out.
  
    So here we are, I have a working mobile broadband connection from 3
using the Huawei E169 dongle in a few steps and no command line
nonesense. It should also work with the E220. I shall outline my set up
and explain the steps necessary to get it working.
    First, my laptop is my secondary computer (my toy), and mobile
broadband is my secondary internet connection (a toy for my toy).
Second, I'm using the great Ubuntu 8.04 LTS fully updated

1.     Forget about all the forums on mobile broadband, they are mostly
out of date with the latest kernal release
2.     Start with a 'fresh install'. Like me, you've probably been
playing and 'messed' a few things up. Install all updates.
3.     From synaptic, install 'Gnome PPP'
4.     Switch off PC, plug in dongle, 
5.     Switch on PC, disable wireless while booting, this step is
important (funtion F2 on my dell)
6.     Once booted, 'Applications' 'Internet' 'Gnome PPP'
7.     Click 'setup'
8.     Click 'detect' on the modem page, it'll come up with
'/dev/ttyUSB0' or similar.
9.     Choose 'USB Modem' in 'Type'
10.   Then choose '460800' in 'speed' and then click 'close'
11.   This is where there seems to be a lot of confusion, Username and
Password, these do not seem necessary for a login to mobile networks but
the software needs an entry. I just use two single quotes for both ''.
12.   Tick 'remember password'
13.   Phone number - this is *99#. I believe this is the same for all UK
networks.
14.   Finally, at last, click 'connect' and click 'log' to check
progress
15.   Be patient, it is a dial-up modem
16.   You should  see the last entries in the log as primary DNS 4.2.2.3
and secondary DNS 4.2.2.4 This is with 3, other networks may vary.
Ocassionally, I get primary DNS 10.11.12.13 and secondary 10.11.12.14.
This is a failed connection, usually when i'm in a poor signal area.
Disconnect, move your PC and connect again, this has always worked for
me.
17.    All  your configurations will be saved for when you next use
mobile broadband, meaning that you just need to click 'connect' in Gnome
PPP next time you use it.
18.   PPP and Ubuntu. After 2 years of dismissing windows and embracing
linux, I still consider myself a 'noob'. I'd rather click 10 times than
resort to the command line. So, those of you like me, don't be put off,
linux isn't all 'CLI'. Oh yes, PPP! As I said I'm a 'noob'. PPP isn't
recognised as a 'network connection', therefore, you need to untick the
'work offline' bit in firefox under 'file' and if you use Pidgin, change
status to 'offline' first and then back to 'available'. I'm sure there
is a fix for this PPP issue and I'm sure that someone will let me know.

    As mobile broadband is set to revolutionise the way we connect to
the internet on the move, it'd be a shame if the linux community felt
left out, or should I say the linux noobie community. As I said earlier,
mobile  broadband is my secondary internet connection, so I have to swap
between the two, this is easy, enable your wireless when booting up for
your normal connection, or disable it if you want mobile broadband.
    I hope this helps and gives you(us) 'noobies' hope in the community,
they are hard at work, but because progress is so fast, communication
can sometimes be overlooked and the 'oldies' can be too quick to assume
that we know the basics. But don't despair, or even worse, go back to
windows, there is usually a solution out there.


I hope this helps you out.

I've just sort of followed these instructions to get an E160G working on 2 laptops an old Fujitsu Lifebook and a newer HP 6720.
The Fujitsu was a fresh install of Hardy Heron, the HP has been running Heron for around 12 months. In both cases after I installed the Gnome PPP I found that it would not work. So I entered a user name and password, not just the single quotes as suggested (I made up the user name and password) and it worked first time on the Fujitsu and I had to unplug and replug in the dongle on the HP and then it sprang in to life.
Both laptops now have mobile internet. Thank you for all your help.

---

### Post by labinnsw on 2009-07-10
On my PC I am running Hardy as my default OS. Some time ago I bought a Huawei E160G USB Modem and subscribed to the 3 network. I used these instructions to set up gnome ppp and [these instructions]("http://ubuntuforums.org/showthread.php?t=797059") to install network manager 0.7.

It was working beautifully, but since I also had adsl2 cable connection, I stopped using the USB modem and kept the service for emergencies.

My rainy day came a few days ago but my umbrella would not work. Based on information from the message log, the modem was detected as a GSM mobile broadband modem but network manager would not detect it.
After 3-4 days of going through the threads and trying every thing posted on Huawei E160G, E169G and E220. Nothing worked. There was not even the slightest hint of any change.

Luckily I also have Jaunty Jackalope on another partition. So I looked at the three file on Jaunty and, in Administrator mode, made some changes to the file on Hardy. Once I rebooted it worked for that evening, but when I came back the following evening, the file reverted to the original and it stopped working again. I was filthy. 

I backed up the network manager directory from Hardy to a safe place. And as added precaution, I also backed up the network manager directory from Jaunty to a safe place. In Administrator mode I deleted the network manager from Hardy and replaced it with a copy of the network manager from Jaunty. After rebooting yesterday evening to my surprise it worked. No other configuration necessary.

I came back this morning and it still works. This is a process that will solve the problem in less than 5 minutes if you already have a working network manager. If you don't have a working network manager, (I have never timed it, but) I am estimating that Jaunty can be installed in approximately 30 mins.

I am suggesting this if you just want your computer to work. But if you want to go through the process of detecting the problem, I failed miserably in that department.

---

