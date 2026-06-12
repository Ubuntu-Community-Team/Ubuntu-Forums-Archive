---
title: "Upgrade option to 9.04 - how many mega bytes?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by culmore on 2009-04-27
Hi

If I download the ISO file I think it is around 600mega bytes. But if I press upgrade option in the "update manager" how many mega byte will that be?

I ask this as I have a slow internet connection. I assume my slow connection doing a download for hours is no issue/problem on the server side??

I did search for this but could not find an answer

thanks for reading.

---

### Post by cariboo on 2009-04-27
The LiveCD is about 699Mb. Depending on what programs you have installed, it is pretty hard to say what size the download will be. If you want to check what siaze the download will be, Press Alt-F2 and type:

```
gksu update-manager -d
```

This will tell you how large the download will be.

---

### Post by culmore on 2009-04-27
Thanks Caribu for the fast reply.

I should have mentioned I don't have much installed in 8.10 just the core packages that come as standard and a a few extras like skype, python,

When I run that command I get the upgrade manager. But I don't see any figure for the amount of data to be downloaded. I see the option to upgrade. If I run that command in a console I get

gksu update-manager -d
No ask_pass set, using default!
xauth: /tmp/libgksu-y0GdXd/.Xauthority
STARTUP_ID: gksu/update-manager/6657-0-culmore_TIME2777734
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: update-manager
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-y0GdXd/.Xauthority
xauth_env: /home/paul/.Xauthority
dir: /tmp/libgksu-y0GdXd

---

