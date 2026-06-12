---
title: "Trying to get a signal from an AD converter."
date: 2009-06-06
forum: Hardware
---

### Post by kapok on 2009-06-06
I have a DATAQ DI-158U AD converter. I checked all of the system sources, hardware listing, etc., and I can not even get the device to appear. If anyone has any idea on how to communicate with the device, I'm sure I can take it from there.

---

### Post by ddrichardson on 2009-06-06
Reading through the manual for this equipment, I'm not sure if you can. The manual discusses Windows software and licensing to enable the device.

Does dmesg recognise it when it's plugged in?

---

### Post by kapok on 2009-06-06
It does not.

---

### Post by ddrichardson on 2009-06-06
I take it neither does lsusb?

---

### Post by kapok on 2009-06-07
Nope. Which is very strange; this thing is constantly sending data. You would think the computer would at least recognize it's signal.

---

### Post by ddrichardson on 2009-06-07
I've never had one that wasn't serial, however dealing with the timing was always an issue.

Have you tried pinging the company an email? They mightn't support Linux but might point you to a mailing list or forum they know of.

---

### Post by kapok on 2009-06-11
They have a 'Linux' section of their forums, but it has very little information and nothing that helps.

As for the e-mail, it is pending now...

---

