---
title: "Intex Wireless Mouse -IT-OP82"
date: 2012-05-23
forum: Hardware
---

### Post by shan4djfun on 2012-05-23
Guys I'm new to Ubuntu but well aware of using Linux systems. recently i bought this [http://www.intexuae.com/Mouse-IT-OP82-blaze-wl.htm](http://www.intexuae.com/Mouse-IT-OP82-blaze-wl.htm) and it doesnt work on ubuntu. And I'm already feeling terrible because I cannot get it work on ubuntu.

it doesnt show up in 

```


sudo lsusb


```plz help

---

### Post by shan4djfun on 2012-05-23
bump

---

### Post by shan4djfun on 2012-05-23
> **shan4djfun said:**
> bump


any GURU?

---

### Post by shan4djfun on 2012-05-23
58 views still no reply :( i'm running ubuntu 10.10 plz help

---

### Post by mörgæs on 2012-05-23
Please show some patience and stop your bumping.

If you feel that you don't receive enough answers this might help:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by shan4djfun on 2012-05-23
> **mörgæs said:**
> Please show some patience and stop your bumping.

If you feel that you don't receive enough answers this might help:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)


thank you very much for reply. but still waiting for an answer :(

---

### Post by shan4djfun on 2012-05-23
> **mörgæs said:**
> Please show some patience and stop your bumping.

If you feel that you don't receive enough answers this might help:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)


thanks for the reply. But i ddnt get a solution yet

---

### Post by shan4djfun on 2012-05-26
installing 12.04LTS ddnt solve the problem

---

### Post by shan4djfun on 2012-05-26
**[SIZE=3]dmesg out put[/SIZE]**

```

[ 8060.469015] usb 1-1: USB disconnect, address 116
[ 8077.696522] usb 2-1: new low speed USB device using uhci_hcd and address 113
[ 8077.970618] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8432
[ 8077.970785] generic-usb 0003:0603:1602.20EF: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8078.024537] usb 2-1: USB disconnect, address 113
[ 8078.764029] usb 2-1: new low speed USB device using uhci_hcd and address 114
[ 8078.981636] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8433
[ 8078.981801] generic-usb 0003:0603:1602.20F0: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8079.016562] usb 2-1: USB disconnect, address 114
[ 8079.752522] usb 2-1: new low speed USB device using uhci_hcd and address 115
[ 8079.969669] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8434
[ 8079.969840] generic-usb 0003:0603:1602.20F1: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8079.969892] usb 2-1: USB disconnect, address 115
[ 8080.544522] usb 2-1: new low speed USB device using uhci_hcd and address 116
[ 8080.761675] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8435
[ 8080.761859] generic-usb 0003:0603:1602.20F2: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8080.761911] usb 2-1: USB disconnect, address 116
[ 8081.488030] usb 2-1: new low speed USB device using uhci_hcd and address 117
[ 8081.705714] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8436
[ 8081.705937] generic-usb 0003:0603:1602.20F3: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8081.706004] usb 2-1: USB disconnect, address 117
[ 8082.280521] usb 2-1: new low speed USB device using uhci_hcd and address 118
[ 8082.499867] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8437
[ 8082.500040] generic-usb 0003:0603:1602.20F4: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8082.500092] usb 2-1: USB disconnect, address 118
[ 8083.224533] usb 2-1: new low speed USB device using uhci_hcd and address 119
[ 8083.445730] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8438
[ 8083.445906] generic-usb 0003:0603:1602.20F5: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8083.445958] usb 2-1: USB disconnect, address 119
[ 8084.016524] usb 2-1: new low speed USB device using uhci_hcd and address 120
[ 8084.233739] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8439
[ 8084.233910] generic-usb 0003:0603:1602.20F6: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8084.233961] usb 2-1: USB disconnect, address 120
[ 8084.960029] usb 2-1: new low speed USB device using uhci_hcd and address 121
[ 8085.177761] input: USB Device USB Device as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8440
[ 8085.177932] generic-usb 0003:0603:1602.20F7: input,hiddev96,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1d.0-1/input0
[ 8085.177984] usb 2-1: USB disconnect, address 121

```

---

### Post by shan4djfun on 2012-06-07
anyone got any thing about this problem yet. or am I the only one with this mouse

---

### Post by shan4djfun on 2012-07-02
[http://shdltechblog.com/blog/index.php?entry=entry120623-124801](http://shdltechblog.com/blog/index.php?entry=entry120623-124801)

---

