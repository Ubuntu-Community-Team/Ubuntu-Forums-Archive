---
title: "HP Pavilion dv5 Touchpad Won't Work in Ubuntu"
date: 2011-01-23
forum: Hardware
---

### Post by mrprez8 on 2011-01-23
Hey Ubuntu People,
I'm fairly new with this version of Ubuntu. (I used it when it was still in version 7, etc.) I have a problem with my touchpad. I've found solutions for "Ubuntu Multi-touch Touchpad" etc,etc. 

Unfortunately, my problem is a bit different. My touchpad buttons are actually on the same face as the touchpad. (They are just rocker buttons, but still part of the touchpad detector.) This poses a problem, because whenever I press the touchpad button and try to move another finger on the touchpad (or anytime I have two fingers on the touchpad--moving a window on screen for example) the mouse goes crazy wild and starts jumping all over the screen. This means multi-touch gestures are ALSO not supported, but that's the least of my problems.

I think it probably has something to do with the Synaptics Touchpad drivers. If anyone could offer any help that would be incredibly appreciated.

--Nick

My hardware specs just in case:
HP Pavilion dv5-2135dx
ATI Radeon Mobility HD4250
4GB DDR3 Ram
AMD 64-bit dual-core processor

(Just ask for more info and I can find it.)

---

### Post by Mamsaac on 2011-01-24
A friend is having the same problem with 10.04 (Lynx), using the same laptop (HP Pavilion dv5).

Trying to find help for this :) Thanks

---

### Post by mrprez8 on 2011-01-24
I'm going to edit the title and tags to include "clickpad." That's the technical name for it.

---

### Post by Mamsaac on 2011-01-25
I wonder if it's not polite to bring this thread back to the first page? My friend and I haven't found a solution and I did search quiet a bit. Anyone that could be his hero? I don't want him to go back to Windows :)

---

### Post by mrprez8 on 2011-01-26
Unfortunately, that's what I'm doing for now. I understand that the clickpad is a somewhat recent development, so I'm not complaining. I'm just using windows 7 again until they fix it (and if they don't it'll be back to windows permanently) in 11.04.

---

### Post by Mamsaac on 2011-01-27
[http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/)

That seems to work just fine on 10.10... I guess I will have my friend upgrade to 10.10 (I'm not very happy with that decision, because the server we're developing for is on the LTS - 10.04). I would need to upgrade the kernel on 10.04 and stuff... just not worth it IMO.

Please tell me if it works! If it does, I will do the upgrade on his laptop and do it too :)

---

### Post by mrprez8 on 2011-01-27
That method (posted on launchpad.net originally) works with limited success. It's still a big hassle to do anything with the mouse though, because of the jumpiness.

---

### Post by chasem1991 on 2011-01-27
I have pretty much the exact same laptop. (HP DV5-2035dx)

I found the solution to making the touchpad work was to add the uTouch PPA. Once the PPA was added, install the synaptics-dkms package. Reboot, change to two-finger scrolling, and it works great.

I will walk you through the easy installation.

1) Add the uTouch PPA by pasting the following into terminal.
```
sudo add-apt-repository ppa:utouch-team/utouch
```

2) Update repositories, and install the synaptics-dkms package.
```
sudo apt-get update && sudo apt-get install synaptics-dkms
```

3) Reboot your laptop.

4) Go to System > Preferences > Mouse. Go to the Touchpad Tab, and click two finger scrolling. Click the close button.

Now you are ready to test your touchpad. 

What do you think? Much better?

If you aren't satisfied with the results you can simply remove the package by opening up terminal again and paste this in.
```
sudo apt-get remove synaptics-dkms
```
:guitar:

---

### Post by mrprez8 on 2011-01-28
That worked! Except for one thing: now I can't right click. :( Multi-touch gestures work great and my mouse isn't jumpy, but I can only left click. 

It seems I can only have limited functionality either way.

---

### Post by chasem1991 on 2011-01-28
> **mrprez8 said:**
> That worked! Except for one thing: now I can't right click. :( Multi-touch gestures work great and my mouse isn't jumpy, but I can only left click. 

It seems I can only have limited functionality either way.

Try tapping with two fingers on wherever you want to right click. Hope that helps. :wink:

---

### Post by Mamsaac on 2011-01-29
chasem, that's great help. Thanks :D

---

### Post by HackerOfDreams on 2011-01-30
Hi,
I followed all your instuctions but it doesn't work.

this is the error message that i get when i use this command:
sudo apt-get update && sudo apt-get install synaptics-dkms

W: Failed to fetch [http://ppa.launchpad.net/utouch-team/utouch/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/utouch-team/utouch/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I will appreciate that you help me.

---

### Post by Mamsaac on 2011-01-30
The reason why that command didn't work is because you're not on Maverick.

---

### Post by daniroj on 2011-02-10
Thanks friend. That worked awesome on mine. I was too much tired of using the touchpad..CHEERS

---

### Post by chasem1991 on 2011-02-10
> **HackerOfDreams said:**
> Hi,
I followed all your instuctions but it doesn't work.

this is the error message that i get when i use this command:
sudo apt-get update && sudo apt-get install synaptics-dkms

W: Failed to fetch [http://ppa.launchpad.net/utouch-team/utouch/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/utouch-team/utouch/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

I will appreciate that you help me.

Sorry, I failed to state that this would only work under 10.10+ right now.

You could try to remove the ppa by pasting the following into the terminal:
```
sudo remove-apt-repository utouch-team/utouch
```

Now no guarantees that this will work but you could then add the following to your sources list to trick the repository into thinking that you were running 10.10 instead.
```
deb http://ppa.launchpad.net/utouch-team/utouch/ubuntu maverick main 
deb-src http://ppa.launchpad.net/utouch-team/utouch/ubuntu maverick main
```

Then try to install the package once again by pasting the following into terminal:
```
sudo apt-get update && sudo apt-get install synaptics-dkms
```

---

