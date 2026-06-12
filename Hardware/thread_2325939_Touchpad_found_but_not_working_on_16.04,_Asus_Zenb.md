---
title: "Touchpad found but not working on 16.04, Asus Zenbook UX305UA"
date: 2016-05-26
forum: Hardware
---

### Post by dale21 on 2016-05-26
I just installed 16.04 recently, dual booting with Windows. The touchpad occasionally works, but sometimes when I boot up it doesn't - only reboot helps, and then only randomly.

Touchpad is Elantech, and computer is Asus Zenbook UX305UA.

 The weird thing is, the system recognizes the touchpad's existence. In system settings under Mouse & Touchpad, it shows me touchpad options. And the output of `xinput list` is:```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

I'm really desperate to get this worked out - I don't want to have to switch OS's to windows when I need to use the gui, and I don't think there are any other distros of linux that are likely to be any better about this issue than Ubuntu. This thread's kind of my last hope for being able to use Linux for my personal computer.

Thanks
Dale

---

### Post by dale21 on 2016-05-26
If this is something that can be fixed by changing some configurations, using some workaround script, anything, fine, I'll do it. If Ubuntu just doesn't support new laptops then fine, just someone please tell me what path to go down in figuring this out.

---

### Post by saou on 2016-05-29
1) Have you tried to install
   gpointing-device-settings
and turn on two-finger scrolling there?

2) According to
  [http://liliputing.com/2016/05/asus-zenbook-ux305ua-laptop-review-core-i5-skylake-model.html](http://liliputing.com/2016/05/asus-zenbook-ux305ua-laptop-review-core-i5-skylake-model.html)
two-finger scrolling does work in linux minut 16.04 after you turn on the appropriate setting.  

Do let us know if this works for your!

On a different:  How's your battery life under linux?  And what's your impression about the touchpad (after you activate it!) -- the review cited in #2 is lukewarm about the touchpad, at best.  Last but not least:  Are you able to get your machine into deep sleep beyond PC3?
   [http://mjg59.dreamwidth.org/41713.html](http://mjg59.dreamwidth.org/41713.html)

Thanks and good luck!

---

