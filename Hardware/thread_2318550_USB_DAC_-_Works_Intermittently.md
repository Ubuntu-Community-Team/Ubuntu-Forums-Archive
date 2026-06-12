---
title: "USB DAC - Works Intermittently"
date: 2016-03-27
forum: Hardware
---

### Post by bitnumus on 2016-03-27
I recently purchased a SMSL Q5 Pro USB DAC/AMP. I have tried it on 14.04, 15.10 and 16.04 beta2.

My generic question is should this device be supported, and just work plug and play? Has anyone else used this device or another by SMSL?

Whats happening:

When plugged in hot, a new output shows up under sound settings, (Analog S-AMP). When plugged in before boot another (Digital S-AMP) is there also. They randomly flash on and off, and if you click one of them quick enough sound will output, then after 5-10seconds it will start to crackle and becomes inaudible.

There are a few differences between ubuntu versions, but none of them work without getting a certain sequence right each time.

Something odd that i've found is that if i launch and leave running "pavucontrol" GUI, things work fine!, at least the crackling disappears, then if i close the window things go downhill. I originally thought it was the device, but because of this strange event i'm starting to thing it could be driver related.

I can get some logs from syslog, but at this stage just wanted to see what i should be expecting!

---

### Post by bitnumus on 2016-04-02
Just updating this: I purchased another one of these units, and things are different yet again. This time the device is showing up and not flashing with disconnects. However there are no audio controls for the device under "alsamixer", and its very quiet at the same volume level compared to the other unit.

Here are some logs i've found:

> Apr  2 08:32:21 tux kernel: [  417.399550] usb 2-1.3: new full-speed USB device number 5 using ehci-pciApr  2 08:32:21 tux kernel: [  417.502460] usb 2-1.3: New USB device found, idVendor=0451, idProduct=0003
Apr  2 08:32:21 tux kernel: [  417.502467] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr  2 08:32:21 tux kernel: [  417.502471] usb 2-1.3: Product: SMSL Q5 AMP  
Apr  2 08:32:21 tux kernel: [  417.502474] usb 2-1.3: Manufacturer: SMSL AUDIO       
Apr  2 08:32:21 tux mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Apr  2 08:32:21 tux mtp-probe: bus: 2, device: 5 was not an MTP device
Apr  2 08:32:21 tux kernel: [  417.535338] usb 2-1.3: 1:1: cannot get freq at ep 0x1
Apr  2 08:32:21 tux kernel: [  417.536912] usbcore: registered new interface driver snd-usb-audio
Apr  2 08:32:21 tux systemd-udevd[2197]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 1' failed with exit code 99.
Apr  2 08:32:21 tux kernel: [  417.555710] usb 2-1.3: 1:1: cannot get freq at ep 0x1
Apr  2 08:32:21 tux kernel: [  417.558584] usb 2-1.3: 1:1: cannot get freq at ep 0x1
Apr  2 08:32:21 tux kernel: [  417.590387] usb 2-1.3: 1:1: cannot get freq at ep 0x1
Apr  2 08:32:21 tux kernel: [  417.593321] usb 2-1.3: 1:1: cannot get freq at ep 0x1
Apr  2 08:32:21 tux rtkit-daemon[1293]: Supervising 3 threads of 1 processes of 1 users.
Apr  2 08:32:21 tux rtkit-daemon[1293]: Successfully made thread 2209 of process 1829 (n/a) owned by '1000' RT at priority 5.
Apr  2 08:32:21 tux rtkit-daemon[1293]: Supervising 4 threads of 1 processes of 1 users.




----------






Apr  2 08:40:54 tux pulseaudio[1820]: [pulseaudio] module-device-restore.c: Could not save format info for sink alsa_output.usb-SMSL_AUDIO_SMSL_Q5_AMP-00.iec958-stereo


----------


Apr  2 08:44:15 tux systemd-udevd[2339]: Process '/usr/sbin/alsactl -E HOME=/run/alsa restore 1' failed with exit code 99

---

