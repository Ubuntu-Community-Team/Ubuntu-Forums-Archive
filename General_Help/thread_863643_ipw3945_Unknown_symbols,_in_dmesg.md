---
title: "ipw3945: Unknown symbols, in dmesg"
date: 2008-07-18
forum: General Help
---

### Post by malanco on 2008-07-18
help guys please!, i do a sudo modprobe ipw3945 and i get this error;

agustin@agustin-laptop:~/ipw3945/ipw3945-1.2.2$ sudo modprobe ipw3945
FATAL: Error inserting ipw3945 (/lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
sh: /sbin/ipw3945d-2.6.24-19-generic: No such file or directory
FATAL: Error running install command for ipw3945

then i give a dsmeg and this is the result;

[11044.208211] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[11044.208439] ipw3945: Unknown symbol ieee80211_wx_set_encode
[11044.208533] ipw3945: Unknown symbol ieee80211_wx_get_encode
[11044.208783] ipw3945: Unknown symbol ieee80211_txb_free
[11044.208932] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[11044.209174] ipw3945: Unknown symbol ieee80211_wx_get_scan
[11044.209288] ipw3945: Unknown symbol escape_essid
[11044.209486] ipw3945: Unknown symbol ieee80211_freq_to_channel
[11044.209968] ipw3945: Unknown symbol ieee80211_set_geo
[11044.210260] ipw3945: Unknown symbol ieee80211_rx
[11044.210350] ipw3945: Unknown symbol ieee80211_get_channel
[11044.210550] ipw3945: Unknown symbol ieee80211_channel_to_index
[11044.211006] ipw3945: Unknown symbol ieee80211_rx_mgt
[11044.211097] ipw3945: Unknown symbol ieee80211_get_geo
[11044.211244] ipw3945: Unknown symbol free_ieee80211
[11044.211577] ipw3945: Unknown symbol ieee80211_tx_frame
[11044.211700] ipw3945: Unknown symbol ieee80211_is_valid_channel
[11044.211797] ipw3945: Unknown symbol ieee80211_get_channel_flags
[11044.211994] ipw3945: Unknown symbol alloc_ieee80211

thanks in advance!! :)

---

### Post by malanco on 2008-07-18
bump, anyone?? plz

---

### Post by lswb on 2008-07-18
Where did you get that module? hardy by default uses the iwl3945 module rather than the older ipw3945. The older iw3945 module can be made to work but you will need a version compiled for your running kernel. If you are sure that this version is for your kernel, try running "sudo depmod" in a terminal. (type "man depmod" for info on what this does) The "unknown symbol" errors are because other modules that ipw3945 depends on are not being loaded. After the depmod command completes (it may take several seconds) try to modprobe ipw3945 again.

---

### Post by malanco on 2008-07-19
im still getting the same error after giving a depmode, i want to rollback to ipw3945, i installed the ipw3945 and patched my kernel with the ieee802, how i can get those modules running for ipw3945??

thanks!

---

### Post by lswb on 2008-07-19
I can only provide a few ideas, sorry but I don't have a complete solution

What is your reason for wanting ipw3945 module instead of iwl3945? I have seen several posts where people enabled the hardy backports repository and had better results with those versions of the iwl3945 modules.

If you really typed depmode instead of depmod, try it again with the correct spelling.

Again, how did you acquire the ipw3945 module? Did you compile it on your system? And the ieee80211 modules I believe are included with hardy, there should be no need to patch the kernel. Though you may need to patch or compile the ieee80211 modules.

Also, IIRC the ipw3945 module requires a daemon ipw3945d to be running as well, it can be loaded automatically from a /etc/modprobe.d file or in init.d if you know how to do that.

---

### Post by charles.figura on 2008-08-25
I'm having the same problem.  I followed the instructions on [http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html#comment-134254](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html#comment-134254)
but am getting the same error messages.

As for why to go back to ipw3945, for me, because it *works*.  iwl3945 was trotted out and it *still* doesn't work for WPA-LEAP networks, which my campus uses.  It also causes a kernel panic on unload (which means that suspend no longer works) - [https://bugs.launchpad.net/ubuntu/+bug/250520](https://bugs.launchpad.net/ubuntu/+bug/250520)

And the led doesn't work anymore (although it did for a while, steady on, it's back dead off again).

iwl3945 seems to have come out WAY prematurely.  I'm not sure what problem with ipw3945 it was supposed to fix, because things were working pretty well (for me, anyway) back in gutsy.

---

