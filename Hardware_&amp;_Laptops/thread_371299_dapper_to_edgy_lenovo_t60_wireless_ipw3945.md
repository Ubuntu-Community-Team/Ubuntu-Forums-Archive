---
title: "dapper to edgy lenovo t60 wireless ipw3945"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by zevatron on 2007-02-26
After upgrading my T60 Thinkpad I find that everything works except my wireless card. The traditional Fn-F5 combo (which used to turn on/off the card) does nothing. To be precise, it doesn't turn on the card, but it does do this:

~ > tail /var/log/acpid
 [Mon Feb 26 18:50:55 2007] action exited with status 0
[Mon Feb 26 18:50:55 2007] completed event "ibm/hotkey HKEY 00000080 00001005"
[Mon Feb 26 19:23:12 2007] received event "ibm/hotkey HKEY 00000080 00001005"
[Mon Feb 26 19:23:12 2007] notifying client 4245[0:0]
[Mon Feb 26 19:23:12 2007] notifying client 4404[108:108]
[Mon Feb 26 19:23:12 2007] executing action "/etc/acpi/ibm-wireless.sh"
[Mon Feb 26 19:23:12 2007] BEGIN HANDLER MESSAGES
[Mon Feb 26 19:23:12 2007] END HANDLER MESSAGES
[Mon Feb 26 19:23:12 2007] action exited with status 0
[Mon Feb 26 19:23:12 2007] completed event "ibm/hotkey HKEY 00000080 00001005"

I've searched the forums and have network-manager installed as well linux-restricted-modules.
I can see the hardware as well:

~ > lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

and this is my kernel:

~ > uname -a
Linux kerouac 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

It's been this  ](*,)  all day so any help would be appreciated.

Cheers.

---

### Post by racmar on 2007-03-13
a rather late reply, but...

I have a t60 and there is a small wireless on/off switch on the lower portion of the laptop.   It is located just below the touchpad and to the left.  For any wireless to work, you should see the green sticker ( switch pushed to the right ).  I'm sure you've already fixed your problem, but maybe someone else will benefit.

---

