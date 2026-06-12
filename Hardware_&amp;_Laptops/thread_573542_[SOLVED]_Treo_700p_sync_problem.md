---
title: "[SOLVED] Treo 700p sync problem?"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by perryrt on 2007-10-11
Folks -

For various reasons that kinda involve the todo bug already documented, I'm having trouble with moving data to my Treo 700p.

The key question for the moment is that I've got a file (ToDoDB.pdb) that causes a sync to crash. However, I stupidly tried to manually install the same file using gpilot-file-install.....and of course it didn't work. My problem is that I used the --later switch on the gpilot-file-install routine and now the offending file keeps trying to install every time I sync (and crashes every time).

How do I clear this entry out of the gpilot-file-install queue? Where can I find this queue? The only thing I've tried so far is restarting and running a systemwide search for the term...but restarting didn't seem to help, and the search is ongoing about three hours now with no luck.

Any help would be appreciated.

---

### Post by perryrt on 2007-10-14
Was solved today, finally. Found out that the files were located in my /home/<username>/.gpilotd directory (note the period).

:)

I had missed them because I was using the search function on the desktop, and hadn't realized that gpilot-install-file renamed the files to be installed when placing them in the above directory. Once I deleted the files in there....all was well.

Thanks, Adresomoradu!

---

