---
title: "it wont turn off!"
date: 2008-08-03
forum: Hardware
---

### Post by Ashton_Durkhun on 2008-08-03
I have ubuntu eee version on my eee 4g surf, and when i tell it to shut down, it acts like its going to but the green power light stays on and the fan keeps running according to how hot the internals are (it turns off after a while if the laptop if on a cool surface and it runs on and on if it's on, for instance, my bed, where het is trapped...) so obviously something isn't powered down fully...

when its in this state it will not power back on either. hitting ht epower button does nothing, neither does holding it.

In the end i have to unplug it and remove the battery to turn it off.

any suggestions?

---

### Post by robertchahine on 2008-08-03
open a terminal and try
```

sudo shutdown -h now

```

---

### Post by rahmath on 2008-08-03
Yes there are suggestions, and i hope we can solve this issue. To start please do the following and get back to us;

1. specify the command which you tried to shutdown the system
2. try running both of the following commands and let us know the feedback of that two commands;
          $ sudo shutdown -h now
          $ sudo poweroff


awaiting for your reply.

---

### Post by Ashton_Durkhun on 2008-08-03
neither command will acctually shut it down, both put it into the state i mentioned above. 

tried sudo poweroff and sudo shutdown -h now, also tried the normal system - quit - shutdown. menu options

---

### Post by dentaku65 on 2008-08-03
Try
```
sudo init 0
```
The above 0=zero

---

### Post by Ashton_Durkhun on 2008-08-03
nope just tried sudo init 0 and it shuts down to the point of the green light.

also i just noticed my bluetooth dongle was still blinking...

another thing that might or might not relate, hibernate will not work, saying there's not enough swap space... of course there is only 500mb left on the ssd, so...

---

### Post by rahmath on 2008-08-03
what about

$ sudo reboot

pls do this and let me know the status

---

### Post by Ashton_Durkhun on 2008-08-03
ok, this is strange...

I tried sudo init 0 and it didn't shutdown, but the next shutdown acctually pwoered off! I just tried sudo reboot and it rebooted properly!

does init 0 change any settings when it makes the laptop shutdown? it seems to be working now (of course my saying that might make it stop...)

---

### Post by Ashton_Durkhun on 2008-08-03
I take it back, shutdown is failing again. however reboot is working fine every time...

---

