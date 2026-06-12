---
title: "Partitioner View Limited During Install``"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-05-13
I'm attempting a second install of Ubuntu 9.04 on a different partition, which has to be manually partitioned.  Trouble is, the default boot screen resolution is only 800x600, and the screen view of the drives and existing partitions is too large to be completely seen on my monitor.  No way that I can see to reset the resolution during the install, and no way to scroll across the large view presented. That means I have no way to go forward.  Any suggestions?

Oh, let me add this:  The problem is that the Forward box in the view window is pushed off screen to the right.  Efforts to try and guess where it might be positioned beyond sight and put my mouse pointer there have not worked.  I can't hange the screen size during the install.  I see an option to work with a driver disk, but i don't know what that entails.  Trying to specify a safe graphics mode have failed at this point.  Going Back, I see that for each of the proceeding screens, their Forward boxes have also now been pushed off screen to the right.  Being forced to Quit, I suddenly find that I have the Ubuntu desktop with the Examples and Install icons on the Desktop.  But I can't set the Display option higher than 800x600 even there.  So we just go through the whole mess again.

I did note that there are two scroll bars on the partition window associated with each drive view to show how the drive is partiioned.  I've two drives, but only one seems to be displayed, though twice.  You can scroll across a large drive presentation. but no way to scroll the whole screen at once.  An easy fix should be to take the Back/Quit/Forward buttons and position them nearer the center of the screen rather than way over on the right side.  Meanwhile I seem to be stuck, with no evident way to get around this problem.  I think this problem came up this time because during my first install, I had the partitoner go ahead and divide up the hard drive into multiple partitions for later installs, so the view of the drive is now extended way out to the right because of the added partitions.  I also note that I do not have the option to just designate one of the free Ext3 partitions that is sitting there empty but formatted, I have to go into manual mode so as to tell it specifically where to install itself.

In other words, you know there are workarounds, i've found a few workarounds myself, but there are a lot of people that would find this too hard or two difficult, or not choosy enough as they go along.  But obviously I don't know enough at this point to deal with a large hard drive that has enough partitions to stretch the view of it way off to the side and cause one or more of the decision buttons to go off screen as well.

---

### Post by oldefoxx on 2009-05-15
I went to the effort of opening a bug report on this.  That took some time, as it was not vary obvious of how to fill out of file a bug report.  I haven't yet figured out a way to bypass or get around a situation like thism and I'd be most interested to see it addressed and resolved.  Manwhile, I'm stuck working on the hardware in one PC, and have some new parts on order.  So I will look into this later, and see if anything has happened on this topic.

---

### Post by zvacet on 2009-05-16
Press F1 ( it is help ) and I think you will find option for changing resolution.

---

### Post by oldefoxx on 2009-05-18
Well, I guess you were eager to jump into this thread without bothering to check to see if F1 could do anythng in this regard or not. How hard would it have been to check for yourself first?

It doesn't.  First, there are only three boot options suggested by using the F1 Help with regards to the video.  First, for laptops, maybe vga=771 might help.  That's not high resolution.  Second, you could ask for a braille tty mode.  No idea what that does, but it would not be visual in the usual sense.  Third, you could try a text mode instead.  Only then you are really flying by the seat of your pants.  Ever try a text-base boot and install?  It's more difficult than you realize.

Another point too.  F1 ia effective at the start of the install process, so you would have already suffered the disappointment of not getting the GUI approach to work, perhaps repeatedly, dispite every effort to find a workaround that would work.  This is a bug, man, and you need to get on board with what is really happening (or in this case, NOT happening) before trying to make little of it.  At least duplicate the conditions, try it yourself, and report back if you either find it true, or have come up with a solution.

Oh, I see.  You have other things to do instead.  Best get to them then.  I don't want to keep you.):P

---

### Post by oldefoxx on 2009-05-20
Man, I've been stuck on this one.  I encountered this problem a number of days ago, and after not being able to get around it, finally posted the first message in this thread.  I amplified on that later after some more futile attempts.  But the only answer thus far just suggested maybe I had not considered the obvious.  I had, in the sense that I had explored every one of the F-key options to see if there was anything I might have missed.  Still a no-go.

So, brooding on this matter last night, asking myself how long I could endure this situation and where to go to next, it finally came to me:  Maybe I could install an earlier version of Ubuntu and then upgrade it to version 9.04 with the tools provided.  So the next question was, which versions will upgrade to 9.04 on their own, and would the install process with any of them work better in this regard?

So I began my search with Google and the phrase Upgrade to Ubuntu 9.04, and checked out the responses that came back.  Man, I will tell you that having Google to work with really makes a difference.  Not only fast, but thorough.

Anyway, according to what I read on one site, the only version of Ubuntu that will upgrade itself to version 9.04 is the one just before it:  8.10 LTS, also known as "Intrepid Ibex".  I was hospitalized and in recover when it came around, so missed out.  The next step was to use Google again and search on Ubuntu 8.10 LTS Download (the word "Download" cuts through all the chatter and gets you to sites where you can actually get the software).  I found one, downloaded it to my desktop, used my installed Brasero Disk Burning software (under Applications/Sound and Video), and told it to burn the image to a blank CD.  No problem there.  But it was late, so the actual effort had to be delayed until this morning.

Guess what?  It booted up nicely off the CD, I indicated I wanted to do the install, and saw some interesting things.  For instance, the little world map with red pinpoints on it, possibly cities of reference when selecting a time zone.  That was a first.  But the really good news was getting to the partitioner section and not only seeing two presentations of my current single disk setup, but one labled Before and the other After to let you know exactly what that choice was going to do to your hard drive.  Now the presentation of two bars for one drive made sense.  And it was properly scaled to appear all together in my monitor's viewable area.  So naturally the Back, Quit, and Forward buttons were properly displayed on the bottom of the screen.

This is so much better and more useful than the turmoil you can get into while trying to install Ubuntu 9.04 directly. I have to get back into the frame of mind where I know which partition I next want to use for this install, and rather than accept the default and do it automatically, I intend to try the manual approach again.  That's where the 9.04 version really blew it, but I am hopeful that this method will work more consistently throughout.  Now if it doesn't, I will still be in a sticky mess.

So rather than get to that point and then face what i would have to write, let me just say that it looks hopeful at this point, and again, going backwards first is what it seems you have to do in order to go forwards.  I wish that were not so often the case, especially with anything so complicated and involved as computer software.

---

### Post by oldefoxx on 2009-05-22
I'm way down the road now, having gotten three installs of 9.04 done (yes, using Ibex first is a good approach), settled on a version of VirtualBox for now (2.0.8 is more in keeping with Win2K and Office2K than later versions up to 2.2.2), and worked out two methods to use one VDI of Windows 2K and Office 2K and clone them for use under the other two installs of VirtualBox.

I know that mention of VirtualBox is more in keeping with the VirtualBox forums, but I see no harm in mentioning that it is very useful if you still want to work with an install of some version of Windows, but now as a client instead of as a host (more secure this way, and generally better performaing, because you do not have to laden Windows down with a bunch of protection software).  Fact is, this is a great combination, because any discontinuance of support for Windows is less of a threat, since the host (Ubuntu) and VM Manager (VirtualBox) serve as two exterior walls to help keep your Windows install safe (or safer) from harm and attack.

Big trick with VirtualBox is picking the right version to work with.  The releases are generally matched up with specific versions of Ubuntu and other host OSes, but you can make some variance there.  The Guest Additions is an ISO image that you can reference once your client's OS is installed, and it adds files and settings to make the client side work a lot better.  But each version of VirtualBox has its own set of Guest Additions, and experience by myself and others have shown that they are not all the same.  So a certain weakness in one might be helped by the Guest Additions from another version, but the GAs, as they are referred to, are not offered separately.  Anyway, visit the VirtualBox forums if interested.

Another little tip:  Searching either set of forums for any possible responses to your earlier postings is made easier by Google.  For instance. I can tell Google to look for Ubuntu Forums oldefoxx, and it picks out where that handle appears on the forums.  Then I can just go down the list.  For VirtualBox, just substitute that name for Ubuntu with Google, and you get a quick return from there as well.

---

