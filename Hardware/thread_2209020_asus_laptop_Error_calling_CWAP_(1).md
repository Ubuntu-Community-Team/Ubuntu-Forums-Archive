---
title: "asus_laptop: Error calling CWAP (1)"
date: 2014-03-03
forum: Hardware
---

### Post by balubeto on 2014-03-03
Hi
 
I installed Lubuntu 13.10 32-bit. 

During the starting up, the "asus_laptop: Error calling CWAP (1)" error is displayed. How come? How do I fix it?
 
Thanks
 
Bye

---

### Post by phidia on 2014-03-04
Copy pasting this from an earlier thread at the forums: 

"The error message comes from line 1456 of asus-laptop.c when write_acpi_int(asus->handle, "CWAP", wapf) returns a non-zero acpi status. That can happen from an invalid handle or the acpi_evaluate_object call.

wapf is related to Fn+Fx key controlling WLAN. The comments indicate that the function needs to be called for some laptops to initialize properly. My Fn+F2 toggles my WLAN properly, so I'm not going to worry about the error anymore..."

See if that is true for your laptop.

---

### Post by balubeto on 2014-03-05
> **phidia said:**
> Copy pasting this from an earlier thread at the forums: 

"The error message comes from line 1456 of asus-laptop.c when write_acpi_int(asus->handle, "CWAP", wapf) returns a non-zero acpi status. That can happen from an invalid handle or the acpi_evaluate_object call.

wapf is related to Fn+Fx key controlling WLAN. The comments indicate that the function needs to be called for some laptops to initialize properly. My Fn+F2 toggles my WLAN properly, so I'm not going to worry about the error anymore..."

See if that is true for your laptop.

This is true.

So, how do I have to do to solve this error during the startup of Lubuntu?

Thanks

Bye

---

### Post by phidia on 2014-03-05
> Fn+F2 toggles my WLAN properly, so I'm not going to worry about the error anymore..."

Use those keys to turn your wireless card on and the error should not appear.

---

### Post by balubeto on 2014-03-07
> **phidia said:**
> Use those keys to turn your wireless card on and the error should not appear.

Since from the **sudo lspci** command I get:
> 
00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


I installed the firmware-b43-installer package to properly recognize this chip. Right?

If so, how do I configure it to make sure that the "asus_laptop: Error calling CWAP (1)" error is no more displayed during the startup of Lubuntu 13.10?

Thanks

Bye

---

### Post by varunendra on 2014-03-07
If you don't have any problems in the functioning of the system, you can safely ignore the message. Most such messages are just debugging information and are not necessarily harmful.

So, if you have a problem, please tell us what it is.

If it is just that you are worried about the error message, while everything on the installation is working properly, just ignore the message, unless you want to go into unnecessary mess of downloading the driver's source-code > find the line(s) and modify it > compile > install manually ( > and possibly be ready for a new error caused due to this).

---

