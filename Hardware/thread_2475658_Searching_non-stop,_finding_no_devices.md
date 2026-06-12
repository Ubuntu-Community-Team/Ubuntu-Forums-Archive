---
title: "Searching non-stop, finding no devices"
date: 2022-06-03
forum: Hardware
---

### Post by liam.gutierrez on 2022-06-03
My PC's power got turned off accidentally and from then on, I haven't been able to find any Bluetooth devices nearby. I reinstalled bluez and other bluetooth related packages with --purge option and that didn't solve anything. 


[https://i.postimg.cc/C5ZMB08B/Screenshot-from-2022-06-03-10-57-47.png](https://i.postimg.cc/C5ZMB08B/Screenshot-from-2022-06-03-10-57-47.png)

---

### Post by #&amp;thj^% on 2022-06-03
Not much help, but try these commands, it might turn something up we can work with.
```
bluetoothctl
Agent registered
```
```
[bluetooth]# power on
Changing power on succeeded
```
[```
bluetooth]# scan on
Discovery started
[CHG] Controller 14:F6:D8:B3:28:14 Discovering: yes
```

---

### Post by liam.gutierrez on 2022-06-03
Thanks for pitching in. The same in terminal, no device discovered :(


[https://i.postimg.cc/h4HQLZGW/Screenshot-from-2022-06-03-11-25-30.png](https://i.postimg.cc/h4HQLZGW/Screenshot-from-2022-06-03-11-25-30.png)

---

### Post by #&amp;thj^% on 2022-06-03
I should have included this in my first reply
```
rfkill list all
```

---

### Post by liam.gutierrez on 2022-06-03
liam@ideacentre:~$ bluetoothctl 
Agent registered
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 9C:B6:D0:B0:85:38 Discovering: no
[CHG] Controller 9C:B6:D0:B0:85:38 Discovering: yes
[bluetooth]#

---

### Post by liam.gutierrez on 2022-06-03
liam@ideacentre:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by liam.gutierrez on 2022-06-03
[CHG] Controller 9C:B6:B0:B0:85:38 Class: 0x00000000
[CHG] Controller 9C:B6:B0:B0:85:38 Powered: no
[CHG] Controller 9C:B6:B0:B0:85:38 Discovering: no
[CHG] Controller 9C:B6:B0:B0:85:38 Class: 0x007c0104
[CHG] Controller 9C:B6:B0:B0:85:38 Powered: yes
[CHG] Controller 9C:B6:B0:B0:85:38 Discovering: yes

---

### Post by #&amp;thj^% on 2022-06-03
snip>>> I see you posted that already>> rfkill
Try putting your system in suspend for a minute or two, and wake it again.
```
systemctl suspend
```
now try to discover and pair.

---

### Post by liam.gutierrez on 2022-06-03
I suspect some config files are messed up. It was all working fine. I wonder if there's a way to reset bluetooth or all wireless settings somehow.

---

### Post by #&amp;thj^% on 2022-06-03
> **liam.gutierrez said:**
> I suspect some config files are messed up. It was all working fine. I wonder if there's a way to reset bluetooth or all wireless settings somehow.

Use with caution, may reset themes, icons, and may interfere with any special edits you have made:
```
dconf reset -f /org/gnome/
```
No warranty implied....;)

---

### Post by liam.gutierrez on 2022-06-03
Thanks for the effort. My desktop changed from dark to light theme but Bluetooth still crippled.  I can't find a similar case like mine in the forums either.

---

### Post by Yellow Pasque on 2022-06-03
What model PC or motherboard or Bluetooth adapter do you have?

---

### Post by #&amp;thj^% on 2022-06-03
> **liam.gutierrez said:**
> Thanks for the effort. My desktop changed from dark to light theme but Bluetooth still crippled.  I can't find a similar case like mine in the forums either.

Yep there is more and more cropping up here as well as other forums.
Most of what I'm seeing is related to Lenovo and newer kernels:
[https://forums.lenovo.com/t5/Other-Linux-Discussions/Thinkpad-P14s-Gen-2-AMD-Linux-support/m-p/5111011?page=2#5508417](https://forums.lenovo.com/t5/Other-Linux-Discussions/Thinkpad-P14s-Gen-2-AMD-Linux-support/m-p/5111011?page=2#5508417)

[https://forums.lenovo.com/t5/ThinkPad-L-R-and-SL-series-Laptops/Wi-Fi-and-Bluetooth-is-not-working-in-Lenovo-ThinkPad-L13/m-p/5111967](https://forums.lenovo.com/t5/ThinkPad-L-R-and-SL-series-Laptops/Wi-Fi-and-Bluetooth-is-not-working-in-Lenovo-ThinkPad-L13/m-p/5111967)

[https://forums.lenovo.com/t5/ThinkPad-11e-Windows-13-E-and/Bluetooth-no-longer-connecting-on-a-ThinkPad-11e/m-p/4551150](https://forums.lenovo.com/t5/ThinkPad-11e-Windows-13-E-and/Bluetooth-no-longer-connecting-on-a-ThinkPad-11e/m-p/4551150)

```
inxi  --bluetooth
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: 14:F6:D8:B3:28:14 bt-v: 3.0

```

---

### Post by liam.gutierrez on 2022-06-03
Bluetooth:
  Device-1: Qualcomm Atheros QCA61x4 Bluetooth 4.0 type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: 9C:B6:D0:B0:85:38 bt-v: 2.1

My humble rig: 
Lenovo ideacentre Y720 Cube-15ISH

---

### Post by Yellow Pasque on 2022-06-03
I would try resetting the BIOS if there is such an option. Sometimes, when there is sudden power loss, things gets stuck in an indeterminate state.

---

### Post by #&amp;thj^% on 2022-06-03
I for one have tried that, to no  avail
WiFi and bluetooth in the crapper. LOL
maybe the OP will have better luck though.

---

### Post by tea for one on 2022-06-04
Can you boot into an earlier kernel?

---

### Post by liam.gutierrez on 2022-06-05
Just booted into an earlier kernel, Bluetooth still finding no devices

---

### Post by tea for one on 2022-06-05
> **Yellow Pasque said:**
> I would try resetting the BIOS if there is such an option. Sometimes, when there is sudden power loss, things gets stuck in an indeterminate state.
Did you try this?
Perhaps, reset the UEFI/BIOS to default?
Alternatively, can you boot into an Ubuntu live session and see if Bluetooth recognises your devices?

A couple of weeks ago, I also lost device recognition with bluetooth after mucking about with kvm/qemu and a Windows 11 VM.
I reset the UEFI settings to default - [COLOR="#FF0000"]failure[/COLOR].
I booted into a live Ubuntu 22.04 session - [COLOR="#FF0000"]another failure[/COLOR].
I rebooted into my installed Ubuntu 22.04 regular session and voilà - [COLOR="#0000FF"]Bluetooth back to normal[/COLOR].

If I could explain it, I would be delighted to do so.......
I have no idea why Bluetooth disappeared nor why it suddenly re-appeared.

---

### Post by liam.gutierrez on 2022-06-17
Thanks, will try your suggestions and update here if that works so fellow users can benefit from.

---

