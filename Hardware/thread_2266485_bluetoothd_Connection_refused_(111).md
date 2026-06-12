---
title: "bluetoothd: Connection refused (111)"
date: 2015-02-23
forum: Hardware
---

### Post by bardov on 2015-02-23
I fail to connect my apple track pad. It worked well in the past, it now fails to connect.
bluetoothd -d gives the following when I try to connect:

```
bluetoothd[5505]: plugins/hciops.c:conn_complete() status 0x00bluetoothd[5505]: src/adapter.c:adapter_get_device() 1C:1A:C0:F1:DC:C5
bluetoothd[5505]: plugins/hciops.c:remote_features_information() hci0 status 0
bluetoothd[5505]: plugins/hciops.c:remote_name_information() hci0 status 0
bluetoothd[5505]: plugins/hciops.c:link_key_request() hci0 dba 1C:1A:C0:F1:DC:C5
bluetoothd[5505]: plugins/hciops.c:get_auth_info() hci0 dba 1C:1A:C0:F1:DC:C5
bluetoothd[5505]: plugins/hciops.c:link_key_request() kernel auth requirements = 0x00
bluetoothd[5505]: plugins/hciops.c:link_key_request() Matching key found
bluetoothd[5505]: plugins/hciops.c:link_key_request() link key type 0x00
bluetoothd[5505]: Connection refused (111)
bluetoothd[5505]: plugins/hciops.c:disconn_complete() handle 12 status 0x00
bluetoothd[5505]: src/event.c:btd_event_disconn_complete() 
bluetoothd[5505]: src/adapter.c:adapter_remove_connection()
```

my /etc/bluetooth/main.conf has the following:
```
[General]Name = %h-%d
Class = 0x000100
DiscoverableTimeout = 0
PairableTimeout = 0
PageTimeout = 8192
DiscoverSchedulerInterval = 30
AutoConnectTimeout = 0
InitiallyPowered = true
RememberPowered = false
ReverseServiceDiscovery = true
NameResolving = true 
DebugKeys = false
AttributeServer = false 

```
I'm running LTS 12.04.5

Any ideas?

---

