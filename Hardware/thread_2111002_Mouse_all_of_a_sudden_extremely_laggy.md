---
title: "Mouse all of a sudden extremely laggy"
date: 2013-01-31
forum: Hardware
---

### Post by Katjing on 2013-01-31
Hello, I am new to Ubuntu in general and especially this forum and I hope I go about this the right way...

I installed Ubuntu 12.10 yesterday and I'm having some issues with my mouse and I have no idea how to determine whats wrong. The problem is that, after a while (seems totally arbitrarily), the mouse pointer starts to behave extremely laggy while, as far as I can tell, everything else works fine. System monitor says that CPU load is around zero and memory usage about 1 GB (with 5 more to spare). No process looks weird to me.

The mouse is a logitech mx518. A reboot seems to resolve the problem until it occurs again without warning. Unplugging and replugging the mouse does not help.

I am very grateful for any help resolving this. I do not know if there is any other information that I can share with you, but if you let me know I will be happy to provide!

---

### Post by Katjing on 2013-01-31
Ok, so I just remembered that I have a wireless keyboard that also came with a mouse that I sometimes use as a remote, and while both mice seem to work fine together after a reboot, I took the battery out of the wireless one. I will report back whether this helps or not when I have had opportunity to test it thoroughly.

---

### Post by Katjing on 2013-02-01
Ok, so removing the battery from the wireless mouse did not help. I am now completely clueless and would deeply appreciate any help.

---

### Post by varunendra on 2013-02-03
First of all, welcome to the forums Katjing! :)

About the problem -
> **Katjing said:**
> I took the battery out of the wireless one.
Why did you do that? Were you suspecting the wireless one was conflicting with the mx518? And how is the performance with the wireless one if you use it alone?

Assuming the mx518 is usb mouse, please post outputs of (while it is plugged) -
```
usb-devices
xinput
lsmod
```

And as soon as it starts lagging, enter (in a terminal)-
```
dmesg | tail -20
cat /var/log/syslog | tail -20
```
and post back their outputs.

Don't forget to wrap the outputs in code tags while posting them (see the link in my signature for an example)

---

### Post by Katjing on 2013-02-06
> **varunendra said:**
> First of all, welcome to the forums Katjing! :)

About the problem -

Why did you do that? Were you suspecting the wireless one was conflicting with the mx518? And how is the performance with the wireless one if you use it alone?

Assuming the mx518 is usb mouse, please post outputs of (while it is plugged) -
```
usb-devices
xinput
lsmod
```

And as soon as it starts lagging, enter (in a terminal)-
```
dmesg | tail -20
cat /var/log/syslog | tail -20
```
and post back their outputs.

Don't forget to wrap the outputs in code tags while posting them (see the link in my signature for an example)
Thank you for your help!

Yes, I was suspecting a conflict.

Anyway, in my desperation I did a clean install of ubuntu 12.04 (downgrade), and since then everything has worked like a charm.

---

