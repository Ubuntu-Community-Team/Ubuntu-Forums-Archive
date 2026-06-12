---
title: "Audio does not auto-switch... the first time"
date: 2015-05-02
forum: Hardware
---

### Post by b00n on 2015-05-02
I have a Bluetooth headset.  When I turn it on, it is auto detected but I need to go to [FONT=courier new]System Settings > Sound > Play sound through[/FONT] and click on the headset entry.

I added the following to [FONT=courier new]/etc/pulse/default.pa[/FONT]:
```
.ifexists module-switch-on-connect.so
load-module module-switch-on-connect
.endif
```

Now when I turn on the headset, it still does not switch the audio stream, but in [FONT=courier new]System Settings > Sound > Play sound through[/FONT], the headset is highlighted (even though sound is still coming out the other speakers).

Next, I click [FONT=courier new]Play sound through[/FONT] on the speakers, then I click on the headset.  Now sound is coming from the headset.  If I turn off the headset, sound comes from the speakers; if I turn on the headset, it switches sound automatically to the headset.  So it works from the second time on, just not the first time.

Background: Ubuntu 14.04 recently updated/rebooted, mostly stock install, not using blueman.

A couple of questions:

[LIST]
[*]Is there a better way to adjust the "switch on connect" preference?  A [FONT=courier new]~/.something[/FONT] configuration seems better than a global change, but I did not figure out how to do that.  (I am a little surprised that's not already a click box under S[FONT=courier new]ystem Settings > Sound[/FONT], something like like "switch sound automatically to new devices", plus I think it already does that if I plug a headset in the front-panel plug, even without [FONT=courier new]module-switch-on-connect[/FONT]. 
[/LIST]
 
[LIST]
[*]What can I do so that switch-on-connect works the first time and not just the second and later times? 
[/LIST]

---

