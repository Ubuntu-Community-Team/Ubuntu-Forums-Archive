---
title: "Dell touchpad - scroll not always working lubuntu 16.06 LTS"
date: 2016-12-26
forum: Hardware
---

### Post by steve234 on 2016-12-26
Morning all,

I have installed Lubuntu 16.06 LTS on a Dell XPS laptop to use as a dedicated video edit machine (using blender).

I'm getting very irritated with it as the touchpad scroll (a little sidebar, not a two-finger job) does not always work each time I log-in.

I followed another post to re-install the drivers (remove and then reinstall xserver-xorg-input-synaptics) and that worked for a few logon sessions, but now it's broken again.

My xinput uptput is this - the touchpad has ID 13:
```
$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Broadcom Corp                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 ALPS GlidePoint                        id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=9    [slave  keyboard (3)]
    &#8627; Broadcom Corp                               id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys   

```

I've cycled (enable / disable ID: 13) and it has not helped. 

Is there a permanent fix?

---

