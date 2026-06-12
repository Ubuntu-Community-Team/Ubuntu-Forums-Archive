---
title: "installing a custom ubuntu ISO with WUBI"
date: 2008-10-28
forum: General Help
---

### Post by pknut777 on 2008-10-28
Hi,

We used remastersys to create a custom Ubuntu ISO.  We are trying to get the WUBI installer to pick up this custom ISO.  All the other posts/threads I've read say "edit isolist.ini".  Fair enough.  We've looked at the file.  We've even taken a guess at editing it.  We recompiled WUBI sucessfully, but the end result didn't work.

Can someone give an example of a modified isolist.ini for a custom Ubuntu ISO?  Or some hints?

thanks!
Adam

---

### Post by ago on 2008-10-28
If your iso is provided on a server, you need to have all the same *metalink* files you see on [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Since the metalink md5 file has to be signed, you either have to add your signing key to trustedkeys.gpg or you have to disable signature checking in data/settings.nsh 

In isolist.ini, you need to provide the URL of the main metalink file, also the isolist.ini distro name, must match the one listed in .disk/info inside the ISO

In fact .disk/info has to be formatted like the same file on Ubuntu CD

---

### Post by ago on 2008-10-28
If it is a one off, you can just run normal wubi, and then swap c:\ubuntu\install\*.iso with your iso before installing (this assumes same kernel/initrd as in ubuntu iso)

---

### Post by pknut777 on 2008-10-28
> **ago said:**
> If it is a one off, you can just run normal wubi, and then swap c:\ubuntu\install\*.iso with your iso before installing (this assumes same kernel/initrd as in ubuntu iso)

Thank you for this information.  I haven't tried this approach yet, but I assume it would work.  However, it isn't exactly ideal for what we are doing.  We are running a workshop in a few months ([http://workshop.molecularevolution.org/eur/]("http://workshop.molecularevolution.org/eur/")) and we will have probably at least 50 participants who will be bringing Windows laptops, and we will strongly suggest they run Ubuntu on them so they have a UNIX environment in which to work.  We want to make this process as painless as possible for them, which is why we were attracted to WUBI.

Our ISO is not provided on a server.  Ideally, we would burn our custom ISO to a CD that we provide to each participant.  I haven't yet tried the CD approach with a custom ISO, but based on what I've seen so far, I doubt it would work.  The "ISO replacement" trick you describe is hardly ideal for our situation, for what I hope are obvious reasons.

So- is there a way to use the custom Ubuntu ISO with WUBI, but doing everything locally?  not going out over the internet to pull something down... and preferably, without doing the ISO replacement trick?  We have verified that we can get the WUBI installer to pick up the "standard" Ubuntu Desktop ISO without downloading it, per the docs, so I assume there has to be a way to get it to pick up a custom one.

Thank you very much for your help!

Adam

---

### Post by ago on 2008-10-29
> **pknut777 said:**
> 
So- is there a way to use the custom Ubuntu ISO with WUBI, but doing everything locally?  

They need to have wubi.exe and the ISO in the same folder, the ISO has to have a properly formatted .disk/info. Add your distro to isolist.ini copying an existing section, the most relevant fields are the distro name, version and arch, that must match the ones in .disk/info (this is how ISOs get checked). Then in settings.nsh set CompulsoryMetalinkSignature to false.

Haven't tried that but should work, in case there is a log in your user temp folder %temp% in windows explorer, go through it, or post it here.

---

### Post by ago on 2008-10-29
Note also that you need to have lupin-support package installed as that provides lupin-casper, I.E. casper hooks that allow the Live CD to boot off an ISO and read local preseed files.

EDIT: you need to have lupin-casper so that the initrd inside the ISO contains the necessary hooks. Plus you need the lupin-support deb inside the ISO available for installation

---

### Post by ago on 2008-10-29
have added more info to the wubi guide.

---

### Post by pknut777 on 2008-10-30
> **ago said:**
> If it is a one off, you can just run normal wubi, and then swap c:\ubuntu\install\*.iso with your iso before installing (this assumes same kernel/initrd as in ubuntu iso)

Dear Ago,

Thanks again for your help.  We did make some progress by manually inserting a .disk/info file into our custom ISO, but for now, let's assume that we're using the ISO-swap-out trick you described earlier.

Using the swap-out trick, the problem we faced first is that when we rebooted to do the WUBI install, the thing sort of hung- it eventually kicked us to an ugly-looking shell.

It's at this point that we remembered to check for the lupin-support package, like you said in your post (and like you added to the guide).  I assume you mean these packages simply need to be installed before we create the ISO with remastersys, e.g., like "sudo apt-get install lupin-support".  It turns out lupin-support was NOT installed, so we installed it and repeated the process.  There was no change- we still got kicked to the ugly prompt after rebooting.  That's when we thought to check for lupin-casper... we thought that was automatically installed with lupin-support, but it turns out it *wasn't* ... so we installed it and repeated the process.  Lo and behold, it went a *little* farther, but eventually kicked us to a prompt.  We started X, which brought us into what looked like a typical "live CD".  No WUBI install was ever initiated.

Soooo... do you have any idea of what we are missing?  Comparing the ISO created with remastersys against the official Ubuntu Desktop ISO shows they are quite different.  Thanks!!

Adam

---

### Post by ago on 2008-10-30
> **pknut777 said:**
> 
Using the swap-out trick, the problem we faced first is that when we rebooted to do the WUBI install, the thing sort of hung- it eventually kicked us to an ugly-looking shell.
If that happens boot in verbose mode and look into /casper.log for errors
One possible reason is that the kernel and initrd come from the original ISO and they do not match the version on your ISO.

> It's at this point that we remembered to check for the lupin-support package, like you said in your post (and like you added to the guide).
The ISO must contain lupin-support as a package as that will be installed, furthermore the ISO initrd must contain lupin-casper. But if you are swapping ISOs that shouldn't matter as in that case it will use the initrd of the original ISO which will contain lupin-casper.

The ISO of course also needs ubiquity and in particular be capable of running ubiquity in automatic mode. I am not too familiar with remastersys, but the ISO should look very much like the Ubuntu one.

---

### Post by pknut777 on 2008-10-30
Right, part of me feels like we're close, but part of me wonders if we'll ever get this working in time.  I'll let you know if we make any additional progress.

Stepping back for a second though- is there a more "WUBI-compatible" way to make a custom ISO, instead of using remastersys?  What would you recommend?  I see something called [_UCK_]("http://uck.sourceforge.net/") here, but I'm not sure if that would be any better.  Thanks!

---

### Post by ago on 2008-10-31
pknut777, it would help a lot if you could provide the logs. Always boot in verbose mode then either provide /casper.log or /var/log/syslog (depending on when the error happens).

---

### Post by pknut777 on 2008-11-04
> **ago said:**
> pknut777, it would help a lot if you could provide the logs. Always boot in verbose mode then either provide /casper.log or /var/log/syslog (depending on when the error happens).

Just to sort of close out this thread: it turns out that UCK is the way to go for creating custom Ubuntu ISOs, at least for our intentions of using it with WUBI.  I'd certainly recommend starting with UCK over remastersys.

---

