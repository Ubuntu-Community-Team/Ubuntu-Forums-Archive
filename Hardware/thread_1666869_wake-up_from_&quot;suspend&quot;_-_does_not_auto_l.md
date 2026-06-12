---
title: "wake-up from &quot;suspend&quot; - does not auto load the DVB-T usb device"
date: 2011-01-14
forum: Hardware
---

### Post by 987a654 on 2011-01-14
When the system resumes from suspend, it does not reload the usb DVB-T module. I have to unplug it and plug it back in. 

and also the system waits for around a min or more to resume. It just sits idle with the following message on screen.

btusb_intr_complete: hci0 urb ed0f8700 failed to resubmit (1)

and some other times with the following message:

option: option_instat_callback: error -2

I checked the system log, it shows up as follows:

[47488.078005] dvb-usb: DigitalNow TinyTwin DVB-T Receiver successfully deinitialized and disconnected.

[47488.078454] btusb_intr_complete: hci0 urb ed0f8700 failed to resubmit (1)

[47488.079453] btusb_bulk_complete: hci0 urb ed0f8e80 failed to resubmit (1)

[47488.080464] btusb_bulk_complete: hci0 urb ed0f8300 failed to resubmit (1)

[47488.082776] option: option_instat_callback: error -2

I thought it had something to do with the modules. Added the following to /etc/modules 

#TV Tuner
dvb_usb_af9015

Did not make a difference.

How can I get the TV tuner to be loaded after resuming from suspend and why does the system wait for couple of minutes before resuming from wakeup?

---

### Post by 987a654 on 2011-01-14
bump.

---

### Post by 987a654 on 2011-01-14
bump.

Or did I post under the wrong section?

---

### Post by CJNZ2011 on 2011-09-15
I have this same problem.. any fix yet??
Very frustrating!

---

### Post by Toz on 2011-09-15
Welcome to the forums.

You can try suspending the module prior to suspend. Create a file called **/etc/pm/config.d/suspends**. The content of the file should be:
```
SUSPEND_MODULES=<name_of_module>
```

I'm not sure what the name of the module is (maybe dvb_usb_af9015?), but:
```
lsmod
```should help to identify it.

---

