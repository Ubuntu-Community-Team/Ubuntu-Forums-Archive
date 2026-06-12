---
title: "Invalid xorg.conf leads to unkillable X server"
date: 2009-01-07
forum: Hardware
---

### Post by joeclarkia on 2009-01-07
I am trying to get an Ubuntu 8.10 system set up to do multiple monitors.  I have two PCI video cards installed.  The kernel sees both (via lspci -v | grep VGA), but xorg only sets up a screen on one (with the default empty xorg.conf file).

I have tried creating a specialized xorg.conf file with the settings necessary to put a screen/display on both monitors.  However, when I think I have it set up to send video to the second monitor, I end up with just two black screens. Much worse than this, I cannot kill the X server with ctrl-alt-backspace (or any other key combo), nor can I do ctrl-alt-F1 to get a command prompt.  The fan eventually kicks on, so it would seem that X is maximizing the CPU. The only way to get out seems to be ctrl-alt-delete, which initiates reboot.

Any ideas of what might be going on?  I'm most concerned about the unkillable X server -- since problems like this could potentially lead to an unbootable system (text-mode startup, then immediately go into unkillable-X-mode).  Seems like an X bug to me(?).

---

