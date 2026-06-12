---
title: "ACPI for Toshiba Laptop"
date: 2009-02-02
forum: Hardware
---

### Post by Daug on 2009-02-02
Hello--

I've installed Hardy on my older Toshiba Satellite M20.  After a slight ACPI tweak (changing etc/default/acpi-support to ACPI_SLEEP_MODE=standby instead of "mem"), and installing WICD, things work pretty reliably (wifi is about 99%, and suspending upon lid-closing is about 75%.  However, the laptop won't sleep overnight without draining the battery, and I can't adjust the LCD brightness.  So, I'm looking for better ACPI support, and discovered the "fnfxd" utility on Synaptic Package Mgr.  It mentions needing CONFIG_ACPI and CONFIG_ACPI_TOSHIBA to be installed/activated.  Running "uname -r" in the terminal yields that I have kernel: "2.6.24-23-generic".  So, I should be good to go, but I'm not sure how to how to activate CONFIG_ACPI and CONFIG_ACPI_TOSHIBA.  Any advice?  Thanks!

---

### Post by rozbarwinek on 2009-02-12
Run the command: modprobe toshiba_acpi

Install the package: fnfxd

Edit the config file for fnfxd, /etc/fnfxd/fnfxd.conf and uncomment the lines for brightness action keys

Restart fnfxd.

And that's it! My Toshiba laptop now has functioning brightness hotkeys. I hope it works for you.

(instruction by: auberginepop)

---

### Post by attam on 2011-02-12
I had a similar problem with my Toshiba laptop function keys. They stopped working when I updated my Ubuntu kernel. I fixed it by following the instructions above, plus editing the etc/fnfxd/fnfxd.conf file by uncommenting the following lines
> action(key="Fn-F6";command="brightness down")
action(key="Fn-F7";command="brightness up")
Note: these lines appear twice in the file. The lines at the bottom were commented  with "#", so I removed that.
After restarting, my brightness keys (Fn+f6, Fn+F7) worked again.
Hopefully, Ubuntu developers will incorporate this fix into future builds.

---

