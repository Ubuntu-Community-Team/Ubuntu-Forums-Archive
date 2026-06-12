---
title: "Lenovo Ideapad 100 won't reboot"
date: 2016-10-29
forum: Hardware
---

### Post by Hesediel on 2016-10-29
don't reboot.
Exact model: Lenovo Ideapad 100 15IBD

If i try to reboot the pc shut off the display for a moment then it go back with a little retroillumination but it stays stucked. No commands or key works, only brutal shut off of the entire pc with the power button.

i made some search and "solved" not properly, but it seems to be a work around, getting:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"

on the file:

sudo kate /etc/default/grub

information from there:

[http://askubuntu.com/questions/706867/power-off-reboot-fail-lenovo-ideapad-100](http://askubuntu.com/questions/706867/power-off-reboot-fail-lenovo-ideapad-100)

the others commands worked for a while then they stopped. I don't know what commands really do, i only tryied them.



So i am using he notebook from several days what i saw:

Other people in a forum in my language have the same issue with the same model:

Changing the /etc/default/grub and the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in GRUB_CMDLINE_LINUX_DEFAULT="" makes the reboot working, i am using the pc now from days and in this way the reboot works from until.

if i re edit the file like GRUB_CMDLINE_LINUX_DEFAULT="splash" the reboot begins again not working and then after the reedit it dont works even deleting all and leaving ""

i had to reinstall the enteire system and edit once and leave it

and a new idea comed to me:

Edit i have a new finding that's maybe connected to this problem
i have this "bug" [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1637709](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1637709)
in few words the light of the webcam is always on it turns off when i open a software that uses it.

i always open google chrome (maybe thanks to hangout) so after a few the light turns off.

Now i tried to not open nothing and leave the led on and then reboot the pc....well every time i am (still) trying this even with the edit and this i wrote in the past messages, well the reboot dont work. if i make something to stop the light....the reboot works! It seems connected


some one with the same pc getting same problems?

---

