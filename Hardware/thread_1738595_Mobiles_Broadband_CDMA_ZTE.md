---
title: "Mobiles Broadband CDMA ZTE"
date: 2011-04-25
forum: Hardware
---

### Post by puipui on 2011-04-25
Hi all,
i'm using Ubuntu since a week. It was functioning really good with all hardware.
But suddenly my Mobiles Broadband got disconnected. I tried to unplugged the usb dongle (CDMA) and plug it again. It got connected again but only for a few seconds and suddenly disconnected .. so all the time.
I could get a IP adress, remote ip, and dns but can not get to the internet.
even if could sometimes. It won't last more then 2 minutes
i looked at the messages.log
--pppd[3165] : LCP terminated by peer
--pppd[3165] : Connection Terminated
--pppd[3165] : Terminating on signal 15
--pppd[3165] : modem hangup
--pppd[3165] : Exit
and from the daemon.log i get these messages
Apr 24 20:20:51 Puipui NetworkManager[947]: <info> Activation (ttyUSB0) starting connection 'libc1 connection 1'
Apr 24 20:20:51 Puipui NetworkManager[947]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Apr 24 20:20:51 Puipui NetworkManager[947]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 24 20:20:51 Puipui NetworkManager[947]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Apr 24 20:20:51 Puipui NetworkManager[947]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Apr 24 20:20:51 Puipui modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Apr 24 20:20:55 Puipui modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> registered)
Apr 24 20:20:55 Puipui NetworkManager[947]: <warn> CDMA connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Apr 24 20:20:55 Puipui NetworkManager[947]: <info> (ttyUSB0): device state change: 4 -> 9 (reason 0)
Apr 24 20:20:55 Puipui NetworkManager[947]: <info> Marking connection 'libc1 connection 1' invalid.
Apr 24 20:20:55 Puipui NetworkManager[947]: <warn> Activation (ttyUSB0) failed.
Apr 24 20:20:55 Puipui NetworkManager[947]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Apr 24 20:20:55 Puipui NetworkManager[947]: <info> (ttyUSB0): deactivating device (reason: 0).
&#12288;
&#12288;
&#12288;
Puipui modem-manager: (net/ppp0): could not get port's parent device
Puipui pppd[2578]: Unable to obtain CHAP password for smart on from plugin
Apr 24 23:18:55 Puipui NetworkManager[889]: real_connection_secrets_updated: assertion `IS_ACTIVATING_STATE (nm_device_get_state (device))' failed
 
 
can someone help me with these problems??? please 
i'm from indonesia and using smart telecom (CDMA) EVDO

---

### Post by lilifiz on 2011-04-25
which ubuntu you are using? how do you used to connect, via wvdial or the mobile broadband under network connections?

---

### Post by puipui on 2011-04-25
hi thank you.
I'm using maverick 10.10 and using Network Manager to connect to internet.
it used to work well ....

---

### Post by lilifiz on 2011-04-25
have you tried to delete this connection and create a new one??

---

### Post by puipui on 2011-04-25
yes i did. but it's just the same.

---

### Post by puipui on 2011-04-25
it suddenly works again.
but i guess it has conflict wih the mini sd memory in the usb modem

---

