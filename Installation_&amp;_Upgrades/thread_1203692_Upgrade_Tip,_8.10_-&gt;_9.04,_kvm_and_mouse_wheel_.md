---
title: "Upgrade Tip, 8.10 -&gt; 9.04, kvm and mouse wheel scroll problem"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Eeqmcsq on 2009-07-03
I just upgraded from ubuntu 8.10 to 9.04, ran into this problem again, and solved it. Hope this tip helps others.

If your mouse is connected to a KVM switch instead of directly to the computer, the mouse scroll wheel might cause erratic behavior. This is most noticeable in Firefox, where the mouse scroll wheel might cause Firefox to move back a page or forward a page as though the back or forward buttons where pushed.

One solution in 8.10 was to edit the file "/etc/modprobe.d/options" and add the line "options psmouse proto=imps" to the end of the file, which worked well enough for me.

The problem occured when I upgraded to 9.04. For whatever reason, the "options" file was renamed to "options.dpkg-bak", which seemed to be ignored. As a result, the kvm mouse scroll problem came back.

The solution: Create your own file with any file name, such as "mymouse_scroll_kvm_fix", in "/etc/modprobe.d/" and add "options psmouse proto=imps" to it. Then reboot and retest to make sure this fix works permanently.

---

### Post by stoian on 2010-01-04
> **Eeqmcsq said:**
> The solution: Create your own file with any file name, such as "mymouse_scroll_kvm_fix", in "/etc/modprobe.d/" and add "options psmouse proto=imps" to it. Then reboot and retest to make sure this fix works permanently.

In Karmic 9.10 this messes up the boot.

---

