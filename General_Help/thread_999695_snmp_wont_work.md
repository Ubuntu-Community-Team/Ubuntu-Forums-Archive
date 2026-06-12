---
title: "snmp wont work"
date: 2008-12-02
forum: General Help
---

### Post by needHelpPlease123 on 2008-12-02
hi all,

i installed snmp and snmpd, it can start and it also says that the service is running but when i try an snmpget or anything else i only get

Timeout: No Response from localhost.

e.g.

pc# snmpget -v 1 -c public localhost .1.3.6.1.4.1.2021.9.1.6.1
Timeout: No Response from localhost.


the only thing i changed about the snmpd.conf is that small part

# com2sec paranoid default public
  com2sec local   localhost public
  com2sec network 192.168.0.0 /24 public
# com2sec readwrite default private

i appreciate any help
thanks

---

### Post by iponeverything on 2008-12-02
Watch your logs:

```
sudo cd /var/log; tail -vf daemon.log syslog messages
```

restart snmpd:

```
sudo /etc/init.d/snmpd restart
```

Then try the snmpwalk

---

### Post by needHelpPlease123 on 2008-12-09
sorry for the late reply

ok so.. i watched my log and some message handler is missing?..

```
==> messages <==
Dec  9 22:53:09 dennis-laptop kernel: [   41.217099] Bluetooth: RFCOMM socket layer initialized
Dec  9 22:53:09 dennis-laptop kernel: [   41.217115] Bluetooth: RFCOMM TTY layer initialized
Dec  9 22:53:09 dennis-laptop kernel: [   41.217118] Bluetooth: RFCOMM ver 1.8
Dec  9 22:53:50 dennis-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Dec  9 22:53:52 dennis-laptop kernel: [   65.386706] NET: Registered protocol family 17
Dec  9 22:53:54 dennis-laptop kernel: [   68.176150] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec  9 22:53:59 dennis-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Dec  9 22:53:59 dennis-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Dec  9 22:53:59 dennis-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Dec  9 22:53:59 dennis-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu

==> syslog <==
Dec  9 22:59:24 dennis-laptop last message repeated 5 times
Dec  9 23:00:01 dennis-laptop /USR/SBIN/CRON[6797]: (www-data) CMD (php /usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)

==> daemon.log <==
Dec  9 22:59:24 dennis-laptop last message repeated 5 times

```

i restarted it
```
Restarting network management services: snmpd.

```

and.. i tried snmpwalk but it says, "no hostname specified" and lists options. shuoldnt like, snmpwalk alone return lots of rows of information?..

thanks for helping o:

---

