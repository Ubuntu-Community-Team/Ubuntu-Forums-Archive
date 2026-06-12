---
title: "Suddenly Failed to load the NVIDIA kernel module! - reboot helped"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by lzap on 2007-10-31
Hello

today I have received this error and XOrg did not come up:

(EE) NVIDIA(1): Failed to load the NVIDIA kernel module! 

I did _not_ changed anything in my configuration, reboot helped - XOrg started and its running ok. No error in logfiles.

Anyone this error? Strange behaviour...

Thanks

---

### Post by bikegirl22 on 2007-11-02
I have this problem intermittently.  Sometimes it boots right into X and sometimes it hangs.

This is a brand new laptop with gutsy installed from factory.

They configured rc.local with:


/sbin/modprobe -r nvidia
sleep 2
/sbin/modprobe nvidia

so that it is loading last.

When it fails, I see this in the Xorg log:


(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"


Before that there are no errors.  Synaptic says that the new nvidia drivers are already
installed. Any help is appreciated.

---

### Post by tiga2001 on 2008-03-12
I had this problem, and I think the people who configured this was trying to hack it into working. It is true that by removing the module and modprobing it again it will sometimes work. But I think the main problem is that you have to load nvidia first, not last. So remove the lines in /etc/rc.local . Instead, edit /etc/udev/rules.d/90-modprobe.rules and add the following line

RUN+="/sbin/modprobe nvidia"

---

### Post by bikegirl22 on 2008-03-26
tiga2001 - Thank you! That seems to have fixed the problem.  I really appreciate it!

---

