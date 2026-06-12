---
title: "Wifi printer works with text, not docs nor pdf"
date: 2018-08-26
forum: Hardware
---

### Post by hans12345 on 2018-08-26
I have a partially working Samsung Wifi M2020W printer.

Both my 18.04 desktops work when I try to print something with the Gnome text editor.

But if I try to print from OpenOffice, or a PDF from Evince, nothing happens. 

Why does one way work but the others not?

I attach a snapshot from syslog which could be relevant.

```

Aug 26 09:31:05 Arctic gnome-shell[2421]: Object .Gjs_AppIndicatorIconActor__1 (0x55cd6cb1b840), has been already finalized. Impossible to set any property to it.
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: == Stack trace for context 0x55cd677e9320 ==
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #0 0x7ffcc5e04ad0 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7fb9f80b5de0 @ 87)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #1 0x55cd67b943a8 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7fb9bc60ef78 @ 58)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #2 0x7ffcc5e056b0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #3 0x7ffcc5e05770 b   self-hosted:916 (0x7fb9f80f12b8 @ 367)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #4 0x7ffcc5e05860 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #5 0x55cd67b94320 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7fb9bc7fbc48 @ 22)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #6 0x7ffcc5e064b0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #7 0x55cd67b94278 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:219 (0x7fb9bc7fb2b8 @ 225)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #8 0x7ffcc5e07090 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #9 0x55cd67b94200 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/extension.js:61 (0x7fb9bc7eb560 @ 37)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #10 0x55cd67b94140 i   resource:///org/gnome/shell/ui/extensionSystem.js:82 (0x7fb9dc65a120 @ 431)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #11 0x55cd67b940c0 i   resource:///org/gnome/shell/ui/extensionSystem.js:344 (0x7fb9dc65abc0 @ 13)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #12 0x7ffcc5e07d90 b   self-hosted:251 (0x7fb9f80c4ab0 @ 223)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #13 0x55cd67b94040 i   resource:///org/gnome/shell/ui/extensionSystem.js:343 (0x7fb9dc65ab38 @ 64)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #14 0x55cd67b93fc0 i   resource:///org/gnome/shell/ui/extensionSystem.js:361 (0x7fb9dc65ac48 @ 87)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #15 0x7ffcc5e09290 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #16 0x7ffcc5e09a30 b   resource:///org/gnome/shell/ui/sessionMode.js:205 (0x7fb9dc26c670 @ 254)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #17 0x7ffcc5e0a710 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #18 0x55cd67b93e80 i   resource:///org/gnome/shell/ui/sessionMode.js:167 (0x7fb9dc26c450 @ 40)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #19 0x7ffcc5e0b2f0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #20 0x55cd67b93dd8 i   resource:///org/gnome/shell/ui/screenShield.js:1282 (0x7fb9dc24fbc0 @ 188)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #21 0x7ffcc5e0bed0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #22 0x55cd67b93d50 i   resource:///org/gnome/shell/ui/screenShield.js:902 (0x7fb9dc24ecd0 @ 18)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #23 0x7ffcc5e0cab0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #24 0x7ffcc5e0d250 b   self-hosted:916 (0x7fb9f80f12b8 @ 367)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #25 0x7ffcc5e0d2d0 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #26 0x55cd67b93cd0 i   resource:///org/gnome/shell/ui/lightbox.js:186 (0x7fb9dc638890 @ 29)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #27 0x7ffcc5e0e700 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (0x7fb9f80d2b38 @ 54)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #28 0x7ffcc5e0ef50 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:337 (0x7fb9f80d2bc0 @ 1626)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #29 0x7ffcc5e0f000 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:350 (0x7fb9f80d2c48 @ 100)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #30 0x7ffcc5e0f090 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:365 (0x7fb9f80d2cd0 @ 10)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #31 0x7ffcc5e0f110 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #32 0x7ffcc5e0f1c0 b   resource:///org/gnome/shell/ui/tweener.js:245 (0x7fb9f80cf808 @ 159)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #33 0x7ffcc5e0f230 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #34 0x7ffcc5e0f230 I   resource:///org/gnome/shell/ui/tweener.js:220 (0x7fb9f80cf780 @ 15)
Aug 26 09:31:05 Arctic gnome-shell[2421]: Object .Gjs_AppIndicatorIconActor__1 (0x55cd6cbb0040), has been already finalized. Impossible to set any property to it.
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: == Stack trace for context 0x55cd677e9320 ==
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #0 0x7ffcc5e04ad0 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7fb9f80b5de0 @ 87)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #1 0x55cd67b943a8 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7fb9bc60ef78 @ 58)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #2 0x7ffcc5e056b0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #3 0x7ffcc5e05770 b   self-hosted:916 (0x7fb9f80f12b8 @ 367)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #4 0x7ffcc5e05860 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #5 0x55cd67b94320 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7fb9bc7fbc48 @ 22)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #6 0x7ffcc5e064b0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #7 0x55cd67b94278 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:219 (0x7fb9bc7fb2b8 @ 225)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #8 0x7ffcc5e07090 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #9 0x55cd67b94200 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/extension.js:61 (0x7fb9bc7eb560 @ 37)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #10 0x55cd67b94140 i   resource:///org/gnome/shell/ui/extensionSystem.js:82 (0x7fb9dc65a120 @ 431)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #11 0x55cd67b940c0 i   resource:///org/gnome/shell/ui/extensionSystem.js:344 (0x7fb9dc65abc0 @ 13)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #12 0x7ffcc5e07d90 b   self-hosted:251 (0x7fb9f80c4ab0 @ 223)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #13 0x55cd67b94040 i   resource:///org/gnome/shell/ui/extensionSystem.js:343 (0x7fb9dc65ab38 @ 64)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #14 0x55cd67b93fc0 i   resource:///org/gnome/shell/ui/extensionSystem.js:361 (0x7fb9dc65ac48 @ 87)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #15 0x7ffcc5e09290 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #16 0x7ffcc5e09a30 b   resource:///org/gnome/shell/ui/sessionMode.js:205 (0x7fb9dc26c670 @ 254)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #17 0x7ffcc5e0a710 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #18 0x55cd67b93e80 i   resource:///org/gnome/shell/ui/sessionMode.js:167 (0x7fb9dc26c450 @ 40)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #19 0x7ffcc5e0b2f0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #20 0x55cd67b93dd8 i   resource:///org/gnome/shell/ui/screenShield.js:1282 (0x7fb9dc24fbc0 @ 188)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #21 0x7ffcc5e0bed0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #22 0x55cd67b93d50 i   resource:///org/gnome/shell/ui/screenShield.js:902 (0x7fb9dc24ecd0 @ 18)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #23 0x7ffcc5e0cab0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #24 0x7ffcc5e0d250 b   self-hosted:916 (0x7fb9f80f12b8 @ 367)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #25 0x7ffcc5e0d2d0 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #26 0x55cd67b93cd0 i   resource:///org/gnome/shell/ui/lightbox.js:186 (0x7fb9dc638890 @ 29)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #27 0x7ffcc5e0e700 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:208 (0x7fb9f80d2b38 @ 54)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #28 0x7ffcc5e0ef50 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:337 (0x7fb9f80d2bc0 @ 1626)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #29 0x7ffcc5e0f000 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:350 (0x7fb9f80d2c48 @ 100)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #30 0x7ffcc5e0f090 b   resource:///org/gnome/gjs/modules/tweener/tweener.js:365 (0x7fb9f80d2cd0 @ 10)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #31 0x7ffcc5e0f110 I   resource:///org/gnome/gjs/modules/signals.js:128 (0x7fb9f80d2230 @ 386)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #32 0x7ffcc5e0f1c0 b   resource:///org/gnome/shell/ui/tweener.js:245 (0x7fb9f80cf808 @ 159)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #33 0x7ffcc5e0f230 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7fb9f80b5de0 @ 71)
Aug 26 09:31:05 Arctic org.gnome.Shell.desktop[2421]: #34 0x7ffcc5e0f230 I   resource:///org/gnome/shell/ui/tweener.js:220 (0x7fb9f80cf780 @ 15)
Aug 26 09:31:05 Arctic gnome-software[2636]: no app for changed ubuntu-appindicators@ubuntu.com
Aug 26 09:31:05 Arctic gnome-software[2636]: no app for changed ubuntu-dock@ubuntu.com
Aug 26 09:35:01 Arctic CRON[5028]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Aug 26 09:40:39 Arctic canonical-livepatch[1548]: Client.Check
Aug 26 09:40:39 Arctic canonical-livepatch[1548]: No payload available.
Aug 26 09:40:39 Arctic canonical-livepatch[1548]: during refresh: cannot check: No machine-token. Please run 'canonical-livepatch enable'!
Aug 26 09:41:20 Arctic wpa_supplicant[962]: wlx7cdd90d0d8f1: WPA: Group rekeying completed with 8c:3b:ad:fc:81:66 [GTK=TKIP]
Aug 26 09:45:01 Arctic CRON[5056]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Aug 26 09:45:13 Arctic colord[1071]: failed to get session [pid 3194]: No data available
Aug 26 09:45:14 Arctic colord[1071]: message repeated 3 times: [ failed to get session [pid 3194]: No data available]
Aug 26 09:48:58 Arctic gnome-software[2636]: no app for changed ubuntu-dock@ubuntu.com
Aug 26 09:48:58 Arctic gnome-software[2636]: no app for changed ubuntu-appindicators@ubuntu.com
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.87/org/ayatana/NotificationItem/software_update_available
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.61/org/ayatana/NotificationItem/multiload
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-WARN] Attempting to re-register :1.61/org/ayatana/NotificationItem/multiload; resetting instead
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-WARN] Item :1.61/org/ayatana/NotificationItem/multiload is already registered
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-WARN] Attempting to re-register :1.61/org/ayatana/NotificationItem/multiload; resetting instead
Aug 26 09:48:58 Arctic gnome-shell[2421]: [AppIndicatorSupport-WARN] Item :1.61/org/ayatana/NotificationItem/multiload is already registered
Aug 26 09:48:59 Arctic gvfsd-metadata[2916]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Aug 26 09:48:59 Arctic gvfsd-metadata[2916]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed

```

---

### Post by hans12345 on 2018-08-26
When I say "nothing happens", that is exact. No warning msg, nothing.

I have the usual cups packages installed.

Oh, and above, I mean LibreOffice, not OpenOffice !

Any ideas?

---

### Post by hans12345 on 2018-08-29
Gentle, kind, respectful bump :D

---

### Post by him610 on 2018-08-31
Hello hans12345 in Luxembourg,

It seems to be an interesting problem. 
Could you tell us what steps, from the beginning, you have gone through to set up your printer, and how it is connected to your computer?

---

### Post by him610 on 2018-08-31
After researching your printer, it seems that Samsung's printer business has been acquired by HP. The drivers for your printer can be download here...
 [https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2020-laser-printer-series/16462592/model/16462596]("https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2020-laser-printer-series/16462592/model/16462596")

Some detailed Linux installation instructions can still be found on the Samsung site, here ...
[http://www.samsungsetup.com/ts/manual/Samsung%20M288x%20Series/English/manual/BABBIBJC.htm?isTocLink=opened]("http://www.samsungsetup.com/ts/manual/Samsung%20M288x%20Series/English/manual/BABBIBJC.htm?isTocLink=opened")

---

### Post by hans12345 on 2018-09-01
Thanks him610

Currently I have had to move my office and now the printer is offline.

I'll get back to this soon.

PS I like your second motto

---

