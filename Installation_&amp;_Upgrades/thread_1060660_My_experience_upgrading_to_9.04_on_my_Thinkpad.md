---
title: "My experience upgrading to 9.04 on my Thinkpad"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-02-05
So far it was not a great experience.

After the upgrade:
My fonts are all huge, making the appearance very unpleasant.
Lost my extra visual effects (Compiz).
My Firefox profile must be screwed up because Firefox crashes every time I try to open any page.
Lost my network drives.
My TrackPoint middle mouse button scrolling stopped working.
More...

During installation I had this error:

Could not install '/var/cache/apt/archives/python-qt4_4.4.4-2ubuntu3_i386.deb'

The upgrade will continue but the '/var/cache/apt/archives/python-qt4_4.4.4-2ubuntu3_i386.deb' package may be in a not working state. Please consider submitting a bugreport about it.

subprocess pre-installation script returned error exit status 1

---------------------

Could not install 'python-qt4'

The upgrade will continue but the 'ppython-qt4 (version 4.4.3-1ubuntu1) will be upgraded to version 4.4ython-qt4' package may be in a not working state. Please consider submitting a bugreport about it.

package python-qt4 is already installed and configured


------------------

Package Hook Crashed
crashed IOError on write

Could not upload report data to crash database:

<urlopen error (-5, 'No address associated with hostname')>


Could not upload report data to crash database:

<urlopen error (-5, 'No address associated with hostname')>

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)

>> OK, hmmm nothing ran. I'll try manually:

me@Ubuntu:~$ sudo dpkg --configure -a
[sudo] password for me: 
me@Ubuntu:~$ 

strange, no response...

-------------------
OK, I'll try Synaptic:

python-qt4 (version 4.4.3-1ubuntu1) will be upgraded to version 4.4
Result: success

network connection not working now...
reboot solved that.

Did a manual upgrade and it updated about 59 packages successfully. No errors.

OK, that's my report. 

I want to see 9.10 ready to kick Windows 7's butt.

---

### Post by sonicb00m on 2009-02-05
Yeah, i guess there are 3 months more development time up to the end of april so I am keeping away from it until at least a beta or rc comes out.

---

### Post by MountainX on 2009-02-06
I resolved most of my issues without too much trouble. :)

I fixed my TrackPoint scrolling with the info here:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

I had to go back to a default Firefox profile, but that isn't a big deal.

I was able to get the proprietary nVidia driver working with nothing more than activating it in the Hardware Drivers tool. Very easy.

The only thing I have not figured out is why my mounted volumes stopped working. fstab looks like I expect it to...

---

