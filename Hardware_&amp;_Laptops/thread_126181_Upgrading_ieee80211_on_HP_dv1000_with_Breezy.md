---
title: "Upgrading ieee80211 on HP dv1000 with Breezy"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by gidkill on 2006-02-05
Can someone help?

I have Breezy installed on an HP dv1000 (Centrino with ipw2200bg wireless). I am trying to upgrade my ieee80211 module. When I try to load the new modules, I receive errors I don't understand.

I downloaded the 1.1.8 source, removed the previous version, ran 'make install' without any errors (that I noticed), unloaded the existing 80211 modules, rebooted, then attempted to load the new 1.18 ieee80211:

root@lucky:/staging# modprobe ieee80211
FATAL: Error inserting ieee80211 (/lib/modules/2.6.12-10-386/net/ieee80211/ieee80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@lucky:/staging# dmesg|grep 80211
[4294773.803000] ieee80211_crypt: registered algorithm 'NULL'
[4294773.914000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4294773.914000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4294773.914000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4294773.914000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4294773.914000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294773.914000] ieee80211: Unknown symbol iee
e80211_crypt_delayed_deinit
[4294773.915000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4294773.915000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4297679.523000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4297683.097000] ieee80211_crypt: registered algorithm 'NULL'
[4297687.675000] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[4297848.380000] ieee80211_crypt: registered algorithm 'NULL'
[4297848.397000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4297848.397000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4297848.397000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4297848.397000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4297848.397000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4297848.397000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4297848.398000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4297848.398000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
root@lucky:/staging#

---

