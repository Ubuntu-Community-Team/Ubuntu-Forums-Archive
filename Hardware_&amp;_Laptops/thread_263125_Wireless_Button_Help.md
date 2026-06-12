---
title: "Wireless Button Help"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Istrancis on 2006-09-22
Yo everyone! I want to install a Linux distro on my HP nx6110 notebook that I just got there last Monday (I won it, W00T!), and I think that Kubuntu might be the right operating system for me. I want to dual boot with Windows XP, so any advice that anyone could offer there would be appreciated.

Anyway, my real question is about the wireless button on my laptop. I got onto the 'Net wirelessly from here (the laptop), but the blue light that indicates whether wireless is switched on or not is unresponsive. The button doesn't seem to respond to being pressed either. I know that this isn't a huge deal, but still, I'd like to get it working, so any advice that anyone could offer would be much appreciated. Thanks in advance.

---

### Post by CELI-Nux on 2006-09-22
Hey hello,

Had the same problem with my HP/Compaq nc8000 with a Intel Corporation PRO/Wireless 2200BG (rev 05) (try the '**[COLOR="Red"]lspci[/COLOR]**' command in a terminal window for your particular wireless card).  Anyway, here is the workaround (for my card at least):

[LIST][COLOR="Red"]
[*]open up a terminal console (Applications -> Accessories -> Terminal)
[*]sudo su (once in terminal)
[*]cd /sys/bus/pci/drivers/<your_card_probably_ipw2200/<your_model_probably_0000:02:04.0> (try some voodoo 'ls -l' command magic here)
[*]cd to the correct directory (ultimately try the 'find / -name led' command)
[*]look for a file name "led" and edit it with 'vim' (vim led)
[*]change the '0' for a '1' (must be a little bit familiar with 'vim' - use 'i' to insert than save using <esc> + wq! - this equates to "write-quit-force(bang))[/COLOR][/LIST]

Your blue led should now be up and running.  If so, and should you want to make this permanent, you'll have to modify your **/etc/rc.local** file to look something like this (remember, this example is only pertinent for my own material - yours could be different):

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[B][COLOR="Red"]# Activate ipw2200 LED button on HP-Compaq nc8000 (D.Celi: 2006-09-15)
echo 1 > /sys/bus/pci/drivers/ipw2200/0000:02:04.0/led
[/COLOR][/B]

exit 0

---

### Post by Istrancis on 2006-09-23
Thanks a lot CELI Nux, I appreciate the help. I'll check it out and see if it works, and if it does I'll be sure to post back here. Thanks again! ;)

---

### Post by sanicki on 2007-11-15
Quick fix did not produce results on my nx6110 but /etc/rc.local/led and reboot has me seeing blue. Thanks!

---

