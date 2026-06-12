---
title: "How to get touchscreen working on Lenovo Ideacentre A720"
date: 2012-08-30
forum: Hardware
---

### Post by TommyHLW on 2012-08-30
Hey Ubuntu-friends,

I have a Lenovo Ideacentre A720 and using ubuntu 12.04 after a lot of hard work with installing everything by hand (graphic, sound, wlan, sd-card)


Sadly there is almost no experience  about ubuntu  on this device in the web 

I'd like to use the Multitouchscreen, just Monotouch would be als ok. 


It's a 27" CoolTouch(TM) from the Advanced Silicon S.A. Company [http://www.advancedsilicon.com/web/products/touchassps/cooltouch.html](http://www.advancedsilicon.com/web/products/touchassps/cooltouch.html)

xserver-xorg-input-evdev is installed

some more infos

    ```
$ xinput_calibrator 
    Error: No calibratable devices found.
  
``````

    $xinput list 
    &#9121; Virtual core pointer                          id=2    [master pointer  (3)]
    &#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
    &#9116;   &#8627; Logitech Unifying Device. Wireless PID:4017       id=9    [slave  pointer  (2)]
    &#9116;   &#8627; HID 0a5c:4503                             id=11   [slave  pointer  (2)]
    &#9116;   &#8627; Lite-On Technology Corp. Lenovo silver silk (wireless) 2.4G K&M kit           id=14   [slave  pointer  (2)]
    &#9116;   &#8627; Lite-On Technology Corp. Lenovo silver silk (wireless) 2.4G K&M kit       id=15   [slave  pointer  (2)]
    &#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
        &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
        &#8627; Power Button                              id=6    [slave  keyboard (3)]
        &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
        &#8627; Power Button                              id=8    [slave  keyboard (3)]
        &#8627; HID 0a5c:4502                             id=10   [slave  keyboard (3)]
        &#8627; Lenovo H264 720P Camera                   id=12   [slave  keyboard (3)]
        &#8627; Lite-On Technology Corp. Lenovo silver silk (wireless) 2.4G K&M kit       id=13   [slave  keyboard (3)]
        &#8627; AT Translated Set 2 keyboard
```

---

