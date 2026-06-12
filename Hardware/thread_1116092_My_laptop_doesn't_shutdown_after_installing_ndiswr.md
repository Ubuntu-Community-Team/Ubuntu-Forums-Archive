---
title: "My laptop doesn't shutdown after installing ndiswrapper"
date: 2009-04-04
forum: Hardware
---

### Post by linderox on 2009-04-04
Ubuntu 8.04. Laptop HP 530. Celeron. 
I installed ndiswrapper for my wificard and then my System doesn't shutdown. It hang ups on this: 
```

NetworkManager: <WARN> nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument
NetworkManager: <WARN> nm_utils_supplicant_request_with_check(): nm_device_802_11_wireless_scan: supplicant error for 'SCAN'. Response: 'TIMEOUT[CLI]'
NetworkManager: <WARN> nm_device_802_11_wireless_scan(): (eth1): could not trigger wireless scan
Network Manager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
Network Manager: <WARN> nm_hal_deinit(): nm_dbus_init() could not get the system bus. Make Sure the message bus daemon is running!
Network manager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed
Network manager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed
Network manager: nm_dbus_signal_device_status_change: assertion `cb_data->data->dbus_connection' failed

```

What I should do?

---

