---
title: "hibernation error"
date: 2008-05-05
forum: Hardware
---

### Post by mahdiarnt on 2008-05-05
When I hibernate my laptop (ThinkPad T61), I get an error, although eventually it does hibernate. So before turning off I get a blue screen(actually :

```

[   30.333981] drm_sysfs_suspend
[   34.591016] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp.
26).
[   34.591018] uvcvideo 7-5:1.1: resume error -5
[   38.302323] uvcvideo ***
[   38.302327] uvcviedo ***
[   38.302349] suspend

```

(Numbers may not be accurate, 0/8 could be mistaken; *** is something I couldn't read before it went away).

Then when I resume the computer, the Ubuntu logo comes with its progress bar, but then it freezes. Then I hear a beep. A blue screen appears and then a black one. Then the screen I was working on before hibernation. Suddenly it disappears; the screen goes black and the login screen comes. After I login my screen comes again and everything is normal.

I don't know what goes on and I'm worried that this could harm my hardware.

Any help is appreciated.

---

### Post by tamias on 2008-06-10
First, don't worry; your hardware can't and won't be harmed in this way. It just looks scary.

Second, it's a known issue and is being fixed as we speak. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239)

Hope this helps,

Mark

---

### Post by mahdiarnt on 2008-06-10
Thank you Mark for the reply. I looked into the link but it was rather too technical for me. But anyway if it's resolved, why do I still have it? Isn't the fix among the standard updates?

I have managed to figure out more of the messages that I get and they are more than just the drm_sysfs_suspend one. In fact they change from time to time. Here's what I get usually. Please see if you know any workarounds for any of them:

```
[] drm_sysfs_suspend
[] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp.26).
[] uvcvideo 7-5:1.1: resume error -5
[] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp.26).
[] uvcvideo 7-5:1.1: resume error -5
[] suspend_device(): usb_suspend+0x0/0x30 [usbcore]() returns ***
[] could not suspend device 7-5: error -32
[] suspend

```
and sometimes I get this among the meesages:

```
[] thinkpad_acpi: unknown LID-related HKEY event ***
```

---

### Post by tamias on 2008-06-10
The fix is still being tested. If you enable hardy-proposed updates it should be installed; otherwise you can just wait until it makes its way to the standard updates repository.

As for the other messages, they are again just scary-looking, but harmless, information messages. I'm sure they will go away in due course with upcoming patches.

---

### Post by Ben256 on 2009-02-24
Hello,

I wanted to know if there is something new concerning this bug.

I have a Dell Inspiron 1720 with Hardy Heron, (and it's up to date I guess) and I have exactly the same problem than what is described in this subject when I try the hibernatation 
(with "uvcvideo failed to querry..." messages. After the quite strange "wake-up" it seems to work though)

Regards,

Ben

---

