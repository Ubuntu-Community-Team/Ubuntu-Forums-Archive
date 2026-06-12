---
title: "Touchpad not working (HP 255 G2 Notebook PC ) (3.13.0-57-generic)"
date: 2015-07-15
forum: Hardware
---

### Post by e-trifonidis on 2015-07-15
Hi

my xinput list:
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=12    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=13    [slave  keyboard (3)]

I Open up the terminal and insert:-

sudo gedit /etc/default/grub

and on the line GRUB_CMDLINE_LINUX=""

change it to:-

GRUB_CMDLINE_LINUX="i8042.noloop"

close and save and run in the terminal:-

sudo update-grub reboot

Did not fix my problem,please help.

---

### Post by e-trifonidis on 2015-07-15
When i login after Shut down and take off the battery touchpad works ok.

---

