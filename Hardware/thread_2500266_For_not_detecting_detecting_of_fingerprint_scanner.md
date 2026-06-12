---
title: "For not detecting detecting of fingerprint scanner"
date: 2024-08-28
forum: Hardware
---

### Post by abgup1540 on 2024-08-28
My laptop has hardware of fingerprint scanner but after installing ubuntu 24.04 LTS, I am not able to use my fingerprint scanner. Please provide me the solution to resolve this issue related to hardware.

---

### Post by TheFu on 2024-08-28
Did it work with prior versions of Ubuntu or Linux?

What is the specific hardware?  Are there Linux drivers for it?

Generally, only hardware that gets linux support directly from the laptop maker will have any Linux drivers for specific features like a fingerprint reader.  For keeping out a little brother, fingerprint readers are fine, but for real security, they have been shown to be very flawed.  For 2FA, they may be of some use. Hard to say.  Laptop models that come pre-installed with Linux from the OEM vendor would be most likely to have support. You'll likely need to run the OS the vendor pre-installed and use their drivers which can be easy with a PPA or difficult if they only make install images.

For laptops that don't come preinstalled with Linux, finding a driver for any specific device is a crap-shoot. You'll need to figure out the exact chip being used.  **lsusb** would be where I started. I'd look for the USBid and then look for drivers using that information.

Of course, how useful any security device is would completely depend on the type of attacker you are trying to thwart.

---

### Post by abgup1540 on 2024-08-28
As my laptop had preinstalled Windows Operating System but I installed Linux for my working purpose.Also, the fingerprint was not working in previous version of Ubuntu 22.04 LTS. I am not understanding what are you telling to do to me. I had the same issue with my camera but when I ran this command "bash -c "sleep 10 && systemctl --user restart pipewire" in the terminal and the camera started working. Please specify clearly.

---

### Post by TheFu on 2024-08-29
You have two choices.

[LIST]
[*]Ask the laptop vendor for the drivers.  Look on their website, post in their forums, call their toll-free support number.
[*]Figure out the exact hardware used inside the laptop for the fingerprint reader, get the USB ID for it and look up which driver, if there is one at all, will control it.  [https://wiki.debian.org/HowToIdentifyADevice/USB](https://wiki.debian.org/HowToIdentifyADevice/USB)   I'd use the program **lsusb**, which is what I suggested above. 10 seconds.
[*]
[/LIST]

Basically, you need to get the driver, install it, and find end-user software that will work with that driver.
Fingerprint reader drivers often DO NOT have Linux drivers.  There is some hope if the laptop is from a Linux-friendly vendor like Lenovo or Dell or System76 - those vendors sell Linux pre-installed on some of their laptops.

**Without the correct linux driver, it won't work.**

I've made lots of assumptions, but none are exactly crazy. They are likely correct.

---

