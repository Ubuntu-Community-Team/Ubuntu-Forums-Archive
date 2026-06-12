---
title: "User access to USB"
date: 2011-02-01
forum: Hardware
---

### Post by linuxonbute on 2011-02-01
I am running Ububtu 10.04 kernel 2.6.32-27-generic #49-Ubuntu SMP on my laptop.

I am trying to use a Maxim ibutton which is a 1-wire device ( DG1921).
OWFS is a system which uses fuse to create a virtual file system. From this I can access the data held on the device and have written some python code to program it and read data held on it.
The problem is that it should be possible to use it as an ordinary user thus:
 /opt/owfs/bin/owfs -C -u -m /home/norman/1-wire 
This is through a DS2490 USB to Serial-1-wire adapter but even though I have tried all the suggestions here: [http://owfs.org/](http://owfs.org/) regarding udev and Fuse but none work. it only works if I launch it via sudo.
It was suggested that the kernel module was grabbing the device but running:
 /opt/owfs/bin/owfs -C -u -m /home/norman/1-wire --foreground --error_level=9 2>ow.log
with ds2490 loaded or not gives the following:

norman@norman-laptop:~$ cat ow.log 
CONNECT: owfs.c:main(123) fuse mount point: /home/norman/1-wire
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(75) Avahi support: libavahi-client loaded successfully
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(77) Avahi library function found: avahi_client_errno
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(78) Avahi library function found: avahi_client_free
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(79) Avahi library function found: avahi_client_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(80) Avahi library function found: avahi_client_get_domain_name
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(81) Avahi library function found: avahi_entry_group_add_service
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(82) Avahi library function found: avahi_entry_group_commit
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(83) Avahi library function found: avahi_entry_group_is_empty
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(84) Avahi library function found: avahi_entry_group_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(85) Avahi library function found: avahi_entry_group_reset
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(87) Avahi library function found: avahi_service_resolver_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(88) Avahi library function found: avahi_service_resolver_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(89) Avahi library function found: avahi_service_browser_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(90) Avahi library function found: avahi_service_browser_new
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(102) Avahi support: libavahi-common loaded successfully.
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(104) Avahi library function found: avahi_simple_poll_free
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(105) Avahi library function found: avahi_simple_poll_get
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(106) Avahi library function found: avahi_simple_poll_loop
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(107) Avahi library function found: avahi_simple_poll_new
  DEBUG: ow_avahi_link.c:OW_Load_avahi_library(108) Avahi library function found: avahi_simple_poll_quit
   DEBUG: ow_avahi_link.c:OW_Load_avahi_library(109) Avahi library function found: avahi_strerror
   CALL: ow_parsename.c:FS_ParsedName_anywhere(91) path=[]
  DEBUG: owlib.c:SetupTemperatureLimits(79) Globals temp limits 0C 100C (for simulated adapters)
 CONNECT: ow_usb_cycle.c:USB_next(68) Bus master found: 3:2
CONNECT: ow_usb_msg.c:DS9490_open(269) Failed to set configuration on USB DS9490 bus master at 3:2.
  DEBUG: ow_usb_msg.c:DS9490_open(290) Did not successfully open DS9490 3:2
 DEFAULT: owlib.c:SetupSingleInboundConnection(196) Cannot open USB bus master
DEFAULT: owlib.c:LibStart(54) No valid 1-wire buses found
  DEBUG: owfs.c:ow_exit(31) owfs: ow_exit(1)

but if ds2490 is loaded it works when run sudo 
I have tried all the methods on the owfs site to overcome this and a few others but none work.
Any suggestions as to what I can try?

---

### Post by linuxonbute on 2011-03-17
Well after a lot of experiments with syntax I now have it working so for anyone with this problem I include the rule I have here.

cat /etc/udev/rules.d/90-ds2490.rules 

SYSFS{idVendor}=="04fa", SYSFS{idProduct}=="2490", GROUP="ow", MODE="0664"

---

