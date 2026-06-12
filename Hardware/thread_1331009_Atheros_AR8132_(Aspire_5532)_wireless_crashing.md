---
title: "Atheros AR8132 (Aspire 5532) wireless crashing"
date: 2009-11-18
forum: Hardware
---

### Post by kbm on 2009-11-18
After awhile, the wireless connection is lost, asks for the WEP key when in has it.  Sometimes the rest of the system is ok, sometimes konsole shells stop working, system shutdown breaks, can't authenticate anything anymore (sudo or kpackagekit and the like).  I'm pretty sure it's the ath9k driver, which others have had problems with, but most seem to have been fixed by 9.10 (I'm running 9.10 kubuntu) or don't quite fit what I am seeing.

The hardware info for the card is:
*-network                                                            
 description: Ethernet interface                                 
 product: Atheros AR8132 / L1c Gigabit Ethernet Adapter          
 vendor: Attansic Technology Corp.                               
 physical id: 0                                                  
 bus info: pci@0000:08:00.0                                      
 logical name: eth0                                              
 version: c0                                                     
 serial: 00:26:22:63:d5:22                                       
 width: 64 bits                                                  
 clock: 33MHz                                                    
 capabilities: bus_master cap_list ethernet physical             
 configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes                                       
 resources: irq:28 memory:d1000000-d103ffff ioport:2000(size=128)

And some of syslog from around the crash:
Nov 18 20:28:49 Beatrice wpa_supplicant[947]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 18 20:28:49 Beatrice NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 18 20:28:49 Beatrice kernel: [168541.060525] wlan0: no probe response from AP 00:14:bf:0e:72:24 - disassociating
Nov 18 20:28:50 Beatrice NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 18 20:28:50 Beatrice kernel: [168541.228934] general protection fault: 0000 [#1] SMP
Nov 18 20:28:50 Beatrice kernel: [168541.228941] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT1/charge_full
Nov 18 20:28:50 Beatrice kernel: [168541.228947] CPU 0
Nov 18 20:28:50 Beatrice kernel: [168541.228949] Modules linked in: ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy joydev snd_seq_oss ath9k iptable_filter ip_tables snd_seq_midi snd_rawmidi snd_seq_midi_event mac80211 snd_seq x_tables ath snd_timer psmouse atl1c snd_seq_device amd64_edac_mod k8temp fglrx(P) i2c_piix4 edac_core serio_raw shpchp led_class snd cfg80211 soundcore snd_page_alloc lp parport video output

Nov 18 20:28:50 Beatrice kernel: [168541.229065] Call Trace:
Nov 18 20:28:50 Beatrice kernel: [168541.229071]  [<ffffffff8142d429>] __kfree_skb+0x19/0xa0
Nov 18 20:28:50 Beatrice kernel: [168541.229076]  [<ffffffff8142d4c9>] consume_skb+0x19/0x40
Nov 18 20:28:50 Beatrice kernel: [168541.229100]  [<ffffffffa033c08b>] ieee80211_tx_status+0x45b/0x530 [mac80211]
Nov 18 20:28:50 Beatrice kernel: [168541.229118]  [<ffffffffa03bcca0>] ath_tx_complete+0x150/0x170 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229129]  [<ffffffffa03bcd5a>] ath_tx_complete_buf+0x9a/0x110 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229140]  [<ffffffffa03be3c8>] ath_draintxq+0xf8/0x2c0 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229150]  [<ffffffffa03a6e00>] ? ath9k_hw_reset+0x490/0x800 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229162]  [<ffffffffa03bf8fc>] ath_drain_all_txq+0x10c/0x180 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229173]  [<ffffffffa03baead>] ath_set_channel+0x9d/0x220 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229185]  [<ffffffffa03bb23e>] ath9k_config+0x20e/0x270 [ath9k]
Nov 18 20:28:50 Beatrice kernel: [168541.229197]  [<ffffffffa033baf5>] ieee80211_hw_config+0x85/0xd0 [mac80211]
Nov 18 20:28:50 Beatrice kernel: [168541.229211]  [<ffffffffa0340b6a>] ieee80211_scan_work+0xba/0x230 [mac80211]
Nov 18 20:28:50 Beatrice kernel: [168541.229224]  [<ffffffffa0340ab0>] ? ieee80211_scan_work+0x0/0x230 [mac80211]
Nov 18 20:28:50 Beatrice kernel: [168541.229232]  [<ffffffff810737a5>] run_workqueue+0x95/0x170
Nov 18 20:28:50 Beatrice kernel: [168541.229237]  [<ffffffff81073924>] worker_thread+0xa4/0x120

So I'm convinced at this point that it is the wireless driver going down.  The syslog and system behaviour vary from crash to crash, but I would expect that from a low lever driver crash I guess.

FYI, I can debug a java app running on WAS like nobody's business, but when it comes to a Linux kernel/driver issue, I'm a bit out of my element.  Basically, if someone holds my hand on this, I could collect a lot more information I think, I just don't know where to look on my own.

Sorry if there is a lot of kruft in my post, but like I said, I don't know the good data from the bad yet.

---

### Post by yoshiki2 on 2009-11-19
sorry about the question. But when u installed ubuntu everything worked out of the box?

---

### Post by robogock on 2009-11-19
Hmm, my problem *might* be related:
[http://ubuntuforums.org/showthread.php?p=8348304](http://ubuntuforums.org/showthread.php?p=8348304)

Mine is happening after I try to resume from suspend, but your post is the only other one I've seen where wireless stops working as do shells and shutdown.

If they are related, then it's not the wireless driver. Mine is an "Intel Corporation Wireless WiFi Link 5100" according to lspci, and using the iwlagn driver.

Unfortunately, I'm also out of my element at debugging linux kernel problems... :(

---

### Post by kbm on 2009-11-19
> **yoshiki2 said:**
> sorry about the question. But when u installed ubuntu everything worked out of the box?

So far the only issue has been the wireless crash.  Out of the box, the graphics were good, but no compositing.  I used the Kubuntu hardware driver tool and installed the ATI driver.  Graphics are up to spec now.

Pretty happy with it. Once this issue is resolved, I'll be real happy - especially for the price.

---

### Post by kbm on 2009-11-19
Ya, the end result sure seems the same.  Weird stuff huh?  I thought I was on to something from another post and tried to rmmod the ath9k driver right after it bailed.  Joke was on me when I got to the terminal.  Could be related in cause or effect (i.e. when the driver goes down, it's taking some innocent memory with it or something).  Anyway, please keep me posted if you find that the update you made keeps you stable for awhile.

---

### Post by yoshiki2 on 2009-11-19
are u still on your 30 days?

---

### Post by kbm on 2009-11-21
30 days?  You mean 30 days to return to Best Buy?  Ya, I suppose I am, but I'm sure this issue will get ironed out.

---

### Post by yoshiki2 on 2009-11-23
any news with your driver?

---

### Post by kbm on 2009-12-03
I updated to the -15 kernel, which will get me the backport stuff that was mentioned in the other thread.  Still getting the driver crash though.  Just switched to WPA authentication instead of WEP to see if that helps (some have reported better stability with other networking issues when using WPA).

As of now, still dealing with driver crashes though.

---

### Post by kbm on 2009-12-04
The switch to WPA seemed to be no help at all.  Actually, it seemed to go down more often, but cause less damage (i.e. the system would still shutdown properly and terminals still worked).  Not much 'real' testing to base that on though.

It seemed I misunderstood what the backports packages were for.  They will not be integrated until 10.04, not with the next kernel update (unless I'm still misunderstanding it).  So... I'm going to try the backports tonight.

---

