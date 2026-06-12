---
title: "Acer Aspire One 722 TouchPad Issue"
date: 2012-05-21
forum: Hardware
---

### Post by anirbanghosh on 2012-05-21
I have recently bought Acer Aspire One 722 Netbook with AMD C60 processor. 
But the touchpad is not working in Ubuntu 12.04 although USB Mouse (Logitech) is working fine.  Following is the output of ***xinput ***command.

```
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam                                      id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)]
```

Is there any solution to the problem? Any help shall be highly appreciated.

---

### Post by kazano on 2012-08-16
I've got the same problem, so pleeeease find and give us a solution.

---

### Post by spetz on 2012-08-19
This may fix your problem it did for me, is pressing fn+f7 it disables the touch pad. So you may just need to press fn+f7 to re-enable it.

---

