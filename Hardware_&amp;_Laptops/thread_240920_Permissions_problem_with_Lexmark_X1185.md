---
title: "Permissions problem with Lexmark X1185"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by MysticAurora on 2006-08-21
I installed xsane so I could use the scanning portion of my printer. When I did all the necessary setup to use with GIMP, I tried xsane out and got the following notice:

> Failed to open device `lexmark:libusb:001:004': Access to resource has been denied.

I then attempted to run xsane as root. It detected my printer's scanner just fine and I was even able to scan (though the quality kinda stunk, but that's probably nothing a tweak or two can't fix). Is there a way I can set up the printer to be accessible by anyone, or at least my main user?

I have the same permissions problem when I attempt to print, but I haven't attempted to print as root yet.

---

### Post by MysticAurora on 2006-08-28
I did a little tinkering around and now I can use my scanner with my normal user account. However, when I exit, it gives me three permission errors. I assume it attempts to save settings upon killing the process and I don't have access.

---

