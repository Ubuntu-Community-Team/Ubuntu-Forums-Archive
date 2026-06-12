---
title: "Network Card not working on boot"
date: 2017-05-28
forum: Hardware
---

### Post by paolol on 2017-05-28
Hi,
I just finish to install in a new MSi laptop and at boot only the wifi card is working the cable card is not  ( Killer 2500).
I was able to fix this with these commands , but I have to do it every time I boot the system :(  :
sudo modprobe alx
echo 1969 e0b1 | sudo tee /sys/bus/pci/drivers/alx/new_id

Any one know how I can avoid it ?
Thanks

---

### Post by TheFu on 2017-05-28
Do you have an installed Linux or are you running from a live-boot flash/optical media?

If you put those commands into /etc/rc.local, then they will be run at the end of boot. No need for sudo or tee since rc.local is run as root already. Assuming the commands are really correct, then:
```

/sbin/modprobe   alx
echo 1969 e0b1 >  /sys/bus/pci/drivers/alx/new_id
/usr/sbin/service networking restart
```

However, realistically with a full install, running modprobe once should be sufficient provided the driver is available on the storage for the current kernel.

[http://www.killernetworking.com/driver-downloads/knowledge-base#](http://www.killernetworking.com/driver-downloads/knowledge-base#) has some instructions too. Did those help?

---

### Post by paolol on 2017-05-29
Hi thanks for reply.
Yes is a full install .
I will look on the link later on.
:)

---

### Post by paolol on 2017-05-30
Sorry but still not working, same as before.
Any more suggestion is welcome
Thanks

---

### Post by TheFu on 2017-05-30
> **paolol said:**
> Sorry but still not working, same as before.
Any more suggestion is welcome
Thanks

Please be extremely clear on what you did. Exactly. we can't read minds.

---

### Post by paolol on 2017-05-31
Sorry,
I try to add the command to the [COLOR=#000000]rc.local .
But still not working, I still have to issue the commands manualy after login.

Thanks[/COLOR]

---

### Post by paolol on 2017-06-01
Hi,
I fixed changing the kernel from 4.4 to 4.8, removed also the lines on the rc.local.

Thanks.

---

