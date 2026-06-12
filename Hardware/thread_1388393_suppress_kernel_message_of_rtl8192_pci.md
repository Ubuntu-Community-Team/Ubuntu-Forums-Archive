---
title: "suppress kernel message of rtl8192_pci"
date: 2010-01-23
forum: Hardware
---

### Post by wonghang on 2010-01-23
Hi everyone,

  I have just got my asus eeepc 1201n works on ubuntu 9.1. The wireless driver rthl8192_pci works well up to now. But there is a problem that it always flood many message in my kernel log (dmesg). Is there anyway to suppress / close the message output of rtl8192_pci? here is a sample output of the message I saw:

```

[  204.978056] ===>ieee80211_associate_procedure_wq(), chan:11
[  204.978066] ==========>HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  204.988061] =================>ieee80211_authentication_req():auth->algorithm is 0
[  204.989971] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  204.989985] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  204.992426] #################ieee80211_sta_send_associnfo(), assocreq_ies_len:24,assocresp_ies_len:24
[  204.993939] Associated successfully
[  204.993955] ============>normal associate
[  204.993988] Using G rates:108
[  204.993994] Successfully associated, ht not enabled(0, 0)
[  204.994029] ===========rtl8192se_update_ratr_table: ff5
[  204.994036] ===>set to B/G mode
[  205.007676] ===>u4bAcParam:731c, ===>u4bAcParam:731c, ===>u4bAcParam:731c, ===>u4bAcParam:731c, ===>DHCP Protocol start tx DHCP pkt src port:68, dest port:67!!
[  255.746083] ===========rtl8192se_update_ratr_table: ff5
[  255.746091] ===>set to B/G mode
[  295.742086] ===========rtl8192se_update_ratr_table: ff5
[  295.742094] ===>set to B/G mode
[  355.754077] ===========rtl8192se_update_ratr_table: ff5
[  355.754084] ===>set to B/G mode
[  435.758041] ===========rtl8192se_update_ratr_table: ff5
[  435.758048] ===>set to B/G mode
[  535.750038] ===========rtl8192se_update_ratr_table: ff5
[  535.750045] ===>set to B/G mode
[  655.738083] ===========rtl8192se_update_ratr_table: ff5
[  655.738090] ===>set to B/G mode
[  775.754035] ===========rtl8192se_update_ratr_table: ff5
[  775.754042] ===>set to B/G mode
[  895.750129] ===========rtl8192se_update_ratr_table: ff5
[  895.750137] ===>set to B/G mode
[ 1015.750054] ===========rtl8192se_update_ratr_table: ff5
[ 1015.750062] ===>set to B/G mode
[ 1135.754030] ===========rtl8192se_update_ratr_table: ff5
[ 1135.754037] ===>set to B/G mode

```  I am running kernel 2.6.31-18-generic and install the driver by following the guide here:

[http://ubuntuforums.org/showthread.php?t=1354666&page=2](http://ubuntuforums.org/showthread.php?t=1354666&page=2)

  Thank you very much.

Best regards.
WONG Hang.

---

### Post by emoguitarist06 on 2010-05-04
I have the 1201N and I installed the wifi drive on from this post
[http://vip.asus.com/forum/view.aspx?id=20100103170804750&board_id=20&model=Eee+PC+1201N&SLanguage=en-us&page=3](http://vip.asus.com/forum/view.aspx?id=20100103170804750&board_id=20&model=Eee+PC+1201N&SLanguage=en-us&page=3)
and I have not had the message
maybe uninstall and reinstall with those directions?

---

