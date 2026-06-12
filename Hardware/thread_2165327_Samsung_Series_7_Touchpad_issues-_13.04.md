---
title: "Samsung Series 7 Touchpad issues- 13.04"
date: 2013-08-04
forum: Hardware
---

### Post by Peter_DeSevo on 2013-08-04
Hey guys,

I installed 13.04 and my touchpad is crap. It only allows one finger click and use. I have no option in the settings for "two-finger" scroll. I posted to reddit looking for help to no avail. I feel like I've tried everything. I am also a beginner and have little experience with ubuntu and I am still learning the jargon.

I've tried these threads:

[http://ubuntuforums.org/showthread.php?t=1935699&page=2&p=11772195#post11772195](http://ubuntuforums.org/showthread.php?t=1935699&page=2&p=11772195#post11772195)
[http://ubuntuforums.org/showthread.php?t=1935699](http://ubuntuforums.org/showthread.php?t=1935699)
 
^these did not work

 
I think an issue may be with this from this thread:

[http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

[SIZE=5][COLOR=Sienna]_Step 2: update synaptics driver_[/COLOR][/SIZE]
This step is probably unnecessary but is only to ensure you have the latest driver.

     Code:

     sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics

this is the response from terminal: 0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.

Synaptics is not updating.

'
When I try to open "Synaptics" it gives me an error saying that no touchpad is found. In the mouse settings it is read as PS/2 Elantech Touchpad.


I have no idea what to do!

---

