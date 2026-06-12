---
title: "Ubuntu 15.04 Vivid, 15.10 Wily - Amped Wireless UA230A (RTL8812AU)"
date: 2015-04-28
forum: Hardware
---

### Post by pravinbravi on 2015-04-28
Make sure the device id = [SIZE=2]```
**0x7392, 0xA813**
```[/SIZE] this you can find by using ```
lsusb
``` command.

1. HowTo from git. Refer : [http://ubuntuforums.org/showthread.php?t=2228244](http://ubuntuforums.org/showthread.php?t=2228244)[INDENT]
for Ubuntu 15.04 and lesser versions (kernel <=3.1)
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
```

for Ubuntu 15.10 and greater versions (kernel >= 4)
```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/csssuf/rtl8812au.git
```

[/INDENT]
2. Turn off power saving feature for USB wifi ([https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters](https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters))
          Modify ~/rtl8812au/Makefile : ```
replace CONFIG_POWER_SAVING = y with CONFIG_POWER_SAVING = n
```

3. The chipset of Amped Wireless UA230A is same as EW-7811UAC (i.e. rtl8812au). I found this from reading the file from windows drivers obtained from AmpedWireless.com support, you may verify. Also refer : [[SOLVED] Edimax EW-7811UAC Wireless Adapter Problems]("http://ubuntuforums.org/showthread.php?t=2259890")[INDENT]Modify the C code:
```
cd ~/rtl8812au
gedit os_dep/linux/usb_intf.c
```
At about line 288 add the line (in BOLD and big font face), make sure insert only in the section indicated, very important:
```
#ifdef CONFIG_RTL8812A
    /*=== Realtek demoboard ===*/
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x8812),.driver_info = RTL8812},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881A),.driver_info = RTL8812},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881B),.driver_info = RTL8812},/* Default ID */
    {USB_DEVICE(USB_VENDER_ID_REALTEK, 0x881C),.driver_info = RTL8812},/* Default ID */
    /*=== Customer ID ===*/
    {USB_DEVICE(0x7392, 0xA811),.driver_info = RTL8821}, /* Edimax - Edimax */
    {USB_DEVICE(0x7392, 0xA812),.driver_info = RTL8821}, /* Edimax - EW-7811UTC */
    [SIZE=3]**{USB_DEVICE(0x7392, 0xA813),.driver_info = RTL8821}, /* Amped Wireless UA230A */**[/SIZE]
    {USB_DEVICE(0x2001, 0x3314),.driver_info = RTL8821}, /* D-Link - Cameo */
    {USB_DEVICE(0x0846, 0x9052),.driver_info = RTL8821}, /* Netgear - A6100 */
```

[/INDENT]
 4. Now build / make the module (directory for running the terminal ~/rtl8812a) : 
                    ```
make
          sudo make install
          sudo modprobe 8812au
```

5.  Now for some reason on my kernel 3.19 it does not load at start up, so edit /etc/modules file and add the 8812au[INDENT]```
sudo gedit /etc/modules
```
add the following line: ```
8812au
```[/INDENT]

Thats it, also note that if you decide to move the device to another USB port or upgrade kernel, you have to run the above again but do the following before ([[ubuntu] auto modprobe startup]("http://ubuntuforums.org/showthread.php?t=783109")) :[INDENT]```
cd ~/rtl8812au
sudo make uninstall
make clean
sudo modprobe -r 8812au
```
make sure there is a line in the /etc/modules file that says "8812au" as noted above in step 3.
[/INDENT]

You will have to repeat the process every time there is a kernel upgrade; so please keep the same saved, you can also make a script file to automate the process, i have done so with .desktop file in ~/.local/share/applications folder. Kindly post feedback for others to improve upon. Thanks folks!

---

