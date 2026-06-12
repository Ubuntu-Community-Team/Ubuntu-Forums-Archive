---
title: "Keyboard problem"
date: 2021-08-22
forum: Hardware
---

### Post by habana on 2021-08-22
I can’t decide whether this is a hardware or software problem:

I am typing an email (Thunderbird) or a document (Libreoffice)  and randomly, after a few minutes or a few hours, the Shift key sticks on and I find myself typing in upper case. If I  hit the Shift key,  it will revert to lower case either immediately or after several attempts. A simple case of a stuck key? No, I have tried three keyboards with no change. I have tried different USB ports and have checked the motherboard voltages in BIOS.

All other keys seem to work normally.

Restarting the computer always fixes the problem, for a few minutes or a few hours. As an electronics engineer I am used to dealing with hardware issues but this doesn’t feel like one.

Anybody got any bright ideas?

Ubuntu 21.04
Gigabyte B360M-HD3

---

### Post by Autodave on 2021-08-22
Well I agree with you that it doesn't feel like a hardware problem, it feels even less likely a software one.  Are you by chance using any USB hub on the machine at all?  Do you have the capability to actually measure the voltage of the 5 volt line?  A meter that will give (and store) your minimum voltage would be helpful.  Try running the PC without ANYTHING else connected to any port.  Does that help?

---

### Post by habana on 2021-08-22
Thanks for your advice. No USB hub. It is a pity that lm-sensors doesn't support the sensing chip on my motherboard but I now have a DMM sitting on the adjacent USB port, 5.06V at present. When the problem occurs I can check the voltage again.

I have no other USB devices connected apart from the mouse, which I have changed. I do have an RJ45 LAN connector, an HDMI monitor connector and an analogue audio connector. I can't see what effect they may have on my problem?

---

### Post by him610 on 2021-08-22
That used to happen to me occasionally, but I figured out I was inadvertently pressing the Caps Lock key instead of one of the adjacent keys, Tab or Shift. This is what I did...
> # Keyboard tips
Swap keys, Caps Lock with Escape
Edit /etc/default/keyboard
change the line 
XKBOPTIONS=""
to read 
XKBOPTIONS="caps:swapescape"
save the file
reboot
test the newly reassigned keys
 
Then I made a little note and stuck it to a flat space on the upper part of my keyboard, 'CAPS Lock switched with ESC.' I think Google had the right idea with eliminating CAPS Lock from Chromebooks.

---

### Post by Autodave on 2021-08-22
I have no other USB devices connected apart from the mouse, which I have  changed. I do have an RJ45 LAN connector, an HDMI monitor connector and  an analogue audio connector. I can't see what effect they may have on  my problem? 				

I don't think that any of them would cause the problem.  I really think that something is pulling that 5V line down too low.  I have seen it happen too many times for too many different reasons including a hard drive that would pull almost 3 times the amperage that it was supposed to pull.  That one took a little while to figure out.  I know that you don't have this, but I have a powered USB port sitting right here which is now just a rather expensive fast charger for my cell phone.  At times, when booting, it would cause my monitor to change resolution, my keyboard and/or mouse to quit working.  And they were NOT hooked up to it!  Only way to fix it was to power it down and back up again.  That would last several weeks at first,  Then several days, then minutes.

If you don't find any problem with the 5V line, check the 12V next just to be sure.  If your power supply is OE, that could very well be the problem since they usually just have enough power to run the machine the way it was built when purchased.  I always keep 2 or 3 extra, new PSUs around.  Can go a year w/o seeing a bad one and then run into a couple in a week's time.

---

### Post by habana on 2021-08-23
@him610
Definitely not Caps Lock as other shift functions (!@#$ etc) occur when the fault appears. Thanks for the suggestion anyway.

@ Autodave
I set my Fluke DMM to MIN after booting my PC. I induced the fault in Writer by pressing the Shift key and a letter a few times. Minimum voltage 5.04V so that can't be it. How would the 12v line affect the keyboard? I built this PC myself using a Gigabyte PW400 PSU which is more than adequate for the other hardware (SSD and DVD). If it was a PSU problem wouldn't it affect other keys? It just acts like a faulty key but I have eliminated that by changing keyboards. Weird.

---

### Post by Autodave on 2021-08-23
The 12V line will not directly affect the keyboard, but it could be affecting something else which could be causing a problem.  If you have the ability to get a maximum over/under reading on your Fluke, just do it and then you'll know.

Another idea just to see if it is a software glitch: make a bootable medium and boot to it and run from that.  If you still have the issue, you can be pretty sure that it is hardware at that point.

---

### Post by habana on 2021-08-23
Thanks Autodave. I do have a live USB stick so I'll give that a go and report back - it might be a while.

---

### Post by habana on 2021-08-23
I ran 20.04 with a live USB stick for an hour or so with no problem. Not conclusive but it's pointing to a software problem. Back in 21.04 I have disabled Sticky Keys so I'll see how that goes

---

### Post by Autodave on 2021-08-23
If you upgraded your 20.04 to 21.04, that could be the problem.  I have seen too many weird things happen when one release is updated to another.  I learned a looooong time ago to stick with the LTS releases only and to do a clean install after backing up my data.

---

### Post by habana on 2021-08-23
Well I've been an Ubuntu user since Gutsy Gibbon and that's not been my experience. I do a clean install every couple of years or so, usually when upgrading hardware. I have issues of course but solve them eventually often with the much appreciated help of these forums - all part of the learning experience. In recent years the upgrade experience has become more and more straightforward.

Having written that, I do automatic daily data backups to my NAS and have another couple of Ubuntu computers I can fall back on.

---

### Post by Autodave on 2021-08-24
I generally have a dozen computers running at various places.  One year, I decided to upgrade all of them instead of clean installs.  1 worked with no issues, 2 worked with minor issues, 9 didn't work and ended up being clean installs.  I learned my lesson.

---

### Post by habana on 2021-08-24
If I was managing a dozen machines I would probably do as you do, stick to the LTS, download the iso once and upgrade the lot. It's a bit different for a reasonably tech-savvy single user. Anyway, the problem seems to have gone away so I am making the assumption that disabling Sticky Keys was the fix. 

Thanks for your advice. I will mark this as solved and if it reappears I will repost in General Help.

---

### Post by andro-bernard on 2021-08-24
May not be pertinent, but I have found odd keyboard issues with just some keys arbitrarily not responding after some time and other strange behaviour when using an NVidia graphics card on 20.04 and 21.04 at least when the default Nouveau driver is in use. Changing that using the Additional Drivers app to the proprietary NVidia driver cures the problem completely. Why this should be I do knot know, but there are threads mentioning this solution on the internet. I do admit that it is baffling to me how a video driver affects a keyboard driver, but it is demonstrably true. You could give that a go, and this would at least do no harm, Hippocrates principle. :-)

---

