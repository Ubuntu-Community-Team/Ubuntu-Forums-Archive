---
title: "keyboard not working until logout"
date: 2008-07-25
forum: General Help
---

### Post by josephdaniel on 2008-07-25
Hi,

This problem has just appeared two days ago on my hardy 8.04.1 installation. Everything was working fine. I hadn't installed any software or altered any significant settings. I only downloaded the new updates available in the repos and here is my case now:

I am using automatic login for my account. After the ubuntu desktop appears, the mouse is working perfectly but the keyboard is not responding. The num lock/caps lock keys don't toggle the lights on the keyboard. Using the mouse I log out, this time the keyboard is working properly and I can type my username and password and login. Everything works fine after that.

I tried to trace it to know when exactly the keyboard fails. I found out that the num lock key is working properly all through the boot process and it only stops working when the GDM starts loading. 

dmesg doesn't report any errors.
and xorg.0.log shows the following:
```

(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us, ar"
(**) Generic Keyboard: XkbLayout: "us, ar"
(**) Option "XkbOptions" "grp:alt_shift_toggle"
(**) Generic Keyboard: XkbOptions: "grp:alt_shift_toggle"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

I thought of turning off the autologin and trying to restart but I fear that I lose access completely. It's now working at least.

Any ideas what might be the problem?

Thanks in advance,
Joseph

---

### Post by josephdaniel on 2008-07-26
bump

---

