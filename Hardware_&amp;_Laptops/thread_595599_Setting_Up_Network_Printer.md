---
title: "Setting Up Network Printer"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by mgaskell on 2007-10-28
Help! I fried the master boot record on my Windows box when I used Gparted to move and resize partitions in preparation for a Gutsy install. Gutsy is now the only working OS on my desktop. I have a HP Laserjet printer with a D-Link print server hardware (DP-301P) on the parallel port attached to my LinkSys router via ethernet.

I don't know how to get Gutsy to see the network printer. The "add printer" setup asks for an address for the print server. I don't know how to get that. Nothing recognizes the print server in any auto config. I'm new at this and I cannot print to the Laserjet. The local Epson color printer connected via USB was recognized automatically. I need to use the Laserjet for heavy lifting printing and I want it on the network so I can print from my laptop wirelessly.

Can somebody point me to a thread or resource that I can use to set this up?

Thanks in advance.

---

### Post by daengbo on 2007-10-29
Try looking at the setup information at this page:
[http://www.fixya.com/support/p278017-d_link_dp_301p_dp_301p_print_server/manual-14218/page-8](http://www.fixya.com/support/p278017-d_link_dp_301p_dp_301p_print_server/manual-14218/page-8)
Follow all the web setup info, noting your print server's IP, workgroup, and printer name. Make sure you do all the tests recommended.

Once you've finished that, go to System -> Adminitration -> Printers and add a new printer. Choose samba printer and input the workgroup, IP, and printer name.

Print a test page.

Best of luck

---

