---
title: "HAL failed to start"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by mosestruong on 2007-01-04
Today, when I tried to start ubuntu, it took a long time to boot, and when it finally finished, I got a message that HAL failed to start.

I tried running restarting dbus using
```
sudo /etc/init.d/dbus restart
```

And I have three errors - 
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping NetworkManager dispatcher                                    [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping NetworkManager daemon                                        [ ok ] 
 * Stopping DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                                     
run-parts: /etc/dbus-1/event.d/20hal exited with return code 2
 * Starting DBUS aware dhcp client: dhcdbd                               [ ok ] 
 * Starting NetworkManager daemon                                        [ ok ] 
 * Starting NetworkManager dispatcher                                    [ ok ] 
 * Starting System Tools Backends system-tools-backends                         
run-parts: /etc/dbus-1/event.d/70system-tools-backends exited with return code 1


Does anyone know what might be causing this? and what solutions there might be? Thank you.

I'm currently running 6.10 edgy, Linux 2.6.17-10-generic #2 SMP i686 GNU/Linux

---

### Post by Tux Aubrey on 2007-01-04
I have had intermittent HAL problems and all have involved a USB device plugged in on boot.  It has usually gone away on the next boot or when I boot without the device plugged in.

I did see a movie once where HAL really gave this guy grief by not opening a door or something.  Can't really remember how he solved it (I was possibly on drugs).:-?

---

### Post by mosestruong on 2007-01-04
Thanks Tux for pointing out that. I had to remove my bluetooth usb dongle, and shutdown the computer and then boot it up again before HAL would work again, restarting the computer didn't do anything.

---

### Post by mosestruong on 2007-01-04
I'm getting this error whenever I do restart a computer.

It boots up normally if the computer was turned off first.

Also, I notice when I shutdown the computer, I sometimes get an error
[17179756.520000] smb_retry: no connection process

I can't remember changing any system/config stuff apart from doing the applying the regular update packages.

Does this have anything to do with it?

---

