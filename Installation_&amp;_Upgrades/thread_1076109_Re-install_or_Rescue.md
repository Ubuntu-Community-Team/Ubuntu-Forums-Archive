---
title: "Re-install or Rescue"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Sleepy-zz-John on 2009-02-21
I've really managed to screw up my Intrepid Ibex as I've explained in  [***this Absolute Beginners thread***]("http://ubuntuforums.org/showthread.php?t=1062823") and in [***this General Help thread***]("http://ubuntu.org/showthread.php?t=1072170") :oops:

I've been trying to use the **Rescue mode **on my original  installation disc,  but that's failing at the "Install the base system" step for reasons I don't really understand;  it might perhaps be to do with some of the files on my broken system being more up-to-date than those on my original installation CD.

I'm slowly coming to the conclusion that it would be a lot easier to download a more updated installation disc and do a complete re-installation.

If possible, though, I'd like to keep my original data and setup information by avoiding reformatting,  so assuming I've downloaded a new up-to-date installation disc, my question here is whether it's practicable and easy to do a new installation without overwriting all my old data and config files.  For example I'd prefer not to have to set up all my e-mail accounts in Thunderbird again fom scratch if I can avoid it :???:

Or does my previous paragaph describe what the Rescue function is supposed to do?  Would I stand a better chance rescuing my old but updated installation with a newly downloaded installation disc rather than with my original - November 2008 one.    :???:

---

### Post by Leaf on 2009-02-21
If I'm not mistaken all your user customizations for your programs are saved in your home folder.  Try booting from a LiveCD, then mount your drive and copy your homefolder to an external partition.  Dont forget to grab your X config too!

edit: I wish I could help you more re: rescue mode across Ubuntu releases, but I really dont know if that would work well.

---

### Post by dzark on 2009-02-21
If you can boot off a live CD, take a copy of your /home folder and put it on an external drive.. reinstall and copy back.. Make sure you press Ctrl-H to see all your hidden folders and files though!

For some reason mozilla makes up silly names for the directories, eg on this computer right now it is:

```
illektr1k@vaiolent:~$ cd .mozilla/firefox/a9ihpmhc.default/bookmarkbackups/

```

so if you have a fresh install you might have to change the a9ihpmhc.default to whatever it is on the new one...

Most of your other settings will come nicely..

---

