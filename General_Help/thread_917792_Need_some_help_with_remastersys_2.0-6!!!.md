---
title: "Need some help with remastersys 2.0-6!!!"
date: 2008-09-12
forum: General Help
---

### Post by Fragadelic on 2008-09-12
Okay folks.  I am Tony the author of the remastersys script that can be used to remaster your Ubuntu install.  I have remastersys 2.0-6 finished except for 1 nagging bug which I desperately need help with.

The problem - installing a remastered livecd/dvd causes Ubiquity to hang at about 94% which is the reconfiguring of the popularity-contest package.  The amount of time it hangs can vary from 5 minutes and up.

I've tried to purge the popularity-contest package and reinstall but it still happens.  Removing the package altogether fixes it but then ubuntu-standard has an unresolved dependency as it depends on popularity-contest.  Further removing the ubuntu-standard package will fix it but then folks don't have the option of participating in the popularity-contest if they want to.

This isn't a showstopper since it does eventually finish the install but having it hang up like that is a pain.

The script that does this within ubiquity is written in perl.  I need to find out why the reconfigure portion of the install is hanging on popularity-contest.

Any help would be greatly appreciated and I don't want to release 2.0-6 until this is done.

---

