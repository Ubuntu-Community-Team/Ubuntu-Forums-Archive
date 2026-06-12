---
title: "Occasionally refuses to hibernate"
date: 2008-11-30
forum: General Help
---

### Post by Aaron44126 on 2008-11-30
Hi, here's my latest question.  :-P

I'm using Ubuntu 8.10 on my laptop and when I try to "hibernate" it sometimes refuses to.  Here's the scenario...

 - I click on the "Hibernate" option from the power menu thing in the top right.  The screen goes blank and shortly after that, there is disk activity.
 - One of two things happens next.  Either the machine eventually powers off (successful hibernate), or the screen comes back with a prompt for me to enter my password and unlock the computer -- as if it had hibernated and resumed without ever powering the machine off.

If the machine successfully hibernates, I never have a problem turning it back on.  However, when it refuses to hibernate, making subsequent hibernate attempts doesn't ever seem to work.  I have to actually shut the machine down and restart it before hibernate will work again.


I read around some and found that a lot of people find uswsusp to work better than the pm-utils that Ubuntu uses by default.  So, I installed uswsusp and have the *same problem when using it*.  Sometimes when I invoke it, it works fine; sometimes, it gives me the "snapshotting system" message and then jumps back to where I was before invoking it (it does not go through the phase where it writes the snapshot to disk when it fails).

By the way, I've tried both the version of uswsusp in the Ubuntu repositories, and the newer one from Debian's sid repo.  Same problem on both.

I'm just looking for a reliable suspend or hibernate.  (Suspend is even more broken, so I'm leaving it alone for now; at least I never lose anything when hibernate fails because it never fails to resume, suspend sometimes fails to resume.)

Has anyone seen similar behavior and resolved it, or, does anyone know what I should check to determine what is causing the problem?
Thanks!

---

### Post by Aaron44126 on 2008-12-01
Here's a snippet from the syslog.  Looks like it does indeed hibernate and then immediately boots back up when some device fails to suspend.  Any insights?


Dec  1 16:09:27 KEI kernel: [20750.925927] PM: Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone (139516 pages freed)
Dec  1 16:09:27 KEI kernel: [20769.390182] PM: Freed 558064 kbytes in 18.46 seconds (30.23 MB/s)
Dec  1 16:09:27 KEI kernel: [20769.390185] Suspending console(s) (use no_console_suspend to debug)
Dec  1 16:09:27 KEI kernel: [20769.390839] sd 2:0:0:0: [sdb] Synchronizing SCSI cache
Dec  1 16:09:27 KEI kernel: [20769.592046] sd 0:0:0:0: [sda] Synchronizing SCSI cache
**Dec  1 16:09:27 KEI kernel: [20769.611299] hub 1-2:1.0: suspend error -16**
Dec  1 16:09:27 KEI bluetoothd[6159]: HCI dev 0 unregistered
Dec  1 16:09:28 KEI bluetoothd[6159]: Unregister path: /org/bluez/hci0
**Dec  1 16:09:28 KEI kernel: [20769.611301] pm_op(): usb_dev_freeze+0x0/0x20 [usbcore] returns -16**
Dec  1 16:09:28 KEI bluetoothd[6159]: HCI dev 0 registered
**Dec  1 16:09:28 KEI kernel: [20769.611343] PM: Device 1-2 failed to freeze: error -16**
Dec  1 16:09:28 KEI kernel: [20769.611469] sd 0:0:0:0: [sda] Starting disk
Dec  1 16:09:28 KEI kernel: [20769.639201] sd 2:0:0:0: [sdb] Starting disk
Dec  1 16:09:28 KEI kernel: [20769.656719] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec  1 16:09:28 KEI kernel: [20769.656744] PM: Device 1-2.1 failed to restore: error -19
Dec  1 16:09:28 KEI kernel: [20769.656752] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec  1 16:09:28 KEI kernel: [20769.656773] PM: Device 1-2.2 failed to restore: error -19
Dec  1 16:09:28 KEI kernel: [20769.656777] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec  1 16:09:28 KEI kernel: [20769.656797] PM: Device 1-2.3 failed to restore: error -19
Dec  1 16:09:28 KEI kernel: [20769.725487] PM: Image restored successfully.


Note: Appears to be the fault of the bluetooth adapter.  I'll see if I can add some stuff to the hibernate script to kill it before suspending...

---

### Post by munooka on 2008-12-21
Same here on a DELL M1330 it got worse with the latest kernel update (2.6.27-11-generic) an now refuses to hibernate:

Dec 21 00:20:59 tomato kernel: [45238.053652] hub 1-2:1.0: suspend error -16
Dec 21 00:20:59 tomato kernel: [45238.053656] pm_op(): usb_dev_freeze+0x0/0x20 [usbcore] returns -16
Dec 21 00:20:59 tomato kernel: [45238.053714] PM: Device 1-2 failed to freeze: error -16
Dec 21 00:20:59 tomato kernel: [45238.055065] sd 0:0:0:0: [sda] Starting disk
Dec 21 00:20:59 tomato kernel: [45238.067109] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec 21 00:20:59 tomato kernel: [45238.067169] PM: Device 1-2.1 failed to restore: error -19
Dec 21 00:20:59 tomato kernel: [45238.067189] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec 21 00:20:59 tomato kernel: [45238.067235] PM: Device 1-2.2 failed to restore: error -19
Dec 21 00:20:59 tomato kernel: [45238.067263] pm_op(): usb_dev_restore+0x0/0x10 [usbcore] returns -19
Dec 21 00:20:59 tomato kernel: [45238.067320] PM: Device 1-2.3 failed to restore: error -19

---

### Post by Aaron44126 on 2008-12-21
That kernel update hasn't been offered to me yet.  Did you get it from intrepid-proposed?

Workaround that works for me...

 - Visit your BIOS setup and make sure that it is set to have the wireless switch on your laptop also control the bluetooth.
 - Make sure you turn off the wireless switch before you hibernate.  (This actually causes the bluetooth controller, which is internally a USB device, to disconnect.)

I tried things like making the hibernate script stop bluetoothd, or unload the bluetooth kernel modules, I even tried blacklisting the bluetooth kernel modules, but none of that worked.  Still had the hibernate problem.

It's silly so of course I hope that we eventually see a proper fix.

---

### Post by kerry_s on 2008-12-21
try adding "pci=routeirq" to your boot line.
have you guys tried with the force switch?
sudo s2ram -f
sudo s2disk --force
sudo s2both --force

---

### Post by Aaron44126 on 2008-12-21
I will try both of these things and see how it goes.

I'll note that this problem happens for me both with Ubuntu's default pm-utils and with s2disk.  However, I've been using s2disk lately because it is so much faster.

---

