---
title: "PCM-3115B PCMCIA adapter driver"
date: 2012-06-21
forum: Hardware
---

### Post by hunter.allen on 2012-06-21
Hello all, 

I am trying to use a PCMCIA adapter (model specified in the title of the thread), and I am running into a lot of difficulty regarding the location of a driver. This is a very old adapter, but I cannot use another method of wireless connectivity on the board. The adapter has a Cisco Aironet 350 wireless LAN adapter on it. Does anyone know of a driver?

Background: 

I have used this adapter before with openSUSE (11.1 I think). After upgrading to Ubuntu 11.04 (because I <3 Ubuntu), it stopped working. 

Thank you all in advance, 
-Hunter A.

---

### Post by gordintoronto on 2012-06-21
The device is 12 years old, and I couldn't find any indication that it ever worked in Linux. (Found messages from people who wanted it to work, none of which indicated a solution.)

Do you have USB slots? Perhaps a different wireless device is the easy solution.

---

### Post by wildmanne39 on 2012-06-21
Hi, I found this link,
[http://linuxwireless.org/en/users/Drivers?highlight=%28Cisco%29|%28Aironet%29|%28350%29|%28wireless%29|%28LAN%29](http://linuxwireless.org/en/users/Drivers?highlight=%28Cisco%29|%28Aironet%29|%28350%29|%28wireless%29|%28LAN%29)
but it would probably be best to buy a usb adapter if usb devices are supported with your computer.
Thanks

---

### Post by hunter.allen on 2012-06-22
Is there a way to install a windows driver for it? Like NDISwrapper?

---

### Post by wildmanne39 on 2012-06-22
Hi, probably but you still have to have a windows driver for the card, I have never done it but I had seen directions for it and I have a friend that is good with ndiswarapper that will most likely help if he is around but please post the output of:
```
sudo pccardctl ident
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by hunter.allen on 2012-07-02
```
allenh1@hmt-lisa:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available

```


```
allenh1@hmt-lisa:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux hmt-lisa 2.6.38-15-generic #61-Ubuntu SMP Tue Jun 12 19:15:11 UTC 2012 i686 i686 i386 GNU/Linux
```

```
allenh1@hmt-lisa:~$ lspci -nnk | grep -iA2 net
00:0e.0 Ethernet controller [0200]: Intel Corporation 8255xER/82551IT Fast Ethernet Controller [8086:1209] (rev 10)
	Kernel driver in use: e100
	Kernel modules: e100
```

```
allenh1@hmt-lisa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"vummiv"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: B4:14:89:D0:B7:A0   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0
```

(here, wlan0 is the wireless usb card).

```
allenh1@hmt-lisa:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
allenh1@hmt-lisa:~$ lsmod
Module                  Size  Used by
airo_cs                12642  0 
airo                   73165  1 airo_cs
vesafb                 13476  1 
i82365                 23633  0 
pcmcia_rsrc            18292  1 i82365
pcmcia                 39671  1 airo_cs
rt2870sta             410104  0 
pcmcia_core            21505  3 i82365,pcmcia_rsrc,pcmcia
arc4                   12473  2 
snd_cs4281             19349  0 
gameport               15027  2 snd_cs4281
snd_ac97_codec        105614  1 snd_cs4281
ac97_bus               12642  1 snd_ac97_codec
rt2800usb              17907  0 
snd_pcm                80042  2 snd_cs4281,snd_ac97_codec
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
snd_page_alloc         14073  1 snd_pcm
rt2x00usb              19693  1 rt2800usb
snd_opl3_lib           18760  1 snd_cs4281
snd_hwdep              13274  1 snd_opl3_lib
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_cs4281,snd_seq_midi
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14110  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd                    55295  9 snd_cs4281,snd_ac97_codec,snd_pcm,snd_opl3_lib,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
cdc_acm                22150  0 
shpchp                 32345  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_piix4              13095  0 
lp                     13349  0 
parport                36746  1 lp
e100                   40108  0 

```


Sorry for the delayed response. I was away from my desk. I have had some progress, however. The PCMCIA card is now detected. For anyone interested, I ran the command:
```
 sudo modprobe i82365
```.

Let me know if you need any more information!
thanks again, 
-Hunter A.

I Figure this will also be helpful:

```
 allenh1@hmt-lisa:~$ pccardctl status
Socket 0:
  no card
Socket 1:
  5.0V 16-bit PC Card

```

```
 allenh1@hmt-lisa:~$ depmod -n | grep airo
kernel/drivers/net/wireless/airo.ko:
kernel/drivers/net/wireless/airo_cs.ko: kernel/drivers/net/wireless/airo.ko kernel/drivers/pcmcia/pcmcia.ko kernel/drivers/pcmcia/pcmcia_core.ko
airo                 0x000014b9 0x00000001 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x00004500 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x00004800 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x00000340 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x00000350 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x00005000 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
airo                 0x000014b9 0x0000a504 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0
alias pci:v000014B9d0000A504sv*sd*bc*sc*i* airo
alias pci:v000014B9d00005000sv*sd*bc*sc*i* airo
alias pci:v000014B9d00000350sv*sd*bc*sc*i* airo
alias pci:v000014B9d00000340sv*sd*bc*sc*i* airo
alias pci:v000014B9d00004800sv*sd*bc*sc*i* airo
alias pci:v000014B9d00004500sv*sd*bc*sc*i* airo
alias pci:v000014B9d00000001sv*sd*bc*sc*i* airo
alias pcmcia:m0105c0007f*fn*pfn*pa*pb*pc*pd* airo_cs
alias pcmcia:m015Fc0007f*fn*pfn*pa*pb*pc*pd* airo_cs
alias pcmcia:m015Fc0005f*fn*pfn*pa*pb*pc*pd* airo_cs
alias pcmcia:m015Fc000Af*fn*pfn*pa*pb*pc*pd* airo_cs
alias symbol:init_airo_card airo
alias symbol:stop_airo_card airo
alias symbol:reset_airo_card airo

```

---

### Post by hunter.allen on 2012-07-04
I found the airo driver in this thread: [http://ubuntuforums.org/showthread.php?t=1514304](http://ubuntuforums.org/showthread.php?t=1514304)


Any idea how I can use this for Ubuntu 11.04 server?

---

### Post by wildmanne39 on 2012-07-04
Hi, there may be a driver for your card in 11.04 but we need to see the information from this command:
```
sudo pccardctl ident
```
if you look at the information that you posted from that card earlier it says no card present, here is a link that will help with directions for your card.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)
Thanks

---

### Post by hunter.allen on 2012-07-05
My penultimate post, first output.

---

### Post by hunter.allen on 2012-07-05
```
allenh1@hmt-lisa:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
```

I have updated my pccardctl from 015 to 018 and it is still not detected. I know for a fact that this card works in linux (openSUSE), so this isn't impossible. 

Also, the USB ports are USB-1.0, so they are not fast enough for USB wireless (when you're doing what I'm doing, you need a fast internet connection (not necessarily with internet)). 

Any tips? I'd love to avoid installing this driver, so, if you have an alternate solution for me, I'm all ears.

---

### Post by wildmanne39 on 2012-07-05
Hi, did you go to the link in post 8 that says how to get older devices like your to be recognized? You will need to scroll down the page some to find the section you need.

Right now it is not be seen so even if we knew the exact driver and if it was included it would not work.
Thanks

---

### Post by hunter.allen on 2012-07-06
So how do I make it visible? Is it a problem with the PCMCIA adapter? It sees that there is a card plugged in, but it cannot recognize it. Is there any way I can make it visible?

---

### Post by wildmanne39 on 2012-07-06
Hi, if you followed the directions in the link then I do not know of anymore you can do.
Thanks

---

