---
title: "Slow Slow Slow Ubuntu wifi wireless :("
date: 2008-12-14
forum: Hardware
---

### Post by ruiseixas on 2008-12-14
I have tried everything, I even install the new ubuntu version 8.10, but nothing again...

The problem is this, my wireless card from my Toshiba Satellite A200, a very rare product, never pass from the 300 KiB/s!! If you think that wifi G on windows leads you through 54MiB/s you get the picture.

This is my hardware:

```
lspci |grep Wireless
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Some people say that you must get rid out from the ubuntu original controller (Administration->Hardware Drivers) and deactivate support. This is simple not easy to be done, because the system starts always with the ubunto driver... It's too much annoying!

That same people, tell you to install the Mad WiFi ( [http://madwifi-project.org/]("http://madwifi-project.org/") ), better, its not the simple apt-get, no, you have to compile it. Here you know that some one transfer the problems to you, because programs that you have to compile are unfinished programs... 

So I compile the brand new mad wifi, and this is the result:

```

root@david:/usr/local/src/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/usr/local/src/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/local/src/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /usr/local/src/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /usr/local/src/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /usr/local/src/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /usr/local/src/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /usr/local/src/madwifi-0.9.4/net80211/ieee80211_power.o
/usr/local/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/usr/local/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/usr/local/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/usr/local/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/usr/local/src/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [modules] Error 2
root@david:/usr/local/src/madwifi-0.9.4# 

```

Well, not a big surprise, this is what happens one some one ask you to compile...

I have installed a lot of packages, required packages but nothing... the result stays the same.

If you are asking if there are some answer, yes there are, it's like > You should update the headers

Thirst, I cant write that on the command line, and second, is he thinking that he gave a good answer?

Bottom Line: After have tried a lot of pseudo solutions, I realize that some hardware are simple not supported, or very badly supported! So, why Ubunto, or others, didn't publish a list of laptops that are Linux friendly, because not every one have time to this issues.

Things like that make windows better off :( If it's not supported published, and if it's, reward those brands by publishing them.

If any one know such laptop please tell me, I'm seriously thinking of buying a new one.

Regards ):P

---

### Post by xscottx3 on 2008-12-14
I know you said you've tried many sudo commands, but have you tried...

sudo iwconfig wlan0 rate 54M

That solved the issue for me when I upgraded to 8.10. The only issue is that you have to input the command every time you login.

---

### Post by ruiseixas on 2008-12-17
> **xscottx3 said:**
> I know you said you've tried many sudo commands, but have you tried...

sudo iwconfig wlan0 rate 54M

That solved the issue for me when I upgraded to 8.10. The only issue is that you have to input the command every time you login.

Thanks for you reply, in my case I have tried as root the following:

```
iwconfig ath0 rate 54M
```

I didn't mentioned, but my router, a [Linksys WRT54GL]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859841350&pagename=Linksys%2FCommon%2FVisitorWrapper"), it's configured to allow only G connections... So my connection has to be a 54M one. Unfortunately, while trying with my home FTP server it didn't went behind 250K... :confused:

Thanks any way,
Rui

---

### Post by ruiseixas on 2008-12-25
When I make iwconfig I get the following...

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dexter"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:4A:FC:C8   
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-69 dBm  Noise level=-94 dBm
          Rx invalid nwid:261  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Regards.

---

### Post by ruiseixas on 2009-01-01
OK guys, problem solved :)

I switch the firmware of my router to the original one, from the Linksys site, version 4.30.12 and it works much better than the one of DD-WRT dd-wrt.v24 SP1!
So, the problem was not from the Atheros, but instead, from the router with an amazingly bad firmware :confused:

---

### Post by ddesire on 2010-01-21
> **ruiseixas said:**
> OK guys, problem solved :)

I switch the firmware of my router to the original one, from the Linksys site, version 4.30.12 and it works much better than the one of DD-WRT dd-wrt.v24 SP1!
So, the problem was not from the Atheros, but instead, from the router with an amazingly bad firmware :confused:

hmm...that's gud...:KS

---

