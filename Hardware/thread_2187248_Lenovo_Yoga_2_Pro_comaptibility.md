---
title: "Lenovo Yoga 2 Pro comaptibility"
date: 2013-11-11
forum: Hardware
---

### Post by nerdcommander on 2013-11-11
has anyone got Ubuntu running on the Lenovo Yoga 2 Pro yet?
thanks in advance.

---

### Post by nerdcommander on 2013-11-17
so I decided to try this out, and i pulled the trigger and bought one. got the i7/8gig ram/250gig ssd version.
after an unsuccessful attempt to dual boot widows 8.1 and ubuntu, i erased the drive and went for it. didn't really intend to use windows but thought about keeping it "just in case" but trying to dual boot was frustrating! 
ubuntu install went well off of USB (no disk drive) 
I had a wifi issue and brightness issue right off the bat, but some searching turned up this excellent review of the machine and using it under Arch Linux:
[http://keithcu.com/wordpress/?p=3270](http://keithcu.com/wordpress/?p=3270)

and the first commenter, named "Eric" did this in ubuntu and i followed it and it worked for me.
> 
after installing Ubuntu I permanently enabled WIFI with this&#8230;
sudo vi /etc/modprobe.d/blacklist.conf
and add this to the file &#8211;> blacklist ideapad-laptop
 to enable screen brightness with working +/- buttons i did this&#8230;
 sudo vi /etc/default/grub
change this &#8211;> GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
to this &#8211;> GRUB_CMDLINE_LINUX_DEFAULT=&#8221;acpi_backlight=vendor quiet splash&#8221;
then run this &#8211;> sudo update-grub2

i also dialed back the screen resolution (3200x1800 was too much everything was tiny) and the touchpad is kind of twitchy, but other than that, i'm happily running ubuntu

---

### Post by viniosity on 2013-11-22
Out of curiosity, what kind of battery life are you seeing with the Y2P? Is it usable at all as a tablet?

---

### Post by nerdcommander on 2013-11-28
> **viniosity said:**
> Out of curiosity, what kind of battery life are you seeing with the Y2P? 
it lasts me most of a work day so far - seems like between 5 and 7 hours of word processing and web surfing mostly.
> **viniosity said:**
> Is it usable at all as a tablet?
it's interesting. the touch screen works (takes input) for many applications - reading pdfs is particularly nice, but mostly it selects stuff when you touch the screen, which isn't all that helpful. the screen does not auto rotate. and the keyboard and touchpad are still active if you flip it all the way around to make a tablet os that is a bit weird too. not sure what the exact answer to your question is - depends on what you want to use it for I guess.

---

