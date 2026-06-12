---
title: "New printer prompts for password. Huh?"
date: 2010-07-28
forum: Hardware
---

### Post by GARoss on 2010-07-28
I have my printer, Epson Artisan 710, installed on a iMac setup to share. I have Ubuntu 10.04 running as a guest on Virtual Box & would like to print with the new Epson just as I did with my old Canon printer using the same setup. Epson provides Linux drivers & install went smooth. In setting up the new printer, the only way I could connect to the printer was through samba so I found & selected the printer, then found the driver. It asked to test print a page & in doing so, it prompted me for authentication name & password. No matter what I type in it fails. In Printer State it says "Idle - Tree connection failed (NT_STATUS_ACCESS_DENIED).

I didn't have these issues with my old printer with the same setup. What gives? Any ideas?

---

### Post by GARoss on 2010-07-28
With a little trial & error I was able to satisfy the password prompt. Samba is for Windows but I have a Mac. I can't explain why my printer was found there but it was. Mac likes passwords so I used the exact name of my Mac computer & password when prompted by Ubuntu printing & it all worked. :guitar:

---

