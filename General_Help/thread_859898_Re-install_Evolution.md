---
title: "Re-install Evolution"
date: 2008-07-15
forum: General Help
---

### Post by MaindotC on 2008-07-15
I restored my /home folder and replaced the .evolution folder, among all the others, which I think is causing the problem.  I had a problem with firefox, so I uninstalled, deleted the .mozilla folder, then re-installed, and now it's good.  I'd like to try re-installing Evolution.  [This thread]("http://ubuntuforums.org/showthread.php?t=395199") says it's ok.  [This thread]("http://ubuntuforums.org/showthread.php?t=353973) says it's bad - both referencing the ubuntu-desktop package.  Can you advise the best way to re-install Evolution?

---

### Post by Elfy on 2008-07-15
I've removed other things that have removed ubuntu-desktop as well - it's not caused me a problem as I reinstalled ubuntu-desktop before I upgraded.

In your case you want to reinstall not remove, so assuming you haven't removed anything else that is part of ubuntu-desktop you have 2 options that I can see

1 - remove and reinstall evolution

2 - remove evolution and reinstall ubuntu-desktop, which should in theory reinstall evolution

If you upgrade rather than do a clean install perhaps option 2 would be better, assuming that it does in fact reinstall evolution for you.

---

### Post by MaindotC on 2008-07-15
What concerns me is that evolution by itself works fine, so it seems to me that the files associated with the evolution settings seem to be the culprit.  Therefore, if I re-install evolution that will simply re-install the program and not the files causing conflicting configurations.  Do you know if any files other than the .evolution folder should be deleted (if that folder at all)?

---

### Post by Elfy on 2008-07-15
I think if you purge evolution rather than just uninstall it then the only files which are left are those in the .evolution folder in your home.

You could try to rename the folder without the . and start evolution it should react as though it hadn't been used before - I think.

---

### Post by MaindotC on 2008-07-15
I've heard of the purge feature before - that's part of apt, right?  Is there a way to do it in Synaptic?

---

### Post by Elfy on 2008-07-15
I think that right click - _mark for complete removal_ is the same thing, but not sure.

I usually do it from terminal

sudo apt-get remove --purge *package*

If it says I need to run autoremove afterwards I do that.

---

### Post by MaindotC on 2008-07-16
I'm not sure if "complete removal" is the same as --purge, but in any event I'm still having problems.  I'm having a problem accessing the campus exchange server and I'm using the exact same settings as before I re-imaged.  I'm just going to wipe it all out and reformat.

One thing I have to remind myself is that once everything is all set and works perfectly, I can't mess with it.  Each time I've re-imaged, I got these bright ideas like replacing the current /home folder with the pre-re-image /home folder, or in other events it's been "let's download and install that ATI driver from the AMD site even though the restricted driver in the repos is working just fine" and then I'm stuck at 640x480 resolution forever and ever.

I'm not educated enough to troubleshoot these issues and it's all my fault for creating them.  Thanks for your help anyway.

---

### Post by MaindotC on 2008-07-16
I think this is a permissions issue.  This all started because I saved my /home folder on a separate partition.  When I re-installed, I did so using the exact same username.  Then, I replaced the current /home folder with the one that I saved.  Some of the folders had root ownership so I started nautilus as root and moved those folders.  Again, just one of those things I shouldn't have done.  I'm certain it's causing all these problems.

But damnit all, Urban Terror works so I'm gonna go hit some nubs.

---

### Post by dcstar on 2008-07-16
[LIST=1]
[*]Shut down Evolution
[*]Rename hidden .evolution folder
[*]Start Evolution (to create fresh folder)
[*]Shut down Evolution
[*]Copy data (like mail, Contacts etc.) from old folder to new folder
[*]Start Evolution
[/LIST]

---

### Post by MaindotC on 2008-07-16
So simple and so foolish of me to overlook this procedure!  Evolution did start properly and now I am connecting to the server and properly retrieving my email.  Thanks dcstart - I guess you have to be smarter than the keyboard on which you're typing to fix these problems.  I'm not sure what file has mail, contacts, etc but I'm going to try finding them on my own.  Stay subscribed to this thread and thank you again.  Star for you :)

I had a problem w/ OpenOffice, too.  Did the same thing - renamed the .openoffice.org2 file to .openoffice.org2.backup and now it works.  This confused me because I thought those files contained the settings they needed to operate, but it seems like they're just user settings and if they're not present the application starts as if it's being run for the first time, eh?

---

