---
title: "Touch Screen not working Lenovo Flex 5, Ubuntu Studio 20.04?"
date: 2020-06-24
forum: Hardware
---

### Post by williamwhite on 2020-06-24
I'm running Ubuntu Studio 20.04 on a Lenovo Flex 5-1570 and everything is working fine except for the touch screen and accelerometer. I know the accelerometer probably won't work but thats not a big issue, but it was my understanding that the touch screen would work fine.

I've tried the linux wacom project drivers and it didn't work.

I'm also open to trying different desktop environments if it would help. XFCE isn't the best for touch interface.

---

### Post by williamwhite on 2020-06-28
Bump

---

### Post by williamwhite on 2020-06-29
According to everything I'm reading it should be working. but it isn't.

jester@WhitesToneFactory:~$ xsetwacom --list
Wacom HID 50E8 Pen stylus           id: 13    type: STYLUS    
Wacom HID 50E8 Finger touch         id: 14    type: TOUCH     
Wacom HID 50E8 Pen eraser           id: 17    type: ERASER    

jester@WhitesToneFactory:~$ sudo xinput test-xi2 --root "Wacom HID 50E8 Finger touch"
Wacom HID 50E8 Finger touch                 id=14    [slave  pointer  (2)]
    Reporting 9 classes:
        Class originated from: 14. Type: XIButtonClass
        Buttons supported: 8
        Button labels: None None None None None None None None
        Button state:
        Class originated from: 14. Type: XIKeyClass
        Keycodes supported: 248
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Abs X
          Range: 0.000000 - 13764.000000
          Resolution: 40000 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Abs Y
          Range: 0.000000 - 7740.000000
          Resolution: 40000 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Abs Pressure
          Range: 0.000000 - 65536.000000
          Resolution: 1 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: None
          Range: 0.000000 - 1.000000
          Resolution: 1 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 4:
          Label: None
          Range: 0.000000 - 1.000000
          Resolution: 1 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XIValuatorClass
        Detail for Valuator 5:
          Label: None
          Range: 0.000000 - 1.000000
          Resolution: 1 units/m
          Mode: absolute
          Current value: 0.000000
        Class originated from: 14. Type: XITouchClass
        Touch mode: direct
        Max number of touches: 10

---

### Post by williamwhite on 2020-07-07
nothing?

---

### Post by mfcarpino on 2020-07-10
You might want to try what I did to get it to work.  [https://ubuntuforums.org/showthread.php?t=2445152&highlight=touch+screen](https://ubuntuforums.org/showthread.php?t=2445152&highlight=touch+screen)

---

### Post by williamwhite on 2020-07-12
Ubuntu Studio doesn't have a snapstore to uninstall and reinstall.

---

