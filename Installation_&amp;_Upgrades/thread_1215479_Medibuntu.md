---
title: "Medibuntu"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by lotusalive on 2009-07-17
Hi Folks:  Prepping my PC with Medibuntu, and have a couple questions.  The Jaunty version given in the Upgrade is generic x86_64, so does that mean I should install all the 64-bit code ?

Also, what is ia-32-libs ?  One of the 64-bit commands could not find it, and I could not find it in Synaptics Pkg Mgr.  Do I need it ?  Where can I find it, or do I just have to do without it ?  (Error Msg Fixes didn't work...)

Thanks for looking at this.:)

---

### Post by Partyboi2 on 2009-07-17
Hi, the ia-32-libs package has the runtime libraries to run 32bit programs on 64bit. It is in the universe repos, but if you are running the 32bit ubuntu it is not available.

---

### Post by lotusalive on 2009-07-17
Thx for that... Also, libflash-mozpluggin is not found in _either_ version, 32-bit nor 64-bit, nor Synaptics.  The only libflash is flash-plugin-nonfree-extrasound...  Should I just leave these errors if the fixes do not find them ?

Should I allow the Medibuntu Source Code for Jaunty in Respositories ?  And / or enable Intrepid also ? ?

---

### Post by Partyboi2 on 2009-07-17
libflash-mozpluggin is only available in the repos for dapper and hardy I would suggest using flashplugin-nonfree instead.

> Should I allow the Medibuntu Source Code for Jaunty in Respositories ?  And / or enable Intrepid also ? ? 	 If you are wanting some of the packages that Mediubuntu has then I would suggest adding the repo to your sources.list as it is a lot easier to let apt-get install the package and its dependencies.
I would also recommend not adding intrepid repos to your jaunty sources.list as this can cause breakages.

---

### Post by lotusalive on 2009-07-18
Thank you partiboy2 !  I already DID add the Intrepid Repo to the Medibuntu 

Repo, BUT the ONLY thing it added was Adobe Flash Plugin ! !  And I was 

having trouble getting You Tube Videos to play BEFORE adding it, since 

suddenly, YouTube required the gstreamer-bad plugins, and it was looping 

the videos, i.e. repeating itself at random, while streaming, weirdest 

'stream' I'd ever encountered !  So, if I leave it this way, I risk 

breakage from other conflicting packages, OR, if I take it out, I can't 

play YouTubes, lol...  I'll look at Medibuntu again tonight...  Or, go 

back to Hardy !  Thanks alot, again partyboi2

---

### Post by Partyboi2 on 2009-07-18
Remove the Intrepid medibuntu, then  add the Jaunty one with
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by lotusalive on 2009-07-20
GEE, thanks...  Looks like to really saved me from conflicting packages in the future !   YouTubes are working fine too.  Really grateful Partiboi2:KS

P.S.  I had to go in and remove adobe-flashplugin-intrepid from Synaptics manually.

---

