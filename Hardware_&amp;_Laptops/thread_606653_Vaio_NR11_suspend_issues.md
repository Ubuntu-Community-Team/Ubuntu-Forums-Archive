---
title: "Vaio NR11 suspend issues"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by sect2k on 2007-11-08
I just got a brand new Sony Vaio NR11Z laptop. FIrst i installed the amd64 version of gutsy on it, and suspend worked.

After having some issues with some applications, I decided to install the 32-bit version.

Now suspend doesn't work any more. It goes to sleep, but after resuming, it just prints "Linu" on the display and stops there. Before (64-bit version), it printed "Linux!" and resumed just fine.

I assume it has something to do with some drivers that weren't available in the  64 bit version, and are causing problems in the 32bit one.

I've checked all the logs in syslog viewer and found nothing relevant.

Any help is welcome.

---

### Post by rvarnam on 2007-11-08
I've just done a clean install of Gutsy on my Sony Vaio TX1XP.  Having had Feisty on it before, working brilliantly, I now find that neither suspend nor hibernate work - I closes as far as a blank screen with an inactive cursor, but doesn't actually suspend or hibernate.

---

### Post by toddwbucy on 2007-11-08
I too am having the same problem on a Toshiba A105-S4164.  It goes to suspend and resumes with a yellow "Linu" then nothing.  Have to do a hard reboot to reset.  no ctr-alt-del

Todd

---

