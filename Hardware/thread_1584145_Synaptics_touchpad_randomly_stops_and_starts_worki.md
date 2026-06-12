---
title: "Synaptics touchpad randomly stops and starts working"
date: 2010-09-28
forum: Hardware
---

### Post by INH on 2010-09-28
Hi all,
I've been using Lucid for a few months now, and I like it a lot - except for this little problem I have with my touchpad.  

I have a Compaq CQ-50 215NR laptop, with: 
Athlon 64 X2 QL-60 1.9GHz processor 
3GB of RAM 
160GB HDD 
and a Synaptics touchpad.  

My problem is as follows:  My touchpad works fine right after I start up.  However, at some random point, it will stop working abruptly and a notification will appear at the top right with a little icon that looks like a touchpad with a red X over it.  Then, at some random point later, the same notification will appear, except without the red X, and the touchpad will start working again.  I can start the touchpad working after it stops by running the following command:  ```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

However, running that stops my hardware switch to turn the touchpad on/off from working.  

Does anybody know what might be causing this?

---

