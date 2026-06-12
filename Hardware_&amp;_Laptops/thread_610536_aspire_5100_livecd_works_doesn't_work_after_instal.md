---
title: "aspire 5100 livecd works doesn't work after install"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by monkeyking on 2007-11-12
Got an acer aspire 5100

Hi I had a working 6.10 installed and decided to install 7.10.
I didn't do a upgrade since I had trouble on other computers doing an upgrade.

The laptop can use the livecd everything semms to work, like  sound, wifi.

But after install I can't boot, or the boot hangs.
I tried changing the /etc/usplash.conf, but that didn't change anything.

I can boot the system in ubuntu failsafe.
But that is as far as it'll go.

Does anyone have any idea on what might be the problem.
Or which log files to look into.

thanks in advance

---

### Post by monkeyking on 2007-11-12
Hi again,
I can elaborate somewhat more now.

I tried the ctrl+alt on the boot,
and it seems to hang either with loading keymap or running rc.local
But after pressing enter, I can log in,
I then tried the startx command,
which complained allot.

After triying to read some log files,
I decided that I wanted to reboot,
and then I saw the nifty ubuntu logo, that made me somewhat happy,
Then I realised that this it was just the usplash.

btw, I also tried the gdm command, but that told me gdm was allready running
So I still don\t have any idea on the problem

---

### Post by monkeyking on 2007-11-12
I fixed the problem.

After I realized that gdm was running,
I just copyied over the xorg.conf, created by the live cd.

And now everything works.

---

