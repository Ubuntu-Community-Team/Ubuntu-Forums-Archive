---
title: "Hayes modem battle, pt. 2"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by rolypolycat on 2006-03-27
Hello!

I re-installed Ubuntu with the modem running after reading here that this solved a member's problem with their modem. Well, it handled part of the problem, but not all. Here is what the log file said while I tried both wvdial and the networking program under systems:
This is the messages I got when trying wvdial:

michelle@mainframe:~$ wvdial
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
michelle@mainframe:~$
************************************************************************
This is the log messages when I used ppp in Networking panel to dial out:

michelle@mainframe:~$ tail -f /var/log/messages
Mar 27 13:06:19 localhost pppd[28275]: pppd 2.4.3 started by root, uid 0
Mar 27 13:06:19 localhost pppd[28275]: Device ttyS1 is locked by pid 28245
Mar 27 13:06:29 localhost gconfd (root-28173): GConf server is not in use, shutting down.
Mar 27 13:06:29 localhost gconfd (root-28173): Exiting
Mar 27 13:06:33 localhost chat[28246]: ^MATDT8225473^M^M
Mar 27 13:06:33 localhost chat[28246]: CONNECT
Mar 27 13:06:33 localhost chat[28246]:  -- got it
Mar 27 13:06:33 localhost pppd[28245]: Serial connection established.
Mar 27 13:06:33 localhost pppd[28245]: Using interface ppp0
Mar 27 13:06:33 localhost pppd[28245]: Connect: ppp0 <--> /dev/ttyS1
Mar 27 13:06:49 localhost pppd[28275]: Device ttyS1 is locked by pid 28245
Mar 27 13:06:58 localhost pppd[28245]: Serial line is looped back.
Mar 27 13:06:58 localhost pppd[28245]: Connection terminated.
Mar 27 13:07:19 localhost pppd[28275]: Device ttyS1 is locked by pid 28245
Mar 27 13:07:29 localhost chat[28360]: timeout set to 60 seconds
Mar 27 13:07:29 localhost chat[28360]: abort on (ERROR)
Mar 27 13:07:29 localhost chat[28360]: abort on (BUSY)
Mar 27 13:07:29 localhost chat[28360]: abort on (VOICE)
Mar 27 13:07:29 localhost chat[28360]: abort on (NO CARRIER)
Mar 27 13:07:29 localhost chat[28360]: abort on (NO DIALTONE)
Mar 27 13:07:29 localhost chat[28360]: abort on (NO DIAL TONE)
Mar 27 13:07:29 localhost chat[28360]: abort on (NO ANSWER)
Mar 27 13:07:29 localhost chat[28360]: send (ATZ^M)
Mar 27 13:07:29 localhost chat[28360]: send (AT&FH0M0^M)
Mar 27 13:07:30 localhost chat[28360]: expect (OK)
Mar 27 13:07:30 localhost chat[28360]: ATZ^M^M
Mar 27 13:07:30 localhost chat[28360]: OK
Mar 27 13:07:30 localhost chat[28360]:  -- got it
Mar 27 13:07:30 localhost chat[28360]: send (ATDT8225473^M)
Mar 27 13:07:30 localhost chat[28360]: timeout set to 75 seconds
Mar 27 13:07:30 localhost chat[28360]: expect (CONNECT)
Mar 27 13:07:30 localhost chat[28360]: ^M
Mar 27 13:07:49 localhost pppd[28275]: Device ttyS1 is locked by pid 28245
Mar 27 13:07:54 localhost chat[28360]: ^MATDT8225473^M^M
Mar 27 13:07:54 localhost chat[28360]: CONNECT
Mar 27 13:07:54 localhost chat[28360]:  -- got it
Mar 27 13:07:54 localhost pppd[28245]: Serial connection established.
Mar 27 13:07:54 localhost pppd[28245]: Using interface ppp0
Mar 27 13:07:54 localhost pppd[28245]: Connect: ppp0 <--> /dev/ttyS1
Mar 27 13:08:19 localhost pppd[28275]: Device ttyS1 is locked by pid 28245
Mar 27 13:08:19 localhost pppd[28245]: Serial line is looped back.
Mar 27 13:08:19 localhost pppd[28245]: Connection terminated.
Mar 27 13:08:36 localhost gconfd (root-28427): starting (version 2.12.0), pid 28427 user 'root'
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Mar 27 13:08:36 localhost gconfd (root-28427): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
*************************************************************
This is my wvdial file:

[Dialer Defaults]
Modem = /dev/ttyS1
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
 Phone = 8225473	
 Username = [email]zetra61@Frontiernet.net[/email]
 Password = ********
Stupid Mode=yes

It does have a password; I didn't want to broadcast it all over the 'Net.

I've also edited my /etc/chatscripts file which had no info in it about my connection replacing the defaults with my info. I edited /etc/peers/provider which likewise had none of the info it needed.Every time I try to edit pap-secrets, it sure is a secret, because it comes up totally empty, with nothing whatsoever in the file. And the device ID of the device locking the process, 28245,gives this message with ps ax command:
28245 ttyS1 Ss+ 0:00 /usr/sbin/pppd  /dev/ttyS1 115200 noauth persist nocrt
That PID changes; last night it was 12454, then 12480, now this attempt, its 28245. All have the same error messages, though.
I also changed the timeouts in the scripts for 180 seconds, because frontiernet takes a loonngg time to connect, even under WinXP. I suppose they must attach each modem by hand, or something.^__^
So which  of these programs whould I concentrate on, and which should I skip using? Are they conflicting with each other? Should I remove one or the other? I also followed the advicde in Norton's guide to Linux, and made a symbolic link to /dev/modem, which didn't exist previously. that took care of the"cannot open /dev/modem: no such file or directory eror message. Now I have brand new error messages. "sigh"
 How do I fix this? Any help is greatly appreciated. I have a Hayes Accura 56k +fax external modem,model 5674US, connected by serial on COM 2.

sincerely,
Michelle

---

### Post by towsonu2003 on 2006-04-14
```
sudo wvdial
``` wvdial needs root privileges to read its configuration fiel as well as to dial.

---

