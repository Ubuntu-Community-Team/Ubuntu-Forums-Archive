---
title: "Touchpad much less usable after moving to 24 from 22"
date: 2024-12-05
forum: Hardware
---

### Post by Linux_newbie_no1 on 2024-12-05
I'm using a fairly old laptop (Lenovo G580) and recently, after installing a new SSD, decided to install U24 rather than U22 which was running on it previously. However, compared to the touchpad options in System Settings in 22, the options in 24 are severely limited e.g. setting edge width, setting tap pressure, configuring tap behaviour (e.g. corner tap for right click) all missing. Having run xinput list I notice that the touchpad is shown as an Elantech touchpad:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294609&stc=1[/IMG]

Now I'm pretty sure that in my previous U22 install the touchpad was treated as a Synaptic device, which I'm assuming is why there were so many additional config options available. As such, is there any way I can replace the current Elan device drivers with Synaptic device drivers and restore the touchpad functionality I previously enjoyed?

---

### Post by Linux_newbie_no1 on 2024-12-07
Bump? I've had a look on Lenovo's website, they do list a set of drivers: [https://support.lenovo.com/gb/en/downloads/ds028212-touchpad-driver-synaptics-elan-for-microsoft-windows-7-32-bit-64-bit-lenovo-g480-2688-20156-g580-2689-20157](https://support.lenovo.com/gb/en/downloads/ds028212-touchpad-driver-synaptics-elan-for-microsoft-windows-7-32-bit-64-bit-lenovo-g480-2688-20156-g580-2689-20157). 

Would it be stupid to install these using Wine?

It's becoming increasingly frustrating that upgrading my version of Ubuntu has left me with a less usable system.

---

### Post by Linux_newbie_no1 on 2024-12-10
OK, I'm obviously asking the wrong questions............

Using the synaptic drivers on U22 I was able to set config values using the command prompt, and to create config files which loaded at start-up. From reading around I believe that synaptics no longer works by default in Ubuntu (what a great decision, I guess that's what they call 'progress'..............) and touchpad drivers are now handled by libinput, which is woefully short on configuration options (again, great decision............). However, the multiple threads on how it *might* be possible to install synaptics and then force the touchpad to use the synaptics drivers instead of libinput are confusing, contradictory and full of comments along the lines of 'I tried this and my keyboard stopped working'. Which makes me very reluctant to try it, being so inexperienced in this Ubuntu lark. So, can anyone give me a clear, simple, step by step guide to how to install synaptics drivers, force my system to use those over libinput, but not bork my system? Thank you

---

### Post by Linux_newbie_no1 on 2024-12-12
Perseverance...........

OK, simplifying my request a bit, there are two things I want to do:

1) Reduce the touchpad sensitivity
2) Slightly increase the portion of the right side of the touchpad that I can use for scrolling

Anyone got any ideas?

---

### Post by Irihapeti on 2024-12-12
These forums are closing in a few weeks. It's likely that the people who can help you have already migrated to Ubuntu Discourse, so I suggest you might be better off posting in the [Support and Help]("https://discourse.ubuntu.com/t/ubuntu-discourse-policy-change-technical-support-topics-are-now-welcome/49981") section there. All the best!

---

### Post by ajgreeny on 2024-12-12
Not sure if this might help but have a good read through [https://manpages.debian.org/buster/xserver-xorg-input-synaptics/synaptics.4.en.html](https://manpages.debian.org/buster/xserver-xorg-input-synaptics/synaptics.4.en.html) to see if you get any clues.

---

### Post by Linux_newbie_no1 on 2024-12-20
Thank you, I shall have a look, and head over to Ubuntu Discourse.  Cheers!

---

