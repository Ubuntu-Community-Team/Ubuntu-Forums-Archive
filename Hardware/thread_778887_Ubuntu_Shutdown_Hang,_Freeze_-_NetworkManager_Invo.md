---
title: "Ubuntu Shutdown Hang, Freeze - NetworkManager Involved?"
date: 2008-05-02
forum: Hardware
---

### Post by twilightomni on 2008-05-02
Hello there.  I recently got Ubuntu 8.04 working on my laptop, everything set up nicely, very impressed.  But I am having a critical problem.  The shutdown process on my Toshiba Satellite laptop is much too long.

After selecting Shutdown from GDM, or from the Quit... Dialog, my X server terminates and then my computer goes to the console.  And then it sits there.  Usually, it takes about three minutes.  After this, it will spit out some error messages about NetworkManager failing to shut down properly, and then power down.

But sometimes, it won't ever spit out error messages.  It will just sit there.  Once I press CTRL-ALT-DEL, it will then say "Closing GNOME Display Manager..." and then it will finally spit out the NetworkManager errors and exit.

So I have two questions.

1.  Why is Ubuntu taking so long to shut down?
2.  Why does it seem, on occassion, to fail to shut down?  (ie, the circumstance in which clicking Shutdown kills the X server, but for some reason the computer won't power down until I also press CTRL-ALT-DEL).

Does this involve NetworkManager at all?  I have Intel wireless hardware which seems to work fine.  Even if I click on the NM icon and uncheck "Enable Networking", I still receive this problem.



This is critical to me for using Ubuntu.  Fedora and OpenSUSE don't have this long hang at shutdown.  I really like Ubuntu 8.04, and I am willing to put some time into figuring out what is wrong.  I have, by the way, searched google and the forums, but I can't seem to find anyone with a similar problem, or in their case it involves a different chipset than the Intel wireless cards.

Does anyone know the problem?  Or, where I could start looking?  (ie, ways I could analyze my shutdown process to find out what's hanging).

---

