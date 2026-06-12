---
title: "synaptic package manager problems....(Newbie)"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by riwa on 2006-01-24
I can't download things from the terminal nor the synaptic package manager. I keep getting this 'broken package' error message. It's really annoying since I can't install video/audio plugins and can't read dvd-movies nor mp3-files. I'm starting to think my installation went wrong because there's a lot of stuff that's messed up on this computer. Can't read the battery, can't use wi'fi (it's an 'acer' laptop), can't read dvd/mp3 (though I can BURN dvd's i just can't read them.) Help is greatly appriciated...

Regards
Richard

---

### Post by simon_is_learning on 2006-01-24
have you tried 
sudo apt-get clean
otherwise it would be easier to help if you posted the exact error message

---

### Post by dueY on 2006-01-24
Try ```
sudo apt-get -f install
```

---

### Post by riwa on 2006-01-24
Did the apt-get clean thing. No error message nor activity. So something happened but the same error message when i try other commands. 

riwa 141839 ~ $ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-plugins: Depends: gstreamer0.8-a52dec (>= 0.8.11) but it is not g oing to be installed
                        Depends: gstreamer0.8-aa (>= 0.8.11) but it is not insta llable
                        Depends: gstreamer0.8-artsd (>= 0.8.11) but it is not in stallable
                        Depends: gstreamer0.8-caca (>= 0.8.11) but it is not ins tallable
                        Depends: gstreamer0.8-cdio (>= 0.8.11) but it is not goi ng to be installed
                        Depends: gstreamer0.8-festival (>= 0.8.11) but it is not  installable
                        Depends: gstreamer0.8-jack (>= 0.8.11) but it is not ins tallable
                        Depends: gstreamer0.8-mad (>= 0.8.11) but it is not goin g to be installed
                        Depends: gstreamer0.8-mikmod (>= 0.8.11) but it is not i nstallable
                        Depends: gstreamer0.8-mms (>= 0.8.11) but it is not goin g to be installed
                        Depends: gstreamer0.8-mpeg2dec (>= 0.8.11) but it is not  going to be installed
                        Depends: gstreamer0.8-sid (>= 0.8.11) but it is not inst allable
                        Depends: gstreamer0.8-swfdec (>= 0.8.11) but it is not g oing to be installed
E: Broken packages

---

### Post by riwa on 2006-01-24
Tried:

riwa 142322 ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
riwa 142327 ~ $

---

### Post by Jucato on 2006-01-24
i think dueY meant

```

sudo apt-get -f install [insert package name]

```

---

