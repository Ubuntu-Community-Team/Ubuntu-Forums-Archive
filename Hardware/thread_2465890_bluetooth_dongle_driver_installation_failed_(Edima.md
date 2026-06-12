---
title: "bluetooth dongle driver installation failed (Edimax BT-8500). Please help."
date: 2021-08-14
forum: Hardware
---

### Post by will0913 on 2021-08-14
Hi, guys, 

Newbie here. I've been trying to install the driver for my dongle to no avail.
I followed the instruction in the readme.txt of the driver.
The following is the error message. I'd appreciate it if anybody could help me.
```
[FONT=monospace][COLOR=#54FF54]**will@B365**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux**[/COLOR][COLOR=#000000]$ sudo make install INTERFACE=all[/COLOR]
mkdir -p /lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth
Start Realtek Bluetooth USB driver installation
mkdir -p /lib/firmware
Copy rtkbt-firmware/lib/firmware/rtl*_fw to /lib/firmware
cp -a rtkbt-firmware/lib/firmware/rtl*_fw /lib/firmware
Copy rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
cp -a rtkbt-firmware/lib/firmware/rtl*_config /lib/firmware
make -C usb install
make[1]: Entering directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb'
rmmod btusb
rmmod: ERROR: Module btusb is not currently loaded
make[1]: [Makefile:7: install] Error 1 (ignored)
mv /lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth/btusb.ko /lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth/btusb_bak
mv: cannot stat '/lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth/btusb.ko': No such file or directory
make[1]: [Makefile:8: install] Error 1 (ignored)
rmmod rtk_btusb
rmmod: ERROR: Module rtk_btusb is not currently loaded
make[1]: [Makefile:9: install] Error 1 (ignored)
make -C ./bluetooth_usb_driver
make[2]: Entering directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver'
make -C /lib/modules/5.11.0-25-generic/build M=/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver m
odules
make[3]: Entering directory '/usr/src/linux-headers-5.11.0-25-generic'
  CC [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_coex.o
  CC [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_misc.o
  CC [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_bt.o
  LD [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_btusb.o
  MODPOST /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/Module.symvers
  CC [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_btusb.mod.o
  LD [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver/rtk_btusb.ko
make[3]: Leaving directory '/usr/src/linux-headers-5.11.0-25-generic'
make[2]: Leaving directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver'
cp -f ./bluetooth_usb_driver/rtk_btusb.ko /lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth/rtk_btusb.ko
depmod -a 5.11.0-25-generic
make -C ./bluetooth_usb_driver clean
make[2]: Entering directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver'
rm -rf *.o *.mod.c *.mod.o *.ko *.symvers *.order *.a
make[2]: Leaving directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb/bluetooth_usb_driver'
echo "install rtk_btusb success!"
install rtk_btusb success!
make[1]: Leaving directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/usb'
Start Realtek Bluetooth UAART driver installation
mkdir -p /lib/firmware/rtlbt
Copy rtkbt-firmware/lib/firmware/rtlbt/rtl*_fw to /lib/firmware/rtlbt
cp -a rtkbt-firmware/lib/firmware/rtlbt/rtl*_fw /lib/firmware/rtlbt
Copy rtkbt-firmware/lib/firmware/rtlbt/rtl*_config /lib/firmware/rtlbt
cp -a rtkbt-firmware/lib/firmware/rtlbt/rtl*_config /lib/firmware/rtlbt
make -C uart install
make[1]: Entering directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart'
mkdir -p /lib/modules/5.11.0-25-generic/kernel/drivers/bluetooth
rmmod hci_uart
rmmod: ERROR: Module hci_uart is not currently loaded
make[1]: [Makefile:10: install] Error 1 (ignored)
make -C bluetooth_uart_driver
make[2]: Entering directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver'
make -C /lib/modules/5.11.0-25-generic/build M=/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver
 modules
make[3]: Entering directory '/usr/src/linux-headers-5.11.0-25-generic'
  CC [M]  /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver/hci_ldisc.o
[COLOR=#000000]**/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver/hci_ldisc.c:**[/COLOR][COLOR=#000000] In function ‘[/COLOR][COLOR=#000000]**hci_uart_init**[/COLOR][COLOR=#000000]’:[/COLOR]
[COLOR=#000000]**/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver/hci_ldisc.c:1086:22:**[/COLOR][COLOR=#FF5454]**error: **[/COLOR][COLOR=#000000]assignment to ‘[/COLOR][COLOR=#000000]**ssi**[/COLOR]
ze_t (*)(struct tty_struct *, struct file *, unsigned char *, size_t,  void **, long unsigned int)[COLOR=#000000]’ {aka ‘[/COLOR][COLOR=#000000]**long int (*)(struct tty_struct *,**[/COLOR]
 struct file *, unsigned char *, long unsigned int,  void **, long unsigned int)[COLOR=#000000]’} from incompatible pointer type ‘[/COLOR][COLOR=#000000]**ssize_t (*)(struct tty_s**[/COLOR]
truct *, struct file *, unsigned char *, size_t)[COLOR=#000000]’ {aka ‘[/COLOR][COLOR=#000000]**long int (*)(struct tty_struct *, struct file *, unsigned char *, long unsigned int**[/COLOR]
)[COLOR=#000000]’} [[/COLOR][COLOR=#FF5454]**-Werror=incompatible-pointer-types**[/COLOR][COLOR=#000000]][/COLOR]
 1086 |  hci_uart_ldisc.read [COLOR=#FF5454]**=**[/COLOR][COLOR=#000000] hci_uart_tty_read;[/COLOR]
      |                      [COLOR=#FF5454]**^**[/COLOR]
cc1: some warnings being treated as errors
make[4]: *** [scripts/Makefile.build:287: /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver/hci_
ldisc.o] Error 1
make[3]: *** [Makefile:1848: /home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver] Error 2
make[3]: Leaving directory '/usr/src/linux-headers-5.11.0-25-generic'
make[2]: *** [Makefile:12: all] Error 2
make[2]: Leaving directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart/bluetooth_uart_driver'
make[1]: *** [Makefile:11: install] Error 2
make[1]: Leaving directory '/home/will/Downloads/BT-8500_Linux_Bluetooth_Driver_1_0_0_1/Linux/uart'
make: *** [Makefile:39: install] Error 2

[/FONT]
```

---

