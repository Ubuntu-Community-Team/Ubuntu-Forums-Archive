---
title: "Problem with lpadmin when setting up Brother HL-1240"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by Zeno Cosini on 2006-01-15
Hi everybody,

I am currently trying to set up a Brother HL-1240 under Ubuntu Breezy Badger. I have installed the foomatic-gui printer installation tool, which I have to start as "root" in order to be able to add new printers (otherwise the "+" is greyed out). As root everything seems to work fine, the printer at the parallel port is detected automatically, and I am able to select the recommended hl1250 driver. However, when clicking "Activate" in the last window ("Almost done!") the printer is not added to the foomatic-gui main window. 

When starting foomatic-gui from the console, I get some output related to the problem:

Use of uninitialized value in substitution (s///) at /usr/share/perl5/Foomatic/DB.pm  line 3432.
lpadmin: add-printer (enable) failed: client-error-forbidden
Could not set up/change the queue "hl1240"!
Usage: /etc/init.d/cupsd {start|stop|restart|force-reload}
invoke-rc.d: initscript cupsys, action "reload" failed.

I have added root to the lpadmin group, so root should have the necessary rights. As for line 3432 in DB.pm, it reads
    $tmpl =~ s!\@\@IEEE1284\@\@!$ieee1284!g;

Does anybody have an idea how to solve this problem? Any help is highly appreciated.

Thanks.

---

### Post by aysiu on 2006-01-15
I have the exact same printer and don't remember having to do any of that.  I just went to System > Administration > Printing and double-clicked "Add Printer." That was it.

---

### Post by Zeno Cosini on 2006-01-15
Thanks for your response, aysiu.

System > Administration > Printing is what I tried at first. However, in the Add a Printer dialog, the printer is not listed as detected. The second option ("Use another printer by specifying a port") is not possible, because the list of ports is empty. See the attached screenshot. 

Which of the two options did you use?

---

### Post by Zeno Cosini on 2006-01-23
I have now found out what the problem was: I am using my notebook at university as well as at home.  At university, I printed via a print server, and therefore, I had a ServerName defined in my /etc/cups/client.conf file. While the comments in that file state that only one sever name (and hence one server) can be specified at a time, I did not know that even local printers are not recognized if some remote host is specified.

Setting up the university printers as network printers (without connecting to the print server) solved the problem: I can now have local and network printers at the same time.

---

