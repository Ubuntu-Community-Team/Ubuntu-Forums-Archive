---
title: "display problem in a VM"
date: 2010-10-21
forum: Hardware
---

### Post by sean.peters on 2010-10-21
Ladies/gents - not entirely sure I'm in the right section of the forum here. I'm running 10.10 in a VirtualBox on my MacBookPro (10.6.x, if that matters). Everything is running absolutely swimmingly, with one exception: the system seems to max out at a display resolution of 800x600... which displays pretty small. I'd like to get to 1024x768. Any thoughts on what might be going on? I'd appreciate any advice.  Sean

---

### Post by RedSingularity on 2010-10-21
Install the guest additions and you will be fine.

---

### Post by sean.peters on 2010-10-22
Hmmm, thanks but still no joy. Mounted the guest additions disk, installed, everything seemed to go normally. Opened "system | Administration | Additional drivers", and the VirtualBox Guest Additions showed up with a green light: "The driver is activated and currently in use". However, when I opened Monitor Preferences, I still get "Monitor: unknown" and the only resolution choices are 800 x 600 and 640 x 480. Just in case, I rebooted. Still no change in the available choices in Monitor Preferences.

Thanks for the help so far... any more thoughts?

Sean

---

### Post by RedSingularity on 2010-10-22
Are you using the OEM version of V-Box?

---

### Post by sean.peters on 2010-10-22
Umm - if I understand you correctly, yes. I got VBox straight from their website, not from a third party...

---

### Post by RedSingularity on 2010-10-22
In the Ubuntu install do the following.

1. Open terminal and enter the following command: 

sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo apt-get install virtualbox-ose-guest-x11 

2. Once installation is finished, restart your **[B]virtualBox machine**[/B]. 

3. Go to System -->Preferences -->Monitors and change the resolution of your screen.

---

### Post by sean.peters on 2010-10-22
Damn, still no joy. All three commands appeared to proceed normally - apt-get update duly went and got packages, both the apt-get-install commands seemed to do their thing and complete normally... but when I restarted and fired up monitor preferences, I'm still in the same boat - the choices are still 800 x 600 and 640 x 480.

I appreciate you sticking with me. Any more ideas?

Sean

---

### Post by RedSingularity on 2010-10-22
What version of virtualbox do you have?

---

### Post by sean.peters on 2010-10-22
3.2.10. The update checker claims it's the most recent version.

---

### Post by RedSingularity on 2010-10-22
There is a known bug in Maverick about this.  I wonder though........i got it working with a fresh install of 10.10.......

Maybe since you have the "Guest additions" already installed it wont work.  To get it working over here I had a fresh install of 10.10 WITHOUT installing the official Vbox Guest additions.  Then I ran that code i gave you and I got the Resolution you want.  I am going to run this by the Bug Squad and see if the developers are working on a fix.

---

### Post by RedSingularity on 2010-10-22
What guest additions are you using?  Version I mean.

---

### Post by sean.peters on 2010-10-22
Ok, thanks. I'll mess around with it a little more (probably tomorrow) and post here if I find out anything of significance. If you hear anything else from the bug team, I'd appreciate it if you'd let me know... thanks again

Sean

---

### Post by sean.peters on 2010-10-22
Whoops, hold on, just noticed your latest. Guest additions are at 3.2.10_66523.

---

### Post by RedSingularity on 2010-10-23
Unfortunately the bug squad cannot fix this because you are using the "Closed source" version.  Ubuntu bug squad can only work with the Open Source version that is available for Linux Hosts.

---

### Post by sean.peters on 2010-10-23
Ok, got it. Thanks for all your help!

Sean

---

