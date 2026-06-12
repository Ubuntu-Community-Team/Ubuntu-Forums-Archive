---
title: "Cryptic USB sound device error message: cannot get freq at ep"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by haynold on 2007-04-14
Hello:

I'm trying to get a Lexicon Lambda to work with Ubuntu, and under Edgy and Feisty I'm getting the same odd series of "cannot get freq at ep" error messages. This is what dmesg has to say after plugging the device in:

```
[ 1354.659202] usb 4-1: new full speed USB device using uhci_hcd and address 21
[ 1354.856797] usb 4-1: config 1 has an invalid interface number: 6 but max is 5
[ 1354.856806] usb 4-1: config 1 has an invalid interface number: 7 but max is 5
[ 1354.856812] usb 4-1: config 1 has no interface number 3
[ 1354.856815] usb 4-1: config 1 has no interface number 5
[ 1354.876921] usb 4-1: configuration #1 chosen from 1 choice
[ 1354.892773] 21:1:1: cannot get freq at ep 0x1
[ 1354.896773] 21:1:2: cannot get freq at ep 0x1
[ 1354.901778] 21:2:1: cannot get freq at ep 0x82
[ 1354.905774] 21:2:2: cannot get freq at ep 0x82

```

usbview sees the device as being handled by snd-usb-audio.

Any ideas how to make this work will be very much appreciated.

Best,

                 Oliver

---

### Post by SenojLuap on 2007-09-17
I'm trying to get the Lambda working as well. I'm afraid I don't have any help. Just wanted to keep the thread fresh

---

### Post by haynold on 2007-09-17
Actually, it seems that seems that these message are called by some slight violations of the USB standard by the Lambda, but don't impair functioning. With the Lambda you won't see a mixer device since the Lambda's mixer is the knobs on front and can't be controlled by software, but you should see a /dev/dspX device and an ALSA device. Just try whether your favorite audio software can see the device. It now works like a charm for me.

---

