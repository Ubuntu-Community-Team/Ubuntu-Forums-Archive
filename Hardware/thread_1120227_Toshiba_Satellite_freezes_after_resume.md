---
title: "Toshiba Satellite freezes after resume"
date: 2009-04-08
forum: Hardware
---

### Post by cudaman73 on 2009-04-08
So my problem isn't that I can't get the laptop to suspend/resume, It does that just fine. I was having the issue with the keyboard/touchpad not working on resume, but I appear to have gotten that issue fixed (I can log back in upon resume).

I even have gotten the issue with wireless not working after resume fixed. In theory, everything works.

The problem is that once the laptop resumes, I have about a minute in which the laptop functions normally, but then ubuntu hardlocks. No response from mouse/keyboard, programs that are running freeze completely. This, of course, is only fixed by a hard reboot.

I've scoured both these forums and google searching for a similar issue, but I can't seem to find anybody else that is having this issue. For most, once they get resume and/or wireless working, everything is peachy.

Where do I need to start looking to find out why it keeps freezing on resume? Any logs I need to take a look at/post?

For reference, I have modified /etc/default/acpi-support, whitelisting fglrx, changing SAVE_VBE_STATE and POST_VIDEO to false (default: true), and uncommenting DOUBLE_CONSOLE_SWITCH=true. 

These changes fixed the resume issue, leaving the wireless not working and the laptop hardlocking after resume.

I have installed linux-backports-modules-intrepid for the "updated wireless stack", fixing the issue with wireless not working after resume, but now I am stumped as to what's causing the laptop to lock up after resume. I haven't specifically timed it, but I would estimate I can use the laptop for 45 seconds to a minute before it freezes.

Any ideas?

---

### Post by jom2000 on 2009-04-14
I have a similar problem with my desktop. It uses the 690G chipset with integrated ATI graphics.

This problem happens with the proprietary graphics drivers. It freezes shortly after resume. 

With the open source drivers, it works after resume.

---

