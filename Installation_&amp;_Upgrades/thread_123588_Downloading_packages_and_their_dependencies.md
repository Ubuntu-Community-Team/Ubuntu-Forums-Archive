---
title: "Downloading packages and their dependencies"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by mohapi on 2006-01-30
Forgive me if I'm asking a question that has been answered elsewhere. I've spent the last 20 minutes with the search function, but I can't seem to refine my terms to find the answer I need.

I need to install some things on an older laptop without an Internet connection. I have a larger machine with a full Ubuntu install and a wireless connection, so getting the packages is not an issue.

However, I've found that apt-get isn't getting all the dependencies because the big machine has a full installation already.

Is there a command to force apt-get to download the package AND all the dependencies, even if they're already installed?

Thanks in advance, and sorry if it's a dumb question.

---

### Post by lol on 2006-01-30
using apt-get, you can use --reinstall to force the reinstallation of already installed packages.
But you should probably have a look at apt-zip. I have never used it, but it looks like the tool you really need.

---

### Post by mohapi on 2006-01-30
Thanks. I'll check that out. It might save me the trouble of building a server installation just to make sure I get the right dependencies.

---

### Post by mohapi on 2006-02-01
Well, it seems that *apt-zip* doesn't download packages that are already installed on the host machine. I tried a few of the options, but I didn't have much luck. No problem. I can reinstall in 20 minutes and download the stuff I need that way. Cheers!

---

### Post by lol on 2006-02-02
> Well, it seems that apt-zip doesn't download packages that are already installed on the host machine.

Actually, I believe it does, if they need to be updated... But the problem is that if you cannot run "apt-get update", then the package list is not updated, and all packages on the computer seems up-to-date...

The main problem therefore is to update the package list. If you can do that, then apt-zip should be able to handle the rest. But I am sorry, I have no clue on how to do that easily.

---

### Post by lol on 2006-02-02
ok, updating your repository can be done simply as well, just copy the required files in /var/lib/apt/lists from your connected computer (after running apt-get update) to the other one (you should make a backup first, just in case...).

That should take care of the step 1 from the following link :
[http://www.mepislovers-wiki.org/index.php?title=Tip:_Upgrade_your_dial-up_computer_using_your_fast_connection_at_work](http://www.mepislovers-wiki.org/index.php?title=Tip:_Upgrade_your_dial-up_computer_using_your_fast_connection_at_work)

You can also have a look at those links for other ideas:
[http://ubuntuforums.org/showthread.php?t=34113](http://ubuntuforums.org/showthread.php?t=34113)
[http://www.batmat.net/apt-offline/](http://www.batmat.net/apt-offline/)
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

IMHO, the best solution is still apt-zip.

---

### Post by UbuWu on 2006-02-02
In dapper the 'add applications' app can make a script to download the right packages (I think it is in the file menu). I don't know if that works on breezy as well though..

---

