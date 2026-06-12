---
title: "snd-bt-sco module fails, cannot use bluetooth headset!"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by psypher on 2007-11-27
Hey everyone, please can someone help.

I have got a Dell Precision M6300 with Gutsy and trying to get a logitech bluetooth headset to work. Unfortunately I am unable to get past ```
sudo modprobe snd-bt-sco
```  using this howto:
[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)

I get this error:

FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg says:
```

[  731.336000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  731.336000] snd_bt_sco: Unknown symbol snd_ctl_add
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  731.336000] snd_bt_sco: Unknown symbol snd_pcm_new
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_card_register
[  731.336000] snd_bt_sco: Unknown symbol snd_card_register
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_card_free
[  731.336000] snd_bt_sco: Unknown symbol snd_card_free
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  731.336000] snd_bt_sco: Unknown symbol snd_ctl_new1
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_card_new
[  731.336000] snd_bt_sco: Unknown symbol snd_card_new
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  731.336000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  731.336000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[  731.336000] snd_bt_sco: Unknown symbol snd_hwdep_new
[  731.340000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[  731.340000] snd_bt_sco: Unknown symbol snd_ctl_notify
[  731.340000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  731.340000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  731.340000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  731.340000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[  945.464000] snd_bt_sco: Unknown symbol snd_ctl_add
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[  945.464000] snd_bt_sco: Unknown symbol snd_pcm_new
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_card_register
[  945.464000] snd_bt_sco: Unknown symbol snd_card_register
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_card_free
[  945.464000] snd_bt_sco: Unknown symbol snd_card_free
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[  945.464000] snd_bt_sco: Unknown symbol snd_ctl_new1
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_card_new
[  945.464000] snd_bt_sco: Unknown symbol snd_card_new
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[  945.464000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[  945.464000] snd_bt_sco: Unknown symbol snd_hwdep_new
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[  945.464000] snd_bt_sco: Unknown symbol snd_ctl_notify
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[  945.464000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[  945.464000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[  945.464000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[ 1171.856000] /dev/vmmon[7094]: host clock rate change request 83 -> 134
[ 1191.600000] /dev/vmmon[7094]: host clock rate change request 134 -> 83
[ 1192.756000] /dev/vmmon[7094]: host clock rate change request 83 -> 297
[ 1197.284000] rtc: lost 1 interrupts
[ 1204.836000] /dev/vmmon[7094]: host clock rate change request 297 -> 83
[ 1214.908000] /dev/vmmon[7094]: host clock rate change request 83 -> 93
[ 1227.808000] /dev/vmmon[7094]: host clock rate change request 93 -> 83
[ 1240.648000] /dev/vmmon[7094]: host clock rate change request 83 -> 87
[ 1257.148000] /dev/vmmon[7094]: host clock rate change request 87 -> 83
[ 1369.504000] /dev/vmmon[7094]: host clock rate change request 83 -> 96
[ 1386.284000] /dev/vmmon[7094]: host clock rate change request 96 -> 83
[ 1455.504000] /dev/vmmon[7094]: host clock rate change request 83 -> 257
[ 1468.556000] /dev/vmmon[7094]: host clock rate change request 257 -> 83
[ 1468.556000] /dev/vmmon[7094]: host clock rate change request 83 -> 221
[ 1481.312000] /dev/vmmon[7094]: host clock rate change request 221 -> 83
[ 1481.312000] /dev/vmmon[7094]: host clock rate change request 83 -> 153
[ 1494.516000] /dev/vmmon[7094]: host clock rate change request 153 -> 83
[ 1494.516000] /dev/vmmon[7094]: host clock rate change request 83 -> 119
[ 1497.332000] /dev/vmmon[7094]: host clock rate change request 119 -> 137
[ 1510.832000] /dev/vmmon[7094]: host clock rate change request 137 -> 83
[ 1510.832000] /dev/vmmon[7094]: host clock rate change request 83 -> 98
[ 1523.984000] /dev/vmmon[7094]: host clock rate change request 98 -> 83
[ 1528.588000] /dev/vmmon[7094]: host clock rate change request 83 -> 92
[ 1543.332000] /dev/vmmon[7094]: host clock rate change request 92 -> 83
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[ 1583.140000] snd_bt_sco: Unknown symbol snd_ctl_add
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 1583.140000] snd_bt_sco: Unknown symbol snd_pcm_new
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_card_register
[ 1583.140000] snd_bt_sco: Unknown symbol snd_card_register
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_card_free
[ 1583.140000] snd_bt_sco: Unknown symbol snd_card_free
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[ 1583.140000] snd_bt_sco: Unknown symbol snd_ctl_new1
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_card_new
[ 1583.140000] snd_bt_sco: Unknown symbol snd_card_new
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1583.140000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[ 1583.140000] snd_bt_sco: Unknown symbol snd_hwdep_new
[ 1583.140000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[ 1583.140000] snd_bt_sco: Unknown symbol snd_ctl_notify
[ 1583.144000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 1583.144000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 1583.144000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 1583.148000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[ 1663.412000] snd_bt_sco: Unknown symbol snd_ctl_add
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 1663.412000] snd_bt_sco: Unknown symbol snd_pcm_new
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_card_register
[ 1663.412000] snd_bt_sco: Unknown symbol snd_card_register
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_card_free
[ 1663.412000] snd_bt_sco: Unknown symbol snd_card_free
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[ 1663.412000] snd_bt_sco: Unknown symbol snd_ctl_new1
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_card_new
[ 1663.412000] snd_bt_sco: Unknown symbol snd_card_new
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1663.412000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[ 1663.412000] snd_bt_sco: Unknown symbol snd_hwdep_new
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[ 1663.412000] snd_bt_sco: Unknown symbol snd_ctl_notify
[ 1663.412000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 1663.412000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 1663.416000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 1663.416000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
[ 1694.212000] /dev/vmmon[7094]: host clock rate change request 83 -> 195
[ 1707.480000] /dev/vmmon[7094]: host clock rate change request 195 -> 83
[ 1846.264000] /dev/vmmon[7094]: host clock rate change request 83 -> 174
[ 1864.084000] /dev/vmmon[7094]: host clock rate change request 174 -> 83
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_ctl_add
[ 2603.744000] snd_bt_sco: Unknown symbol snd_ctl_add
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_pcm_new
[ 2603.744000] snd_bt_sco: Unknown symbol snd_pcm_new
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_card_register
[ 2603.744000] snd_bt_sco: Unknown symbol snd_card_register
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_card_free
[ 2603.744000] snd_bt_sco: Unknown symbol snd_card_free
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_ctl_new1
[ 2603.744000] snd_bt_sco: Unknown symbol snd_ctl_new1
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_card_new
[ 2603.744000] snd_bt_sco: Unknown symbol snd_card_new
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_pcm_lib_ioctl
[ 2603.744000] snd_bt_sco: Unknown symbol snd_pcm_lib_ioctl
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_hwdep_new
[ 2603.744000] snd_bt_sco: Unknown symbol snd_hwdep_new
[ 2603.744000] snd_bt_sco: disagrees about version of symbol snd_ctl_notify
[ 2603.744000] snd_bt_sco: Unknown symbol snd_ctl_notify
[ 2603.752000] snd_bt_sco: disagrees about version of symbol snd_pcm_set_ops
[ 2603.752000] snd_bt_sco: Unknown symbol snd_pcm_set_ops
[ 2603.752000] snd_bt_sco: disagrees about version of symbol snd_pcm_period_elapsed
[ 2603.752000] snd_bt_sco: Unknown symbol snd_pcm_period_elapsed
```

What could be wrong??
Thanks

---

### Post by wieman01 on 2007-11-27
First of all what are you trying to achieve? Does the Bluetooth applet not work for you?

The guide is outdated and as far as I know, "snd_bt_sco" has been replaced or something like that. So no surprise you get these error messages.

Please tell us exactly what you plan to do (e.g. connecting headphones) and we should be able to advise.

---

### Post by psypher on 2007-11-27
yeah i found another link mentioning that it's outdated. but no easy way to make it work

I'm trying to setup my bt headset to connect to the laptop so i can use it with voip software like skype and hopefully maybe even my company avaya voip system. but the latter is a bit of a pipedream. 

anyway. I can see the device in my bluetooth list. how do i make it work without snd-bt-sco?

Thanks

---

### Post by wieman01 on 2007-11-27
That's a tool that has reportedly helped quite a number of people:

[http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/")

---

### Post by psypher on 2007-11-27
I don't know where to go further. I got the headset paired but only with the hcitool cc macaddress command. I then tried the blueman tool which confirms the device is paired. I decided that voip in the office is the most important so I am trying to get ekiga working. Ekiga does not see the headset as a sound device. I used this site:

[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

which explain the btsco thing well. I am assuming since I am not trying to play audio that the section about headset profile is valid to me. 

All the commands seem to go through fine but still ekiga does not find the bt headset as an audio device.  Seems so close!!!

Thanks for your help so far. The blueman prog is definitely better than any other I've tried, i can disconnect and connect perfectly from there, so far!

---

### Post by wieman01 on 2007-11-27
Have you also tried Skype v1.4? It should work perfectly and should detect your headset as sound device.

---

### Post by psypher on 2007-11-28
The wiki entry at bluez seemed to to do the job for skype perfectly, i can hear and be heard. And once again I HIGHLY recommend the blueman above all else. But still ekiga does not see the bluetooth audio device so i cannot select it. Is it even possible with ekiga? if not is there another softphone voip app you can recommend?

thanks

---

