---
title: "[SOLVED] Capture bad EIP values during boot"
date: 2008-12-15
forum: Hardware
---

### Post by carolinason on 2008-12-15
I'm receiving bad EIP values and stack traces during boot. The messages pass to quickly to read. I've looked in my log messages, but don't see these.

How can I captures these errors?

---

### Post by regala on 2008-12-15
> **carolinason said:**
> I'm receiving bad EIP values and stack traces during boot. The messages pass to quickly to read. I've looked in my log messages, but don't see these.

How can I captures these errors?

If boot completes, you can get these messages in the output of the command ```
dmesg
```.

---

### Post by carolinason on 2008-12-15
I do not see anything that indicates bad EIP value, stack trace or the output of a stack trace in the file /var/log/dmesg. Or any other log file for that matter.

---

### Post by regala on 2008-12-15
> **carolinason said:**
> I do not see anything that indicates bad EIP value, stack trace or the output of a stack trace in the file /var/log/dmesg. Or any other log file for that matter.

I said the COMMAND "dmesg"...

---

### Post by carolinason on 2008-12-17
Sorry, i must have been drinking. 

This worked thank you.

---

