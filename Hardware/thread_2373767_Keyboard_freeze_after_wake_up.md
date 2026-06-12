---
title: "Keyboard freeze after wake up"
date: 2017-10-09
forum: Hardware
---

### Post by foxreymann on 2017-10-09
I run Xubuntu 17.10 on Lenovo 470s. I put the laptop to sleep with:


$ xfce4-session-logout --suspend


and wake up with power button. After the wake the keyboard doesn't work. To make it work I need to open some menu with a mouse, get to some input fields, and it starts working. I've tired all solution I've found online but none of them works. So what I did is:


1. created /lib/systemd/system-sleep/keyboard file with


case $1/$2 in
  pre/*)
    echo "Going to $2..."
    # Place your pre suspend commands here, or `exit 0` if no pre suspend action required
    modprobe -r usbhid
    ;;
  post/*)
    echo "Waking up from $2..."
    # Place your post suspend (resume) commands here, or `exit 0` if no post suspend action required
    sleep 2
    modprobe usbhid
    ;;
esac


2. I did


$ sudo apt-get install --reinstall xserver-xorg-input-all


multiple times


3. I've modified /etc/default/grub with


GRUB_CMDLINE_LINUX_DEFAULT="atkdb.reset i8042.nomux quiet splash"


Nothing works. No change at all. Please help!

---

### Post by martinr on 2017-10-10
Hi foxreymann,

Are you sure that it is only the keyboard? I'm also experiencing a frozen keyboard after resume from suspend, but that is triggered / caused by using the touchpad. Can you try to not touch the touchpad at all after resume and see if the keyboard still works?

Furthermore some dmesg loggin after resume might be helpful. ($ dmesg > dmesg.out).

Cheers,

BTW I looked up your [Thinkpad]("https://www3.lenovo.com/us/en/laptops/thinkpad/thinkpad-t-series/T470s/p/22TP2TT470S"). Nice Hardware!!! 
What a shame that XUbuntu won't run on it out of the box.
Is it possible to get the Thinkpad without Windoze 10 (the nightmare continues) OS and not pay for it either?

---

### Post by foxreymann on 2017-10-10
thank you for the only reply Martinr.

I've fixed the issue by unisntalling Xscreensaver. I has been weird that after wake up I had to log in twice. I didn't know why and it gave me the idea of just doing 

$ sudo apt remove x-screensaver

now  the laptop works perfectly:)

The laptop is nice and I don't care about Windows. I always buy second hand Thinkpads with Windows and remove Windows ASAP:)

---

### Post by martinr on 2017-10-11
I'm glad you were able to fix it and thanks for sharing.
It would've been a waste not to have been able to run XUbuntu on such a fine piece of hardware.
(BTW your rig must be lightning fast with XUbuntu  I expect).

---

