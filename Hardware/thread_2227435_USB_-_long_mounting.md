---
title: "USB - long mounting"
date: 2014-06-02
forum: Hardware
---

### Post by guber90 on 2014-06-02
Hello guys I have problem with my ubuntu, when I plug in any usb it needs about 1 minute to mount it.
Also when I use something that I copied from ubuntu to USB, on lets say Windows I have problems, I get all kind of errors ect.

Anyone knows is there fix to this?

Thx :).

---

### Post by matt_symes on 2014-06-02
Hi

Open a terminal and type

```
sudo dmesg -c
```

Enter your password. It will not be echoed to the screen.

Plug in your USB and wait until it's mounted then type

```
dmesg
```

Post the output back here. It will tell us what the kernel was doing when itt mounted the USB stick.

After that type (with the USB stick plugged in)

```
lspci -nnk | grep -iA2 usb
```

Capital A above.

Post that back here and lastly post back the output of this command with the stick plugged in.

```
lsusb -t
```

Hopefully that will give us a starting point.

Kind regards

---

