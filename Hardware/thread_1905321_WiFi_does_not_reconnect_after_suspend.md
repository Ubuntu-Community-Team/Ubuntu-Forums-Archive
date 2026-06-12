---
title: "WiFi does not reconnect after suspend"
date: 2012-01-06
forum: Hardware
---

### Post by DoRullings on 2012-01-06
Hi

I am having a problem with a laptop which fails to reconnect to the wireless network after suspend mode. After waking the computer from suspend mode the WiFi icon is animating like it is trying to reconnect. After a while the card is disabled, or it appears to still be enabled but does not find any network. I have several other wireless devices connected to the network without any problems, including another laptop, an iPhone and an iPad.

System:
[LIST]
[*]Laptop: Asus U45JC
[/LIST] 
[LIST]
[*]Network controller: Atheros AR9285
[/LIST]
[LIST]
[*]Ubuntu 10.04 LTS Lucid Lynx
[/LIST]

Network:
[LIST]
[*]Linksys WRT54GL (with DD-WRT firmware on channel 1)
[/LIST]
[LIST]
[*]Linksys E4200 (in bridge mode with original firmware on channel 11 on 2.4 GHz)
[/LIST] 

What I have tried so far:
After reading some googling I have tried to run this commands:
[LIST]
[*]sudo modprobe -rf ath9k
[/LIST]
[LIST]
[*]sudo /etc/init.d/networking start
[/LIST]
[LIST]
[*]sudo service networking start
[/LIST]
[LIST]
[*]sudo service network-manager restart
[/LIST]
[LIST]
[*]sudo modprobe -v ath9k nohwcrypt=1
[/LIST]
and added this: 
> options ath9k nohwcrypt=1
to:
> /etc/modprobe.d/ath9k.conf

dmesg output while trying to reconnect after suspend mode:
> [ 4271.007747] ath9k: Two wiphys trying to scan at the same time
[ 4271.007795] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[ 4271.216896] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[ 4271.221358] wlan0: direct probe responded
[ 4271.221362] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[ 4271.225177] wlan0: authenticated
[ 4271.225199] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[ 4271.228910] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=3)
[ 4271.228914] wlan0: associated
[ 4316.573516] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)


dmesg output while trying to reconnect after suspend mode 2:
> [13603.312865] wlan0: direct probe to AP 00:21:96:37:4f:18 timed out
[13613.408419] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13613.411138] wlan0: direct probe responded
[13613.411144] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13613.413015] wlan0: authenticated
[13613.413048] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13613.415596] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13613.415602] wlan0: associated
[13624.309683] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13624.508482] ath9k: Two wiphys trying to scan at the same time
[13624.508531] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13624.698440] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13624.701172] wlan0: direct probe responded
[13624.701177] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13624.703456] wlan0: authenticated
[13624.703481] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13624.705940] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13624.705943] wlan0: associated
[13628.019505] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13637.003614] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)
[13637.192284] wlan0: direct probe to AP 00:25:9c:24:6b:56 (try 1)
[13637.195136] wlan0: direct probe responded
[13637.195139] wlan0: authenticate with AP 00:25:9c:24:6b:56 (try 1)
[13637.197088] wlan0: authenticated
[13637.197113] wlan0: associate with AP 00:25:9c:24:6b:56 (try 1)
[13637.199857] wlan0: RX AssocResp from 00:25:9c:24:6b:56 (capab=0x411 status=0 aid=2)
[13637.199860] wlan0: associated
[13682.279401] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[13720.128916] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[13720.338887] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[13720.343304] wlan0: direct probe responded
[13720.343307] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[13720.345534] wlan0: authenticated
[13720.345552] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[13720.349257] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=3)
[13720.349261] wlan0: associated

dmesg output after the card has "giving up" and is disabled:
> [13493.162192] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)
[13493.359734] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[13493.363638] wlan0: direct probe responded
[13493.363641] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[13493.365848] wlan0: authenticated
[13493.365861] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[13493.369555] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=3)
[13493.369558] wlan0: associated
[13493.379506] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[13503.635134] wlan0: no IPv6 routers present
[13539.297102] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)
[13569.259885] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13569.448511] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13569.451263] wlan0: direct probe responded
[13569.451268] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13569.453232] wlan0: authenticated
[13569.453261] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13569.456991] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13569.456995] wlan0: associated
[13569.457802] cfg80211: Calling CRDA for country: NO
[13569.460544] cfg80211: Received country IE:
[13569.460548] cfg80211: Regulatory domain: NO
[13569.460551] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13569.460555] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[13569.460558] cfg80211: CRDA thinks this should applied:
[13569.460560] cfg80211: Regulatory domain: NO
[13569.460562] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13569.460566] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13569.460569] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13569.460572] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13569.460576] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[13569.460578] cfg80211: We intersect both of these and get:
[13569.460580] cfg80211: Regulatory domain: 98
[13569.460582] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13569.460586] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13569.460593] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[13569.460596] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[13569.460602] cfg80211: Current regulatory domain updated by AP to: NO
[13569.460605] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13569.460608] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13578.144499] wlan0: deauthenticated from 00:21:96:37:4f:18 (Reason: 1)
[13579.234372] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13579.435256] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[13579.438175] wlan0: direct probe responded
[13579.438179] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13579.440064] wlan0: authenticated
[13579.440088] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13579.442524] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13579.442529] wlan0: associated
[13590.349302] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13590.557239] ath9k: Two wiphys trying to scan at the same time
[13590.557271] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13590.756879] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13590.956401] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[13590.959136] wlan0: direct probe responded
[13590.959144] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13590.961087] wlan0: authenticated
[13590.961121] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13590.963667] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13590.963673] wlan0: associated
[13602.292896] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13602.502244] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13602.712260] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13602.913093] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[13603.112980] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 3)
[13603.312865] wlan0: direct probe to AP 00:21:96:37:4f:18 timed out
[13613.408419] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13613.411138] wlan0: direct probe responded
[13613.411144] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13613.413015] wlan0: authenticated
[13613.413048] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13613.415596] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13613.415602] wlan0: associated
[13624.309683] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13624.508482] ath9k: Two wiphys trying to scan at the same time
[13624.508531] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13624.698440] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[13624.701172] wlan0: direct probe responded
[13624.701177] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[13624.703456] wlan0: authenticated
[13624.703481] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[13624.705940] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[13624.705943] wlan0: associated
[13628.019505] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[13637.003614] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)
[13637.192284] wlan0: direct probe to AP 00:25:9c:24:6b:56 (try 1)
[13637.195136] wlan0: direct probe responded
[13637.195139] wlan0: authenticate with AP 00:25:9c:24:6b:56 (try 1)
[13637.197088] wlan0: authenticated
[13637.197113] wlan0: associate with AP 00:25:9c:24:6b:56 (try 1)
[13637.199857] wlan0: RX AssocResp from 00:25:9c:24:6b:56 (capab=0x411 status=0 aid=2)
[13637.199860] wlan0: associated
[13682.279401] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[13720.128916] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[13720.338887] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[13720.343304] wlan0: direct probe responded
[13720.343307] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[13720.345534] wlan0: authenticated
[13720.345552] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[13720.349257] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=3)
[13720.349261] wlan0: associated
[13766.173259] wlan0: deauthenticating from 58:6d:8f:7c:45:81 by local choice (reason=3)
[13815.476788] ath9k 0000:03:00.0: PCI INT A disabled
[13815.477794] ath9k: Driver unloaded


dmesg after reboot:
> [   32.658086] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   32.658121] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   32.662098] wlan0: direct probe responded
[   32.662101] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   32.663976] wlan0: authenticated
[   32.663996] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   32.666476] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   32.666481] wlan0: associated
[   32.666921] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.666993] cfg80211: Calling CRDA for country: NO
[   32.668491] cfg80211: Received country IE:
[   32.668493] cfg80211: Regulatory domain: NO
[   32.668494] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.668496] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   32.668497] cfg80211: CRDA thinks this should applied:
[   32.668498] cfg80211: Regulatory domain: NO
[   32.668499] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.668501] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.668503] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.668504] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.668505] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   32.668506] cfg80211: We intersect both of these and get:
[   32.668507] cfg80211: Regulatory domain: 98
[   32.668508] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.668510] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.668514] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   32.668515] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   32.668519] cfg80211: Current regulatory domain updated by AP to: NO
[   32.668520] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.668522] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   42.204063] wlan0: deauthenticated from 00:21:96:37:4f:18 (Reason: 6)
[   43.201790] wlan0: no IPv6 routers present
[   43.301740] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   43.501553] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[   43.503746] wlan0: direct probe responded
[   43.503751] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   43.505954] wlan0: authenticated
[   43.505990] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   43.508460] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   43.508462] wlan0: associated
[   54.895589] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   55.094371] ath9k: Two wiphys trying to scan at the same time
[   55.094419] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   55.283754] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   55.286588] wlan0: direct probe responded
[   55.286595] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   55.288464] wlan0: authenticated
[   55.288489] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   55.290960] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   55.290964] wlan0: associated
[   65.809782] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   66.008718] ath9k: Two wiphys trying to scan at the same time
[   66.008745] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   66.217301] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   66.408201] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[   66.410977] wlan0: direct probe responded
[   66.410983] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   66.414079] wlan0: authenticated
[   66.414111] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   66.417464] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   66.417468] wlan0: associated
[   75.630310] wlan0: deauthenticated from 00:21:96:37:4f:18 (Reason: 1)
[   76.722039] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   76.912157] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[   76.915867] wlan0: direct probe responded
[   76.915872] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   76.917810] wlan0: authenticated
[   76.917837] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   76.920387] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   76.920391] wlan0: associated
[   87.836296] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   88.035153] ath9k: Two wiphys trying to scan at the same time
[   88.035200] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   88.226039] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   88.228797] wlan0: direct probe responded
[   88.228802] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   88.230764] wlan0: authenticated
[   88.230789] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   88.233264] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=3)
[   88.233267] wlan0: associated
[   91.754671] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   99.649690] ath9k: Two wiphys trying to scan at the same time
[   99.649773] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[   99.849574] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[   99.854047] wlan0: direct probe responded
[   99.854052] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[   99.856028] wlan0: authenticated
[   99.856052] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[   99.861456] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=3)
[   99.861460] wlan0: associated
[   99.945773] Intel AES-NI instructions are not detected.
[   99.995611] padlock: VIA PadLock not detected.

dmesg after reboot 2:
> [   70.865547] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   70.865568] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   70.865591] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   70.869921] wlan0: direct probe responded
[   70.869923] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   70.871818] wlan0: authenticated
[   70.871838] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   70.874343] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[   70.874346] wlan0: associated
[   70.874793] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.874864] cfg80211: Calling CRDA for country: NO
[   70.876401] cfg80211: Received country IE:
[   70.876403] cfg80211: Regulatory domain: NO
[   70.876405] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   70.876406] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   70.876408] cfg80211: CRDA thinks this should applied:
[   70.876409] cfg80211: Regulatory domain: NO
[   70.876410] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   70.876411] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   70.876413] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   70.876414] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   70.876416] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   70.876417] cfg80211: We intersect both of these and get:
[   70.876418] cfg80211: Regulatory domain: 98
[   70.876419] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   70.876420] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   70.876424] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   70.876425] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   70.876429] cfg80211: Current regulatory domain updated by AP to: NO
[   70.876430] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   70.876432] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   79.909471] wlan0: deauthenticated from 00:21:96:37:4f:18 (Reason: 6)
[   80.906463] wlan0: no IPv6 routers present
[   81.006383] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   81.198188] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 2)
[   81.200982] wlan0: direct probe responded
[   81.200987] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   81.203007] wlan0: authenticated
[   81.203037] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   81.208457] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[   81.208461] wlan0: associated
[   92.427798] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   92.626632] ath9k: Two wiphys trying to scan at the same time
[   92.626679] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[   92.816529] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[   92.819428] wlan0: direct probe responded
[   92.819432] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[   92.821405] wlan0: authenticated
[   92.821433] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[   92.824223] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[   92.824227] wlan0: associated
[  106.407182] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[  106.607308] ath9k: Two wiphys trying to scan at the same time
[  106.607405] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[  106.817776] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[  106.820558] wlan0: direct probe responded
[  106.820562] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[  106.823153] wlan0: authenticated
[  106.823177] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[  106.825762] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[  106.825766] wlan0: associated
[  115.195813] wlan0: deauthenticated from 00:21:96:37:4f:18 (Reason: 1)
[  116.259756] wlan0: direct probe to AP 00:21:96:37:4f:18 (try 1)
[  116.262504] wlan0: direct probe responded
[  116.262507] wlan0: authenticate with AP 00:21:96:37:4f:18 (try 1)
[  116.264481] wlan0: authenticated
[  116.264498] wlan0: associate with AP 00:21:96:37:4f:18 (try 1)
[  116.267038] wlan0: RX AssocResp from 00:21:96:37:4f:18 (capab=0x411 status=0 aid=2)
[  116.267040] wlan0: associated
[  126.242779] wlan0: deauthenticating from 00:21:96:37:4f:18 by local choice (reason=3)
[  126.450091] wlan0: deauthenticating from 00:25:9c:24:6b:56 by local choice (reason=3)
[  126.630845] wlan0: direct probe to AP 58:6d:8f:7c:45:81 (try 1)
[  126.635305] wlan0: direct probe responded
[  126.635310] wlan0: authenticate with AP 58:6d:8f:7c:45:81 (try 1)
[  126.637266] wlan0: authenticated
[  126.637287] wlan0: associate with AP 58:6d:8f:7c:45:81 (try 1)
[  126.640990] wlan0: RX AssocResp from 58:6d:8f:7c:45:81 (capab=0x411 status=0 aid=2)
[  126.640994] wlan0: associated
[  126.780168] Intel AES-NI instructions are not detected.
[  126.832645] padlock: VIA PadLock not detected.
[  128.425418] ath9k: timeout (100000 us) on reg 0x806c: 0xdeadbeef & 0x01f00000 != 0x00000000
[  128.425542] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef
[  134.631104] ath9k: timeout (100000 us) on reg 0x806c: 0xdeadbeef & 0x01f00000 != 0x00000000
[  134.631221] ath9k: RX failed to go idle in 10 ms RXSM=0xdeadbeef

I have not been able to interpret these outputs. All help will be appreciated.

Thanks!

---

### Post by DoRullings on 2012-01-08
I have tried to fix this the whole weekend, without any luck. Can I provide some more information that can help you guys help me?

This is somehow related to suspend mode and I had trouble getting the laptop entering suspend mode when I first installed Ubuntu. With the help of this blogpost I manage to fix this problem and suspend mode worked just fine. From the beginning I noticed that the wireless network was unstable, but most of the time it worked just fine. Now the network always fails to reconnect being waked up from suspend mode. Now I'm not sure if the network card start at all suspend mode because the wireless led on the front of the laptop doesn't light up.

I will really apriciate it if anybody could help me debugging this problem, because now I have a laptop that I can't suspend.

Thanks!

---

