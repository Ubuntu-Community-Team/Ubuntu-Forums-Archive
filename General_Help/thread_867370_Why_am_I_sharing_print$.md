---
title: "Why am I sharing print$ ???"
date: 2008-07-22
forum: General Help
---

### Post by komputes on 2008-07-22
Looking at the network, I can see that a newly installed computer is has a share called print$ which (when I log in) contains two directories: W32X86 and WIN40 (which are directories located /var/lib/samba/printers).

This computer does have samba and samba-common but I never set up a share or a printer. Can someone help me to understand why this is here? I do not want to be broadcasting presence on the network.

---

### Post by komputes on 2008-07-22
I tried going into Sys > Admin > Printing and deleting the printer named PDF, yet this share remains. While I'm at it, does anyone know how to list local smb shares via command line. I have tried "smbclient -L" but that just spits back usage guidelines.

---

### Post by Brando569 on 2008-07-22
use smbtree to list shares, check the man pages for more options and install system-config-samba to help you configure samba shares. hopefully this helps.

---

### Post by komputes on 2008-07-23
smbtree is great, thank you for this. Although I never did set up a print$ share, this is what I get:

$smbtree

WORKGROUP
        \\HOST                      babyblue server (Samba, Ubuntu)
                \\HOST\IPC$                 IPC Service (host server (Samba, Ubuntu))
                \\HOST\print$               Printer Drivers

I am still not sure how or why this share got automatically set up.

---

