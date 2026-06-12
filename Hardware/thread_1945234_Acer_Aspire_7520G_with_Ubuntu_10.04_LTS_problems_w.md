---
title: "Acer Aspire 7520G with Ubuntu 10.04 LTS problems with wireless"
date: 2012-03-22
forum: Hardware
---

### Post by rgmno1 on 2012-03-22
Hello people, 

I'm new to ubuntu and I have installed Ubuntu 10.04 LTS (awesome OS) I haven't found any problem with it except for the fact that after about 1 hour of browsing the internet, watching videos online, listening to music or talking on Skype my wireless automatically disconnects. I have searched for the problem and already tried the rfkill solution with no good, 'rfkill list' shows me that nothing is blocked yet I can't connect to the wireless. I have tried 'sudo apt-get install linux-backports-modules-wireless-lucid-generic' as well with no luck. Shutting down and restarting my laptop fixes the problem but again only for a while, and to be honest I hate having to restart my machine every hour.

Please help, I've been fighting this thing for over 2 days now :( , everything is appreciated :)

PS: I'm new to the forum as well so any detailed info is good for me. THANK YOU in advance :D

---

### Post by rgmno1 on 2012-03-23
anyone?

---

### Post by janisgeiger on 2012-03-23
Sorry... I don't think I can help you out really... I'm a linux newbie too.

But, only some suggestions
maybe it's something about the ip getting resetet or to be called again? (this is not knowledge just  I don't know really.) but it seems like a procedure, like the company sending you another "whatever.." every hour... and that linux doesn't catch up.

2nd. did you try "connect to hidden wireless network?" (left-click + entering your details again. or deleting your connection previously and setting it up again?

that could be faster as a restart if it would help.
also disabling / enabling your wireless hardware directly, though I don't have a clue on how to do that in linux.



here are some things I stored in a file while I had problems with a certain wireless connection too. (though none of them worked). but maybe they will for you or lead you to something via google



sudo killall dhclient
sudo dhclient eth0
sudo /etc/init.d/networking restart

[http://serverfault.com/questions/24515/ubuntu-server-how-do-i-request-a-new-ip-from-my-dhcp-server](http://serverfault.com/questions/24515/ubuntu-server-how-do-i-request-a-new-ip-from-my-dhcp-server)

/var/lib/dhcp3/dhclient.leases

sudo dhclient -r




cheers, sorry if it's not so professional ;)

---

### Post by rgmno1 on 2012-03-23
Help
I have tried somethiyng on my own and followed the ubuntu help icon and installed windows wireless drivers and used it to install the same driver i used with windows vista. Now ubuntu can't detect my wireless card anymore. I tried uninstalling the drive but it didn't fix the problem and now I don't even have temporary internet :(( 
Please help or I will have to switch toi windows 7 until a proper ubuntu wireless support is relesed.

---

### Post by rgmno1 on 2012-03-23
And thanks for the reply but i forgot to mention that after i am disconnected if i cljose and than restart wireless or network from software it shows me that they are both disconnected afterwards

---

### Post by rgmno1 on 2012-03-23
Ok so I've freshly reinstalled ubuntu 10.04.4 because of my own supidity and I am still stuck with the same problem: 
After some time of being connected to the interned I get a big disconnect, 
rfkill list shows nothing is blocked and switching off network or wireless from software or switch and than restarting them does nothing.
Only thing I can do is shut down (not restart) and than start my machine again... 
Oh and I only have a time limit of aprox 1h of internet usage before I get this lovely problem...

Please help me.

---

### Post by janisgeiger on 2012-03-23
ok, so left-click on the wireless icon shows you no connections anymore? or can you still see some, but just can't connect to them?

if you can still see some, I would still give "Connect to hidden wireless network" a try. it would mean that your wireless adapter is still behaving normally, but for some reason can't connect to your network anymore. Enter name of your network, connection type (most common WPA & WPA2 personal) and the password.

as rfkill doesn't show anything, I don't think it will lead you to a solution.

have you tried out booting into windows (normal restart, not shutting down) after your wireless disconnects? if so, does wireless work then?

I'm confused why your wireless works again after you shut down completely, but not after rebooting into linux without shutting down! kind of suspicious. maybe an IT person could tell you something about it..... (go into a shop. or call Acer)

also, I found [this]("http://linuxwireless.org/en/users/Drivers/madwifi") on [this]("http://www.linlap.com/wiki/acer+aspire+7520") site. (was that the one you installed?)

here are the drivers for windows, just in case
 [http://seoroot.com/blog/windows-xp/acer-invilink%E2%84%A2-nplify%E2%84%A2-80211bgdraft-n-wlan-drivers.html](http://seoroot.com/blog/windows-xp/acer-invilink%E2%84%A2-nplify%E2%84%A2-80211bgdraft-n-wlan-drivers.html)

at the moment, I think the problem could be
-your ip needs to be refreshed / called again after 1 hour (see link in the post above), windows is able to do that, linux ubuntu apparently not (bad combination)
-or something wrong with ubuntu in general, bad support for your wireless card...

by the way,are you running on battery when it disconnects? but I guess rfkill.

if the latter, i would advise you to google.... It's all I can say, from my experience. Naming your wireless adapter (which seems to be "Acer InviLink 802.11b/g") + linux + ubuntu, or similar. (eg "acer wireless ubuntu")
Also, search in synaptic package manager naming the terms "wireless" or "acer" or similar, if something sounds like a good thing to install. (can uninstall later if nothing helps)

ubuntu +linux' biggest problem is the hardware / driver support, so I'm sorry if something doesn't work for you. but maybe you have luck and can find something on the net (as you're not the only person with an Acer Aspire 7520G running linux on it I hope.)

[http://www.ehow.com/about_6704740_dhcp-lease-time_.html](http://www.ehow.com/about_6704740_dhcp-lease-time_.html)
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)
[http://ubuntuforums.org/showthread.php?t=1141310](http://ubuntuforums.org/showthread.php?t=1141310)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

though the drivers are pretty different, I just read, guys with Acer laptops on the net, a wireless card close to yours (acer invilink) apparently posted that it seems to work with them.

You'll have to find out. cheers, good luck.

---

### Post by rgmno1 on 2012-03-24
Thank you again for the response.... and to answer your question.... on windows wireless works perfectly, on ubuntu it completely disconnects (no other connections available)... 
I'll try to see what I can find on the web like you suggested, there has to be someone else with a laptop like mine somewhere :D

---

### Post by janisgeiger on 2012-03-24
Another thing I found out about:

Try [ndiswrapper]("http://en.wikipedia.org/wiki/NDISwrapper"), if nothing else works.
snyaptic-> ndiswrapper
*ndiswrapper-utils-1.9, ndiswrapper-common*

then install ndisgtk
synaptic -> ndisgtk
*ndisgtk*

Now launch ndisgtk via a terminal

> sudo ndisgtk(alternatively, *ALT-F2, *sudo ndisgtk)

You should be able to locate ndisgtk to your Wireless Driver for Windows
- either on your Windows Partition
- or as an alternative, download the driver from your wireless company's homepage (probably ACER), double-click in Ubuntu to let it be installed via Wine (just so that the files are there), then locate the file (.inf) in ndisgtk.

> to do so, in ntdisgtk go to
install new driver, location, push STRG-H[SIZE=1]*[/SIZE] and scroll up a bit, to *.wine**/drive_c/Program Files/nameOfWirelessDriver*

* As .folders or .files are hidden files in the file-browser, you can only see them if you do a STRG-H (and .wine is a hidden folder). Cheers, goodluck!

---

### Post by rgmno1 on 2012-03-25
I tried installing the xp driver but I got the error unable to load c:\users\rgmno1\(sth long)\(the same)\InstallHelper.dll
I also tried installing directly without installing into wine first and I couldn't use wireless anymore not even after uninstalling the driver and the program, ubuntu couldn't find my wireless card anymore, so I reinstalled ubuntu (again) and I upgraded to 11.10. It seemed it solved part of the problem... I mean I can stay on internet for as long as I want but without overdoing it (i.e. playing online games), it would seem that if my pc receives too much data at once it simply blocks itself and I can't start it again without shutting down the machine (stop the power from getting to the wireless card I think).
I'm begging to wonder if there is a setting somewhere which prevents a certain amount of data to be received by the system at one time (i.e. online games*).
Any thoughts on this?

---

### Post by rgmno1 on 2012-03-25
And thanks janisgeiger... It would seem you are the only guy interested in this topic and helping me out o.O

---

### Post by rgmno1 on 2012-03-25
I guess this is becoming more of a diary than a thread for discussion and a plea for help but anyway.....
It seems I was wrong with the last statement... I have noticed that the more I shut down and start up my machine the less time I can use the wireless.... after a fresh install I can use the wireless as much as I want but there are updates to do and these require a restart after the restart there seems to be a limit to how much I can use the wireless, I don't know if there is anything in the updates that causes this so I won't jump to conclusions....
But the sad reality is that after the first restart of ubuntu I am limited to the use of wireless... to describe it more accurately the wireless completely disconnects (it shows me Wireless network disconnected where I choose the connection I wish to use).
When using:
rfkill list
the output shows me that nothing is blocked so 
rfkill unblock all 
does nothing.
Using ndiswrapper makes my wireless card disappear (I am only showed wired connections) and not even rfkill can detect it anymore... not even after uninstalling the program and the windows driver (only thing I could think of to solve this is reinstalling ubuntu).
So I'll add this line just so it doesn't look like a diary.

Dear fellow Ubuntu users do you have any thoughts on this issue?

---

### Post by wildmanne39 on 2012-03-26
Hi, I will try to help you I work in the networking section I am not an expert but I will give it my best, please post the outputs of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by rgmno1 on 2012-03-26
So here is the output
 ```

~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Avaahn-laptop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: forcedeth
--
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
    Kernel driver in use: ath5k
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 004 Device 002: ID 192f:0416 Avago Technologies, Pte. 
rgmno1@Avaahn-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Piratnet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:10:12:5A:53   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_realtek   330815  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
nvidia              11713772  43 
joydev                 17693  0 
snd_hda_intel          33390  4 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               92992  1 uvcvideo
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17083  1 videodev
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
ath5k                 156371  0 
ath                    24067  1 ath5k
mac80211              462046  1 ath5k
bch                    22061  1 nand_bch
psmouse                73882  0 
r592                   18144  0 
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
memstick               16569  1 r592
edac_core              53746  0 
cfg80211              199630  3 ath5k,ath,mac80211
soundcore              12680  1 snd
k8temp                 13057  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
binfmt_misc            17540  1 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
wmi                    19256  1 acer_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
usbhid                 47198  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
hid                    95463  1 usbhid
sdhci                  32166  1 sdhci_pci
forcedeth              67563  0 
crc_itu_t              12707  1 firewire_core
pata_amd               14121  0 
ahci                   26002  2 
libahci                26861  1 ahci

```
Thank you very much for the help :)

---

### Post by wildmanne39 on 2012-03-26
Hi, we have been having a few people with issues with this card in the last 2 days, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```
do not reboot after running the commands, if it helps we will need to make it permanent.
Thanks

---

### Post by rgmno1 on 2012-03-26
Thank you for the help...
If it helps here is the output after I get disconnected... happened 5 min ago >__>
```

rgmno1@Avaahn-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Avaahn-laptop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
rgmno1@Avaahn-laptop:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: forcedeth
--
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
    Kernel driver in use: ath5k
rgmno1@Avaahn-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 004 Device 002: ID 192f:0416 Avago Technologies, Pte. 
rgmno1@Avaahn-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rgmno1@Avaahn-laptop:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
rgmno1@Avaahn-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_realtek   330815  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
nvidia              11713772  43 
joydev                 17693  0 
snd_hda_intel          33390  4 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               92992  1 uvcvideo
arc4                   12529  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17083  1 videodev
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
ath5k                 156371  0 
ath                    24067  1 ath5k
mac80211              462046  1 ath5k
bch                    22061  1 nand_bch
psmouse                73882  0 
r592                   18144  0 
nand_ecc               13230  1 nand
mtd                    33181  2 sm_common,nand
snd                    68266  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
memstick               16569  1 r592
edac_core              53746  0 
cfg80211              199630  3 ath5k,ath,mac80211
soundcore              12680  1 snd
k8temp                 13057  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
binfmt_misc            17540  1 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
wmi                    19256  1 acer_wmi
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
usbhid                 47198  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
hid                    95463  1 usbhid
sdhci                  32166  1 sdhci_pci
forcedeth              67563  0 
crc_itu_t              12707  1 firewire_core
pata_amd               14121  0 
ahci                   26002  2 
libahci                26861  1 ahci

```

---

### Post by rgmno1 on 2012-03-26
I entered the commands you said now.... 
I hope it works
Stay tuned ;)

---

### Post by rgmno1 on 2012-03-26
It didn't work :(
here is the output after I got d/c
```

rgmno1@Avaahn-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Avaahn-laptop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
rgmno1@Avaahn-laptop:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:0126]
    Kernel driver in use: forcedeth
--
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC [1468:0428]
    Kernel driver in use: ath5k
rgmno1@Avaahn-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 004 Device 002: ID 192f:0416 Avago Technologies, Pte. 
rgmno1@Avaahn-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
rgmno1@Avaahn-laptop:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
oh and the problem isn't 2 days old... I have experienced this problem with ubuntu 9 as well but I thought that it would be fixed later on like a fool.... and now ubuntu 11.10 and still same problem... I'm an idiot for not reporting this at that time

---

### Post by rgmno1 on 2012-03-26
it would seem the problem was solved with that command.... 
I tried it again without having any program running.... and after the last command I closed network connections and input it again.... than started the network...
I will keep the thread open for some more time in case it dies out again if it'll be ok I'll mark it as solved.
Thanks again

---

### Post by wildmanne39 on 2012-03-26
Hi, remember that this is for one boot only if you reboot you will have to run those commands again, so we will need to make it permanent like this:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```

Add a single line:

```
options ath5k nohwcrypt=1
```

Proofread carefully, save and close gedit. Reboot.

---

### Post by rgmno1 on 2012-03-26
so I did that and got the following warnings 

```
(gksudo:1940): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:1947): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.B4PACW': No such file or directory

```

It still opened an empty text document where I inserted the code you said and than restarted.... did it still work?

---

### Post by wildmanne39 on 2012-03-26
Hi, it should have that warning is not important for what we were doing.
Thanks

---

### Post by rgmno1 on 2012-03-26
The fix wasn't made permanent so I turned the commands you gave me into an executable.
Just had to restart.
Or I wonder if this made the wireless take up more data before locking itself...
I will keep posting... about it if it goes down again

---

### Post by wildmanne39 on 2012-03-26
Hi, > Or I wonder if this made the wireless take up more data before locking itself...I do not know.

Please post the contents of:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
thanks

---

### Post by rgmno1 on 2012-03-27
Sorry for the late reply.
This is all the content there is 

options ath5k nohwcrypt=1

the rest of the document is blank

---

### Post by wildmanne39 on 2012-03-27
Hi, just below options ath5k nohwcrypt=1 does it say exit o? If not add it.
Thanks

---

### Post by rgmno1 on 2012-03-27
I've just added "exit o" ...
And as I said, apart from  "options ath5k nohwcrypt=1" the whole document is blank, nothing there.
I've just confirmed a few moments ago that I got d/c again while downloading a torent (worked ok for 4 hours) and talked on skype and watched some online videos .... 
So the issue still stands :(

---

### Post by wildmanne39 on 2012-03-27
Hi, it that file it should be exit 0 and not exit o that was my mistake.

You said you > I turned the commands you gave me into an executableyou might undo that when you change the file and see if that helps.
Thanks

---

### Post by rgmno1 on 2012-03-27
adding "exit 0" in the script made the wireless unusable.
As soon as I boot up the pc it connects to the wireless and a few moments later it disconnects completely.
Now when I start up the pc I run the commands you told me in a terminal.

---

### Post by wildmanne39 on 2012-03-27
Hi, paste the exact content of the file here please.

Did you change the executable?
Thanks

---

### Post by rgmno1 on 2012-03-27
the commands aren't working anymore :(( ... is this thing evolving or something?

---

### Post by wildmanne39 on 2012-03-27
Hi, this file will not open?
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
if not does it give an error message? because I really need to see the complete contents of that file.

What commands are you talking about?

Is it possible that you hit a key and change the name of the file when you saved it?

Did you get rid of the executable?
> is this thing evolving or somethingNot sure are you having any other issues besides wireless?
Thanks

---

### Post by rgmno1 on 2012-03-27
ok first this is the output 

```
~$ gksudo gedit /etc/modprobe.d/ath5k.conf

(gksudo:2257): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2257): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2257): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2257): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",



```and this is the whole contents of the file:

```

options ath5k nohwcrypt=1
exit 0

```NOTHING ELSE THERE...and as for the commands I was talking about: 

```

sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```And what I meant by evolving is that the commands worked before and now they stopped working.
And I am positive that I saved the file correctly. 
I copied the code (options ath5k nohwcrypt=1 and exit 0) from the forum and pasted it in 
```

gksudo gedit /etc/modprobe.d/ath5k.conf


```than hit ctrl+s and after that I checked to see if I didn't type something by mistake

---

### Post by wildmanne39 on 2012-03-27
Hi, leave in the option line and take out the exit 0 and see if that helps, It may not be needed in this file.

I know it is in the rc.local file, but I actually have walking pneumonia right now and I can not think clearly at this moment I need to rest for a while.

You should not have to run the commands in the terminal that is why we put it in the file.

But it may be conflicting with the executable. 
Thanks

---

### Post by rgmno1 on 2012-03-27
I'm sorry to hear about your health... I hope you get better....
I left the option line there... and restarted but I got d/c again... so after another boot I entered the codes in the terminal as well as kept the option in the file and it seems to be working again....
I'll post again tomorrow about any changes.... it's already 3 am here and I have to go to college at 8 so I hope I'll have anything by tomorrow :D.
Get well and thanks for your support

---

### Post by rgmno1 on 2012-03-29
I would seem the problem is solved... to resume everything I've done so far in order to get to this point.

1. I upgraded to 11.10
2. I used the commands
```

sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```
in a terminal and see if it worked (and it did)
3. I used this command 
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
and then pasted this
```
options ath5k nohwcrypt=1
``` 
in the file that opened
4. Restart PC

So far that's what I've done... I will keep testing for a week to see if there are any more issues, if not I will mark the thread as solved. 

Thank you for your help so far :D

---

### Post by wildmanne39 on 2012-03-29
Hi, it sounds good, I am glad it it working.
Enjoy

---

### Post by rgmno1 on 2012-03-30
I'm sad to say this but I am still having problems.... I've been using the internet for about 23hours now to test it out and it finally disconnected after running a game in wine and downloading a torrent at the same time. 
I have noticed that wine makes my cooler run like crazy when it is operational but it doesn't heat up to critical levels such as pc shutting down but it is enough to warm up quite a lot....
I would like to know if a heated computer could influence the functionality of the wireless card (although I think it does) and if so can it be fixed, because on windows I have been using the computer for as long as 48h + and didn't have such issues....

---

### Post by wildmanne39 on 2012-03-30
Hi, I believe this is a different issue, that people are having when using torrents or heavily downloading it appears to be a bug without a fix it was suggested to download things without using torrents when possible or to not do other internet intense activities at the same time.

You could install wicd and then uninstall network manager that may help but do it in that order.
Thanks

---

### Post by rgmno1 on 2012-03-30
Thank you for your reply ....
I have just confirmed that my wireless problem seems to come from a heated system.
I have been able to confirm this by installing Jupiter

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```Than restart...

It quickly lowered the temperature of my CPU from 70*C to 60*C and under when not using the pc....

I have confirmed that my wireless blocks out  when my CPU is over 70*C....
Jupiter tries to keep the temperature below 65 but when and with no usage of the pc the temperature stabilises to about 50*C while when watching a 25 min video the temperature rises to about 63-66*C (I don't know if that is more or less than normal).

Still I am wondering if there is an issue with the ubuntu boot up script (or whatever it is called) that blocks the wireless when over a certain temperature, as of yet I haven't confirmed any other processes or devices stopping...

Playing a game in Wine alone heats up my pc by about 15-20*C (again I don't know if it is normal or not).... 

And I believe this issue is only for certain CPU because a friend of mine has a different pc (Dell Inspiron 500m) and doesn't have issues with temperature or anything else no matter what he runs on it, it is always kept at a cool temperature (a constant of about 60*C to 65*C at the most)....

Any thoughts on this?

EDIT: my friend also runs ubuntu 11.10, and after installing and restarting jupiter I set it on power saver....

---

### Post by wildmanne39 on 2012-03-30
Hi, I have never heard of overheating effecting wireless in that way without causing the computer to turn off first, I still think it is that at the same time it is getting hot you happen to be using the internet heavily to play games.

I have no more ideas I am sorry for that.

---

### Post by rgmno1 on 2012-03-30
I wasn't referring to online games but sp games in wine and nothing else running except for the game...

I noticed that after the pc starts heating up the wireless disconnects....

---

### Post by rgmno1 on 2012-04-05
so there have been 5 days since I started keeping the temperature of my system below 70*C and there haven't been any more issues.

However I would like to mention that a fix should be made in further ubuntu releases for such a problem as I'm sure that there are more pc out there with the same problem.....

If there is anybody who found the same problem with their wireless please post here....

For your information I installed Jupiter 

sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

and after restarting I set it on power saver (a lightning bolt should appear on the top right of the taskbar after restart).... this reduces performance for functionality (that's the reason why I'm asking if a fix is possible for this) and keeps the temperature below 70*C (if possible) and at an average of 60*C....

Thank you and please post here  if you have experienced the same issue and this helped you....

---

