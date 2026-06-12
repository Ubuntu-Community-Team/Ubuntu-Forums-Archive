---
title: "Solution Deskjet 3320 series won't print"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by Agio on 2007-03-01
Hello!

This is a solution to the problem where a HP Deskjet 3320 printer that is detected and that the job is "printed", it still won't print, the paper goes in and out as white as milk. so I hope it helps some else =). Please note I only print black, and only have installed a black cartridge (the problem relied here at the end).
At least it got mine fixed, 

Printer: Deskjet 3325
Driver: The latest one for HP printer from ubuntu repository.  HPIJS (recomended).

Ok, so install the printer, configure it and afterwards, go into cups web interface. I did it through  
"$ hp-toolbox" (password for cups was the same as my user's), and there, change to the correct configuration. In my case, as I mentioned, I only use the black but cups didn't reflect this and had configured the color cartriedge, so no wonder the printer didn't print, save and print a test page. Bottom line is CUPS wasn't reflecting the settings that were set in the "add printer" GUI.

Hope this helps some one.

Regards.

---

