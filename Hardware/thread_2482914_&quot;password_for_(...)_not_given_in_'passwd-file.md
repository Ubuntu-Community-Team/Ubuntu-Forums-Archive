---
title: "&quot;password for (...) not given in 'passwd-file' (..)&quot; wifi kubuntu 22.10"
date: 2023-01-13
forum: Hardware
---

### Post by draxavi on 2023-01-13
edit: new issue

A new issue is happening, it's switch randomly from the previous to the new one:

```

Error: Connection activation failed: The Wi-Fi network could not be found

```

I am trying to connect using a wifi usb dongle, I had always a hard  time before updating to 22.10 and the new kernel, but now I can't  connect at all. If I connect the connection can't keep up for a long  time or just is really slow.
 the model of the wifi is:

 ```
Realtek Semiconductor Corp. 802.11ac NIC

``` [HR][/HR] ```
nmcli c up DAVI-5G

``` [HR][/HR] ```
Passwords or encryption keys are required to access the wireless network 'DAVI-5G'.
Warning: password for '802-11-wireless-security.psk' not given in 'passwd-file' and nmcli cannot ask without '--ask' option.
Error: Connection activation failed: Secrets were required, but not provided
Hint: use 'journalctl -xe NM_CONNECTION=60caf727-5ae3-425e-a4d4-1cda9369f728 + NM_DEVICE=wlxa0d768202865' to get more details.

``` [HR][/HR] ```
journalctl -xe NM_CONNECTION=60caf727-5ae3-425e-a4d4-1cda9369f728 + NM_DEVICE=wlxa0d768202865

``` [HR][/HR] ```
jan 13 17:37:07 mimi NetworkManager[833]: <info>  [1673642227.0987] device (wlxa0d768202865): state change: config -> need-auth (reason 'supplicant-disconnect', sys-iface-state: 'managed')
jan 13 17:37:07 mimi NetworkManager[833]: <info>  [1673642227.1987] device (wlxa0d768202865): supplicant interface state: disconnected -> inactive
jan 13 17:37:45 mimi NetworkManager[833]: <info>  [1673642265.8135] device (wlxa0d768202865): state change: need-auth -> deactivating (reason 'unmanaged', sys-iface-state: 'managed')
jan 13 17:37:45 mimi NetworkManager[833]: <info>  [1673642265.8259] device (wlxa0d768202865): state change: deactivating -> unmanaged (reason 'removed', sys-iface-state: 'managed')
jan 13 17:37:46 mimi NetworkManager[4678]: <info>  [1673642266.0690] device (wlxa0d768202865): driver supports Access Point (AP) mode
jan 13 17:37:46 mimi NetworkManager[4678]: <info>  [1673642266.0693] manager: (wlxa0d768202865): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/4)
jan 13 17:37:46 mimi NetworkManager[4678]: <info>  [1673642266.0694] device (wlxa0d768202865): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
jan 13 17:37:46 mimi NetworkManager[4678]: <info>  [1673642266.2194] device (wlxa0d768202865): supplicant interface state: internal-starting -> disconnected
jan 13 17:37:46 mimi NetworkManager[4678]: <info>  [1673642266.2203] device (wlxa0d768202865): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5671] device (wlxa0d768202865): Activation: starting connection 'DAVI-5G' (60caf727-5ae3-425e-a4d4-1cda9369f728)
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5672] device (wlxa0d768202865): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5675] device (wlxa0d768202865): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5678] device (wlxa0d768202865): Activation: (wifi) access point 'DAVI-5G' has security, but secrets are required.
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5678] device (wlxa0d768202865): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5679] sup-iface[a98432f14e7e8efc,1,wlxa0d768202865]: wps: type pbc start...
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5687] device (wlxa0d768202865): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5689] device (wlxa0d768202865): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5691] device (wlxa0d768202865): Activation: (wifi) connection 'DAVI-5G' has security, and secrets exist.  No new secrets needed.
jan 13 17:38:05 mimi NetworkManager[4678]: <info>  [1673642285.5901] device (wlxa0d768202865): supplicant interface state: disconnected -> associating
jan 13 17:38:12 mimi NetworkManager[4678]: <info>  [1673642292.7360] device (wlxa0d768202865): supplicant interface state: associating -> disconnected
jan 13 17:38:12 mimi NetworkManager[4678]: <info>  [1673642292.8410] device (wlxa0d768202865): supplicant interface state: disconnected -> scanning
jan 13 17:38:19 mimi NetworkManager[4678]: <info>  [1673642299.1433] device (wlxa0d768202865): supplicant interface state: scanning -> associating
jan 13 17:38:20 mimi NetworkManager[4678]: <info>  [1673642300.5919] device (wlxa0d768202865): supplicant interface state: associating -> disconnected
jan 13 17:38:21 mimi NetworkManager[4678]: <info>  [1673642301.0924] device (wlxa0d768202865): supplicant interface state: disconnected -> scanning
jan 13 17:38:27 mimi NetworkManager[4678]: <info>  [1673642307.3327] device (wlxa0d768202865): supplicant interface state: scanning -> associating
jan 13 17:38:30 mimi NetworkManager[4678]: <warn>  [1673642310.7038] device (wlxa0d768202865): Activation: (wifi) association took too long
jan 13 17:38:30 mimi NetworkManager[4678]: <info>  [1673642310.7039] device (wlxa0d768202865): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:30 mimi NetworkManager[4678]: <info>  [1673642310.7040] sup-iface[a98432f14e7e8efc,1,wlxa0d768202865]: wps: type pbc start...
jan 13 17:38:30 mimi NetworkManager[4678]: <warn>  [1673642310.7042] device (wlxa0d768202865): Activation: (wifi) asking for new secrets
jan 13 17:38:30 mimi NetworkManager[4678]: <warn>  [1673642310.8808] device (wlxa0d768202865): no secrets: No agents were available for this request.
jan 13 17:38:30 mimi NetworkManager[4678]: <info>  [1673642310.8808] device (wlxa0d768202865): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
jan 13 17:38:30 mimi NetworkManager[4678]: <warn>  [1673642310.8811] device (wlxa0d768202865): Activation: failed for connection 'DAVI-5G'
jan 13 17:38:30 mimi NetworkManager[4678]: <info>  [1673642310.8812] device (wlxa0d768202865): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
jan 13 17:38:32 mimi NetworkManager[4678]: <info>  [1673642312.7738] device (wlxa0d768202865): supplicant interface state: associating -> disconnected
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0477] device (wlxa0d768202865): Activation: starting connection 'DAVI-5G' (60caf727-5ae3-425e-a4d4-1cda9369f728)
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0478] device (wlxa0d768202865): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0481] device (wlxa0d768202865): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0483] device (wlxa0d768202865): Activation: (wifi) access point 'DAVI-5G' has security, but secrets are required.
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0483] device (wlxa0d768202865): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0484] sup-iface[a98432f14e7e8efc,1,wlxa0d768202865]: wps: type pbc start...
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0492] device (wlxa0d768202865): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0494] device (wlxa0d768202865): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
jan 13 17:41:54 mimi NetworkManager[4678]: <info>  [1673642514.0496] device (wlxa0d768202865): Activation: (wifi) connection 'DAVI-5G' has security, and secrets exist.  No new secrets needed.
jan 13 17:42:06 mimi NetworkManager[4678]: <info>  [1673642526.9737] device (wlxa0d768202865): supplicant interface state: disconnected -> scanning
jan 13 17:42:13 mimi NetworkManager[4678]: <info>  [1673642533.3872] device (wlxa0d768202865): supplicant interface state: scanning -> associating
jan 13 17:42:19 mimi NetworkManager[4678]: <warn>  [1673642539.7035] device (wlxa0d768202865): Activation: (wifi) association took too long
jan 13 17:42:19 mimi NetworkManager[4678]: <info>  [1673642539.7035] device (wlxa0d768202865): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
jan 13 17:42:19 mimi NetworkManager[4678]: <info>  [1673642539.7037] sup-iface[a98432f14e7e8efc,1,wlxa0d768202865]: wps: type pbc start...
jan 13 17:42:19 mimi NetworkManager[4678]: <warn>  [1673642539.7038] device (wlxa0d768202865): Activation: (wifi) asking for new secrets
jan 13 17:42:20 mimi NetworkManager[4678]: <info>  [1673642540.2482] device (wlxa0d768202865): supplicant interface state: associating -> disconnected
jan 13 17:42:20 mimi NetworkManager[4678]: <info>  [1673642540.2540] device (wlxa0d768202865): supplicant interface state: disconnected -> scanning
jan 13 17:42:26 mimi NetworkManager[4678]: <warn>  [1673642546.7213] device (wlxa0d768202865): no secrets: User canceled the secrets request.
jan 13 17:42:26 mimi NetworkManager[4678]: <info>  [1673642546.7214] device (wlxa0d768202865): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
jan 13 17:42:26 mimi NetworkManager[4678]: <warn>  [1673642546.7216] device (wlxa0d768202865): Activation: failed for connection 'DAVI-5G'
jan 13 17:42:26 mimi NetworkManager[4678]: <info>  [1673642546.7217] device (wlxa0d768202865): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
jan 13 17:42:27 mimi NetworkManager[4678]: <info>  [1673642547.4566] device (wlxa0d768202865): supplicant interface state: scanning -> disconnected

``` [HR][/HR] ```
ifconfig -a

``` [HR][/HR] ```
enp7s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 24:4b:fe:0c:44:9e  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx0217ff1544d3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.71.68  netmask 255.255.255.0  broadcast 192.168.71.255
        inet6 fe80::d5f9:5d93:c2f8:4f7a  prefixlen 64  scopeid 0x20<link>
        ether 02:17:ff:15:44:d3  txqueuelen 1000  (Ethernet)
        RX packets 17175  bytes 14421233 (14.4 MB)
        RX errors 3  dropped 0  overruns 0  frame 3
        TX packets 13469  bytes 3002498 (3.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6258  bytes 566031 (566.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6258  bytes 566031 (566.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlxa0d768202865: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a0:d7:68:20:28:65  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 399 (399.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

``` [HR][/HR] ```
sudo dkms status

``` [HR][/HR] ```
rtl8821cu/5.12.0, 5.19.0-29-generic, x86_64: installed

```


That's all I can think at the moment, any suggestion?

 TY

---

### Post by draxavi on 2023-01-14
It's possible to change the name? It need to be updated

---

