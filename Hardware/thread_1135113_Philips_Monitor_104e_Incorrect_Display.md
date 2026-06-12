---
title: "Philips Monitor 104e Incorrect Display"
date: 2009-04-24
forum: Hardware
---

### Post by KhurramM on 2009-04-24
Hello, All.

I had my ub606 run on my current system w/o any display issue.

But for a clean install of ub804, I have wrong display of 1280x768

I use:

$ xrandr -s 1024x768 -r 60

$ gnome-session-save

The issue is solved, untill I reboot my machine to find out the display is back to 1280x768

I think this is the reason I get a blank screen after grub menu and before
login screen. There is no display at all.

This issue is at clean install. I havent yet installed anything else.

Next I even tried this:

goto 

displayconfig-gtk or others> Screens

the 104e Philips 13.3inch isnt available in the list.

So I tried here:

changing from generic + Monitor + Plug'n'Play

to generic + monitor + 1024x768

$ gnome-session-save

Trying System Restart

At restart it goes back to -s 1280x768 + generic + Monitor + Plug'n'Play

it should have been 1024x768, so whats the fault?

I execute:

$ xrandr -s 1024x768

Now it comes back.

Agian restart to give me the same issue.

Best Regards

---

### Post by KhurramM on 2009-04-27
Hi all

Just got my prblemo solved.

So i thoght I better post it for help of all:

_**I simply live run dapper, copied its xorg.conf to that of hardy.**_

...

**Al-Hamd-u-Lillah! It works superb now, without an error.**

Now I am loving Hardy. Catch u guys later.

Adios!!!.....

---

### Post by KhurramM on 2009-04-28
One thing I skipped, my boot wasnt showing, so I removed splash from:

/boot/grub/menu.lst

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd0,6)
#kernel         /boot/vmlinuz-2.6.24-23-generic root=UUID=108b2dc1-2927-4aec-91b5-312103f160fb ro quiet splash
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=108b2dc1-2927-4aec-91b5-312103f160fb ro quiet
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

Now the boot in text is shown to me.

---

