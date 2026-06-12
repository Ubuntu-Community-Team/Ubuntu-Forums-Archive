---
title: "HP F4240 printer issues"
date: 2008-10-21
forum: General Help
---

### Post by dgerwin11 on 2008-10-21
Here is an off the wall question from some one who is not totally conversant with computer operation.  I am on a new computer that was built to handle the apps I use, basic stuff like spreadsheets, surfing and email.  I told them not to install high end stuff for gaming, music downloads etc.  The shop downloaded Ubuntu to  Cd and them installed and configured the system.  Every thing is fine, except my HP F4240 All-in-One printer/scanner/copier won't print or scan.  I have gone thru these forums and to the HP web site.  All roads lead to terminal command "sh hplip-2.8.8.44.run" When I enter this, I always get "sh: can't open hplip-2.8.8.4.run"  What gives?

Is it possible that A) the download they did was corrupted
                    B) Or did they make a mistake in configuration.

I really want to keep using Ubuntu, as I so far find it superior to Windows, but also would like to print from this computer, ratherthan having to send files to another computer to print.

Finally, the off the wall question I promised you.  Should I go to Ubuntu site and re download Ubuntu to see if that resolves my printer issues?

Thanks
dgerwin11

---

### Post by neilengineer on 2008-10-21
Seems the hplip-2.8.8.44.run didn't have the permission to execute?
Try:

$sudo chmod +x hplip-2.8.8.44.run 
$sh hplip-2.8.8.44.run

---

### Post by kostkon on 2008-10-21
OK, I assume you need to install *hplip* to make your multifunction printer to work. Thus, you need to go to *Add/Remove* (*Applications -> Add/Remove*), select *All Available Applications* from the *Show* drop-down menu, search for it (i.e. search for "hplip") and then install it.

Then, go to *System -> Administration -> Printing* to setup your printer. Furthermore, go to *System -> Preferences -> HPLIP Toolbox* for a finer setup/control of your printer and scanner.

---

