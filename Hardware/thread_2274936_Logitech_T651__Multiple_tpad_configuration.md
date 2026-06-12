---
title: "Logitech T651 / Multiple tpad configuration"
date: 2015-04-23
forum: Hardware
---

### Post by llucmillat on 2015-04-23
Hello,

I just bought a logitech T651 trackpad and I'm trying to configure it via Xinput and Synclient. Everything works great until I want to set the configuration permanent by modifying the file 50-synaptics.conf on /etc/X11/xorg.conf.d
The problem is I don't want to overwrite the configuration I've already set for my laptop trackpad (MBook Air 4.2), and the parameters in this file seem to rule all synaptics touchpads.

Anybody knows a solution for this?

Thanks a lot!

---

### Post by dino99 on 2015-04-23
hm, xorg.conf.d might not be the good place now as the system has full control over it
a related (old) thread with the same device [http://ubuntuforums.org/showthread.php?t=2006375](http://ubuntuforums.org/showthread.php?t=2006375)

---

### Post by llucmillat on 2015-04-23
Thanks dino99,

I've tried to find the files mentioned on the thread you quote (/lib/udev/rules.d/95-keymap.rules) with no success.
Also they seem to discuss an older Logitech device there, but I imagine the solution may be similar.

I'm going to try a few things more and I'll write another reply when I'll find a solution.

Thanks again!

---

### Post by llucmillat on 2015-04-23
I think I have it.
To make permanent the changes set via Synclient:

1) You need to copy the file 50-synaptics.conf from /usr/share/X11/xorg.conf.d to /etc/X11/xorg.conf.d
2) Then, edit it adding the following at the end:

[COLOR=#ff0000]Section "InputClass"
    Identifier "Logitech T651"
    MatchProduct "Logitech Rechargeable Trackpad T651"
    MatchDriver "synaptics"
    Option "OptionName*" "value*"
Endsection[/COLOR]

*For every option and value set using synclient

3) It is usefull to test the touchpad capabilities and settings using "xinput -watch-props ID" on the command line. To get the device ID, "xinput -list".

It worked for me, so I'm going to mark it as solved.

---

### Post by dino99 on 2015-04-23
> **llucmillat said:**
> I think I have it.
To make permanent the changes set via Synclient:

1) You need to copy the file 50-synaptics.conf from /usr/share/X11/xorg.conf.d to /etc/X11/xorg.conf.d
2) Then, edit it adding the following at the end:

[COLOR=#ff0000]Section "InputClass"
    Identifier "Logitech T651"
    MatchProduct "Logitech Rechargeable Trackpad T651"
    MatchDriver "synaptics"
    Option "OptionName*" "value*"
Endsection[/COLOR]

*For every option and value set using synclient

3) It is usefull to test the touchpad capabilities and settings using "xinput -watch-props ID" on the command line. To get the device ID, "xinput -list".

It worked for me, so I'm going to mark it as solved.

Sounds good ):P

---

