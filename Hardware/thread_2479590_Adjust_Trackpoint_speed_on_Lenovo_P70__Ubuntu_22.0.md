---
title: "Adjust Trackpoint speed on Lenovo P70 / Ubuntu 22.04"
date: 2022-09-29
forum: Hardware
---

### Post by ts1971 on 2022-09-29
Hi,

I recently had to replace a failed keyboard on my Lenovo P70 running Ubuntu 22.04.  Generally, everything is working fine, with one exception.  The trackpoint (eraser in the middle of the keyboard) is VERY slow and I can't figure out how to adjust it.  First I tried turning the speed up for both the touchpad and the mouse in the 'mouse and touchpad' settings dialog.  The touchpad changes did take effect, though I don't use the touchpad so that's not much help.  I don't use an external mouse, but I did confirm that those settings had no effect on the trackpoint.  I've googled around a lot and tried a couple of things, but it seems like most of the suggestions are pretty old at this point, I'm skeptical that they are still relevant to 22.04.  

Here is the output of 'input':
> 
ThinkPad-P70:~$ xinput
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:16                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:16                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:16                id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:16                        id=9    [slave  keyboard (3)]

It's not even clear to me if one of those devices is the trackpoint.  If so, which one?  

Anyway, if anyone has any suggestions about how I could move forward here, I'd really appreciate it!

Thanks

---

### Post by csae2608 on 2022-10-09
there have been solutions given in the past, you could check here and try if a solution works for you; 
[https://askubuntu.com/questions/37824/what-is-the-best-way-to-configure-a-thinkpads-trackpoint](https://askubuntu.com/questions/37824/what-is-the-best-way-to-configure-a-thinkpads-trackpoint)
good luck.

---

