---
title: "Laptop Touchpad laggy / choppy after waking from suspend."
date: 2022-10-24
forum: Hardware
---

### Post by hozer223 on 2022-10-24
Hello folks,

I bought a new laptop and have been having issues with it. I obviously reformatted it as soon as I got it and installed the latest Ubuntu Desktop 22.04. Install went fine, everything works so far except the touch pad. Booting from cold-start is fine, touch pad is appropriately responsive and accepts gestures. If I put the laptop into suspend, as one commonly does, and then wake up, the pointer is jumpy, laggy, choppy, and is interpreting some of the movements as click events. Obviously, not very usable.

Diving into the forums, I found a few threads that seemed to speak to what is happening to me. All of the solutions provided revolve around removing the kernel modules responsible for the input device, and then re-adding them to reset the behavior. Although I've tried this in many different variations, no relief. Rebooting the entire system works to bring back the desired behavior.

Related posts:
[https://askubuntu.com/questions/367441/touchpad-acts-funny-after-sleep](https://askubuntu.com/questions/367441/touchpad-acts-funny-after-sleep)
[https://askubuntu.com/questions/671910/touchpad-not-working-after-suspending-laptop](https://askubuntu.com/questions/671910/touchpad-not-working-after-suspending-laptop)
[https://askubuntu.com/questions/1072167/thinkpad-touchpad-mouse-cursor-laggy-choppy-ubuntu-18-04](https://askubuntu.com/questions/1072167/thinkpad-touchpad-mouse-cursor-laggy-choppy-ubuntu-18-04)


To my layperson's analysis, it still does seem like the issue is related to the loading / unloading of modules after the system comes back up from suspend. Here's some supporting information

Output from lshw:

```
*-input:6
       product: ASUE1201:00 04F3:3125 Mouse
       physical id: 7
       logical name: input7
       logical name: /dev/input/event4
       logical name: /dev/input/mouse0
       capabilities: i2c
  *-input:7
       product: ASUE1201:00 04F3:3125 Touchpad
       physical id: 8
       logical name: input8
       logical name: /dev/input/event5
       logical name: /dev/input/mouse1
       capabilities: i2c

```

All hid related modules from lsmod. If the "remove / reload module" theory is true, it's possible I might be missing some input related ones here as I'm just grep'ping for "hid" and removing & inserting some or all of the modules listed here.

```
 hid_multitouch         32768  0
mac_hid                16384  0
hid_generic            16384  0
i2c_hid_acpi           16384  0
i2c_hid                36864  1 i2c_hid_acpi
hid                   151552  3 i2c_hid,hid_multitouch,hid_generic
 
```

After suspending, but before trying to remove / insert the modules, I noticed this in the journalctl output, but it seems to just be describing the symptom:
```
Oct 19 20:44:14 satcom gnome-shell[1126]: libinput error: event5  - ASUE1201:00 04F3:3125 Touchpad: kernel bug: Touch jump detected and discarded.
```

After suspending, after removing and inserting the modules, this error shows up in the dmesg output. Removing and inserting the modules prior to the suspend works flawlessly without any errors in either dmesg or journalctrl: simply the expected informational outputs.

```
i2c_hid_acpi i2c-ASUE1201:00: i2c_hid_get_input: IRQ triggered but there's no data
```

My thought is that something in the wake-from-suspend process is coming up out of sequence but at this point I'm stuck. Any thoughts?

---

