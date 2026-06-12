---
title: "5 button microsoft mouse on feisty?"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by voided3 on 2007-04-20
Hello, I have a five button Microsoft Intellimouse Explorer usb mouse and I am trying to get the forward and back buttons to work with it on feisty. Adding the following line to the "InputDevice" section for the "Configured Mouse" worked in the past on edgy:

> Option      "ButtonMapping" "1 2 3 6 7"

Any ideas as to how I can enable the buttons again? Thanks!

---

### Post by MindRiot on 2007-04-20
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection


Did you remember "Button" "7"?

---

### Post by voided3 on 2007-04-20
Ah, I got it. The "Protocol" option said "ImPS/2" instead of "ExplorerPS/2"; I changed it and it worked just fine. Thanks!

---

### Post by Bashed on 2007-05-10
I have Microsoft Wireless Laser Mouse 6000 and I enabled the 5 button settings with the below:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection


I'm hoping someone can help me to get the horizontal scroll to work. Also, I would like the back button to work when browsing the file system (under places > computer for example). That would be great.

Thanks

---

### Post by Bashed on 2007-06-28
Can some one please help out on the back button issue?

---

### Post by n00blar on 2007-12-19
> **TalkJesus said:**
> I have Microsoft Wireless Laser Mouse 6000 and I enabled the 5 button settings with the below:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection


I'm hoping someone can help me to get the horizontal scroll to work. Also, I would like the back button to work when browsing the file system (under places > computer for example). That would be great.

Thanks

Just want to say that these settings also work on my Microsoft Wireless Laser Mouse 6000. No need to add any other piece of software. Just make the change and restart X...it's that easy!

---

