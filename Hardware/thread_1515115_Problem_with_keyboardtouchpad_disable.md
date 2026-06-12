---
title: "Problem with keyboard/touchpad disable"
date: 2010-06-21
forum: Hardware
---

### Post by opethfan89 on 2010-06-21
Hi guys,

I haven't posted a problem in a while, but I guess its because I didn't notice it until now. I noticed recently that if I disable my touchpad using the button on the top of it, it will disable my keyboard and I'm unable to type, however I'm still able to do a ctrl + alt + delete keystroke to restart my computer. The laptop that I am using is an HP Pavillion dv7-3060US running Ubuntu 10.04LTS.

I'm not sure if this is a bug or a result of some sort of incorrect configuration on my part, but I hope to have it fixed so as not to deal with it in the future.

Also, while I'm on the topic, is there any easy way to disable the touchpad while I'm typing so as not to have it move around if my thumb accidentally brushes it? I know I've seen a few blog posts but they did not work for me.

Thanks for any and all help,
Opethfan89

---

### Post by opethfan89 on 2010-06-25
Bump?

---

### Post by frekja on 2010-07-05
I've got this problem too. Very frustrating as the trackpad is really badly located on my HP dv6000 series. See [https://bugs.launchpad.net/ubuntu/+bug/571638](https://bugs.launchpad.net/ubuntu/+bug/571638) for details.

Relevant excerpt from the discussion thread:

-------
Excerpt of #103 of Bug Report #549727 for everyone's convenience...

You need to prevent gnome-settings-daemon from disabling your touchpad in the first place, because the Synaptics touchpad driver does this already. To do so, run the following command in a terminal:

Code:

gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad ""

This dissociates the key to lock your touchpad from gnome-settings-daemon. If for any reason, the latter command breaks the lock touchpad support for you, than you probably have a different issue. To re-associate the key with gnome-settings-daemon, run this command:

gconftool-2 --type string --set /apps/gnome_settings_daemon/keybindings/touchpad XF86TouchpadToggle

-------

---

