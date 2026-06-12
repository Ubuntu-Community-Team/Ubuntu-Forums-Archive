---
title: "[SOLVED] Cannot Configure Touch Pad"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Sam Plamondon on 2007-11-25
I cannot configure my laptop's touch pad so that tapping on the pad does not "click".  When I first installed Ubuntu 7.10, I could just go to System, Preferences, Mouse and their would be a touch pad tab where I could configure clicking, and horizontal and vertical scrolling.  Now this tab has disappeared.
According to the Device Manager, my touch pad is a "SynPS/2 Synaptics TouchPad".  How can I configure it to my liking?
Apparently, this problem is caused by "xserver-xgl".

---

### Post by jcsteele on 2007-11-25
Have you recently made any adjustments to your system?  There is an open bug at [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/152375](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/152375) that is similar to the situation you describe which is why I am curious.  

Is this occuring with any other users on the system?  If you haven't tried, can you create another user on the system then reboot and login with the new user's credentials and confirm/deny that the problem still exists?

//jcs

---

### Post by Sam Plamondon on 2007-11-25
I created a "test" user and the same problem was present; I also tried "root", and the problem was still present.

---

### Post by Sam Plamondon on 2007-11-25
Actually, the bug described at the page you linked to is the exact bug I have.  I installed "xserver-xgl" (for my restricted ATI graphics driver) and the error appeared after this.

---

### Post by erfahren on 2007-11-25
I have a Synaptics as well, but don't have that option in my regular mouse settings.

Anyway, I disable the tap-to-click by putting the following in the touchpad section of xorg.conf
Option "MaxTapTime" "0"

more info here: [http://ubuntuforums.org/showthread.php?p=3839086](http://ubuntuforums.org/showthread.php?p=3839086)

that may work for you

---

### Post by jcsteele on 2007-11-26
I would file a reply to that bug report and ask what information you can provide.  The solution erfahren offered up does indeed work (make a backup of /etc/X11/xorg.conf BEFORE editing it), however I was more concerned with the fact that your touchpad settings "suddenly" disappeared, as thats not suppose to happen ;)

Like I said, file a reply and see what you can provide...this helps out ubuntu tremendously, as well as hastens the process of fixing a bug.

//jcs

---

### Post by bluedragon436 on 2007-11-26
I know of you go into the Synaptic Package Manager there is a settings control you can get for the touchpad...I believe it is found if you type a search for GSynaptics......I can't remember for sure what it was called when I got it for my touchpad...and between that and the mouse settings already installed with Ubuntu, I was able to configure it the way I want for the touchpad, the little nipple mouse, and my USB Optical Mouse....without having to be everchanging!!!

---

### Post by Sam Plamondon on 2007-11-26
Erfahren, your method worked for me.  Thanks for the help.
JCSteele, I replied to the bug report, and included Erfahren's solution for getting rid of tapping to click.
Thanks to everyone for the help!

---

