---
title: "Dell touchpad not working at all in Ubuntu 14.04 or 15.04...PLEASE HELP"
date: 2015-08-24
forum: Hardware
---

### Post by timothy-j-neill on 2015-08-24
PREFACE.....I am not a programmer or computer wiz.  I love UBUNTU because of the idea of a simplistic, free OS that is completely unlocked.  I say this so you can tailor your advice based on my knowledge of computers.

I recently bought a DELL Inspiron 14 laptop, installed 14.04 and the touchpad was not working at all.  No movement, no clicks, nothing.  I upgraded to 15.04 thinking that there might be a patch, but no luck, still doesn't work.  I can, or course, still use an external, but I hate to be reliant on an external mouse.  

Please help.

---

### Post by aymen3 on 2015-08-24
You may have to update your drivers. Is it dual booted?

---

### Post by weatherman2 on 2015-08-24
What make/model of Dell is it?

What's the output of these two terminal commands?  (Control Alt t key combo to open a terminal.)

```

sudo lspci
sudo lshw

```

I suggest you go back to Ubuntu 14.04 LTS for stability, as it will be supported until 2019, whereas 15.04 support will end in January 2016 and you'll have to upgrade to get further support.

---

### Post by weatherman2 on 2015-08-24
Also, are you sure the touchpad isn't disabled in hardware?  There may be a function key combo (Fn + some function key) to toggle the touchpad enabled/disabled.  I know many people who disable their laptop touchpad because they use an external mouse all the time.  The OS can't re-enable it if that's the case.

---

### Post by xshadorx on 2015-09-10
When I type **xinput**, I get this:
> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; DLL0651:00 06CB:2985                        id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]


, where "DLL0651:00 06CB:2985" probably implies my Dell Inspiron 15 touchpad is not recognized in Ubuntu 15.04. However, it worked fine in 14.04. Is there any way of fixing it? I've followed the instructions from [https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html](https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html) already, but it didn't help. Also, the buttons on the touchpad work, so it's definitely not disabled.
Thanks!

UPDATE: it seems **sudo modprobe -r i2c_hid **and rebooting did the trick. Now the trackpad is working again, even though it looks exactly the same in **xinput **output.

---

