---
title: "Touchpad not working"
date: 2018-11-26
forum: Hardware
---

### Post by sneakyhox on 2018-11-26
Hello everyone. Having a slight issue here with 18.04

So I am having an issue where my xinput is showing that it recognizes my Touchpad, but it isn't working at all. I tried using the FN+F9 (enable/disable) touchpad, and the monitor shows the icon for enabling/disabling of the touchpad, but it still does not work. Below is my xinput:

> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Asus Keyboard                               id=13    [slave  pointer  (2)]
&#9116;   &#8627; Asus Keyboard                               id=14    [slave  pointer  (2)]
&#9116;   &#8627; ELAN1203:00 04F3:301E Touchpad              id=15    [slave  pointer  (2)]
&#9116;   &#8627; ckb1: Corsair Gaming SCIMITAR RGB Mouse vKB    id=18    [slave  pointer  (2)]
&#9116;   &#8627; ckb1: Corsair Gaming SCIMITAR RGB Mouse vM    id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Asus Wireless Radio Control                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627;             Logitech              Logitech Z205      id=10    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam: USB2.0 HD             id=11    [slave  keyboard (3)]
    &#8627; Asus Keyboard                               id=12    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=16    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    &#8627; Asus Keyboard                               id=20    [slave  keyboard (3)]
    &#8627; ckb1: Corsair Gaming SCIMITAR RGB Mouse vKB    id=21    [slave  keyboard (3)]
    &#8627; ckb1: Corsair Gaming SCIMITAR RGB Mouse vM    id=22    [slave  keyboard (3)]


As you can see above, it shows the &#8627; ELAN1203:00 04F3:301E Touchpad              id=15    [slave  pointer  (2)]

I tried looking around for how to fix this and I stumbled on someone else who was having trouble and it was suggested to make the following changes:
> 

 
[LIST=1]
[*] Try the below command and if it is not detecting touchpad     in the output then it means Ubuntu don't support your touchpad     unfortunately.

     less /proc/bus/input/devices 
[*] After that or if you have already done step 3 you can try      
     sudo rmmod i2c_hid
sudo modprobe i2c_hid 
[*] If it is showing your touchpad you have to edit the     configuration file for GRUB.
     sudo nano /etc/default/grub     and replace
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"     with      
     GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"     save the file and exit, then run
      sudo update-grub     and restart your laptop. 
[/LIST]

[LIST=1]
[*]I tried doing that but it still did not fix the issue. Can anyone help me with this? 
[/LIST]

---

