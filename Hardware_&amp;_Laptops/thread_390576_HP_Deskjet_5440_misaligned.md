---
title: "HP Deskjet 5440 misaligned"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by PereUbu on 2007-03-22
Hi there!

I have a problem with my HP Deskjet 5440. When I print text it is blurry with a grey shadow. Photos/pictures are clearly dotted. I have tried to align my cartridges with the hp-toolbox without any luck.

According to openprinting.org it is supposted to work perfectly. 
See: [http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5440](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5440)

A search on the HPLIP mailinglist was not giving me the solution either...
[http://search.gmane.org/?query=alignment&author=&group=gmane.comp.printing.hplip.user&sort=relevance&DEFAULTOP=and&xP=alignment&xFILTERS=Gcomp.printing.hplip.user---A](http://search.gmane.org/?query=alignment&author=&group=gmane.comp.printing.hplip.user&sort=relevance&DEFAULTOP=and&xP=alignment&xFILTERS=Gcomp.printing.hplip.user---A) 
...except there seems to be more people having the same trouble getting nice prints form the DJ 5440.

Anybody know what to do?

Best regards
Pere Ubu

---

### Post by 11hjpphty76lkjj on 2007-03-23
I haven't seen any specific problems with the DeskJet 5440.  Can you try connecting the printer to a windows box and see if it has the same print problem?  Possible to try a different ink cartridge?

---

### Post by PereUbu on 2007-03-23
Hi kalosaurusrex,
thanks for the tip.

The printer works fine in windows, so there is no need to change cartridges. 

I have the same problem as this poster on the HPLIP mailinglist:
[http://thread.gmane.org/gmane.comp.printing.hplip.user/606](http://thread.gmane.org/gmane.comp.printing.hplip.user/606)

It's just not possible to get the alignement right with the alignement utility in the HP-toolbox. You can do it over and over again, and it ends up misaligned every time. 

Maybe there is a problem with the driver?

I hope somebody has a solution for my HP DJ 5440. :) 

/Pere Ubu

---

### Post by PereUbu on 2007-03-30
Hi kalosaurusrex

I think I have found out what the problem is. Please see my reported bugs:
[https://bugs.launchpad.net/ubuntu/+bug/98920](https://bugs.launchpad.net/ubuntu/+bug/98920)
[https://bugs.launchpad.net/ubuntu/+bug/98909](https://bugs.launchpad.net/ubuntu/+bug/98909)

As you see I get good print quality when printing a testpage through the HP-toolbox utility, but not from the gnome printing utility. 

How are HP-toolbox (which I think uses th HPLIP driver), and the gnome printing utility (which is using the HPIJS driver) related? 

How can I get the same good results through the gnome printing utility using my default printer?

/Pere Ubu

---

### Post by 11hjpphty76lkjj on 2007-03-30
Hmm not sure.  I'll have a look at your bugs.  :)

A

---

### Post by ramjet_1953 on 2007-03-31
Check this out, it may help.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5440](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5440)

Regards,
Roger :cool:

---

### Post by PereUbu on 2007-04-02
I filed a bug on this and got my problem solved! :) 

Run hp-align - the command line alignment utility and it works.

More info on the bug here:
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/98920](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/98920)

/Pere Ubu

---

