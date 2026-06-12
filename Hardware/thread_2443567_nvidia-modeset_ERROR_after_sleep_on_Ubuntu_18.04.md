---
title: "nvidia-modeset: ERROR after sleep on Ubuntu 18.04"
date: 2020-05-17
forum: Hardware
---

### Post by gsync on 2020-05-17
Hello, 

Up to now I was using my Legion Y740 under Ubuntu by selecting only Intel as GPU.

Recently I noticed that in case I'd like to use my external monitor I need to select the Nvidia card and then reboot.

All good, but this is leading to something else - after sleep I'm getting the following error:

```
nvidia-modeset: ERROR: GPU 0: Idling display engine time out: ......
```

Of course when the OS is using only Intel, there's no problem after sleep!

Any boot params I need to enter, in order for the OS to survive the wake up call after sleep?

I'm using nvidia-driver-435, because 440 isn't recognizing external monitors,
but I did the test with 440, and there's no difference.

---

### Post by CelticWarrior on 2020-05-17
Is your UEFI firmware updated and is Secure Boot disabled?

---

### Post by gsync on 2020-05-17
> **CelticWarrior said:**
> Is your UEFI firmware updated and is Secure Boot disabled?

Yes, firmware is up to date, and secure boot is disabled.

---

### Post by gsync on 2020-05-17
After doing some testing with different boot parameters the following is working:

```
GRUB_CMDLINE_LINUX="nouveau.modeset=1"
```

But it got even more interesting.

After the OS loads and I put the machine to sleep, it's all good.
But in case the machine goes to sleep again and then when I wake it up, it's showing the exact same error.

I have no idea why it's working always just the first time, but not the second...

---

