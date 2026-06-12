---
title: "please help me"
date: 2008-11-27
forum: General Help
---

### Post by giuspen on 2008-11-27
i installed ubuntu 8.04 but didn-t see my user in the login window,
ubuntu told me i have too low uid in /etc/passwd 
so i tried to change that text document from

beppe-nastya:x:500:500:beppe-nastya,,,:/home/beppe-nastya:/bin/bash
libuuid:x:501:501::/var/lib/libuuid:/bin/sh

to

beppe-nastya:x:503:503:beppe-nastya,,,:/home/beppe-nastya:/bin/bash
libuuid:x:501:501::/var/lib/libuuid:/bin/sh

but my shell died, i tried to reboot but can-t login.
now i-m on live/cd but can-t edit the text file back cause have no permissions... please help me :(

---

### Post by caljohnsmith on 2008-11-27
Can you simply reinstall at this point? Ubuntu shouldn't complain about a user having "too low a UID" if all goes well during the installation, so I think I would reinstall if I were you. Do you know what you might have done during or right after the installation that would cause that?

---

### Post by giuspen on 2008-11-27
> **caljohnsmith said:**
> Can you simply reinstall at this point? Ubuntu shouldn't complain about a user having "too low a UID" if all goes well during the installation, so I think I would reinstall if I were you. Do you know what you might have done during or right after the installation that would cause that?

i just installed fedora core 10 (very disappointed from it) then install the 8.04, and i'm up with this problem my user isn't visible in login window.
now i'm in again into ubuntu from the hard disk, i tried safe boot, i opened the terminal and was able god knows how to remember 2 commands to edit the text file back to 500:500

---

### Post by giuspen on 2008-11-27
now i kept user 500:500
and put down minimum from 501 to 500 and he tells me:
"the user does not exist" when i try to add to the login window.
incredible.

---

