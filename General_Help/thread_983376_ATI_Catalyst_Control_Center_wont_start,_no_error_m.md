---
title: "ATI Catalyst Control Center wont start, no error msg."
date: 2008-11-15
forum: General Help
---

### Post by cellv14 on 2008-11-15
Hello!

ATI Catalyst Control Center will not start once pressed upon.
It will not give me error msg, it simply wont do anything.

I need it to put my resolution to 3840x1080.
"Yes im mad, but running MAtrox Dualhead, and yes it works"

Running Ubuntu fully updated. Installed drivers with Envy, and yes it works like a charm. But CCC won't work like a charm, it wont start at all. "worked in 8.04"

Any help will result in a big thanks.

---

### Post by shmish on 2008-12-06
Did you ever fix or solve this problem?

thx

---

### Post by Fionnzer on 2009-08-09
I have the exact same problem. SOmeone please help. Thanks!

---

### Post by PHaLaNX on 2009-10-16
Same thing here, the driver setup created 4 links for CCC in KDE menu, none of them works. There is no error message or anything.

---

### Post by driven1 on 2010-02-17
I have the same issue. Catalyst launches but remains inactive. Anyone resolve this issue?

---

### Post by gewone on 2010-12-14
Running Ubuntu 10.10. Same issue.

Anyone?

---

### Post by 4Orbs on 2010-12-14
The below, in a terminal, should launch the control center as root user.
```
gksudo amdcccle
```
EDIT: I should also add that sometimes it doesn't launch on the first attempt. Odd.

---

### Post by kroem on 2011-01-04
Same problem here...

---

### Post by Bright_View on 2011-01-26
> **kroem said:**
> Same problem here...

I had this problem after updating to 10.10, and I found a 'solution' that worked for me.  

None of the shortcuts worked, and neither did typing 'gksudo amdcccle' in a terminal.  

What I did do to get it working was open nautilus as root:

gksudo nautilus

then navigate to /usr/lib/fglrx/bin

and double click on the binary 'amdcccle'

I could then configure my monitors.  I'm sure someone more clever may be able to figure out why I have to do this.  

Hope this helps you guys.

Dave.

---

### Post by SundeepG on 2011-02-14
I managed to fix my problem. After running gksu amdccle, the launch failed and the error message displayed that I had an Invalid Section Class in my /etc/x11/xorg.conf file. I had manually added an entry to enable SHMConfig a while back when I was trying to fix multi-touch on my touchpad. Anyways, since the entry was obsolete I simply removed it (have to edit as sudo) and then restarted. Before making any changes to xorg.conf, it is a good idea to copy it to a backup file, ie xorg.conf.bak in case of any problems.

AMD Catalyst Control Center now works both from the command-line and the System->Preferences links. For anyone else having problems, I recommend searching synaptic for "ati" and reinstalling every associated package, especially fglrx. Then restart, run "gksu amdcccle" from the terminal, and document any errors messages you receive so that someone can help you out.

---

