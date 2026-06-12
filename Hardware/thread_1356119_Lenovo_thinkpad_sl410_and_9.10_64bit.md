---
title: "Lenovo thinkpad sl410 and 9.10 64bit"
date: 2009-12-15
forum: Hardware
---

### Post by IgnasM on 2009-12-15
Hi there,

i've searched all forums, but found nothing. Maybe because it's a new model, or maybe i haven't searched well enough :) It would be superb if you could help me with some issues:

Fn combinations that don't work:
fn+f2, fn+f3, fn+f5, fn+f6, fn+f7, fn+f8, fn+f12.

Also there are problems with multitouch touchpad; bluetooth; sound mute button -  it mutes only external speaker but not the system (up and down keys work); microphone mute button. 

Older drivers discussed on this[ page]("http://gianlucamagalotti.wordpress.com/2009/02/16/lenovo-thinkpad-sl-series-hotkeys/") don't work. 

On the other hand brightness controls work out-of-the-box, and there aren't any problems with wireless connections.

Hope this thread will be useful not just for me, and i'm looking forward to your answers.

Cheers,
IgnasM

---

### Post by IgnasM on 2009-12-18
Bump!

---

### Post by raparks on 2009-12-19
> **IgnasM said:**
> and there aren't any problems with wireless connections.

Which model SL410 do you have?  I just loaded Ubuntu 9.10 x64 on a ThinkPad SL410 2874-32U and the wireless is not detected.  Any suggestions would be much appreciated.

Thanks!

---

### Post by raparks on 2009-12-19
Disregard my earlier question regarding Wi-Fi.  I found the answer ([link]("http://ubuntuforums.org/showpost.php?p=8529100&postcount=4")).

---

### Post by TwitchingPeacefully on 2009-12-24
I have the 2842-7pu version and I'm experiencing the same problems minus bluetooth (dosen't have any) and my internal mic is not working, as well as the HDMI output is green. Does anyone have an soultion for the mic?

---

### Post by IgnasM on 2010-01-03
Today i've discovered that card reader is not working either.

Come on! All those small things are starting to become annoying... Is it just me experiencing these problems? No other ubuntu users using this model?

Ignas M.

---

### Post by jfanaian on 2010-01-26
I am also experiencing these issues on the SL410, on Ubuntu 9.10. Any updates?

---

### Post by warfacegod on 2010-01-27
Check Synaptic and make sure you have "tpb" installed. It's for special keys.

---

### Post by buddajah on 2010-02-14
i'm having the same issue with the mic, tpb was not listed in synaptic so i installed it from CLI with apt. but i still can't get the mic working. it's weird cause i was able to send the audio from my pc, to a friend over skype but no mic input.

any suggestions

---

### Post by nawab on 2010-02-24
my wireless is dropping connection every 10 mins and i have to restart network manager and then it work son Lenovo sl 400 series laptop. 
driver is of RealTalk semiconductor. please help

Feb 22 09:34:41 ubuntu kernel: [11705.152629] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:41 ubuntu kernel: [11705.152635] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:44 ubuntu kernel: [11707.652588] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:34:44 ubuntu kernel: [11707.652597] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:34:44 ubuntu kernel: [11707.652600] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:34:44 ubuntu kernel: [11707.662619] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:44 ubuntu kernel: [11707.662624] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:46 ubuntu kernel: [11710.160082] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:34:46 ubuntu kernel: [11710.160092] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:34:46 ubuntu kernel: [11710.160096] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:34:46 ubuntu kernel: [11710.170116] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:46 ubuntu kernel: [11710.170120] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:49 ubuntu kernel: [11712.670521] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:34:49 ubuntu kernel: [11712.670528] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:34:49 ubuntu kernel: [11712.670531] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:34:49 ubuntu kernel: [11712.680545] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:49 ubuntu kernel: [11712.680548] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:51 ubuntu kernel: [11715.180093] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:34:51 ubuntu kernel: [11715.180103] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:34:51 ubuntu kernel: [11715.180107] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:34:51 ubuntu kernel: [11715.190118] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:51 ubuntu kernel: [11715.190124] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:54 ubuntu kernel: [11717.680037] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:34:54 ubuntu kernel: [11717.680044] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:34:54 ubuntu kernel: [11717.680048] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:34:54 ubuntu kernel: [11717.690072] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:34:54 ubuntu kernel: [11717.690075] softmac_mgmt_xmit():insert to waitqueue!
Feb 22 09:34:55 ubuntu kernel: [11718.913174] Save max pwr
Feb 22 09:34:55 ubuntu kernel: [11719.232568] gen_RefreshLedState first init
Feb 22 09:34:55 ubuntu kernel: [11719.232577] =================> NIC version : C-cut
Feb 22 09:34:55 ubuntu kernel: [11719.342893] ===>rtl8192_SetWirelessMode(), wireless_mode:0x4, support_mode:0x16
Feb 22 09:34:55 ubuntu kernel: [11719.342897] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Feb 22 09:34:55 ubuntu kernel: [11719.353094] ===>ieee80211_start_scan_rsl()
Feb 22 09:34:55 ubuntu kernel: [11719.367563] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 22 09:34:55 ubuntu kernel: [11719.369220] r8169: eth0: link down
Feb 22 09:34:55 ubuntu kernel: [11719.369691] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 22 09:35:03 ubuntu kernel: [11727.422866] alg name:WEP
Feb 22 09:35:03 ubuntu kernel: [11727.423006] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:35:03 ubuntu kernel: [11727.423023] Linking with Tassu,channel:6, qos:1, myHT:0, networkHT:0, mode:6 cur_net.flags:0x40e
Feb 22 09:35:03 ubuntu kernel: [11727.423122] ===>ieee80211_associate_procedure_wq(), chan:6
Feb 22 09:35:03 ubuntu kernel: [11727.423126] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Feb 22 09:35:03 ubuntu kernel: [11727.433149] =================>ieee80211_authentication_req():auth->algorithm is 0
Feb 22 09:35:04 ubuntu kernel: [11727.435396] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
Feb 22 09:35:04 ubuntu kernel: [11727.435400] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
Feb 22 09:35:04 ubuntu kernel: [11727.445017] #################ieee80211_sta_send_associnfo(), assocreq_ies_len:32,assocresp_ies_len:53
Feb 22 09:35:04 ubuntu kernel: [11727.445059] ===>u4bAcParam:a425, ===>u4bAcParam:a449, ===>u4bAcParam:5e431c, ===>u4bAcParam:2f321c, 
Feb 22 09:35:04 ubuntu kernel: [11727.445067] Associated successfully
Feb 22 09:35:04 ubuntu kernel: [11727.445069] ============>normal associate
Feb 22 09:35:04 ubuntu kernel: [11727.445077] Using G rates:108

---

### Post by nawab on 2010-02-25
i checked /var/log/messages and i can see a lot of these messages. not sure what exactly is this. please help
```

Feb 24 22:46:08 ubuntu kernel: [27158.853496] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27158.955903] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.058298] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.160705] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.263097] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.365507] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.467907] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.570296] ===>tx queue is not empty:6, 23
Feb 24 22:46:08 ubuntu kernel: [27159.672706] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27159.775101] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27159.877500] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27159.979889] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27160.287086] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27160.389495] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27160.491893] ===>tx queue is not empty:6, 23
Feb 24 22:46:09 ubuntu kernel: [27160.594312] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27160.777207] ===>u4bAcParam:a425, ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27160.901508] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27161.003886] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27161.311103] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27161.414653] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27161.515913] ===>tx queue is not empty:6, 23
Feb 24 22:46:10 ubuntu kernel: [27161.618314] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27161.720700] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27161.823116] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27161.925511] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.027907] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.130318] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.232702] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.335123] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.437521] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.539916] ===>tx queue is not empty:6, 23
Feb 24 22:46:11 ubuntu kernel: [27162.642310] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27162.744699] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27162.847113] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27162.949523] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.051924] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.256707] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.359135] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.461520] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.563923] ===>tx queue is not empty:6, 23
Feb 24 22:46:12 ubuntu kernel: [27163.666291] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27163.768696] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27163.871130] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27163.973529] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27164.075930] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27164.383127] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27164.485537] ===>tx queue is not empty:6, 23
Feb 24 22:46:13 ubuntu kernel: [27164.587930] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27164.690307] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27164.792708] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27164.895129] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27164.997532] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27165.099938] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27165.304706] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27165.509540] ===>tx queue is not empty:6, 23
Feb 24 22:46:14 ubuntu kernel: [27165.611940] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27165.714335] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27165.816717] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27165.919132] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.021504] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.123952] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.328723] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.431140] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.533536] ===>tx queue is not empty:6, 23
Feb 24 22:46:15 ubuntu kernel: [27166.635935] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27166.738340] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27166.776576] ===>u4bAcParam:a425, ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27166.943141] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.045542] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.147945] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.250341] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.352731] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.455156] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.557541] ===>tx queue is not empty:6, 23
Feb 24 22:46:16 ubuntu kernel: [27167.659944] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27167.762346] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27167.864727] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27167.967149] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.069554] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.171950] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.274345] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.376735] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.479152] ===>tx queue is not empty:6, 23
Feb 24 22:46:17 ubuntu kernel: [27168.581548] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27168.683949] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27168.786345] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27168.888724] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27168.991143] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.093564] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.195960] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.298345] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.400747] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.503165] ===>tx queue is not empty:6, 23
Feb 24 22:46:18 ubuntu kernel: [27169.605558] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27169.707954] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27169.810359] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27169.912745] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.015157] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.117568] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.219961] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.322337] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.424740] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.527164] ===>tx queue is not empty:6, 23
Feb 24 22:46:19 ubuntu kernel: [27170.629561] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27170.731962] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27170.834356] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27170.936742] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.039162] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.141562] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.243966] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.346367] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.448763] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.551169] ===>tx queue is not empty:6, 23
Feb 24 22:46:20 ubuntu kernel: [27171.653572] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27171.755974] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27171.858373] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27171.960745] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.063173] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.165572] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.267982] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.370376] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.472757] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.575175] ===>tx queue is not empty:6, 23
Feb 24 22:46:21 ubuntu kernel: [27172.677570] ===>tx queue is not empty:6, 23
Feb 24 22:46:23 ubuntu kernel: [27173.776235] ieee->state is IEEE80211_LINKED
Feb 24 22:46:23 ubuntu kernel: [27173.783865] gen_RefreshLedState first init
Feb 24 22:46:23 ubuntu kernel: [27173.783871] =================> NIC version : C-cut
Feb 24 22:46:23 ubuntu kernel: [27173.914416] Associated successfully
Feb 24 22:46:23 ubuntu kernel: [27173.914419] Using G rates:108
Feb 24 22:46:23 ubuntu kernel: [27173.914421] Successfully associated, ht not enabled(0, 0)
Feb 24 22:46:23 ubuntu kernel: [27173.914431] ===========rtl8192se_update_ratr_table: ff5
Feb 24 22:46:23 ubuntu kernel: [27173.914432] ===>set to B/G mode
Feb 24 22:46:23 ubuntu kernel: [27173.914437] ==================>silent reset associate
```

---

### Post by nawab on 2010-03-13
please can anyone let me know if you get a work around to solve the issue.

---

### Post by tonymoyoy on 2010-03-22
I tried Ubuntu 10.4 Beta 1 and seems to detect lots of stuff, i will post about it when the RC is out

---

### Post by williamdemeo on 2011-01-08
My new Thinkpad Edge was having the same problem.  I solved it by adding the following line to the file /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=thinkpad

Good luck!
-William

---

### Post by thisisspeedy on 2011-04-29
> **williamdemeo said:**
> My new Thinkpad Edge was having the same problem.  I solved it by adding the following line to the file /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=thinkpad

Good luck!
-William

Where did you add that at?

---

### Post by DV-109 on 2011-07-04
Not sure if this will help anyone.

But I have a **Think Pad T410** which had Ubuntu factory loaded and the sound stopped working one day when I plunged in the Earphone Jack. 

I went to the Sound Preferences box which is at the top of the screen under the **speaker Icon.**


Then I selected 

**Sound Preferences....**
  
 **Go to Output Tab**

 Under the title  
 

 **Choose a device for sound output:**

 **(*) Internal Audio Analog Stereo *Sterio***
 

  ( ) High Definition Audio Controller Digital Stereo (HDMI) Sterio
  

  

  **I selected the first option,[ Internal Audio Analog Stereo *Sterio *] and the sound worked fine.**
  

  Not sure how it got on the HDMI Setting and stopped working.  :D

**This is for Ubuntu 11.04**

---

