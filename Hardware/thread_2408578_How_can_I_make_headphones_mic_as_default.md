---
title: "How can I make headphones mic as default?"
date: 2018-12-20
forum: Hardware
---

### Post by Roboteck on 2018-12-20
I record my vice every day. And sometime I forget to switch mic from laptop mic ro headphones. Sound was bad and I need do record again :(

I wrote the script for switch mic to headphones.

**/home/roma/Scripts/micHeadset.sh**:

```
#!/bin/bash

## https://superuser.com/questions/919033/quickly-change-audio-device-in-kde


## &#1055;&#1077;&#1088;&#1077;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1077; &#1085;&#1072; &#1084;&#1080;&#1082;&#1088;&#1086;&#1092;&#1086;&#1085; &#1085;&#1072;&#1091;&#1096;&#1085;&#1080;&#1082;&#1086;&#1074;
/usr/bin/pactl set-source-port 1 analog-input-headset-mic
echo "test" >> /home/roma/test
```

And it work. When i run it, mic switch to headphones. And created file /home/roma/test.

Also, I made listener of headphones connect action **/etc/acpi/events/autoConnectHeadPhones**:

```
event=jack/headphone HEADPHONE plug
action=/etc/acpi/autoConnectHeadPhones.sh
```

Wrote file, whitch run by the action **/etc/acpi/autoConnectHeadPhones.sh**:

```
#!/bin/bashsleep 1
sudo -u roma /home/roma/Scripts/micHeadset.sh
```

And now, when I connect headphones, file /home/roma/test created. But mic don't switch to headphones.

Help me please. What can I do for automatic switch mic to headphones?

---

