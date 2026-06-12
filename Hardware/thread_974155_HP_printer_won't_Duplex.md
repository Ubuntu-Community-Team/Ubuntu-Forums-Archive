---
title: "HP printer won't Duplex"
date: 2008-11-07
forum: Hardware
---

### Post by Pauldgh on 2008-11-07
I've just started with a fresh install of Heron 8.10 and when I've tried printing duplex on my HP 1012, it won't do it. The printer was identified and the driver was installed without a hitch, and for the most part it works perfectly. When I was trying to print from Adobe Reader 8.0 it allowed me to choose duplex on the printer properties, but then wouldn't do it. It just prints as if duplex was not selected.

I've tried reinstalling the driver with no effect. 

I'm using a thinkpad T42.

Any thoughts?

---

### Post by phidia on 2008-11-07
Have you installed the hplip-gui package? If you haven't install that and setup your printer through that.

---

### Post by Pauldgh on 2008-11-07
Just did, and I reinstalled the printer through HPLIP toolbox. It allowed me to set duplex as a default printing option. Still no change, however. I just tested it with openoffice word and it still doesn't duplex.

---

### Post by phidia on 2008-11-07
Sorry-that seems like it should have worked. I would try resetting everything & rebooting but assuming that doesn't get it working you can see if anyone has resolved duplexing issues for your printer at the [open printing forums]("http://forums.openprinting.org/index.php?18") or perhaps at [HP's linux site]("http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html").

---

### Post by fromgi on 2008-11-07
I don't think it's your HP.  I have the same problem with a Brother laser.  I checked CUPS "([http://localhost:631](http://localhost:631) and its properly setup and identified.  I never had this issue with 8.04.

---

### Post by phidia on 2008-11-07
> **fromgi said:**
> I don't think it's your HP.  I have the same problem with a Brother laser.  I checked CUPS "([http://localhost:631](http://localhost:631) and its properly setup and identified.  I never had this issue with 8.04.

Have you filed a bug report?

---

### Post by Pauldgh on 2008-11-09
I've checked CUPS, and have reset everything. I'm guessing this isn't going to go away easily. I will try duplexing with another printer to see if it is specific to my HP. I'll file a bug report regardless. Thanks to all.

---

### Post by FredVanH on 2010-02-15
[SIZE=3]I'm having the same problem with my HP C6180 all-in-one with an HP Automatic Two-Sided printing Accessory installed.  My O/S is Ubuntu 9.10.  First the Fax wouldn't install;   so I fixed that by    	[/SIZE] 	 	[FONT=KacstLetter][SIZE=4][FONT=Nimbus Roman No9 L, serif][SIZE=3][SIZE=4]downloading and installing hplip-3.9.12 from [http://hplipopensource.com/](http://hplipopensource.com/).  Now, in the Writer Print dialog | Properties | Paper | Duplex dropdown list, there are only two choices - "Off" and "<ignore>".  On my first time in the print dialog I set Properties | Device | Duplexer Installed to "Installed" but I still cannot get any duplex lip service or operation.  This feature worked ok with another O/S.  Any leads?
Thanks,  Fred
[/SIZE][/SIZE][/FONT][/SIZE][/FONT]

---

