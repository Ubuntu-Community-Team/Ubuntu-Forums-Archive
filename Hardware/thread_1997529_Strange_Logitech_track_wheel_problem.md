---
title: "Strange Logitech track wheel problem"
date: 2012-06-05
forum: Hardware
---

### Post by ice2921 on 2012-06-05
Hello,

I recently upgraded from Ubuntu 10.04 to Ubuntu 12.04. The upgrade when smooth for the most part, but with one issue. My logitech wireless mouse track whell is acting up. When I use it to scroll up and down within a web page it actually double clicks at times. It was working previously on 10.04. Has anyone seen something like this or have some suggestions? Thanks. 

X Configuration File input section:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

