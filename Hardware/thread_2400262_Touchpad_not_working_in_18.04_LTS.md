---
title: "Touchpad not working in 18.04 LTS"
date: 2018-09-04
forum: Hardware
---

### Post by boundule on 2018-09-04
[SIZE=3][COLOR=#242729][FONT=Arial]I have installed Xubuntu 18.04 LTS on my newly purchased low config laptop along side Windows 10 (duel boot).Everything of Installation was working fine but the Touchpad [/FONT][/COLOR]**SYNA3602 (0911:5288)**[/SIZE][COLOR=#242729][FONT=Arial][SIZE=3]is not working. In windows the touchpad works fine, so hardware should be ok. But in Xubuntu 18.04 it never worked.
[/SIZE]
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/jBb4O.png[/IMG]

[SIZE=3][COLOR=#242729][FONT=Arial]Here's the output of [/FONT][/COLOR][/SIZE][B][SIZE=3]xinput:[/SIZE]
```
boundule@PAW:~$ xinput
&#9121; Virtual core pointer                      id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; A4Tech USB Mouse                          id=8    [slave  pointer  (2)]
&#9116;   &#8627; SYNA3602:00 0911:5288 Touchpad            id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; USB 2.0 Web Camera: USB 2.0 Web           id=9    [slave  keyboard (3)]
    &#8627; Intel HID events                          id=11   [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                  id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
```
My System is:
```
System:    Host: PAW Kernel: 4.15.0-33-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31)
           Distro: Ubuntu 18.04.1 LTS
```

[/B]&#8203;[B][I]I have tried following command to solve the problem. It works instantly & found the touchpad working find. But after reboot again touchpad not working.
[/I][/B]```
sudo -i
echo 'on' > /sys/bus/i2c/devices/i2c-SYNA3602\:00/power/control
rmmod i2c_hid
modprobe i2c_hid
```
[COLOR=#242729][FONT=Arial]**How can I fix / solve this problem??**[/FONT][/COLOR]

---

