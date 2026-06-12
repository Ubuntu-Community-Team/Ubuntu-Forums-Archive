---
title: "rename port name"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by Steel98 on 2006-11-30
Hello! I'm using multiport card (8 comports). Then i install card, i have: # ls /dev | grep ttyS
ttyS4
ttyS5
ttyS6
ttyS7
ttyS8
ttyS9
ttyS10
ttyS11 

but i need rename ttyS4 to ttyS10 for example.. i do..

rm /dev/ttyS*
mknod -m 666 /dev/ttyS10 c 4 64
setserial /dev/ttyS10 port uart irq baud_base
chown root:tty /dev/ttyS10


but something wrong.. not all port configurate complite.. 

how it work? 
why major must be 64+port?

---

### Post by zgornel on 2006-11-30
I can partially answer you: When you create a device file with mknod, regardless wether it is char or block based, it requires two numbers, minor and major. These are pre-configured in the kernel (see [http://www.kernel.org/pub/linux/docs/device-list/devices.txt](http://www.kernel.org/pub/linux/docs/device-list/devices.txt)) so you have to choose the exact major and minor in order for the device to function properly. The major acts as a type of device identifier and the minor as the index of the device. I never configured the serial port myself but what exactly does not work ? And why rename the serial ports ?

---

### Post by Steel98 on 2006-12-01
facility for the sake :) 
so,

mknod -m 666 /dev/ttyS10 c 4 64
mknod -m 666 /dev/ttyS11 c 4 65
mknod -m 666 /dev/ttyS12 c 4 66

good idia ?

---

### Post by zgornel on 2006-12-02
No. The rule is ttyS**X** --> mknod -m 666 /dev/ttyS10 c 4 64+**X**. I have no idea how you'll associate the new ports to the phy ports on the board but I gues you know how.

---

