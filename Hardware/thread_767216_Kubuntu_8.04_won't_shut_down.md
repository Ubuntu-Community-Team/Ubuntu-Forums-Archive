---
title: "Kubuntu 8.04 won't shut down"
date: 2008-04-25
forum: Hardware
---

### Post by joshtheitguy on 2008-04-25
I've been using Kubuntu long since the first beta, my only issue is when I go to shutdown, logoff or reboot KDE will start to close then rather then shutting down, rebooting, or returning to the logon window the screen remains black. During this time the system will not respond to ctrl+alt+f1-12, ctrl+alt+backspace or ctrl+alt+del.

I have to force shut via the power button. The work around I found is to launch a terminal and do a sudo reboot or halt. Then the desktop manager successfully shuts down and the system reboots. Though no configuration settings stay when I do this.

Are there any log files anywhere on the system that might help me determine what is causing the system to not shutdown properly?

I forgot to mention it is a IBM T43.

---

### Post by justmenodupes on 2008-04-28
having the same problem on a fujitsu amilo m1405 (with ubuntu)

maybe related to these:
[https://bugs.launchpad.net/bugs/208479](https://bugs.launchpad.net/bugs/208479)
[https://bugs.launchpad.net/ubuntu/+bug/222056](https://bugs.launchpad.net/ubuntu/+bug/222056)

---

### Post by joshtheitguy on 2008-04-30
I tried everything they suggested but I think it has something to do with the ATI fglrx drivers.

---

### Post by justmenodupes on 2008-04-30
mmm... yeah, those are just related to intel drivers :(

---

### Post by kurisu_rs on 2008-05-05
I had this problem too and I think you might find a fix here:

[https://bugs.launchpad.net/bugs/211318](https://bugs.launchpad.net/bugs/211318)

I'll summarize:

The problem is that XDM_AUTH_MASK in /etc/ati/authatieventsd.sh points to the wrong place. It should be amended to read:

XDM_AUTH_MASK=/var/run/xauth/A$1*

Hope this helps :)

P.S. this will possibly not work until after a reboot

---

### Post by joshtheitguy on 2008-05-18
> **kurisu_rs said:**
> I had this problem too and I think you might find a fix here:

[https://bugs.launchpad.net/bugs/211318](https://bugs.launchpad.net/bugs/211318)

I'll summarize:

The problem is that XDM_AUTH_MASK in /etc/ati/authatieventsd.sh points to the wrong place. It should be amended to read:

XDM_AUTH_MASK=/var/run/xauth/A$1*

Hope this helps :)

P.S. this will possibly not work until after a reboot

worked flawlessly, thanks.

---

### Post by sgtkazz on 2008-09-26
I do not have ATI and have the same issue. I have searched for over two months to a resolution for this issue and 'nothing' I have done will work. I continue to have to hard down my machine w/ the power button. Does anyone, anywhere have an news on how to shutdown this release. 'shutdown -h now (no), logoff and click shutdown from the menu (no), init.o and shutdown (no), halt (no), nothing works.

---

