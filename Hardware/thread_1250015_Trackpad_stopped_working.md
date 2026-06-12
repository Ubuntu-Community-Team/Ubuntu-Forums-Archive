---
title: "Trackpad stopped working"
date: 2009-08-26
forum: Hardware
---

### Post by MindVirus on 2009-08-26
I recently used Computer Janitor to remove unnecessary programs. Now my trackpad does not work at all. No clicking; no moving. The following is a list of programs that it removed. I put descriptions for packages that I think might have caused the issue.
[LIST]
[*]eeepc-config (configuration for my EeePC)
[*]gsynaptics-elantech (trackpad drivers!!!)
[*]libpt2.6.1
[*]libpt2.6.1-plugins-alsa
[*]libpt2.6.1-plugins-v4l2
[*]linux-eeepc-lean (kernel for EeePC, since replaced by linux-netbook-eeepc)
[*]linux-headers-eeepc-lean (headers for said kernel; also replaced)
[*]nvidia-177-modaliases
[*]rt2860-dkms
[/LIST]

None of these are available from any repository anymore AFAIK.

I had a huge hunch that it was gsynaptics-elantech for some reason -- not that it had my mousepad drivers or anything. I found gsynaptics-elantech.deb somewhere on Google and installed it. The trackpad still does not work after rebooting.

Furthermore, I tried `modprobe ftdi-elan` because it seems to have something to do with the trackpad driver. This doesn't help even after restarting GDM.

If anyone sees this page with a malfunctioning trackpad/mouse, press Ctrl+Shift+Alt+Numlock to use the numpad keys as a mouse (5 is click).

---

### Post by MindVirus on 2009-08-26
My solution was [here]("http://www.statux.org/wiki/index.php?title=EeePC_Optimizations"). I copied the InputDevice config and put "options psmouse proto=imps" into /etc/modprobe.d/eeepc.conf (you can choose whatever filename you want as long as it ends with .conf and is in /etc/modprobe.d).

---

