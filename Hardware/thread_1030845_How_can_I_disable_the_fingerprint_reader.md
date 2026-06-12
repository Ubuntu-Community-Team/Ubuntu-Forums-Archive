---
title: "How can I disable the fingerprint reader?"
date: 2009-01-04
forum: Hardware
---

### Post by coverup1128 on 2009-01-04
How can I disable the fingerprint reader? My laptop runs much hotter under Ubuntu than Mandriva and or Windows XP, and the battery time is at least 30 min less. I suspect the fingerprint is a culprit, since it does not work under Mandriva. In Ubuntu, the fingerprint reader is always on - even when the laptop is suspended. 

By the way, the laptop is ThinkPad T61.

---

### Post by coverup1128 on 2009-01-05
bump? I'd really like to disable the fingerprint scanner for good.

---

### Post by cefn on 2009-01-31
Me too. This is what powertop reports when I'm trying to optimise my battery life...

Top causes for wakeups:
  47.0% (133.0)       <interrupt> : uhci_hcd:usb3, wifi0 
  33.3% ( 94.3)           firefox : futex_wait (hrtimer_wakeup) 
   8.8% ( 24.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   2.1% (  6.0)       <interrupt> : ata_piix
   2.1% (  5.9)   gnome-system-mo : schedule_timeout (process_timeout)
   1.4% (  4.1)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)

A USB device is active 100.0% of the time:
/sys/bus/usb/devices/3-2

Which tells me that my AES2501 on Hub 3 Port 2 is causing more power usage than firefox, and I don't even use the fingerprint reader!

I don't have an answer yet, but I'll let you know if I find one.

---

### Post by sarah.fauzia on 2009-02-02
I'd also like to know how to do the same, for a slightly different reason: sometimes my fingerprint works on boot-up, and sometimes it doesn't. Frankly, it's annoying, it uses battery power, and I don't need it. I have a Thinkpad X61t, and I'm running Arch Linux (but I had the same problem when I used Ubuntu). I'll keep looking for an answer! :)

---

### Post by coverup1128 on 2009-02-04
> **cefn said:**
> Me too. This is what powertop reports when I'm trying to optimise my battery life...

Top causes for wakeups:
  47.0% (133.0)       <interrupt> : uhci_hcd:usb3, wifi0 
  33.3% ( 94.3)           firefox : futex_wait (hrtimer_wakeup) 
   8.8% ( 24.9)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   2.1% (  6.0)       <interrupt> : ata_piix
   2.1% (  5.9)   gnome-system-mo : schedule_timeout (process_timeout)
   1.4% (  4.1)   <kernel module> : usb_hcd_poll_rh_status (rh_timer_func)

A USB device is active 100.0% of the time:
/sys/bus/usb/devices/3-2

Which tells me that my AES2501 on Hub 3 Port 2 is causing more power usage than firefox, and I don't even use the fingerprint reader!

I don't have an answer yet, but I'll let you know if I find one.

You seem to be more knowledgeable than me :)... Do you know which kernel module fingerprint scanner use? We could try unloading/blacklisting it.

---

### Post by brunjes on 2009-06-19
> **coverup1128 said:**
> You seem to be more knowledgeable than me :)... Do you know which kernel module fingerprint scanner use? We could try unloading/blacklisting it.

I too am looking for a way to completely disable the fingerprint reader under Jaunty. There must be a way but my googles have come up with nothing on disabling it.

Anyone??

Thanks,

Roy

---

### Post by earthtux on 2009-07-17
fingerprint scanner is pretty cool at the beginning, 
but now it is not as sensitive as it was.
The worse thing is that if I type my password to login (instead of using fingerprint), I cannot login(yes, I am sure I typed the right password, cause it works when I use sudo)
Now I really want to shut it off!
Anyone can help please?
thanks!

---

### Post by ellankavi on 2010-07-19
Hi,

Hope yo have already figured it by now... But if not, maybe this helps...

Type 'lsusb' to see the usb ports that are active currently.. 
Look for the field that says Fingerprint reader and note the bus number and the device number
Go to /dev/bus/usb/<bus number>
remove the device number corresp to the Fingerprint reader.

Check using 'lsusb' to see if the port is still powered.. Should be off now.

I think this could be a solution.. If not, let me know :)

---

