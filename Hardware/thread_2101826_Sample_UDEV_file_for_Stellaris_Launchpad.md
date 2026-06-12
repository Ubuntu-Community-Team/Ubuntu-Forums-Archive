---
title: "Sample UDEV file for Stellaris Launchpad"
date: 2013-01-05
forum: Hardware
---

### Post by nesslersreagent on 2013-01-05
Hi,

I'm trying to get my **Stellaris Launchpad** to work with the **Energia IDE**.
I'm told to upload programs and to run the serial port I've got to **create a udev entry**.

I'm relatively new to linux (although not Ubuntu) so could anyone please provide me with a **sample udev file**.

My Stellaris board's on port /dev/ttyACM0, VID=1cbe and PID=00fd.

As of now I'm using the attached udev file(text file).

It's as follows ->

# This file allows non-root access to TI stellaris launchpad
# See udev(7) for syntax.
#
SUBSYSTEM=="usb",ATTRS{idVendor}=="1cbe",ATTRS{idProduct}=="00fd",MODE="0666"
KERNEL=="ttyACM0",ATTRS{idVendor}=="1cbe",ATTRS{idProduct}=="00fd",MODE="0666"
#   

Thanks in advance

---

### Post by nesslersreagent on 2013-01-07
**Problem solved**.

For those with the same or a similar problem. Here's the simple solution.

**Step 1:** Add your username to the "dialout" group. In terminal type,
           ```
sudo adduser <username> dialout
```**Step 2:** Create a udev (eg: 61-stellpad.rules)  file in the directory: /etc/udev/rules.d/ 
           with the contents as,
           ```

SUBSYSTEM=="usb", ATTRS{idVendor}=="1cbe", ATTRS{idProduct}=="00fd", MODE="0666"

```**Step 3:** Save, unplug and replug the Stellaris board. All done.

**[Note]:** The solution was provided by a fellow Stellaris Launchpad user - Bernard. 
           Works perfectly now.

Cheers.

---

### Post by krish2487 on 2013-01-27
Hello Nessler

Thanks for the post.
It helped me fix the same problem I ve had with my stellaris 
on ubuntu.

However I used only the first 

```

# This file allows non-root access to TI stellaris launchpad
# See udev(7) for syntax.
#
SUBSYSTEM=="usb",ATTRS{idVendor}=="1cbe",ATTRS{idP roduct}=="00fd",MODE="0666"
KERNEL=="ttyACM0",ATTRS{idVendor}=="1cbe",ATTRS{id Product}=="00fd",MODE="0666"
# 
```

It did not work for me initially.

However after looking carefully i noticed this

> SUBSYSTEM=="usb",ATTRS{idVendor}=="1cbe",**ATTRS{idP roduct}=="00fd"**,MODE="0666"

The space between the P and r in "Product" made the udev rules ineffective.

Once, that was fixed then the original udev rule you posted works just fine.

Ditto with the "kernel" line too!!

---

### Post by nesslersreagent on 2013-02-09
Hi [krish2487]("http://ubuntuforums.org/member.php?u=1140626"),

Thanks for that. 
I actually had copied it from an online post. It had never occurred to me before though.

---

