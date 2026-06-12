---
title: "Can't install Intrepid from LiveCD"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by PoopLoops on 2009-06-15
Okay, story is I got a new laptop, stuck in a 2nd hard drive, installed Jaunty 64bit, and then it turns out there are no drivers for my ATI card on Jaunty.  Okay, I decide to install Intrepid instead, but first I wanted to transfer all of my files so that I don't lose them.  I wanted to use Gparted to shrink the partition, install Intrepid next door, switch the files, and then delete the Jaunty partition.

I tried to use Gparted to shrink the partition, but I had to have the partition unmounted to touch it.  Okay, so then I tried to make a USB boot "disk" for Gparted, but it wouldn't boot to it.  I then decided to see if the Intrepid LiveCD has it already, as I read that Gparted is on a lot of LiveCDs.  I got to the partitioning section, couldn't find anything, so I canceled and booted normally.  

I realized that if I were in Vista, the Jaunty partition would be unmounted, so I didn't really need to make a bootable USB thing.  After looking around online for a program that would do it, I got nothing really and just got fed up with it.  So, I decided to just move all my files to my Vista disk (I installed a program that let's me access my ext3 partitions), completely wipe the 2nd hard drive, and install Intrepid fresh.  

Except that now my Intrepid CD won't "boot".  It will get to the main menu, I'll hit "install", it will start to think, but eventually I see something "fails" and I get dropped to a ubuntu@ubuntu terminal, which I'm guessing is the LiveCD partition or something.  So I burned a 2nd CD, just in case, and same deal.  Now I feel bad for wasting an extra blank CD. :(

Booting from either hard drive still works fine, so I'm even more confused.  I guess it *could* be my CD drive, though I installed Jaunty on it just fine, and Intrepid went all the way to the partition section of the install...

Does ANYBODY have any ideas what I can do next?  Because this is redonkulus.

---

### Post by PoopLoops on 2009-06-15
I just tried to install from a 32-bit Intrepid LiveCD (it was a 64-bit last time) that was burned on a different machine.  Same thing happened.  Decided to just boot from the CD to the "trial" desktop to see if at least that works.  No dice.  Dumps me into the terminal.  If I try to run '/etc/init.d/gdm start', it fails.  I went to the /var/log folder and in the Xorg.0.log file it said:

Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Now, I had installed Jaunty on this thing and Intrepid was working the first time I tried it, so I don't know what could have happened.  My BIOS doesn't let me change my monitor settings and this is booting straight from the CD.  I then tried to install again, using "safe graphics" mode.  Same thing happened, same error in the Xorg.0.log file.

This is an Alienware M17 laptop, by the way.  I don't know if that helps at all.  It has 4GB of DDR3 RAM.

EDIT:  Okay, I found a solution here:

[http://ubuntuforums.org/showpost.php?p=2947425&postcount=5](http://ubuntuforums.org/showpost.php?p=2947425&postcount=5)

Basically I install the correct drivers from the prompt of the LiveCD, get to the Desktop, and run the Install icon.  Good enough, I guess, but still kind of lame...

---

