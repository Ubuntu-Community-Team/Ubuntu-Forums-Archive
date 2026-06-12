---
title: "Logitech H800 bluetooth headset"
date: 2015-01-02
forum: Hardware
---

### Post by cpdondo on 2015-01-02
I'm struggling to set up a Logitech H800 bluetooth headset.  My laptop can see it, it connects, but it won't pair.  I get a "failed to add device" and a "Authentication failed" when I try to pair.  If I skip pairing, then the headset shows up in pulseaudio, but if I try to use it the source just freezes.  For example, streaming audio from the web doesn't stream; it just pauses.  If I change the output device to the built-in speakers it will start running.

I'm stuck.  Has anyone gotten bluetooth headsets working?  If so, has anyone gotten this particular headset working?

Any advice?

---

### Post by cpdondo on 2015-01-03
After fighting with this headset for several hours, and reading up on all the issues that people are having, it's going back.  Too bad; it's a nice headset, but when it fails work reliably with Windows 7, 8, 8.1, Ubuntu 14.04, and all of these are documented all over the web, it's time to give up.

I did get it to pair, and pulseaudio would recognize it most of the time, but at times it would show up as a bluetooth device, but fail to show up in pulseaudio.  Even if it showed up in pulseaudio, it would never stream anything, although volume control would work.  People reported similar problems with Windows, so it's the headset....

Any recommendations for a good bluetooth headset that actually works?

---

### Post by cpdondo on 2015-01-03
After fighting with this headset for several hours, and reading up on all the issues that people are having, it's going back.  Too bad; it's a nice headset, but when it fails work reliably with Windows 7, 8, 8.1, Ubuntu 14.04, and all of these are documented all over the web, it's time to give up.

I did get it to pair, and pulseaudio would recognize it most of the time, but at times it would show up as a bluetooth device, but fail to show up in pulseaudio.  Even if it showed up in pulseaudio, it would never stream anything, although volume control would work.  People reported similar problems with Windows, so it's the headset....

Any recommendations for a good bluetooth headset that actually works?

---

### Post by RCheesley on 2015-10-16
After much faffing about I finally got these to work following these steps:

Ensure that you have bluetooth up and running, and that you can connect to other devices. This might be helpful in checking if you've got issues with Bluetooth:

> uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth 

If you get any errors, just search the forums for the relevant process.

If you are able to connect to other devices then do the following:

Open up bluetooth manager
Turn your headphones to Bluetooth mode by sliding the switch to the middle position on the side of the headphones
See whether they appear on the scan of devices
If they don't appear (possibly if you've already paired to some device before this one) then you need to enable pairing mode by sliding the next track slider (beneath the off/bluetooth/USB switch) up, and pressing & holding the volume up button. Wait until the green light flashes rapidly, indicating that it's in pairing mode.
Scan for devices, add the headphones when they appear
Once added, you'll need to set up the headphones as an audio device. The headphones **must be in pairing mode** to do this, so you might need to repeat the steps above once again.
When going through the setup, use a custom code of 0000

This worked for me, then I used pauvcontrol to change the device that my Chome browser was using.

In my experience, bluetooth works, but the USB dongle has a far superior sound quality. So if you must use Bluetooth (e.g. for using up to seven other devices) then use it, but if you want good quality sound stick with the USB dongle.

Hope this helps and saves people throwing tantrums like I've been doing for the last two hours!

Ruth

---

### Post by firecentaur on 2015-10-21
Hi there, 
I am using Ubuntu 14.04, and surprisingly, the usb dongle actually works with Ubuntu!  With the dongle inserted, the logitech headphones show up as a bluetooth device - just make sure the headphones are also set to the dongle NOT the bluetooth icon!  Now I am able to use the headphones with ubuntu using the dongle, then switch to my phone via bluetooth!  Awesome logitech! Thanks!

---

