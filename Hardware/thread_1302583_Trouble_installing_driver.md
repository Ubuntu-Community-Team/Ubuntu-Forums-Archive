---
title: "Trouble installing driver"
date: 2009-10-27
forum: Hardware
---

### Post by vdtdriver on 2009-10-27
I have the ESD usb driver.  They provide some source code and some precompile objects for the driver.  I have successfully installed
the driver on Ubuntu 9.04 and RHEL 4.4.  I have a Dell Latitude E5400
that also has Ubuntu 9.04.  When I do:

sudo modprobe esdcan-usb331 

I get the following in dmesg:
(paraphrasing because I am too  lazy to post from machine that has problem)
[..] esdcan_usb331: Unknown symbol usb_register_driver
unknown symbols include usb_bulk_msg, usb_submit_urb, usb_deregister,
usb_string, usb_kill_urb, usb_buffer_free, usb_buffer_alloc, usb_alloc_urb, 
usb_free_urb

This are all from the usb_core directory.
Using grep on /proc/kallsyms I get stuff like this
c03b8ce0 T usb_alloc_urb
c03b73e0 T usb_resister_driver.

With it being a core built in feature and the symbols showing up in
/proc/kallsyms leads me to believe there shouldn't be a problem.
I am guessing I am just missing one step someplace.

---

