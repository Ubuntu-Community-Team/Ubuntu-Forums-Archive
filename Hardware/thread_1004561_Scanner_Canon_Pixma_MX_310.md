---
title: "Scanner Canon Pixma MX 310"
date: 2008-12-07
forum: Hardware
---

### Post by EmaLac on 2008-12-07
Hi,
I've just bought a multifunction Canon Pixma MX 310: it works percfectly but the scanner, I can use Xsane only as root.

I've looked for the permissions in /etc/group: my user has them for scanner and plugdev, maybe I need other permissions.

Any advices?

---

### Post by compu73rg33k on 2008-12-07
My MX310 doesn't even let me run it as root. When I try to start xsane I get ```
device `v4l:/dev/video0' is a Noname USB2.0 Camera virtual device

```
I get the same message for sudo scanimage -L

As far as getting it to work for all users, I think [this link may help](http://ubuntuforums.org/showthread.php?p=2656092)

> In order to make the scanner available for all users, you have to add the following rule to the '/etc/udev/rules.d/45-libsane.rules' file:
Code:
```

# Epson CX4000 | DX4000 | DX4050
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="664", GROUP="scanner"
```

Add these lines anywhere between the SUBSYSTEM and LABEL tags.

Apply the new rules:```

$ sudo /etc/init.d/udev restart
```

Obviously change the idVendor and idProduct to the values you get from running```
sane-find-scanner | grep USB

```

---

### Post by EmaLac on 2008-12-13
GREAT!!! It works, thanks a lot.

---

### Post by TRANQU111TY on 2009-01-03
Hey I'm a newb and I wanted to get my scanner function working on my Canon PIXMA MX310 aswell.

What do I need to put into the terminal?

Thanks for reading!

---

### Post by EmaLac on 2009-01-11
> **TRANQU111TY said:**
> Hey I'm a newb and I wanted to get my scanner function working on my Canon PIXMA MX310 aswell.

What do I need to put into the terminal?

Thanks for reading!


Sorry but I can't help you because... it doesn't work...

I don't have any *45-libsane.rules* and without it my printer works.
When I create that file my scanner works but the printer doesn't.

You can read in forums other users (with Epson or other printers) have had the same problem and they solved removing *45-libsane.rules*... but it isn't the right solution for me because I would come back to the beginning, when my printer worked and my scanner didn't .

I have been yet waiting for a solution. Sorry.

---

