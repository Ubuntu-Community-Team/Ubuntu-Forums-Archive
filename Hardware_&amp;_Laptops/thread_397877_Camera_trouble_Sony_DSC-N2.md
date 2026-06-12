---
title: "Camera trouble Sony DSC-N2"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by jsgaarde on 2007-03-31
Hi there.
I have bougt a digital camera called Sony Cyber-Shot DSC-N2. I can't make ubuntu extract pictures from the device. When I have plugged it into the USB port I select either the "PictBridge" or "PTP" protocol on the camera and ubuntu pops up the import pictures dialog.
So far so good.
If PictBridge:
[LIST=1]
[*]The "Import pictures" dialog pops up emmidiately.
[*]The camera displayes "Enable Printer to connect" approximately 10 seconds after enabling PictBridge.
[*]Choosing "Import" from the import pictures dialog gives me the following error:
[/LIST]
```

An error occurred in the io-library ('Could not claim the USB device'):
Could not claim interface 0 (Operation not permitted). Make sure no other
program or kernel module (such as sdc2xx, stv680, spca50x) is using the
device and you have read/write access to the device.
```

If PTP:
[LIST=1]
[*]The "Import pictures" dialog pops up emmidiately.
[*]The camera displayes 4 red dots which become white after a few seconds.
[*]Choosing "Import" from the import pictures dialog gives me the same error as with PictBridge.
[/LIST]

What can be wrong? I don't have any trouble with other USB devices like memory sticks.
gphoto2 is installed.
I have tried on both Dapper and Edgy (not Feisty, since it is not in final release yet).

Is there anybody out there having this device working properly on ubuntu?

---

### Post by jsgaarde on 2007-03-31
Never mind - got it working. I used the last USB option "Mass Storage" and it worked perfectly!

---

### Post by Toadmund on 2007-03-31
The advice I followed was to go into system-->administration-->synaptic and downgrade
'libgphoto2-2' and libgphoto2-port0.

I then went into 'package' picked 'force download' I then picked the previous version.
Then (in 'package') I locked them both.

Force download and lock these files seperately, not both at once.

Worked for me.

---

### Post by warbread on 2007-04-07
> **Toadmund said:**
> The advice I followed was to go into system-->administration-->synaptic and downgrade
'libgphoto2-2' and libgphoto2-port0.

I then went into 'package' picked 'force download' I then picked the previous version.
Then (in 'package') I locked them both.

Force download and lock these files seperately, not both at once.  

Worked for me.

This worked for me on a PowerShot A510 in Edgy. Don't forget libgphoto2-2-dev, though.

---

