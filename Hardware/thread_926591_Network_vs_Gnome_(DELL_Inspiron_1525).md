---
title: "Network vs Gnome (DELL Inspiron 1525)"
date: 2008-09-22
forum: Hardware
---

### Post by Oenologist on 2008-09-22
I happen to have a strange problem with my laptop. Until I was using only the wireless connection, everything worked OK, however when I connected to my university network (check the link for details: [http://www.inf.aber.ac.uk/advisory/faq/138/#unix](http://www.inf.aber.ac.uk/advisory/faq/138/#unix) ), a strange thing started to occur. 

When the computer is booted with network cable plugged in, after logging in gnome freezes, there's an orange screen and cursor and nothing can be done. Interestingly, when I boot with network cable unplugged, everything works fine. I believe that when the cable is plugged in, it starts somekind of network processes which are in conflict with gnome. 

Any help?

EDIT. I have browsed the internet and found a bit similar problems people had with Intel graphic cards, but I believe its partly the fault of the university network configuration which utilises authentication by wpa_supplicant, or something.

---

### Post by oralalikaroaku on 2008-09-22
Have you tried to plug network cable with anorher notebook let say under windows OS? if you are experiencing the same case, then perhaps the network cable problem. You know what, I have the same problem bith using notebook with Win or Lin the booting take ages and system is slowing down... then what happen is that the cable network  kind of leaking, perhaps some rate eat the cable. But after my IT guy change the new cable, all back to normal.

It's stupid tips. But it happen. Im not IT nor ubuntu expert, Im a linux newbie that think linux works like windows.

Greet from Indonesia.
DJ
Dell inspiron 700m
Ubuntu 8.4

---

### Post by Oenologist on 2008-09-22
Not stupid at all.
I should check other net cables, however it's not the most convenient thing to uplug the cable each time I want to reboot.

Moreover, the combination CTRL+ALT+BKSPC works, I'm taken back to the logging screen, but then its impossible to log in again. The same thing as with booting with cable pluged - complete freeze. 

Assumption - once the cable is plugged while booting, the network processes become active and it prevents from logging to the system. Only reboot with unplugged net cable makes logging in possible. Then after few minutes network finally comes to life.

So, I don't have to say that such course is pretty irritating, cause it really diminishes the functionality of system (long wait before net connection, X restart is impossible, playing with the cable - plugging/unplugging, etc.).

I really wish somebody fixed this, cause it looks like a minor, but really irritating bug.

---

### Post by IntuitiveNipple on 2008-09-22
It sounds to me as if with the network connected the system configures the interface.

Later, when applications are executing they will try to resolve the name of the PC. In some circumstances that can cause a DNS look-up to be attempted (of the PC's local name) and if there is no good answer it can cause applications to become unresponsive and effectively lock-up the system.

What are the contents of the system's /etc/network/interfaces file?

Also, attach (compressed) copies of the system's daemon.log and kern.log files captured when the error occurs:
```

cd ~
cat /var/log/daemon.log | gzip > daemon.log.gz
cat /var/log/kern.log | gzip > kern.log.gz

```

---

### Post by Oenologist on 2008-09-22
> **IntuitiveNipple said:**
> 

What are the contents of the system's /etc/network/interfaces file?


> #BEGIN

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
address 169.254.0.0
netmask 255.255.0.0
gateway 0.0.0.0

#END


It has been configured accordingly to the university network requirements, I can also show you the wpa_supplicant.conf file:

> # BEGIN wired network configuration

ap_scan=0

ctrl_interface=/var/run/wpa_supplicant

network={
          key_mgmt=IEEE8021X
          eap=PEAP
          phase1="peaplabel=1"
          phase2="auth=MSCHAPV2"
          identity="xxxxxxx@aber.ac.uk"
          password="xxxxxxxxxx"
}

# ENG wired network configuration



---

### Post by IntuitiveNipple on 2008-09-22
The only thing I notice there is in /etc/network/interfaces, you've got some additional static entries for eth0:
```

address 169.254.0.0
netmask 255.255.0.0
gateway 0.0.0.0

```
It is possible they conflict but they shouldn't cause the symptoms you're reporting.

I can't see anything obvious in the two logs so far. Can you attach **/var/log/wpa_supplicant.log** ? It is possible there is some clue there.

---

### Post by IntuitiveNipple on 2008-09-22
Just to be thorough, is this the MAC address you've registered with the Operators for the Halls Network?
```

00:21:9b:d1:a2:93

```

---

### Post by IntuitiveNipple on 2008-09-22
I noticed the error in kern.log:
```

Sep 22 10:29:02 dell-desktop kernel: [  198.586553] compiz.real[6051]: segfault at 00000040 eip 08055a6d esp bfcb9e10 error 4

```
Can you disable compiz and test it?

System > Preferences > Appearance > Visual Effects: **None**

---

### Post by Oenologist on 2008-09-22
Switching effects hasn't helped. There's still the same problem with logging while having the net cable plugged. 

The address you've given is indeed the Mac I needed to enter during the hall registration.

I have no idea where those IPs come from, but I believe they've been somehow entered auatomatically during the connection configuration. But I'm not sure.

The wpa_supplicant.log is empty.

---

### Post by IntuitiveNipple on 2008-09-22
Daft question, but is the wpa_supplicant package installed and running?
```

dpkg-query -l 'wpa*'

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  wpagui                      <none>                      (no description available)
ii  wpasupplicant               0.6.3-2ubuntu1~ppa2h        Client support for WPA and WPA2 (IEEE 802.11i)

```

And also:
```

ps -ef | grep wpa

root      6785     1  0 Sep19 ?        00:00:01 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log

```

---

### Post by Oenologist on 2008-09-22
Hey. Got some new stuff for you to think over.

I decided to wait a while after logging with cable plugged. During the next few minutes such things happened:

- on the orange screen a gray window appeared, no text in it
- after few more minutes the text appeared on the grey window:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Gnome started, everything was loaded, the network is working but everything has a strange layout (like Windows 3.11 ;) ). After a few more minutes I have heard the Ubuntu sound...

---

### Post by IntuitiveNipple on 2008-09-22
Hang on - lets back up. When I asked you earlier to show the contents of /etc/network/interfaces, did you report the *entire* contents of the file? If so, the local loop interface is missing, it should have this in it as well:
```

auto lo
iface lo inet loopback

```
Remember when I said:
> 
Later, when applications are executing they will try to resolve the name of the PC. In some circumstances that can cause a DNS look-up to be attempted (of the PC's local name) and if there is no good answer it can cause applications to become unresponsive and effectively lock-up the system.

If the local loopback interface (localhost) is missing the same and worse can happen.

---

### Post by Oenologist on 2008-09-22
> **IntuitiveNipple said:**
> Hang on - lets back up. When I asked you earlier to show the contents of /etc/network/interfaces, did you report the *entire* contents of the file? If so, the local loop interface is missing, it should have this in it as well:
```

auto lo
iface lo inet loopback

```
Remember when I said:

If the local loopback interface (localhost) is missing the same and worse can happen.

Yes. It was the entire file. Had no auto lo entry there. 
I'll put it there and check what happens.

---

### Post by Oenologist on 2008-09-22
Incredible! Everything runs smoothly, no problems at all! My friend, you're the man! A'right! Cheers for your time and help!

---

### Post by coolfusion on 2008-09-23
this is not at all a problems ! 
it has very simple solution,little 
unusal but really effective ,before unpluging the network cable.
goto 
sudo su 
$cd /etc/network
$vi interfaces 
$comment auto etho <# auto etho>
now on rebooting ur system it will not look for devices and 
will work fine.
but now in order to restart the network remove the comment 
cheersssssssssssssssss!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Oenologist on 2009-01-02
Refreshing the topic instead of creating a new one.

I got a second laptop, the same configuration as the previous one. The old one works perfectly, the new one seems to be configured in the same way, but...another network issue appears.

A nasty and recurring thing - the system looses the network connection approx. an hour after starting. Then the thing appears randomly throughout the day. A fast reset of the connection (with sudo /etc/init.d/networking restart) does the job, but sooner or later it crashes again. 

I thought it might be the issue of NTP and clock syncronization, but after disabling the process, the problem persists...

---

### Post by Oenologist on 2009-01-08
Anyone?

---

