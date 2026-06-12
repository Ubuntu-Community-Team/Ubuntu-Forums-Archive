---
title: "Rotation on HP tc4400 with wacom"
date: 2015-12-13
forum: Hardware
---

### Post by chrisllemay on 2015-12-13
Hi, 

Hopefully this is an ok place to post as I am trying to get wacom hardawre working.  I have been playing around quite a bit with different distros on an older HP tc4400 tabletpc.  My goal has been to get a relatively lightweight distribution that supports the wacom stylus, including being able to use the stylus when the display is rotated. 

OpenSUSE did this fine, but I found openSUSE somewhat awkward to use.  Most of the Linus Distros I have used are Ubuntu based, and I am sure that contributes to this (nothing against openSUSE).  At any rate I did quite a bit of research before I installed Xubuntu 14.04 and from what I saw I figured if it wasn't working out of the box I could certainly use one of the scripts out there. 

Well since I am opening this thread it's obvious that the rotation did not work out of the box.  Specifically, the display rotates, but the wacom setup does not.  Wacom cursor moves in a different direction than the travel of the stylus.  Not a huge deal; on to plan B, a script.  I tried the one suggested in this thread:  [http://ubuntuforums.org/showthread.php?t=2116275](http://ubuntuforums.org/showthread.php?t=2116275) along with the modifications to reflect the result of: xinput list as suggested.  There are a couple methods covered in the guide, I am using the "part 2" the Rotation Script.

Once again, like the rotation of the display in settings, the screen rotates but the stylus does not.  I have done a lot of searching and tried a few other similar scripts with the same results.  Most of the advice given is from 2008-2012, and some postings note that scripts like this no longer worked starting with 12.04.   

Not sure where to go next as it certainly seems possible as openSUSE works, but I can't seem to find any info about getting the stylus rotation in Ubuntu 14.04. It seems like the wacom script commands are not actually going anywhere/doing anything. Anyone have any suggestions concerning this, or experience with a tc4400/tc4200 with recent versions of Ubuntu?

Thanks,
               Chris

---

### Post by chrisllemay on 2015-12-15
So, I found another post with a similar script, but suggests that the input names in the script need to be in "quotes".  I did so, and everything seems to be working fine now.  Here is that link for anyone having similar difficulties:

[http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

Chris

---

