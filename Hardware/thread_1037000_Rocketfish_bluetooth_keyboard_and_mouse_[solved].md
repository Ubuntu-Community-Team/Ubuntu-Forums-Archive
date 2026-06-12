---
title: "Rocketfish bluetooth keyboard and mouse [solved]"
date: 2009-01-11
forum: Hardware
---

### Post by 7xs on 2009-01-11
A lot of folks have difficulties with switching this mouse/keyboard from HID to HIC (e.g. no scroll support in HID). I found that the following changes to the bluez driver and kernel module seem to solve the problem:

1. Extract the kernel module hci_usb.c (2.6.27-9) and add the following line:

{ USB_DEVICE(0x0a5c, 0x2120), .driver_info = HCI_RESET | HCI_WRONG_SCO_MTU }

to the structure defined by
static struct usb_device_id blacklist_ids[] = {

add the following lines to the makefile:

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

and compile and load the new module.

This resets the USB dongle to HCI model.

(This step may not be necessary but it is likely to help).

2. Download the bluez driver and look for the hid2hci.c utility in the tools directory.

add the following 3 lines:

{ HID, 0x0a5c, 0x2120, switch_dell   },	/* Rocketfish */
{ HCI, 0x0a5c, 0x4502, switch_dell   },	/* Rocketfish */
{ HCI, 0x0a5c, 0x4503, switch_dell   },	/* Rocketfish */

to the structure defined by:
static struct device_id device_list[] = {

recompile using "make hid2hci" (make sure you have the usb libraries). You might have to add -lusb at the linking stage and remove the following lines to compile:

#ifdef NEED_USB_GET_BUSSES
static inline struct usb_bus *usb_get_busses(void)
{
        return usb_busses;
}
#endif

Now, to switch your rocketfish from hid mode to hci mode:

simply type:
 
sudo hid2hci

Hope this helps. I realize that these are very sparse information but that's all I have time for now. If there is interest, I can give more step by step instructions. If this is confirmed to work, I will ask the bluez developers to incorporate these changes the bluez code.

---

### Post by pradeep.sawlani on 2009-03-15
Thanks for this information. I got my rocketfish keyboard and mouse(with rocketfish dongle/BCM2045B3 chip) working on ubuntu 8.10 after following your instructions with some modification for eg hci_usb.c is replaced by btusb.c in 2.6.27. Let me know if you need any information.

---

### Post by slayr007 on 2009-04-13
where do u go to extract it? i am in Ubu 9.04 beta version

---

### Post by pradeep.sawlani on 2009-05-06
I extracted the kernel module from ubuntu kernel

---

### Post by maybememe on 2009-07-14
Could you please please please give a more detailed how to?
I am compotent with computer, just never done anything like modify the kernnel before, and really want the scroll wheel , et al to work!

---

### Post by 7xs on 2009-08-03
On Ubuntu, do the following to get the kernel source:

sudo apt-get install linux-source

cd to your home directory and issue the following command:

tar jxf /usr/src/linux-source-2.6.27.tar.bz2 linux-source-2.6.27/drivers/bluetooth/

then

cd linux-source-2.6.27/drivers/bluetooth/

you should now see the file btusb.c in the directory

edit this file with any editor and add the following line:
	{ USB_DEVICE(0x0a5c, 0x2120), .driver_info = BTUSB_RESET | BTUSB_WRONG_SCO_MTU },

as described in my first post.

Edit the Makefile in the same directory as described in my first post (remember that the indentation must be done using a tab and not spaces for the makefile to work.

type make and you should find a new version of btusb.ko

Install it by typing:

sudo cp btusb.ko /lib/modules/2.6.27-14-generic/kernel/drivers/bluetooth/

This will overwrite the old one. You may want to keep a copy first.

stop bluetooth by typing:

sudo /etc/init.d/bluetooth stop

remove the old module:

sudo /sbin/modprobe -r btusb

Install the new module:

sudo /sbin/modprobe btusb

start bluetooth:

/etc/init.d/bluetooth start

and you should be ready to go.

Your last step is to pair the mouse and keyboard.

---

### Post by 7xs on 2009-08-03
One more thing, your makefile should look like this:

#
# Makefile for the Linux Bluetooth HCI device drivers.
#

obj-$(CONFIG_BT_HCIUSB)		+= hci_usb.o
obj-$(CONFIG_BT_HCIVHCI)	+= hci_vhci.o
obj-$(CONFIG_BT_HCIUART)	+= hci_uart.o
obj-$(CONFIG_BT_HCIBCM203X)	+= bcm203x.o
obj-$(CONFIG_BT_HCIBPA10X)	+= bpa10x.o
obj-$(CONFIG_BT_HCIBFUSB)	+= bfusb.o
obj-$(CONFIG_BT_HCIDTL1)	+= dtl1_cs.o
obj-$(CONFIG_BT_HCIBT3C)	+= bt3c_cs.o
obj-$(CONFIG_BT_HCIBLUECARD)	+= bluecard_cs.o
obj-$(CONFIG_BT_HCIBTUART)	+= btuart_cs.o

obj-$(CONFIG_BT_HCIBTUSB)	+= btusb.o
obj-$(CONFIG_BT_HCIBTSDIO)	+= btsdio.o

hci_uart-y				:= hci_ldisc.o
hci_uart-$(CONFIG_BT_HCIUART_H4)	+= hci_h4.o
hci_uart-$(CONFIG_BT_HCIUART_BCSP)	+= hci_bcsp.o
hci_uart-$(CONFIG_BT_HCIUART_LL)	+= hci_ll.o
hci_uart-objs				:= $(hci_uart-y)

all:
<TAB>make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
<TAB>make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

and remember to use a tab just before the "make -C /lib/...." lines.


and the btusb.c file should look like this:

static struct usb_device_id blacklist_table[] = {
        /* CSR BlueCore devices */
        { USB_DEVICE(0x0a12, 0x0001), .driver_info = BTUSB_CSR },

        /* Broadcom BCM2033 without firmware */
        { USB_DEVICE(0x0a5c, 0x2033), .driver_info = BTUSB_IGNORE },

        /* Broadcom BCM2035 */
        { USB_DEVICE(0x0a5c, 0x2035), .driver_info = BTUSB_RESET | BTUSB_WRONG_S
        { USB_DEVICE(0x0a5c, 0x200a), .driver_info = BTUSB_RESET | BTUSB_WRONG_S

(...)
        [COLOR="Red"]/* Broadcom BCM2120 */
        { USB_DEVICE(0x0a5c, 0x2120), .driver_info = BTUSB_RESET | BTUSB_WRONG_S
[/COLOR]        /* ANYCOM Bluetooth USB-200 and USB-250 */
        { USB_DEVICE(0x0a5c, 0x2111), .driver_info = BTUSB_RESET },

        /* HP laptop with Broadcom chip */
        { USB_DEVICE(0x03f0, 0x171d), .driver_info = BTUSB_RESET | BTUSB_WRONG_S

(...)

---

### Post by keyset on 2009-10-25
When I try the Make command, I'm not getting the btusb.ko file. When I try make btusk.c -B to force, it tells me "make: Nothing to be done for `btusb.c'." Help?

---

### Post by PRoPAiN! on 2011-04-26
Ok, bad form bumping an ancient thread and all, but here goes anyways.

Solution ITT worked for me on Maverick, with one snag: ran into an error about BTUSB_RESET not being defined.  Googled it, found it should be defined as 0x02, so just replaced it w/ that and all was right with the world (except the modifier key issue).

---

