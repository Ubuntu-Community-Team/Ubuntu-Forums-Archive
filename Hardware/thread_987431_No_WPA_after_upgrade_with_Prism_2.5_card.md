---
title: "No WPA after upgrade with Prism 2.5 card"
date: 2008-11-19
forum: Hardware
---

### Post by megazorg on 2008-11-19
Hi all, I usually don't use ubuntu, but I tried 8.04 and it worked great. so I upgraded to 8.10 (made the backup + fresh install using Live Media).
My problem, I was able to connect to WPA (with 8.04) using my
Intersil Corporation Prism 2.5 Wavelan chipset (rev 01).
This is no longer the case with Ubuntu 8.10.

Details:
- Box: (Old) IBM Thinkpad T30
With 8.04: 
- I was able to connect using:
  $ sudo wpa_supplicant -iwlan0 -Dhostap -c/etc/wpa_supplicant.conf
  $ sudo dhclient wlan0
- I had "blacklist orinoco" in /etc/modprobe.d/blacklist
- Never used Network-Manager
With 8.10:
- Exact same configuration: Wifi works, but only WEP, no WPA
- When I write:
  $ sudo wpa_supplicant -iwlan0 -Dhostap -c/etc/wpa_supplicant.conf
  Unsupported driver "hostap"
- (Yes, I installed hostapd and hostap-utils)
- Tried using "blacklist hostap" instead of "blacklist orinoco", no luck (reboot everytime, same result).

- If I try something like this, I get :
  $ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf
Received 1093 bytes of scan results (8 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'coruscant'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 24 pairwise 24 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8

This suggests to me that wext is being used (?).

and dmesg shows:

[ 4160.396372] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[ 4162.947788] ADDRCONF(NETDEV_UP): wifi0: link is not ready
[ 4162.950586] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4163.529382] wifi0: LinkStatus=6 (Association failed)
[ 4163.529678] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[ 4163.957822] wifi0: LinkStatus=2 (Disconnected)
[ 4163.958119] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[ 4164.080774] wlan0: Trying to join BSSID 00:00:00:00:00:00
[ 4164.086763] wifi0: LinkStatus=2 (Disconnected)
[ 4164.087039] wifi0: LinkStatus: BSSID=44:44:44:44:44:44

As mentioned, I am using the exact same wpa_supplicant.conf. It works well with Windows (dual-boot).

Is there something I am missing? Any suggestions?

Thanks

---

### Post by vom on 2008-12-10
Looks like they took the hostap driver out of wpa_supplicant in Intrepid :(

wpa_supplicant -h
<snip>
drivers:
  wext = Linux wireless extensions (generic)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver
</snip>

[http://changelogs.ubuntu.com/changelogs/pool/main/w/wpasupplicant/wpasupplicant_0.6.4-2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/w/wpasupplicant/wpasupplicant_0.6.4-2/changelog)

Says this:

  * Disable building of hostap driver backend, the version of hostap driver in
    existence since Linux 2.6.14 (or before) uses the wext driver backend.

So wext *should* be working.  I'm at work right now so I can't test this without taking my connection down.  When I get a free moment I'll see if I can get my hostap card talking WPA using wext.

---

### Post by vom on 2008-12-10
No luck :(

I am using a Senao / Engenius PCMCIA card that worked fine using the hostap driver for wpa_supplicant.  It looks like wext is definitely making the card 'do things' but alas is not working.  It basically starts the 4-way handshake and then dies and loops.

I even upgraded the firmware on the card several times and still nothing.  I guess you could file a bug report asking for this to be brought back in.  It's very minimal to add back in and I think that we have 2 confirmed cases of wext driving a prism card on paper, but not in reality.

Sorry, good luck.

---

### Post by megazorg on 2008-12-14
Yes, no more hostap driver in Ubuntu.
So, I moved to Puppy Linux... Using a live image from a 250MB USB Drive, I have my wifi up and running again. No configuration required, simply amazing.

Thanks anyway.

---

### Post by mightyiam on 2011-10-30
To solve this with this prism2 card I upgraded the firmware on the card to 1.8.2 using this guide:
[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

---

### Post by nothingspecial on 2011-10-30
There is a Necromancer on the loose. :shock:

Closed.

---

