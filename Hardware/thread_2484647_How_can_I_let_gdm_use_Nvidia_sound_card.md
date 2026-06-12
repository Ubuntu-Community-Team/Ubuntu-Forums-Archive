---
title: "How can I let gdm use Nvidia sound card?"
date: 2023-03-05
forum: Hardware
---

### Post by luffyx on 2023-03-05
Hi community,

I would like to play sound at the gdm login screen. It works fine with the headphone, however, it does not work if I would like the monitor to play the sound at the gdm login screen (monitor has sound after login, but not before login in). The monitor is connected to the Nvidia gpu by HDMI cable.

I think by default, gdm does not have access to the GPU sound card, is there an easy to give it the access?
I tried ```
sudo -H -u gdm bash -c 'aplay -l'
```  and the output is ```
aplay: device_list:274: no soundcards found...
```
I also found a similar post [https://bbs.archlinux.org/viewtopic.php?id=223615](https://bbs.archlinux.org/viewtopic.php?id=223615) in which op said > [COLOR=#333333][FONT=sans-serif] but so far I still cannot output HDMI audio in my display manager[/FONT][/COLOR], which I believe is exactly the same problem I am facing.

Any help would be much appreciated.

---

### Post by #&amp;thj^% on 2023-03-05
need to see this:
```
loginctl seat-status
```

---

### Post by luffyx on 2023-03-05
Hi thanks for helping, please see below:
```

seat0
    Sessions: *13
     Devices:
          &#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
          &#9474; input:input1 "Power Button"
          &#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
          &#9474; input:input0 "Power Button"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:06.0/0000:07:00.0/leds/phy0-led
          &#9474; leds:phy0-led
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.1/usb1
          &#9474; usb:usb1
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.1/usb1/1-5
          &#9474;   usb:1-5
          &#9474;   &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.1/usb1/1-5/1-5.3
          &#9474;     usb:1-5.3
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.1/usb2
          &#9474; usb:usb2
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3
          &#9474; usb:usb3
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2
          &#9474;   usb:3-2
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1
          &#9474;   &#9474; usb:3-2.1
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.0/0003:046D:C547.0002/input/input2
          &#9474;   &#9474; &#9474; input:input2 "Logitech USB Receiver"
          &#9474;   &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3
          &#9474;   &#9474;   input:input3 "Logitech USB Receiver Keyboard"
          &#9474;   &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3/input3::capslock
          &#9474;   &#9474;   &#9474; leds:input3::capslock
          &#9474;   &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3/input3::compose
          &#9474;   &#9474;   &#9474; leds:input3::compose
          &#9474;   &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3/input3::kana
          &#9474;   &#9474;   &#9474; leds:input3::kana
          &#9474;   &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3/input3::numlock
          &#9474;   &#9474;   &#9474; leds:input3::numlock
          &#9474;   &#9474;   &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.1/3-2.1:1.1/0003:046D:C547.0003/input/input3/input3::scrolllock
          &#9474;   &#9474;     leds:input3::scrolllock
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3
          &#9474;   &#9474; usb:3-2.3
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4
          &#9474;   &#9474; &#9474; input:input4 "Boardsource Technik-O"
          &#9474;   &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4/input4::capslock
          &#9474;   &#9474; &#9474; &#9474; leds:input4::capslock
          &#9474;   &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4/input4::compose
          &#9474;   &#9474; &#9474; &#9474; leds:input4::compose
          &#9474;   &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4/input4::kana
          &#9474;   &#9474; &#9474; &#9474; leds:input4::kana
          &#9474;   &#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4/input4::numlock
          &#9474;   &#9474; &#9474; &#9474; leds:input4::numlock
          &#9474;   &#9474; &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.0/0003:4273:0079.0005/input/input4/input4::scrolllock
          &#9474;   &#9474; &#9474;   leds:input4::scrolllock
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.1/0003:4273:0079.0006/input/input5
          &#9474;   &#9474; &#9474; input:input5 "Boardsource Technik-O Mouse"
          &#9474;   &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.1/0003:4273:0079.0006/input/input6
          &#9474;   &#9474; &#9474; input:input6 "Boardsource Technik-O System Control"
          &#9474;   &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.3/3-2.3:1.1/0003:4273:0079.0006/input/input7
          &#9474;   &#9474;   input:input7 "Boardsource Technik-O Consumer Control"
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.4/3-2.4:1.0/input/input23
          &#9474;   &#9474; input:input23 "HD Pro Webcam C920"
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.4/3-2.4:1.0/media0
          &#9474;   &#9474; media:media0
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.4/3-2.4:1.0/video4linux/video0
          &#9474;   &#9474; video4linux:video0 "HD Pro Webcam C920"
          &#9474;   &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.4/3-2.4:1.0/video4linux/video1
          &#9474;   &#9474; video4linux:video1 "HD Pro Webcam C920"
          &#9474;   &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb3/3-2/3-2.4/3-2.4:1.2/sound/card2
          &#9474;     sound:card2 "C920"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb4
          &#9474; usb:usb4
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/0000:03:08.0/0000:08:00.3/usb4/4-2
          &#9474;   usb:4-2
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.0
          &#9474; [MASTER] pci:0000:0b:00.0
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.0/drm/card0
          &#9474; &#9474; [MASTER] drm:card0
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.0/drm/renderD128
          &#9474;   drm:renderD128
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0
          &#9474; sound:card0 "NVidia"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input10
          &#9474; &#9474; input:input10 "HDA NVidia HDMI/DP,pcm=7"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input11
          &#9474; &#9474; input:input11 "HDA NVidia HDMI/DP,pcm=8"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input12
          &#9474; &#9474; input:input12 "HDA NVidia HDMI/DP,pcm=9"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input13
          &#9474; &#9474; input:input13 "HDA NVidia HDMI/DP,pcm=10"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input14
          &#9474; &#9474; input:input14 "HDA NVidia HDMI/DP,pcm=11"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input15
          &#9474; &#9474; input:input15 "HDA NVidia HDMI/DP,pcm=12"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:03.1/0000:0b:00.1/sound/card0/input9
          &#9474;   input:input9 "HDA NVidia HDMI/DP,pcm=3"
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.3/usb5
          &#9474; usb:usb5
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.3/usb6
          &#9474; usb:usb6
          &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1
          &#9474; sound:card1 "Generic"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input16
          &#9474; &#9474; input:input16 "HD-Audio Generic Front Mic"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input17
          &#9474; &#9474; input:input17 "HD-Audio Generic Rear Mic"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input18
          &#9474; &#9474; input:input18 "HD-Audio Generic Line"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input19
          &#9474; &#9474; input:input19 "HD-Audio Generic Line Out Front"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input20
          &#9474; &#9474; input:input20 "HD-Audio Generic Line Out Surround"
          &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input21
          &#9474; &#9474; input:input21 "HD-Audio Generic Line Out CLFE"
          &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:08.1/0000:0d:00.4/sound/card1/input22
          &#9474;   input:input22 "HD-Audio Generic Front Headphone"
          &#9500;&#9472;/sys/devices/platform/eeepc-wmi/input/input8
          &#9474; input:input8 "Eee PC WMI hotkeys"
          &#9500;&#9472;/sys/devices/platform/efi-framebuffer.0/graphics/fb0
          &#9474; graphics:fb0 "EFI VGA"
          &#9500;&#9472;/sys/devices/virtual/misc/kvm
          &#9474; misc:kvm
          &#9500;&#9472;/sys/devices/virtual/misc/rfkill
          &#9474; misc:rfkill
          &#9492;&#9472;/sys/devices/virtual/misc/uinput
            misc:uinput



```

---

### Post by #&amp;thj^% on 2023-03-05
I can't find my notes kept from 4 years ago, but something like described here: [https://forums.developer.nvidia.com/t/howto-multiseat-with-ubuntu-16-04-systemd-gdm-proprietary-drivers/42864](https://forums.developer.nvidia.com/t/howto-multiseat-with-ubuntu-16-04-systemd-gdm-proprietary-drivers/42864)
I remember it being very problematic though, are you sure you want to this?

---

### Post by luffyx on 2023-03-10
Thank you for providing the link. Is multiseat mandatory for letting gdm play sound before logging in?

---

