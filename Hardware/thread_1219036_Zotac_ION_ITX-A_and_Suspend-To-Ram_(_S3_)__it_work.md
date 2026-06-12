---
title: "Zotac ION ITX-A and Suspend-To-Ram ( S3 ) : it works only once"
date: 2009-07-21
forum: Hardware
---

### Post by micantox on 2009-07-21
Hi all,

I own this mini-ITX standard motherboard from Zotac and I'd like to
exploit it to build an HTPC. So far, I'm quite happy with it, for it 
performs pretty well in this field.

The only feature I miss or, better, I partially miss is the suspend to 
ram. I definitely need it in order to avoid waiting for the complete 
system to come up every time.

The problem is that the very first time on every boot, the suspend-to-ram 
works perfectly, no matter what command is issued (s2ram -f , pm-suspend 
and so on so forth). Once I get it resumed, I cannot make it go into a 
suspended state again: it does the very same procedure, according to 
dmesg, as the successful one, but it gets awaken without my intervention. 
It is exactly the same behaviour you would obtain in case a peripheral 
had continuously issued the wake-up signal to the platform, during the 
suspending process.


I made millions of experiments: unplugged all the usb devices, unloaded 
forcedeth and all usb controller related modules, leaving my ps/2 
keyboard as the only attached peripheral, ifconfig-ed down my interfaces. 
No success.

My installation was made starting from a Jaunty minimal CD with a 
standard base system and openssh server in place only. I then installed 
all the things necessary to my set-up (since I had to compile XBMC to 
apply a couple of patches of mine I had to apt-get build-dep it).


Please find attached the following contents:

- the output from lspci -Q -vv
- the successful suspend to ram dmesg output
- the failing suspend to ram dmesg output

In case you need further info, I'll be more than happy to provide it.

Thanks to everyone will have the time and will to help.

M.

---

### Post by Slither2007 on 2009-10-06
I've got exactly the same mobo running Jaunty Desktop with exactly the same issue.

---

### Post by micantox on 2009-10-08
Ok, I've made few progresses.

As I've discovered on the XBMC forum, in order to let it work throughout multiple suspends and resumes you just need to add this on the kernel row in the GRUB menu.lst.

```
usbcore.autosuspend=-1
```

So, as an example, this is my kernel row:

```
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=362bda08-efc8-46e4-a30e-7dca5d1f92c9 ro quiet splash usbcore.autosuspend=-1
```

That should do the trick. Please let me know if it doesn't.

M.

---

### Post by Slither2007 on 2009-10-08
> **micantox said:**
> Ok, I've made few progresses.

As I've discovered on the XBMC forum, in order to let it work throughout multiple suspends and resumes you just need to add this on the kernel row in the GRUB menu.lst.

```
usbcore.autosuspend=-1
```

So, as an example, this is my kernel row:

```
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=362bda08-efc8-46e4-a30e-7dca5d1f92c9 ro quiet splash usbcore.autosuspend=-1
```

That should do the trick. Please let me know if it doesn't.

M.


Thanks for getting back to me so quick.

I'll try that right now and post back in 5 minutes.

---

### Post by Slither2007 on 2009-10-08
It turns out I already had that setting in my grub menu.lst from when I followed this guide : [http://www.xbmc.org/forum/showthread.php?t=56305](http://www.xbmc.org/forum/showthread.php?t=56305)

Here is an extract : 

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            44e4c0a0-c2ba-4ec8-9320-ed2da7515450
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=44e4c0a0-c2ba-4ec8-9320-ed2da7515450 ro quiet splash usbcore.autosuspend=-1
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            44e4c0a0-c2ba-4ec8-9320-ed2da7515450
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=44e4c0a0-c2ba-4ec8-9320-ed2da7515450 ro  single
initrd          /boot/initrd.img-2.6.28-15-generic


I'm able to suspend fine multiple times but the computer wakes up by itself with the BIOS wakeup settings all disabled and my /proc/acpi/wakeup all disabled + no usb devices connected or lan connection....i'm baffled.

Thankyou anyway for your suggestion.

Regards,

Slither2007.

---

### Post by Eldis on 2009-12-08
Good thread, the usbcore.autosuspend=-1  trick did it for me.

Running karmic with zotac ion the 330 version.

---

