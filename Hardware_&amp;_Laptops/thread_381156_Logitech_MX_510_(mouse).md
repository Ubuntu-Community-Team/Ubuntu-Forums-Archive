---
title: "Logitech MX 510 (mouse)"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by michi-michi-michi on 2007-03-10
In order to get the forward, backward, and other  buttons of your Logitech MX 510 mouse to work, just follow these steps:

1.) Open a terminal

2.) Type: 
```
sudo gedit /etc/X11/xorg.conf
```

3.) Scroll down to where it says: 
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

4.) Ad the following line under "ZAxisMapping" "4 5":
```
Option         "ButtonMapping" "1 2 3 6 7"
```

5.) Now it should look like that:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection
```

6.) Save changes (!)

7.) Restart using CTRL+ALT+Backspace

Now it should work just fine! xD

---

### Post by commondork on 2008-03-23
I know this is an old post but it applies to my problem.  I tried this solution but my mouse isn't doing what I believe it should be doing.  The Forward button still acts like right-click and the back button still acts like the left-click.  Was anyone able to configure their Logitech MX-510 mouse to use the forward/backward buttons correctly?

---

