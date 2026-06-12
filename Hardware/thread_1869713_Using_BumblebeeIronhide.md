---
title: "Using Bumblebee/Ironhide"
date: 2011-10-26
forum: Hardware
---

### Post by SyntheticShield on 2011-10-26
I have a Dell XPS 17 L702X with the Nvidia 550M Optimus.  I have been reading about Bumblebee which apparently is now branched to currently being Ironhide.  I want to install this and see if I can get the Nvidia card working which I have been unsuccessful in doing so since getting the laptop.  However, I am unclear, or the information doesnt seem to be clear on it whether or not I need to have any nvidia drivers installed before using bumblebee/ironhide.

I have disabled the proprietary driver and purged bumblebee which I had installed.  So I believe Im strictly on the integrated graphics card at the moment.  Also, during the configuration of bumblebee it asked, and I forget what the configuration was now, but a couple of the choices were XV, JPEG, YUV I believe and one other and I have no idea which one is correct.  Can anyone shed any light on that?

I would appreciate any assistance in getting bumblebee/ironhide set up.  Thanks in advance.

---

### Post by netmaxed on 2011-11-05
Hi
I've got the same problems with my Toshiba Qosmio x775.
As I understood, NVIDIA card is not directly connected to the video output, so it writes into Intels' video memory, thats where the modes XV, JPEG, YUV come into play.
Have you tried all of these modes?
At the current stage, however, it didn't help me in any way to switch to NVIDIA card :)
Good luck!

---

### Post by SyntheticShield on 2011-11-05
I tried a couple of them and both ended up messing up my system to the point of having to do a re-install.  Right now I have all the Nvidia drivers removed, no proprietary drivers installed.  

Overall I am very disappointed.  I had hoped Linux, specifically Ubuntu would have evolved to the point it would not force people to settle on using entry level, low end spec'd hardware.  Apparently that is not the case.

I see many posts out there about people having issues with the Nvidia cards but very little in the way of assistance which is a bit disappointing as well.  As you can see, I made this post a week ago and you are the first reply.  Ive been trying to do my own research but its difficult to tell what is worthy of attention and what is not when no one replies.  My first laptop with more than base hardware and I cant really take advantage of it.  Much of the information out there is outdated which is another surprising issue.  I can imagine all the people that work in development of Ubuntu and not one of them has any kind of system with Nvidia video cards and therefore has not worked out a way to make it work.

System76 has apparently found a way also as they sell high end laptops with Nvidia graphics but I do not know how they have done it.  So now my $1000.00 laptop is virtually nothing more than a $500.00 entry level unit and my friggin fan runs constantly, I believe due to the Nvidia issue and so now my battery life sucks and Ive posted on that, posted in the IRC channel and nothing.

Its frustrating because I am so grateful for something like Ubuntu being out there and available and an alternative to Windows but then I keep asking myself how are they to encourage anything other than just casual surf the web and email computer users if they dont have help or solutions for such issues.

---

### Post by netmaxed on 2011-11-07
well, after some trials and fails I've managed to install Ironhide and it is working.
So I can run programs on Intel graphics just starting them and I can run them on NVidia by typing "optirun" before the name.

I'm not exactly sure what actually happened so everything worked out, but my last steps were:
0 I've tried to purge remove all nvidia drivers, all ironhide and related packages (acpi-call, etc.)
It showed some errors because it couldn't remove ironhide-xen (whatever it is), but I ignored that.
1 installing NVidia-current driver by "sudo apt-get install nvidia-current"
2 running "nvidia-xconfig", which I had to locate first somewhere in the /usr folders (it couldn't find it in the PATH, i suppose). Actually it has generated xorg.conf.nvidia in /etc/X11 which is not in use right now. So i'm not sure if this is necessary.
3 I have activated "nvidia-current" driver through System Settings -> Additional Drivers.
4 install Ironhide by "sudo apt-get install ironhide"
during Ironhide setup I've selected default XV option and it works fine for me.
And this was the only time when Ironhide has actually set up correctly and displayed some example with rotating gears.

So, right now my xorg.conf looks like this:
----
Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection
----
This is the only configuration that allows lightdm or gdm to start.

I don't know if this is of any help to you, so good luck!

---

### Post by SyntheticShield on 2011-11-08
Thank you for posting that netmaxed.  I was, just a day or so trying once again to get the Nvidia card working.  After a couple of hours of trying just about everything I found on the forums and from google searching I decided I had wasted enough of my life on this issue.

Though, now that you have posted your progress, I suppose it wont hurt to give it a shot and see if I can get anything going.  If it doesnt work, I will have to hang my head in shame at the thought that all the people I have tried to convince to use Linux (Specifically Ubuntu) will be left with no choice but to buy entry level computers because anything that has any performance is a mess to try and set up.  The whole ordeal just has me very frustrated and disappointed.

In fact I just got done consulting with a small start up company a couple weeks ago with regards to their network set up and computer operating systems (before I got the laptop with the Nvidia card) and touting Linux Ubuntu to them and they all loved it.  Now I guess I have to hope and pray they dont want any computer hardware with anything above minimal performance.

I am curious, netmaxed, is your fan constantly running on your laptop now that you have the nvidia driver working?  Was it running all the time before you got it working?  My CPU fan runs constantly and Im certain its due to the Nvidia issue since they share the same cooling tubes and theres only one fan to move the heat off the CPU and GPU and the CPU rarely goes over 120* according to the sensors unless Im doing a lot of different things at once on it.

---

### Post by netmaxed on 2011-11-08
how is it going?

I ran some extensive calculations today and my fans were much more active than usual.
Right now I neither hear them nor feel hot air stream.
But I've got Toshiba, not Dell

---

### Post by SyntheticShield on 2011-11-11
Ive actually given up on it.  Im in the stages of considering selling the laptop and buying something that doesnt have a dedicated graphics card.  The problem is that this laptop has the JBL sound system which sounds FABULOUS and it has dual hard drives.  And thus far I have not been able to find a Dell laptop with those options without a Nvidia or ATI graphics card.

I cant take the thing and use it on battery for all that long (in comparison to the 7 - 8 hours I get on my other Dell laptops) because the stupid fan runs constantly, though CPU temps are in the 120* range.  I have a Dell Inspiron 1750 with not quite the hardware and its temps run just about in the same range and the fan hardly ever comes on and I can easily get 7 hours of computing out of it.

So my plan is that as soon as I can find a Dell laptop that has everything this one does without the Nvidia graphics card, this laptop is gone and I'll buy a new one.  Its a disappointing experience.  Chalk it up to lesson learned.  You can buy above average hardware and use Ubuntu apparently or any Linux distro it would seem.  The issue with the Nvidia card is not strictly an Ubuntu issue.

That all said, I do appreciate you taking the time to try and help out netmaxed.  It is very much appreciated.  I just wish the outcome were different.

---

