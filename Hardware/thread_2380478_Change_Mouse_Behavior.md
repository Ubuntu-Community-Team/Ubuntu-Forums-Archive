---
title: "Change Mouse Behavior"
date: 2017-12-18
forum: Hardware
---

### Post by a-wiekens on 2017-12-18
I'm using a Bluetooth touch enabled mouse with Ubuntu and notice that  it has some extra keyboard mappings in it, that have no practical use  for me. Left swipe on the mouse gives a 'd' and right swipe gives an  Backspace. I have try to alter the key mapping with xinput and input-kdb  but without any luck so far. I'm using 16.04

  ```
$ xinput list "ThinkPad Bluetooth Touch Mouse"
ThinkPad Bluetooth Touch Mouse                 
       Reporting 6 classes:
            Class originated from: 10. Type: XIButtonClass
            Buttons supported: 7
            Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
            Button state:
            Class originated from: 10. Type: XIKeyClass
            Keycodes supported: 248
            Class originated from: 10. Type: XIValuatorClass
            Detail for Valuator 0:
              Label: Rel X
              Range: -1.000000 - -1.000000
              Resolution: 1 units/m
              Mode: relative
            Class originated from: 10. Type: XIValuatorClass
            Detail for Valuator 1:
              Label: Rel Y
              Range: -1.000000 - -1.000000
              Resolution: 1 units/m
              Mode: relative
            Class originated from: 10. Type: XIValuatorClass
            Detail for Valuator 2:
              Label: Rel Vert Wheel
              Range: -1.000000 - -1.000000
              Resolution: 1 units/m
              Mode: relative
            Class originated from: 10. Type: XIScrollClass
            Scroll info for Valuator 2
              type: 1 (vertical)
              increment: -1.000000
              flags: 0x2 ( preferred )

```

Disabling the buttons didn't help (mapping them to 0), the various characters were still generated.

  Using input-kbd to make changes to the keymapping resulted in a error.

  ```
$ sudo input-kbd 6
/dev/input/event6
bustype : BUS_BLUETOOTH
vendor  : 0x17ef
product : 0x6063
version : 87
name    : "ThinkPad Bluetooth Touch Mouse"
phys    : "9c:b6:d0:ec:e1:c4"
uniq    : "f0:65:dd:b0:b6:d5"
bits ev : EV_SYN EV_KEY EV_REL EV_MSC EV_REP

map: 12 keys, size: 19/64
0x90001 = 272  # BTN_LEFT
0x90002 = 273  # BTN_RIGHT
0x90003 = 274  # BTN_MIDDLE
0x70006 =  46  # KEY_C
0x70007 =  32  # KEY_D
0x7002a =  14  # KEY_BACKSPACE
0x70014 =  16  # KEY_Q
0x7002b =  15  # KEY_TAB
0x700e3 = 125  # KEY_LEFTMETA
0x700e0 =  29  # KEY_LEFTCTRL
0xc0224 = 158  # KEY_BACK
0xc0225 = 159  # KEY_FORWARD

```  Creating a file with 0x70007 = 240 mapping the d to KEY_UNKNOWN causes a 


  ```
$ sudo input-kdb -f keymap 6
/dev/input/event6
map: 12 keys, size: 19/64
scancode 458759 out of range (0-19)

```
 
Is there another way of mapping these keyboards input stemming from the mouse, somehow?

---

