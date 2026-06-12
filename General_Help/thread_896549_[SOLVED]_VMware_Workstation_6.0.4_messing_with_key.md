---
title: "[SOLVED] VMware Workstation 6.0.4 messing with keyboard for host"
date: 2008-08-21
forum: General Help
---

### Post by arch0njw on 2008-08-21
I run Windows XP SP3 in a VM from time to time to do things like watch Netflix movies on-line and other such things that only work under Windows.

Somewhere along the way, something happened to something.  I know, that is terribly specific.  I wish I had a good point in time to point at...

After I run any of my Windows VMs for a short bit and then move back to the host, they keyboard starts making very strange thinks happen.  For example, my Win+R (I know... I know...) closes windows.  ctrl+alt+return (full-screen vm) closes windows.  Just about any keyboard action with ctrl, alt, or win closes windows.  And some keys just stop working (e.g., R no longer types the character R, nor does anything as far as I can tell).

I have noticed no oddities in my logs.  Hmm...

Linux my_machine 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

VMware Workstation:  6.0.4 build-93057

I have also posted this over in the VMware communities.
[http://communities.vmware.com/thread/164428](http://communities.vmware.com/thread/164428)

---

### Post by arch0njw on 2008-08-22
Resolution is at that community thread.  But to repeat it here:

(run this command on the host OS; model, layout and options are in your /etc/X11/xorg.conf file)

For example:
$ setxkbmap -model pc105 -layout us,ru -option ",winkeys"

---

