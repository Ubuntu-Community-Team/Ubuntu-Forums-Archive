---
title: "Convince me of some things about /home"
date: 2008-09-08
forum: General Help
---

### Post by jorwex on 2008-09-08
Okay, I've been messing around with Ubuntu for long enough, and I just got a new harddrive, so I think it's time to progress to mounting my home folder somewhere other than the default. I've seen people recommending that since forever.

I've read that it keeps your programs and settings separate incase you want to reinstall your OS or switch to a different flavor of linux, etc..

But when I've installed things in the past, they aren't always installed to home. Like if I install MATLAB (which, I'll admit gives you the option of where to install) the default is in /opt or /usr/bin or something like that. 

Coming from a life of experiences with Windows, I just can't imagine that if I installed a big program like MATLAB to my home directory on a different partition, reformatted & reinstalled, and then mounted my /home appropriately, that I would have the same functioning app as before.

Is this truly the case? Or by 'programs & settings' have I made too many assumptions? 

Thank you for your time,

Jordan

---

### Post by squaregoldfish on 2008-09-08
I may be wrong, but my understanding is as follows:

Some programs and applications contain all the libraries they need within their own application installation, and are known as statically linked. If you put these on a separate partition and reinstall the OS, these should still be fine.

Other applications will make use of libraries that are already installed on your system (dynamically linked). These applications may have trouble if you reinstall the OS, but if you make sure you reinstall all the libraries they used you should be OK. If you haven't reinstalled the libraries, the programs will complain about which files they want, and you should be able to go and find them in the repositories.

As for all your personal files, they will indeed be untouched if you replace the OS underneath them.

A couple of other things to note:

If you want to install applications on a separate partition, I wouldn't put them in /home. Create another directory on your new partition to put them in (maybe mount /opt from your new partition as well).

Your application path will usually remain in /usr/bin or /usr/local/bin, so shortcuts to your applications will often still end up there. Obviously you'll lose these if you nobble the OS.

In short, I'd go for it. You may have a few small problems with dynamically linked applications, but you'll be a damn sight better off than if you don't do it.

Hope this helps, although I've got a feeling I may have confused you even more. If so, complain and I'll do something about it. :)

Steve.

---

### Post by mb_webguy on 2008-09-08
Programs are rarely installed to your home folder -- but the settings and preferences for those programs are generally saved there.  If you don't have a separate partition for your data (as many people who dual-boot do), then all of your personal files are also located there.  By having a separate home directory, you don't lose any of your preferences, and you don't have to backup and restore your data.

If you also want to keep your programs separate from your OS, then you can also mount the /usr directory to a separate partition.  There are a few issues to doing this, however, such as the possibility of not being able to remove these programs using a package manager after installing or reinstalling Linux.

---

### Post by skullmunky on 2008-09-08
I'm a big believer in having /home on its own partition, or even its own drive, but as others mentioned, more because of keeping my data in its own place rather than for apps.

I learnt that as a young 'un on old Macs, because that way if your system drive fails, your data is safe - you can just reinstall the OS without having to stress about rescuing your data.   This happens a lot, at least to me.

I also have the ingrained habit of fresh installing instead of upgrading, no matter what OS it is.  so the separate /home is good for that too.

Coincidentally, I think my /home drive crashed this week; having everything else on another drive makes recovery, repair, or restoring a lot easier.  

Actually here's what I do - I leave /home on the primary drive, where I put a kind of default admin or rescue account, and other things like that.  Then I have a second drive, which is /home2, and that's where I put my real user account.

---

