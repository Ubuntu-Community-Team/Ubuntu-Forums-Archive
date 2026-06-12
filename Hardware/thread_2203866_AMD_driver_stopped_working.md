---
title: "AMD driver stopped working"
date: 2014-02-05
forum: Hardware
---

### Post by jameshoneysett on 2014-02-05
Looking for some help with this problem.

Dell laptop running Ubuntu 12.04 64-bit with ATI Mobility Radeon HD 4650.  I'm also running a classic gnome desktop.

Today, I have turned my laptop on and the graphics are not working properly.  When I try to run the AMD Catalyst Control Center it gives the following error message:

"There was a problem initialising Catalyst Control Center Linux edition. It could be caused by the following: No AMD graphics driver installed, or the AMD driver is not functioning properly.  Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig."

Typing aticonfig into a terminal gives the following message: "aticonfig: No supported adapters detected"

Clicking on the additional drivers in system settings doesn't return any results.

None of the compiz settings are working, e.g. wobbly windows and effects etc.

It's like my graphics card suddenly doesn't exist or Ubuntu us running in low graphics mode.

Any help would be greatly appreciated.

Thank you.

---

### Post by jameshoneysett on 2014-02-05
Seem to have found a solution.  Turns out there was an update yesterday to the fglrx and fglrx-amdcccle packages.  Have forced them back to the previous version and now everything is working as it should.

---

### Post by egeezer on 2014-02-05
I had the same problem, but instead of using the old fglrx driver I gave in and used the opensource driver.  Works equally well on my system.

---

### Post by Olimpusmons on 2014-02-05
> **jameshoneysett said:**
> Seem to have found a solution.  Turns out there was an update yesterday to the fglrx and fglrx-amdcccle packages.  Have forced them back to the previous version and now everything is working as it should.

Looks like I'm having the same problem, can you tell me what you did exactly? I'm not very familiar with this.

---

### Post by egeezer on 2014-02-05
The best reference is one that will show you how to get rid of the fglrx driver and revert to the opensource one; that one works well enough to use Compiz in all its glory!:
  	 	 	 	    [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3]*[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)*[/SIZE][/FONT][/COLOR]

---

### Post by cschroter on 2014-02-05
System Settings > Additional Drivers

Select non post-release-update driver and activate.

Also having problems with the new update.

Multi-Display Desktop (Extended Desktop) stopped working. Dragged windows to other display would disappear, if second desktop was activated the window would show up but could not be clicked on.

Rolled back driver, all working as it should. Xorg crashed at startup though.

---

### Post by Olimpusmons on 2014-02-06
> **egeezer said:**
> The best reference is one that will show you how to get rid of the fglrx driver and revert to the opensource one; that one works well enough to use Compiz in all its glory!:
                         [COLOR=#000000][FONT=Liberation Serif][SIZE=3]*[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)*[/SIZE][/FONT][/COLOR]

Thanks! 
I got rid of the update driver, installed the older one, works as it should now!

---

### Post by jameshoneysett on 2014-02-06
I used Synaptic Package Manager to roll those 2 packages back to their previous versions and then forced them not to update.  Seems to be working fine at the moment but if I get any problems I might have to start using the opensource driver instead.

Do you think they will fix this issue with future updates?

---

### Post by cschroter on 2014-02-06
AMD graphics driver updates are a gamble. In my W7 load the latest releases cause problems, so those are rolled back and will not be updated until I am really bored.

If you are not experiencing any problems, applying the updates is not recommended.

Search the support forums on AMDs site for information on the new releases. They do try to fix reported problems. _AMD support forums:_ [http://forums.amd.com/game/categories.cfm?catid=488&entercat=y](http://forums.amd.com/game/categories.cfm?catid=488&entercat=y) for linux or [http://forums.amd.com/game/](http://forums.amd.com/game/) for all categories.

Post on the AMD site and report your problem. Maybe they will get fixed in new updates. Always a bunch of unhappy campers on the AMD forums, unlike here.

The open source driver does work but lacked functionality in managing my displays.

---

### Post by cschroter on 2014-02-06
> **jameshoneysett said:**
> I used Synaptic Package Manager to roll those 2 packages back to their previous versions and then forced them not to update.  Seems to be working fine at the moment but if I get any problems I might have to start using the opensource driver instead.

Do you think they will fix this issue with future updates?

Thanks for referencing the Synaptic Package Manager, had not used it yet. Another way to do the same thing.



2:13.101-0ubuntu0.0.1 is the version that is working for me.

---

### Post by soiled skivvies on 2014-02-11
Bug: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379)

Solution from that very page:  [COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install fglrx=2:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]8.960-0ubuntu1[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]                                   sudo apt-mark hold fglrx

[/FONT][/COLOR]Solution mentioned worked first try and I did it right through the regular terminal in UI mode with Ctrl + Alt + T.  I hope it works for ya. :)

Edit: Be sure to double check auto updates now and make sure fglrx isn't checked or you'll have to do the above until it's either fixed or someone can teach us how to make it ignore updating.

---

### Post by jameshoneysett on 2014-02-16
> **soiled skivvies said:**
> Bug: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379)

Solution from that very page:  [COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install fglrx=2:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]8.960-0ubuntu1[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]                                   sudo apt-mark hold fglrx

[/FONT][/COLOR]Solution mentioned worked first try and I did it right through the regular terminal in UI mode with Ctrl + Alt + T.  I hope it works for ya. :)

Edit: Be sure to double check auto updates now and make sure fglrx isn't checked or you'll have to do the above until it's either fixed or someone can teach us how to make it ignore updating.

Thanks for that :)

---

