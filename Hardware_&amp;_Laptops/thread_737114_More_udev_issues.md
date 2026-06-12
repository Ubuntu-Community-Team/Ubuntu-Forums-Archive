---
title: "More udev issues"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by revoohc on 2008-03-27
I am having issues with Udev taking up a lot of cpu issues.  I have noticed this especially when I plug my blackberry in to charge.  Udev is taking 60%+ of the cpu.

I do not have evms installed, so that is not the issue in this case.  

I have noticed that /var/log/syslog, /var/log/debug, and /var/log/daemon.log start to grow quite quickly.


Thanks for any help with this issue:

Chris


Here are the contents of the files:

/var/log/syslog:

Mar 27 10:15:22 choover-laptop NetworkManager: <debug> [1206627322.017648] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:22 choover-laptop NetworkManager: <debug> [1206627322.140898] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:22 choover-laptop NetworkManager: <debug> [1206627322.944394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:23 choover-laptop NetworkManager: <debug> [1206627323.078289] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:24 choover-laptop NetworkManager: <debug> [1206627324.029094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:24 choover-laptop NetworkManager: <debug> [1206627324.124607] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').


/var/log/daemon.log
Mar 27 10:15:51 choover-laptop NetworkManager: <debug> [1206627351.642011] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:51 choover-laptop NetworkManager: <debug> [1206627351.732705] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:52 choover-laptop NetworkManager: <debug> [1206627352.582861] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:52 choover-laptop NetworkManager: <debug> [1206627352.652806] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:53 choover-laptop NetworkManager: <debug> [1206627353.496601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:15:53 choover-laptop NetworkManager: <debug> [1206627353.569263] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').


/var/log/debug:
Mar 27 10:16:10 choover-laptop NetworkManager: <debug> [1206627370.921262] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:11 choover-laptop NetworkManager: <debug> [1206627371.028569] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:11 choover-laptop NetworkManager: <debug> [1206627371.857043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:11 choover-laptop NetworkManager: <debug> [1206627371.944690] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:12 choover-laptop NetworkManager: <debug> [1206627372.782531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:12 choover-laptop NetworkManager: <debug> [1206627372.874648] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').
Mar 27 10:16:13 choover-laptop NetworkManager: <debug> [1206627373.630466] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0').

---

