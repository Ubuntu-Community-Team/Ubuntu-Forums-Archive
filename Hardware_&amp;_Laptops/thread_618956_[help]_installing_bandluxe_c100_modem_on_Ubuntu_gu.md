---
title: "[help] installing bandluxe c100 modem on Ubuntu gutsy"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by winon4 on 2007-11-21
Dear expert,
I have difficulty in installing bandluxe c100 modem on my ubuntu gutsy. I always got these error messages every time I plugged in the usb  cable :
[ 9044.648000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9046.928000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9049.204000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9051.480000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9053.756000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9056.032000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9058.312000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9060.588000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9062.864000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9065.140000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9
[ 9067.416000] usb 1-1: reset full speed USB device using uhci_hcd and
address 9

FYI, based on information that I got from bandrich I've add on linux-2.6.22.1/drivers/usb/storage/unusual_devs.h and also on linux-2.6.22.1/drivers/usb/serial/option.c these new information (without + ofcourse):

linux-2.6.22.1/drivers/usb/storage/unusual_devs.h and 

/* Patched by David Chiou <tkchiou@bandrich.com> */
UNUSUAL_DEV(  0x1A8D, 0x1002, 0x0000, 0x0000,
              "BandRich",
              "BandLuxe CDROM USB Device",
              US_SC_DEVICE, US_PR_DEVICE, NULL,
              US_FL_IGNORE_DEVICE ),
/* Reported by Leon Leong <upleong@bandrich.com> */
UNUSUAL_DEV(  0x1c15, 0x1002, 0x0000, 0x0000,
              "TeleWell",
              "TeleWell TW-3G+ virtual CDROM",
              US_SC_DEVICE, US_PR_DEVICE, NULL,
              US_FL_IGNORE_DEVICE ),
UNUSUAL_DEV(  0x1761, 0x1002, 0x0000, 0x0000,
              "RCG",
              "RCG FxSecure Key virtual CDROM",
              US_SC_DEVICE, US_PR_DEVICE, NULL,
              US_FL_IGNORE_DEVICE ),
UNUSUAL_DEV(  0x1186, 0x3e04, 0x0000, 0x0000,
              "D-Link",
              "DWM-652 virtual CDROM",
              US_SC_DEVICE, US_PR_DEVICE, NULL,
              US_FL_IGNORE_DEVICE ),


 linux-2.6.22.1/drivers/usb/serial/option.c

 /* Function prototypes */
+static int option_probe (struct usb_interface *interface, const struct usb_device_id *id);
 static int  option_open(struct usb_serial_port *port, struct file *filp);
 static void option_close(struct usb_serial_port *port, struct file *filp);
 static int  option_startup(struct usb_serial *serial);
@@ -118,6 +119,15 @@
 #define BANDRICH_PRODUCT_C100_1                    0x1002
 #define BANDRICH_PRODUCT_C100_2                    0x1003
 

+#define TELEWELL_VENDOR_ID                      0x1C15
+#define TELEWELL_PRODUCT_TW_3G_PLUS         0x1002
+
+#define RCG_VENDOR_ID                          0x1761
+#define RCG_PRODUCT_FXSECURE_KEY               0x1002
+
+#define DLINK_VENDOR_ID                              0x1186
+#define DLINK_PRODUCT_DWM_652                       0x3E04
+
 #define DELL_VENDOR_ID                                0x413C

  static struct usb_device_id option_ids[] = {
@@ -174,6 +184,9 @@
       { USB_DEVICE(ANYDATA_VENDOR_ID, ANYDATA_PRODUCT_ADU_500A) },
       { USB_DEVICE(BANDRICH_VENDOR_ID, BANDRICH_PRODUCT_C100_1) },
       { USB_DEVICE(BANDRICH_VENDOR_ID, BANDRICH_PRODUCT_C100_2) },
+      { USB_DEVICE(TELEWELL_VENDOR_ID, TELEWELL_PRODUCT_TW_3G_PLUS) },
+      { USB_DEVICE(RCG_VENDOR_ID, RCG_PRODUCT_FXSECURE_KEY) },
+      { USB_DEVICE(DLINK_VENDOR_ID, DLINK_PRODUCT_DWM_652) },
       { USB_DEVICE(DELL_VENDOR_ID, 0x8118) },         /* Dell Wireless 5510 Mobile Broadband HSDPA ExpressCard */
       { } /* Terminating entry */
 };

@@ -181,7 +194,7 @@
 static struct usb_driver option_driver = {
       .name       = "option",
-       .probe      = usb_serial_probe,
+      .probe      = option_probe,
       .disconnect = usb_serial_disconnect,
       .id_table   = option_ids,
       .no_dynamic_id =   1,

@@ -282,6 +295,66 @@
 module_init(option_init);
 module_exit(option_exit);

+/* Functions used by new usb-serial code. */
+static int option_probe (struct usb_interface *interface,
+                      const struct usb_device_id *id)
+{
+      struct usb_device *dev = interface_to_usbdev (interface);
+      int retval;
+
+      /* upleong */
+      /* Bandrich Bandluxe Series
+         Three devices for mode 0x1001
+         If#1 -> RRDM  If#2 -> Ethernet  If#3 -> Diag
+         Three devices for mode 0x1002
+         If#0 -> CDROM  If#1 -> Modem  If#2 -> Diag
+         Two devices for mode 0x1003
+         If#0 -> Modem  If#1 -> Diag
+      */
+
+      if (dev->descriptor.idVendor == BANDRICH_VENDOR_ID)
+      {
+          if (((dev->descriptor.idProduct == BANDRICH_PRODUCT_C100_1) &&
+              (interface == dev->actconfig->interface[0])) ||
+              ((dev->descriptor.idProduct == 0x1001) &&
+              (interface == dev->actconfig->interface[2])))
+          {
+              unlock_kernel();
+              return -ENODEV;
+          }
+      }
+      else if (dev->descriptor.idVendor == TELEWELL_VENDOR_ID)
+      {
+          if ((dev->descriptor.idProduct == TELEWELL_PRODUCT_TW_3G_PLUS) &&
+              (interface == dev->actconfig->interface[0]))
+          {
+              unlock_kernel();
+              return -ENODEV;
+          }
+      }
+      else if (dev->descriptor.idVendor == RCG_VENDOR_ID)
+      {
+          if ((dev->descriptor.idProduct == RCG_PRODUCT_FXSECURE_KEY) &&
+              (interface == dev->actconfig->interface[0]))
+          {
+              unlock_kernel();
+              return -ENODEV;
+          }
+      }
+      else if (dev->descriptor.idVendor == DLINK_VENDOR_ID)
+      {
+          if ((dev->descriptor.idProduct == DLINK_PRODUCT_DWM_652) &&
+              (interface == dev->actconfig->interface[0]))
+          {
+              unlock_kernel();
+              return -ENODEV;
+          }
+      }
+      retval = usb_serial_probe (interface, id);
+
+      return retval;
+}
+
 static void option_rx_throttle(struct usb_serial_port *port)
 {
       dbg("%s", __FUNCTION__);

kind regards,
-fuad-

---

### Post by worldbloke on 2007-11-29
I'm posting this from a Sony Vaio TZ-series laptop using a Bandrich C100 HSDPA modem (in the ExpressCard format). My kernel in Gutsy is 2.6.22-10 (so that hibernate works).

I was having similar problems to that mentioned above. After doing some websurfing, it looks like something to do with the simulated MMC-CDROM (??) device that holds the Windows drivers is interfering with the function of the simulated serial ports offered by the HSDPA modem.

My current, barely-working solution is to disable hal (!!) so that the usb storage offered by the card doesn't load or mount or something. Running "sudo /etc/init.d/hal stop" seems to do it. However, this is a very bad solution as it will probably break lots of other things. Incidentally, the problem recurs immediately the hal daemon is restarted, and the driver volume mounts.

We need to:
a) learn how to disable the autoload/automount of only the Windows drivers disk image so that people can use their expensive datamodems
b) identify the real culprit, because this shouldn't cause an issue, surely?

If I find out more, I will post.

---

### Post by worldbloke on 2007-12-08
After a week of living with a disabled hald (awful, just awful), some investigation has showed an acceptable way to fix the problem. I've tested this with both Linux 2.5.22-10-generic and 2.6.22-14-generic on Gutsy on a Sony Vaio TZ-170.

The problem is simply stated, the USB bus keeps getting reset by something higher up the dynamic device mounting tree when the Bandrich Bandluxe C100 is inserted, disabling the modem. Log messages like the following, every 2 seconds, seem to be a symptom:

```
Dec  8 18:34:48 hostname kernel: [  152.744000] usb 2-2: reset full speed USB device using uhci_hcd and address 2
```

Well before the problem eventuates, the udev system creates the devices /dev/ttyUSB0 and /dev/ttyUSB1. And just before the endlessly repeating message appears, the NetworkManager starts dealing with the simulated CD-ROM that is also contained in the modem.

Adding a file called /etc/hal/fdi/preprobe/10-bandrich-c100.fdi (I think you'll need to put it there with root privileges) with the following contents forces the dynamic device mounting software higher up the tree to ignore the fake CD-ROM on the modem, and the bus resets don't occur. Here's the file:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device> 
    <match key="usb.vendor_id" int="6797">
      <match key="usb.product_id" int="4096">
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

This very simple code simply instructs HAL to tell other software to ignore a device with vendor id (integer) 6797 and product id (integer) 4096. To get it working immediately just reset the DBUS system via ```
sudo /etc/init.d/dbus restart
```.

Hope this helps other people.

---

### Post by bv8ag on 2008-01-26
1) Open from the menu "System->Administration->Network"

2) Check the modem connection from "Network Settings->Connections->Modem connection"

3) Click the "Properties" for BandLuxe settings

3.1) In tab "General",
Check "Enable this conncetion"
Phone number: *99#
Fill in your username and password too... (if no username/pasword required, just type something which ubuntu does not allow a blank field)

3.2) In tab "Modem",
Type in the Modem port: /dev/ttyUSB1
(sometimes choose /dev/ttyUSB0)

3.3) in tab "Options",
Check "Set modem as default route to internet"
Check "Use the internet service provider namervers"
Check "Retry if the connection breaks or fails to start"

4) Ubuntu will do the connection automatically.

5) The Green (3G) or Blue (3.5G) led will lit on continuously if the connection is successfully connected
=============================================================
PS:
[COLOR="Red"]You have to umount Bandluxe CD and disable usb_storage first.[/COLOR]
#modprobe -r usb_storage

---

### Post by foxiness on 2008-03-22
it work fine on beta, but epiphany goes to "work offline"

---

### Post by Maha1980 on 2008-04-27
> **bv8ag said:**
> 1) Open from the menu "System->Administration->Network"

2) Check the modem connection from "Network Settings->Connections->Modem connection"

3) Click the "Properties" for BandLuxe settings

3.1) In tab "General",
Check "Enable this conncetion"
Phone number: *99#
Fill in your username and password too... (if no username/pasword required, just type something which ubuntu does not allow a blank field)

3.2) In tab "Modem",
Type in the Modem port: /dev/ttyUSB1
(sometimes choose /dev/ttyUSB0)

3.3) in tab "Options",
Check "Set modem as default route to internet"
Check "Use the internet service provider namervers"
Check "Retry if the connection breaks or fails to start"

4) Ubuntu will do the connection automatically.

5) The Green (3G) or Blue (3.5G) led will lit on continuously if the connection is successfully connected
=============================================================
PS:
[COLOR="Red"]You have to umount Bandluxe CD and disable usb_storage first.[/COLOR]
#modprobe -r usb_storage

i did all what you have done
but nothing
still red light
i'm using Dell inspiron 1525
Linux ubuntu 8.04

---

### Post by bv8ag on 2008-04-28
> **Maha1980 said:**
> i did all what you have done
but nothing
still red light
i'm using Dell inspiron 1525
Linux ubuntu 8.04
I have got a document from bandrich.com ,pls see attach file!!

---

### Post by arshadg on 2008-05-11
hi 
i was run configuration file what it does it cant show in my computer now where it shown before as a hard disk what do we do if i want to revert back to normal urgently reply request.thanks

Regards

---

### Post by Maha1980 on 2008-05-12
solution:

[http://marvinrebooted.wordpress.com/]("http://marvinrebooted.wordpress.com/")

---

