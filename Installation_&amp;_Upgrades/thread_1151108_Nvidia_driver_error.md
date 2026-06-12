---
title: "Nvidia driver error"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Jay Car on 2009-05-06
Hardware is, MSI Motherboard, AMD processor, 1GB RAM, nvidia graphics card (8500GT).  Ubuntu Hardy was previously installed.  This morning did a fresh install of Jaunty.

After installation and restart, a notice popped up that restricted drivers were available.  However, after giving permission to update those drivers, this error shows.  
 
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Not sure what's causing it. Can't seem to get past it.  Any ideas?  

Thanks for any help...

---

### Post by Jay Car on 2009-05-06
Update:

We've removed all items listed as Nvidia in synaptic, then reinstalled nvidia 180.  Also have tried several solutions we found in the forums.  Finally just reinstalled Ubuntu Jaunty and tried again.  Still cannot play commercial DVDs, and desktop effects works once then deselects and compiz settings are greyed out.  

To be honest, we've tried so many things that I've lost track.  What's really puzzling is that Jaunty has installed beautifully on several other computers, with similar hardware.  I just don't know where to look next for a solution.  Help, please? Thanks.

---

### Post by Jay Car on 2009-05-06
Update 2:

We've followed the instructions shown in the "Comprehensive Multimedia & Video Howto", but so far no luck. After making sure the medibuntu, multi-verse and universe sources were all enabled...have attempted to update several times. But with each attempt, in the Update Manager, the Proposed Updates list only shows one update:
"Linux-Restricted-Modules-Generic"
But it is greyed out and cannot be selected.

Help, help (please?) Thank you.
Jay Car

---

### Post by Jay Car on 2009-05-08
My first three posts on this topic were part of helping someone else with their Ubuntu computer.  I wanted to show the young lady I was helping how to use the Ubuntu forums to get help.  

I'm thinkin' I didn't do a very good job.  

Anyway, she is coming over today, and we are going to tackle the video card problem again.  

Since I last posted here I've tried to think it all through.  I'm wondering if the Ubuntu driver is not seeing her video card at all.  Maybe it is only detecting the onboard video card and not the installed one?  

Both the motherboard and the added video card are MSI-branded products.  The add-on card is has an Nvidia chipset (is that the correct way to describe it?), is an 8500 Gforce (I don't have it here yet, so I'm going by memory, but I think that was it).  It has its own processor and 512M of RAM, so there is no reason it shouldn't be able to handle the 3-D desktop effects at the very least.  

On Wednesday we honestly tried every solution we could find before we posted this to the forums.  

I haven't done hundreds of Ubuntu installations, but I've done enough to know that the problem she's having is odd.  The computer is two years old, it has never had Windows on it, its first system was Mandriva, but was changed to Ubuntu Hardy (I did those installations and both were very easy).  

She now wants to learn more for herself and asked that we go through upgrading to Jaunty.  I have Jaunty on my own computer and only had one small problem that was quickly fixed with an update.  My computer is the same age as hers, so I saw no reason not to do the upgrade. It seemed like a great learning experience.

I try very hard not to bother people here, you are all very busy and others need help too...but I wish someone would answer this post and at least point us in a good direction.  I am sure there's a solution for this.

Is it possible that the motherboard needs a driver update?  I believe it's a VIA board. I did check the MSI website to see if there might be a Linux driver for this video card, but it was a little confusing...yes, we are probably trying to do things beyond our current skills, but isn't that how people are supposed to learn new things?

We also tried installing other distros (Ubu-Jaunty, Ubu-Studio, Puppy, Mint, Kubuntu, and finally PCLinuxOS), and had the same problem with all of them, so it has to be the video card itself, or maybe we just don't know how to make the software see past the onboard video.  

We've decided to install Jaunty again today, and start fresh...at least now we know what doesn't work (hey, that's progress, yes?) :)

Anyway, even if no one answers this post, at least wish us luck.  We're pretty determined to figure this out, one way or another.  Having someone to give a little guidance would be greatly appreciated though.  


Jay

---

### Post by Jay Car on 2009-05-08
Did I post all of this under the wrong forum topic?  Should I try "Hardware" instead? Or "Multimedia and Video"?  

I guess I just picked this one because we were doing an upgrade, but maybe it would do better somewhere else?

---

### Post by cariboo on 2009-05-08
The error you are getting about the medibuntu repositories has nothng to do with the nvidia drivers, so just ignore that error for the time being. When instlling the restricted drivers, don't get impatient, dpending on how busy the repositories are it may take some time to download them.

BTW please don't bump a thread until after 24 hours has elapsed, click the Do's & Don't's link in my siganture.

---

### Post by jenkinbr on 2009-05-08
> **Jay Car said:**
> Hardware is, MSI Motherboard, AMD processor, 1GB RAM, nvidia graphics card (8500GT).  Ubuntu Hardy was previously installed.  This morning did a fresh install of Jaunty.

After installation and restart, a notice popped up that restricted drivers were available.  However, after giving permission to update those drivers, this error shows.  
 


Not sure what's causing it. Can't seem to get past it.  Any ideas?  

Thanks for any help...
You aren't doing anything wrong - sometimes it just takes people time to reply.  As for your issue, it is simple, and I'm not sure why nobody has helped you yet.

The error you are getting here is because you do not have the public key for the medibuntu repositories.  The problem can be solved by installing the [medibuntu-keyring]("http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb") package by downloading it directly and double-clicking it.  A window will open and you should see the option to install the package.  Click 'Install Now' and enter your password.  The package will install, and this warning (It is a warning, and not an error) should go away.

---

### Post by Jay Car on 2009-05-09
I promise to never bump inappropriately again. I would never intentionally be ill-mannered, and I apologise if my posts seemed impatient or unkind.

Your thoughtful responses have been noted. 

Thanks.
Jay

---

