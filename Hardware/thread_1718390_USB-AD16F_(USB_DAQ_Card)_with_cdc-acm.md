---
title: "USB-AD16F (USB DAQ Card) with cdc-acm"
date: 2011-03-31
forum: Hardware
---

### Post by JSalzi on 2011-03-31
Hello

For a few days I have attempted to get this DAQ card running: [http://www.bmc-messsysteme.de/us/pr-usb-ad16f.html](http://www.bmc-messsysteme.de/us/pr-usb-ad16f.html)

The manufacturer has been unhelpful and have not provided any possible solutions. Below is a description of my system and the daq card. Below I have also included information regarding testing that I have performed and debug data.

I now have no idea what to try next. I would apperciate any suggestions...

Thanks!

- Ubuntu 10.04 LTS with 2.6.32-28-generic
- lsusb -v
> Bus 003 Device 003: ID 09ca:4132  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x09ca 
  idProduct          0x4132 
  bcdDevice            1.10
  iManufacturer           1 BMC Messsysteme GmbH
  iProduct                2 USB-BASE Analog/Digital I/O Board
  iSerial                 3 000605
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
- After plugging the card into my system dmesg:
> [   96.376146] usb 3-1: USB disconnect, address 2
[   98.912059] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   99.104455] usb 3-1: configuration #1 chosen from 1 choice
What the manual says:
> Under MAC OS X, FreeBSD and Linux, driver installation is not necessary.Some more infomation I found in the programmer manual from the library (sorry just in german):
> Das USB-AD bzw. die USB-PIO implementiert die CDC Klasse als ACM. Für diese Geräte bietet Linux einen entsprechenden Treiber an, so dass die Geräte direkt von Linux unterstützt werden, wenn das Kernel entsprechend konfiguriert ist.That means: The card implements the CDC class as ACM. For this type of hardware Linux has driver if the kernel is configured correctly.

What I have already tested:

1) Loaded cdc-acm via modprobe -> no effect
2) Loaded cdc-acm via modprobe and added new id with echo "0x09ca 0x4132" > /sys/bus/usb/drivers/cdc_acm/new_id -> dmesg:
> [  299.218265] usbcore: registered new interface driver cdc_acm
[  299.218410] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  300.325792] cdc_acm 3-1:1.0: Zero length descriptor references
[  300.332359] cdc_acm: probe of 3-1:1.0 failed with error -22
3) I downloaded the source for the kernel, edited the file cdc-acm.c and added the following to the usb_device_id acm_ids[] struct:
>     { USB_DEVICE(0x09ca, 0x4132), /* BMCM USB-AD16f */
    .driver_info = NO_UNION_NORMAL, /* has no union descriptor */
    },After rebooting with the new kernel dmesg:
> [   33.816090] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   34.012524] usb 3-1: configuration #1 chosen from 1 choice
[   34.032119] BUG: unable to handle kernel NULL pointer dereference at 00000004
[   34.036014] IP: [<f83edb37>] acm_probe+0xf7/0xbf0 [cdc_acm]
[   34.036014] *pde = 7f14e067 
[   34.036014] Oops: 0000 [#1] SMP 
[   34.036014] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/bInterfaceClass
[   34.036014] Modules linked in: cdc_acm(+) nfsd exportfs nfs lockd nfs_acl auth_rpcgss sunrpc dm_crypt hwmon_vid coretemp ppdev lp parport_pc serio_raw parport dm_raid45 xor fbcon tileblit font bitblit softcursor vga16fb vgastate i915 drm_kms_helper drm intel_agp r8169 i2c_algo_bit mii agpgart video output usbhid hid ramzswap xvmalloc lzo_decompress lzo_compress
[   34.077037] 
[   34.077037] Pid: 1106, comm: modprobe Not tainted (2.6.32-30-generic #59) 945GSE
[   34.077037] EIP: 0060:[<f83edb37>] EFLAGS: 00010246 CPU: 0
[   34.077037] EIP is at acm_probe+0xf7/0xbf0 [cdc_acm]
[   34.077037] EAX: f655e200 EBX: 00000000 ECX: 00000000 EDX: 00000000
[   34.077037] ESI: f6adc992 EDI: 00000000 EBP: f5f91e28 ESP: f5f91dc0
[   34.077037]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   34.077037] Process modprobe (pid: 1106, ti=f5f90000 task=f5f98000 task.ti=f5f90000)
[   34.077037] Stack:
[   34.077037]  f5f91e18 f5f91dd8 c0261934 f5f91e18 f6efeca8 f6efeca8 00000001 f5f91de8
[   34.077037] <0> c021df45 f5f91e18 f5f91e0c c026164b f5f91e18 f5f91e0c f5f91e08 00000010
[   34.077037] <0> f66cf864 f66cf800 f5f91e00 00000000 f655e200 00000001 f655e200 f655e200
[   34.077037] Call Trace:
[   34.077037]  [<c0261934>] ? __sysfs_add_one+0x24/0xc0
[   34.077037]  [<c021df45>] ? iput+0x25/0x60
[   34.077037]  [<c026164b>] ? sysfs_addrm_finish+0x3b/0xf0
[   34.077037]  [<c044d460>] ? usb_probe_interface+0xc0/0x180
[   34.077037]  [<c0261f37>] ? sysfs_create_link+0x17/0x20
[   34.077037]  [<c03e967d>] ? really_probe+0x4d/0x140
[   34.077037]  [<c03eff8e>] ? pm_runtime_barrier+0x4e/0xc0
[   34.077037]  [<c03e97ac>] ? driver_probe_device+0x3c/0x60
[   34.077037]  [<c03e9851>] ? __driver_attach+0x81/0x90
[   34.077037]  [<c03e8c93>] ? bus_for_each_dev+0x53/0x80
[   34.077037]  [<c03e954e>] ? driver_attach+0x1e/0x20
[   34.077037]  [<c03e97d0>] ? __driver_attach+0x0/0x90
[   34.077037]  [<c03e8f15>] ? bus_add_driver+0xd5/0x280
[   34.077037]  [<c03e9b4a>] ? driver_register+0x6a/0x130
[   34.077037]  [<c044d201>] ? usb_register_driver+0x81/0xf0
[   34.077037]  [<c03b7512>] ? tty_register_driver+0xf2/0x1c0
[   34.077037]  [<c03b78d1>] ? alloc_tty_driver+0x51/0x70
[   34.077037]  [<f855d0a1>] ? acm_init+0xa1/0xd0 [cdc_acm]
[   34.077037]  [<c0101131>] ? do_one_initcall+0x31/0x190
[   34.077037]  [<f855d000>] ? acm_init+0x0/0xd0 [cdc_acm]
[   34.077037]  [<c0182f50>] ? sys_init_module+0xb0/0x210
[   34.077037]  [<c01033ec>] ? syscall_call+0x7/0xb
[   34.077037]  [<c0590000>] ? do_general_protection+0x10/0x170
[   34.077037] Code: 7f cb 85 db 0f 85 f2 01 00 00 85 d2 0f 8e 5b 01 00 00 8b 45 dc e8 da 41 05 c8 8b 55 f0 89 55 e8 89 c3 39 5d e8 0f 84 5b 05 00 00 <8b> 43 04 80 78 05 0a 0f 84 e4 00 00 00 8b 4d e8 8b 41 04 80 78 
[   34.077037] EIP: [<f83edb37>] acm_probe+0xf7/0xbf0 [cdc_acm] SS:ESP 0068:f5f91dc0
[   34.077037] CR2: 0000000000000004
[   34.077968] ---[ end trace b556f2e3186523a5 ]---


---

### Post by tekguru123 on 2011-09-13
Instead of going through all the trouble with your current daq card, just purchase a USD DAQ system from Futek Instruments. Their products are really easy to use. It comes with their own program, but if want to use another program, they will provide the drivers. Browse through their USB DAQ products at [www.futekinst.com](www.futekinst.com), they have a lot. But if you are looking for something more specific, they will design one for you.

---

### Post by bmcm support on 2013-04-11
Hello JSalzi,

unfortunately I have received this thread so late ...

As far as I know it should work without any hazzle if there are some minor things in mind ... login as "root" and do check the rights ...
Please read the manual every line ... we are not able to provide the complete path for all linux, unix, ubuntu, kernels ...

If you read the [manual]("http://www.bmcm.de/us/dld.php?action=getdld&fileid=UM-LIBAD4&version=4.5&lang=en") (Libad) very carefully you will recognize the sytem is not named "USB-AD16f" ... it has to be called "usbbase" ...

Please refer the (german) forum: [Ubuntuusers]("http://forum.ubuntuusers.de/post/2650735")  ... summary: "everythings works well"    :)

So please think about *unhelpful* and let me know or resend your hotline request by email to [EMAIL="hotline@bmcm.de"]hotline@bmcm.de[/EMAIL]

BR
Frank

---

### Post by JSalzi on 2013-04-12
Hi Frank

> **bmcm support said:**
> 
So please think about *unhelpful* and let me know or resend your hotline request by email to [EMAIL="hotline@bmcm.de"]hotline@bmcm.de[/EMAIL]
Frank

You're right, I have received an answer after more than 2 years. I really have to think about *unhelpful* support ;-)
Just kidding... I can't remember exactly what the problem was, I no longer work in this project (not even for that company). The only thing I can say is that it worked somehow in the end. Maybe I got help from your technical support - maybe not. I can't say that after 2 years.

JSalzi

---

