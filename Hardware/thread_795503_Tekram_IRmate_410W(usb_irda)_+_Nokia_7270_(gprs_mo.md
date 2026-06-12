---
title: "Tekram IRmate 410W(usb irda) + Nokia 7270 (gprs modem) slow gprs connection"
date: 2008-05-15
forum: Hardware
---

### Post by alsokoloff on 2008-05-15
I have usb Irda Tekram IRmate 410W and Nokia 7270 acting as gprs modem. I conect to the internet without problem. 
But there is problem with speed. In Windows i have 10-14 Kb/sec and in Linux only 2-4 Kb/sec.

Here **dmesg**
After usb plug in 
```
usb 3-1: new full speed USB device using uhci_hcd and address 2
usb 3-1: device descriptor read/64, error -71
usb 3-1: configuration #1 chosen from 1 choice
SigmaTel STIr4200 IRDA/USB found at address 2, Vendor: 66f, Product: 4200
```
**sudo irattach irda0 -s**
```
/build/buildd/linux-2.6.24/drivers/net/irda/stir4200.c: IrDA: Registered SigmaTel device irda0
irlap_change_speed(), setting speed to 9600
```
[B]sudo modprobe ircomm
sudo modprobe ircomm-tty[/B]
```
IrCOMM protocol (Dag Brattli)
```
**pppd call gprs**
```
ircomm_tty_attach_cable()
ircomm_tty_ias_register()
irlap_change_speed(), **setting speed to 115200**
ircomm_param_service_type(), services in common=04
ircomm_param_service_type(), resulting service type=0x04
ircomm_param_port_type(), port type=1
ircomm_param_port_type(), port type=1
ircomm_param_xon_xoff(), XON/XOFF = 0x11,0x13
ircomm_param_enq_ack(), ENQ/ACK = 0x13,0x11
ircomm_tty_check_modem_status()
```

I also used **stty -F /dev/ircomm0 115200** to change speed but it doesnt help. 
Must be something else...

---

