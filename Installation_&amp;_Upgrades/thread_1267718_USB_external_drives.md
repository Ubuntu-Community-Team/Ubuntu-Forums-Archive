---
title: "USB external drives"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2009-09-16
I have a friend who wants to try Ubuntu, but does not initially want to partition her HD where XP presently resides. She has done some reading and realizes that if she was able to load ubuntu onto that USB external it would be slower but those are her terms.
My question that she asked me that I said I would aske you is what must she do to that USB its brand new out of the box 160GB to get it ready. (she has my 9.04 live CD) to install it on her external.If need be I can loan her a gparted or burn one for her.
Her fear is not being able to get back into windows that she uses for quilting.
She wants to do it herself (thank God) so give me your best detailed advice or resource.
I seem to remember way back in a similar situation and a panic of gstting an error 17. I want her to do it right first time.
So give me your best advice and thanks.

---

### Post by earthpigg on 2009-09-16
why partition? have you considered WUBI? 

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

no partitioning at all, gives you an option at boot to use either Windows or Ubuntu, and will allow her to uninstall ubuntu with the Windows add/remove programs tool.

she could also use Ubuntu's USB Startup Disk Creator on the 160gb drive - the advantage of this is that it would function like a LiveCD and be runnable on any other computer. she could bring her ubuntu settings, personal files, etc, with her wherever she went.

she could also boot from a live CD with the usb drive plugged in and install it onto that usb drive as normal. tell her to be very careful and triple check everything when she gets to the partitioning part and selects 'manually partition'. if she wants to make it impossible to mess up, she could go ahead and physically disconnect the windows hard drive when she does this.

then, set the boot order in bios to be: 1) usb 2) cd 3) internal hard drive.

plug the ubuntu external hard drive in when she wants to use ubuntu, unplug it when she wants to use windows.


those are about all the options i can think of off the top of my head that would meet her objectives.

---

### Post by texas.chef94 on 2009-09-16
Manu thanks for the reminder on wubi will certainly pass that on and I have a question about that process, fprshe will probably ask. She has a 40GB HS and is into quilting and genology so there is that software present and for grins lets say her C drive after wubi install has 8-10 GB remaining. She then lets say grows C some more with her additions to ubuntu. Do you see where I am going here, how cloce can one get and still allow XP to function or am I all wet. 

Your other option and you said "she could also use Ubuntu's USB Startup Disk Creator on the 160gb drive - the advantage of this is that it would function like a LiveCD and be runnable on any other computer. she could bring her ubuntu settings, personal files, etc, with her wherever she went."
If time permits can you explain that in detail or point me to a resource.
Thangs and again thank you so much

---

### Post by earthpigg on 2009-09-16
wikipedia :)

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

post back if you have any questions.

it essentially functions exactly like a LiveCD in that it will probe the computer's hardware every boot, *except you can save changes, files, documents, install additional software, etc*.

---

