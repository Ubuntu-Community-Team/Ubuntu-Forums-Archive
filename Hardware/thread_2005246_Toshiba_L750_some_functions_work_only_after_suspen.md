---
title: "Toshiba L750 some functions work only after suspend"
date: 2012-06-17
forum: Hardware
---

### Post by qwe2 on 2012-06-17
Hi.

Sorry if it's a repost but I have been looking it up for weeks and didn't find any useful information.

I have a Toshiba L750-1N3, Ubuntu 12.04 x64. First of all my problem is that some of my Fn keys won't work. For example Fn+3 is working for sound control but Fn+F7 for brightness is not. (can adjust brightness on system panel)
However if I suspend then resume my system they strangely everything is working as supposed, but if I reboot again they will not work till another suspend/resume again. The situation is the same with battery status. If I don't (un)plug the cable or suspend/resume I can't get ubuntu indicate it.

If somebody could provide me with any ideas it would be highly appreciated. What does a suspend/resume trigger that the boot does not?

Also I noticed that I get the following error after booting pressing just the Fn key but I dont get it after resuming my suspended system:
```
atkbd serio0: Unknown key released (translated set 2, code 0x55 on isa0060/serio0).
atkbd serio0: Use 'setkeycodes 55 <keycode>' to make it known.
```

Thank you in advance.

---

### Post by qwe2 on 2012-06-27
Upgrading to 3.4 kernel solved the battery issue and I set some of the keycodes manually by adding setkeycodes to the /etc/rc.local file. 

```
setkeycodes e025 152 #fn+f1
setkeycodes e02d 236 #fn+f2
setkeycodes e026 142 #fn+f3
setkeycodes e027 205 #fn+f4
setkeycodes e029 227 #fn+f5
setkeycodes 0xef 224 #fn+f6
setkeycodes e06e 225 #fn+f7
setkeycodes e054 238 #fn+f8

setkeycodes e02c 419 #fn+1
setkeycodes e02b 418 #fn+2
setkeycodes e031 420 #fn+space
```It's very far from being a good solution but at least my fn keys are working now.

---

