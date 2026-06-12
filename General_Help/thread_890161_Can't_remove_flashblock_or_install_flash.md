---
title: "Can't remove flashblock or install flash"
date: 2008-08-14
forum: General Help
---

### Post by a5h3n on 2008-08-14
I made the mistake of installing flash block, then made the mistake of uninstalling flash without first trying to uninstall flash block (though I'm starting to think I'd have the same problems anyway).

When I try to use Adept it says: 

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

I get the same message when trying to re-install flash.

I tried uninstalling flash block using the instructions on their website and on the mozdev.org site to no avail, as the extension still shows in 
Tools>>Add Ons>>Extensions menu.

I can't uninstall in safe mode (the option isn't there), and the userContent.css file is empty, so I can't remove the reference from there.

I looked in the extensions.rdf file to see if that might enlighten me on where to find the installation location, and that said the location was "global - app".

I can install other packages just fine, so I know the problem isn't adept.

Does anyone have any ideas as to what this might be?

---

### Post by colobix on 2008-08-14
TRy this. Close firefox or whatever u use, open root terminal and paste in this code:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install libdvdcss2 w32codecs mozilla-mplayer ubuntu-restricted-extras flashplugin-nonfree

---

### Post by a5h3n on 2008-08-14
Seems to have worked!

Thanks for the help!

---

