---
title: "[SOLVED] Need help to see/place transferred archived email folder in Thunderbird plea"
date: 2008-07-15
forum: General Help
---

### Post by Visible Spirit on 2008-07-15
Hi all,

I have a problem transferring email messages from TB on a separate windows machine, to the Thunderbird app. in Ubuntu_Studio-(Hardy Heron v8.04). I copied the xxxx-folder from the Windows XP machine TB profile 'mail' folder and transferred it via a USB Flash Drv, pasting it too Home/.mozilla-thunderbird/xxxxx.default/Mail/Local Folders/ . The transferred 'folder in question' is not showing up in the Ubuntu TB 'LocalFolder' with archived emails.

One thing I did notice is the transferred 'mailbox' files have an "executable" icon rather than a "text" icon like the existing emails that were dwnldd via TB in Ubuntu.

Would someone be kind enough to help me straiten this out so I can access my archived emails folder in my Ubuntu TB app please?

Thanks...

---

### Post by Visible Spirit on 2008-07-16
Would someone be kind enough to help me straiten this out so I can access my archived emails folder in my Ubuntu TB app please?

Thanks...

---

### Post by Visible Spirit on 2008-07-16
Bump

---

### Post by Visible Spirit on 2008-07-16
Bump

---

### Post by Visible Spirit on 2008-07-17
Bump

---

### Post by Visible Spirit on 2008-07-18
I'm very surprised no one responded to my request here, but after many hours of digging I finally found the solution to my problem.

The problem was trying to transfer my archived Thunderbird v2.X emails from my WinXP machine to my Ubuntu Studio v8.04 machine. The conventional 'copy and paste' via a USB flash drive didn't work for me. I found an extension to do the work and hope anyone that needs to accomplish this task in the future finds this info helpful.

**Interesting thread that lead me to the answer:** [http://forums.mozillazine.org/viewtopic.php?f=39&t=742345](http://forums.mozillazine.org/viewtopic.php?f=39&t=742345)

**Extension to dwnld and install in TB:** [https://nic-nac-project.org/~kaosmos/mboximport-en.html](https://nic-nac-project.org/~kaosmos/mboximport-en.html)

The extension is compatible with Thunderbird 1.0 - 3.0 and has the autoupdate enabled. Read the page to learn/understand how best to use it, then find the dwnld link at the bottom of the page.

Hints:
1) _Highlight the folder you intend to export from_ and right click it. Use the context menu 'Import/Export' entry.
2) _Highlight the folder you intent to Import too_ BEFORE you choose the >Tools >Import/Export entry. The files will be put in the folder that is highlighted once you start the process so pay attention.

HTH

---

