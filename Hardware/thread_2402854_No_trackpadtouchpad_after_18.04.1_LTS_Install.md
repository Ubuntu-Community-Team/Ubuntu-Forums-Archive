---
title: "No trackpad/touchpad after 18.04.1 LTS Install"
date: 2018-10-05
forum: Hardware
---

### Post by jojojohn on 2018-10-05
Hey guys

Been having a lot of problems trying to find a solution to why my trackpad doesn't work at all (no touch or buttons work).
 
I have a no brand laptop (Direkt Tek DTLAPY116-2). Everything on the laptop works other than the trackpad not working. External mouse works

I've found this ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1776155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1776155)) but still am having no luck.

Not sure what else I should try, any suggestions?

This is what I get from xinput:

jj@jj-DTLAPY116-2:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Hewlett Packard HP Wireless Keyboard Kit Consumer Control    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Hewlett Packard HP Wireless Keyboard Kit    id=12    [slave  pointer  (2)]
&#9116;   &#8627; 04F3200A:00 04F3:2606                       id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Hewlett Packard HP Wireless Keyboard Kit    id=8    [slave  keyboard (3)]
    &#8627; Hewlett Packard HP Wireless Keyboard Kit System Control    id=10    [slave  keyboard (3)]
    &#8627; Hewlett Packard HP Wireless Keyboard Kit    id=11    [slave  keyboard (3)]
    &#8627; USB 2.0 PC Camera: PC Camera                id=13    [slave  keyboard (3)]
    &#8627; 04F3200A:00 04F3:2606 Pen                   id=15    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=16    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=17    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=18    [slave  keyboard (3)]
    &#8627; Hewlett Packard HP Wireless Keyboard Kit Consumer Control    id=19    [slave  keyboard (3)]
jj@jj-DTLAPY116-2:~$ 

I believe 04F3200A:00 04F3:2606  is the trackpad, but I have no idea how to get it installed.
Thoughts?

---

### Post by Autodave on 2018-10-05
Did you do a clean install or did you upgrade from an earlier version?

---

