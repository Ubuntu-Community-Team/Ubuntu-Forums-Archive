---
title: "receiving a 404 when running apt updates"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by gmoog on 2008-12-29
Greetings:
First time poster long time forum voyeur. I am having some problems receiving updates when using apt from the command line. 
I think I have made a mistake in my sources.list configuration. I had it set to download from se.ubuntu but later switched it to us.ubuntu when I noticed a 404 from one of the lines in my sources.list file. 

I am running this command to get updates: *sudo apt-get update*

The following error shows up in the results: 

[I]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) universe/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/universe/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/universe/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

The rest of the information returned looks similar to this but is quite long so here is one example:

*Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages*

Also here is what my sources.list looks like:

[I]## UBUNTU REPOSITORIES
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports universe multiverse

#proposed - unstable
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-proposed main restricted
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-proposed multiverse universe

## Source based install, mostly unnecessary
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe multiverse
#
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-backports main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-backports universe multiverse
[/I]

I know very little about apt and what everything in sources.list really means. I have been reading the man page but I'm still confused, can anyone link me to a good documentation outside of the man page?
Anyones opinions are greatly appreciated. 

-Gmoog

---

### Post by konungursvia on 2008-12-29
It's not apt, it's just network timeouts on busy servers. Try system > admin > software sources and find best server automatically, then redo your update that failed.

---

### Post by taurus on 2008-12-29
> **gmoog said:**
> Greetings:
First time poster long time forum voyeur. I am having some problems receiving updates when using apt from the command line. 
I think I have made a mistake in my sources.list configuration. I had it set to download from se.ubuntu but later switched it to us.ubuntu when I noticed a 404 from one of the lines in my sources.list file. 

I am running this command to get updates: *sudo apt-get update*

The following error shows up in the results: 

[I]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) universe/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/universe/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/universe/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

The rest of the information returned looks similar to this but is quite long so here is one example:

*Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages*

Also here is what my sources.list looks like:

[I]## UBUNTU REPOSITORIES
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
**[COLOR="Red"]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) universe multiverse[/COLOR]**
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports universe multiverse

#proposed - unstable
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-proposed main restricted
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-proposed multiverse universe

## Source based install, mostly unnecessary
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe multiverse
#
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-updates universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-backports main restricted
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) intrepid-backports universe multiverse
[/I]

I know very little about apt and what everything in sources.list really means. I have been reading the man page but I'm still confused, can anyone link me to a good documentation outside of the man page?
Anyones opinions are greatly appreciated. 

-Gmoog

That line is missing the word** intrepid** in there.

---

