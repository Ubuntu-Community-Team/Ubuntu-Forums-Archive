---
title: "Mozilla apps messed up"
date: 2008-10-06
forum: General Help
---

### Post by raysa on 2008-10-06
Thunderbird and Firefox were working fine. Then I followed instructions to instal Googlearth (which works OK but not brilliantly) and also instal some extra fonts.  But now Thunderbird crashes out if I click on any messages arriving in my inbox, and many (but not all) of website visited with Firefox don't come up properly (lots of text and links missing).
I don't really need Googlearth so would happily go back to where I was before. How can I repair the Moxilla apps?  
Thanks, Ray

---

### Post by ajgreeny on 2008-10-06
Just for the moment try renaming your hidden folders .mozilla and .mozilla-thunderbird in /home/username to see if that solves the problem.  Use Ctrl+H in nautilus if you can't find them, they should than appear.  If it does the trick, try adding back the files and folders from the old versions of .mozilla(-thunderbird) one by one until the problem re-appears again.  You will then know what is the problem and can remove the offending files if you need to.  Your old emails will still be in the old .mozilla-thunderbird folder so make sure you copy the mail folders across.  You may lose some of your configuration, but that may be a small price to pay.  Also perhaps worth removing googleearth as well if that really was the original cause.

---

### Post by raysa on 2008-10-06
Thanks. Removed Googlearth.  Renamed the .mozilla and .mozilla thunderbird folders.  Fired up the apps and noticed that new .mozilla and .mozilla thunderbird folders had been created.  But without moving any files at all from the renamed folders to the new ones, the apps are still giving the same problems - almost blank websites in Firefox, and Thunderbird instantly crashing out when messages clicked. 

Any other thoughts?

---

### Post by ajgreeny on 2008-10-06
Apart from removing the apps completely with synaptic and then reinstalling, I can't think what else to suggest.  Just make sure you have your old emails backed up somewhere, if you have not already done so.

---

### Post by raysa on 2008-10-06
Completely removed the Mozilla apps, re-booted the computer, then re-installed the apps and rebooted again. The newly-reinstalled apps are doing exactly as before. Looks like the problems are being imposed on the apps rather than being the apps themselves being faulty.

Opera and Konqueror both render websites OK, but not Firefox. Tried Evolution and it lets me read emails fine, so the problem seems to only effect the Mozilla apps.

Is it possible to undo all changes made over the past couple of days to get the system back to how it was before this happened?

---

