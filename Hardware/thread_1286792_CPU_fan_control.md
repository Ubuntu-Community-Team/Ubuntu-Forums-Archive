---
title: "CPU fan control"
date: 2009-10-09
forum: Hardware
---

### Post by sjosh_theone on 2009-10-09
I have searched a lot on this issue bt to no avail . Till now. 

I own a Toshiba Satellite L505D-S5965. Whn i installed Jaunty , initially after 15-20 mins CPU fan used to go out of control ,rotating at its full speed making hell of a noise. Its worth noting that when it booted the fan never turned on.

I thought of updating my kernel .Initially it was 2.6.28-11-generic and now it is 2.6.28-15-generic.

Now when i boot , fan works at a constant speed with very, very low noise. I am really happy. Ubuntu is too good to be sacrificed. 

Hope updating kernel works for you all. 

PS:- But the CPU fan wont start when i restart my PC after suspending it. So i never suspend it. Sorry for the "go green" enthus.

---

### Post by tacoboye on 2009-12-11
I have the same laptop and I fixed this issue by passing commands to GRUB boot.  Now I would show you my boot config, but I have forgot what I did to change the boot style..... Actually, I may have found it: 

Run "sudo gedit /etc/default/grub" and see if your file is different than mine....specifically on this line that says Grub Commandline Linux Default = quiet splash acpi_osi=force.  I believe changing these options helped me somewhat, but then again, I could be talking out my *** given that was like 2 kernels ago...I wish I REALLY knew linux instead of knowing very little lol.

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=force"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


Good luck, I hope I helped.
-james

---

### Post by spud1 on 2010-01-19
I was hoping you might help me I got the same laptop but when I upgraded to 9.10 my cpu over heats and shuts down

---

### Post by anoknusa on 2010-01-22
Golly friggin' gee, all, I own the same machine and have been searching for a solution to this for almost four months.  Diggin' through the dregs of the internet, here's what I've found:* jack all.* I started with jaunty and the fan seemed a little finicky, but since I upgraded to karmic I've been having problems.  If my processor is running full-tilt, my fan sometimes won't start at all *unless* I suspend and then restore my session, at which point the fan itself would run full-tilt.  I've found a few scripts that I haven't really tried (though i plan to, and lm-sensors doesn't even work anyway), and I'll post those; but be warned: our particular model is returned to the manufacture for repair under warranty for overheating problems more than all other problems combined.  We may be looking at an otherwise good machine that's just doomed to die young.

Here's what I've seen; good luck.
[http://danamlund.dk/eee-control/eee-control.html](http://danamlund.dk/eee-control/eee-control.html)
[http://www.linux.org/docs/ldp/howto/Ecology-HOWTO/ecology-howto-power-management.html](http://www.linux.org/docs/ldp/howto/Ecology-HOWTO/ecology-howto-power-management.html)

P.S: Not sure when you folks got your boxes, but there was a BIOS update in October or November that I've yet to download.  Anyone tried that?

---

