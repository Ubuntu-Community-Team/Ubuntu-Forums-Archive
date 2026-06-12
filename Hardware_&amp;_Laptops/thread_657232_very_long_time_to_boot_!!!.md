---
title: "very long time to boot !!!"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by M.Abdullah on 2008-01-03
Hi all

I've laptop ACER 5600 with camera. When i boot from ubuntu 7.10 it take 5 minutes to boot.

This is the error message.

```
[ 2118.856000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[ 2119.068000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
```

I don't care about camera, actually i don't use it.

So how can i tell kernel to ignored camera and doesn't tried to configure it ?

---

### Post by evil316 on 2008-01-03
Are you sure this error is what is taking so long to boot?  My wife has an Acer laptop and it took a long time to boot and I just removed the spash screen and that fixed it.  Hit F2 during boot and see if it boots faster that way.

---

### Post by frankos44 on 2008-01-03
Does it display the splash screen during boot?

---

### Post by M.Abdullah on 2008-01-03
evil316:
yes, i am. after boot i type dmesg and i found this messages repeated:

```

[ 1030.640000] gspca: probe of 5-6:1.0 failed with error -5
[ 1030.640000] usb 5-6: USB disconnect, address 67
[ 1030.912000] usb 5-6: new high speed USB device using ehci_hcd and address 68
[ 1031.068000] usb 5-6: configuration #1 chosen from 1 choice
[ 1031.068000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321)

```

it's same thing when i press F2.


frankos44:

yes it does. the system looks like hang, after few minutes i can see login screen.

i tried to boot without quiet splash parameters but nothing different.

what can i do?

---

### Post by evil316 on 2008-01-03
> **M.Abdullah said:**
> 

So how can i tell kernel to ignored camera and doesn't tried to configure it ?

I'm not sure how you do that.  I'd do some googling for it.  I imagine you will have to recompile the kernel though.  Is there anything in your bios where you can turn the camera off?

---

### Post by frankos44 on 2008-01-05
I had a slow boot problem on a laptop and it was due to screen resolution being set incorrectly in usplash.conf. In my case I could not see the splash screen but its worth a look all the same.

$ sudo nano /etc/usplash.conf
$ sudo update-initramfs -u

---

### Post by buddha001 on 2008-01-05
> **M.Abdullah said:**
> evil316:
yes, i am. after boot i type dmesg and i found this messages repeated:

```

[ 1030.640000] gspca: probe of 5-6:1.0 failed with error -5
[ 1030.640000] usb 5-6: USB disconnect, address 67
[ 1030.912000] usb 5-6: new high speed USB device using ehci_hcd and address 68
[ 1031.068000] usb 5-6: configuration #1 chosen from 1 choice
[ 1031.068000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321)

```

it's same thing when i press F2.


frankos44:

yes it does. the system looks like hang, after few minutes i can see login screen.

i tried to boot without quiet splash parameters but nothing different.

what can i do?

I have the exact same problem, except it just keeps repeating those error messages and it doesn't seem to boot at all. I'll try letting it do this for longer and see what happens. Anyone have any ideas?

---

### Post by frankos44 on 2008-01-06
Not sure about the history but has this machine ever been up and running correctly?

If yes, you could take the easy route and affect a fresh load of Ubuntu 7.10 as it dose'nt take very long.

---

