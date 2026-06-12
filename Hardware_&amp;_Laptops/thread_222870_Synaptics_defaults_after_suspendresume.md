---
title: "Synaptics defaults after suspend/resume"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by hpklett on 2006-07-25
Hello all, I've just got a Dell D620 (yay!), and I found that suspending and resuming reset all my synaptics touchpad settings to default.  synclient -l showed all the right stuff, but it behaved as default.  I googled and found the following little tidbit:

[http://www.nabble.com/Suspend-to-ram-and-synaptics-t1938633.html](http://www.nabble.com/Suspend-to-ram-and-synaptics-t1938633.html)

So did
```

sudo rmmod psmouse
sudo modprobe psmouse

```
then Ctrl-Alt-F1 Ctrl-Alt-F2.

Most of my Linux knowledge came from Gentoo, and I never really bothered with power management.

So my question is, what script do I put this stuff in to make it always run?

This seems to be a common problem, so it would be cool to get this into a Howto.  Oh and yes, I did look to see if this was answered for Ubuntu and specifically Dapper, but couldn't find anything definitive.  Sorry if I'm mashing the same potatoes.

Thanks

---

### Post by 5-HT on 2006-07-25
Try adding "psmouse" to the "MODULES=" line in /etc/default/acpi-support.
Any modules listed there should be removed on suspend and reloaded on resume.

To switch from X to a virtual terminal and back again on resume, you can uncomment the "DOUBLE_CONSOLE_SWITCH=true" line in the same file.

Hope that helps and you get suspend working properly.

By the way, are you having any issues with hibernation on your notebook?

---

### Post by hpklett on 2006-07-25
That works beautifully, THANK YOU!  Wifi died, but I don't honestly care.  When I resume I'm not neccesarily going to be in the same place anyway.

I've only hibernated a few times; it seemed to work just fine until I tried to shut down from gnome.  X locked up, so I had to go to console and sudo reboot.  Of course, a few minutes ago I added resume=/dev/sda3 to my kernel parameters, so honestly I have no idea how it worked at all.  I'll test stuff out later with the kernel params and let you know.

Again, thanks!

---

### Post by hpklett on 2006-07-25
4 hibernations, first worked perfectly, second locked up, third and fourth flawless.  I guess I'll just have to keep playing with it.  Pleny of standby's went perfectly.

One thing I just realized though.  I only gave myself a gig of swap.  I've got two gigs of memory - doh!  Oh well, I've so far not broken the 600mb mark, so I don't really care.  Maybe I'll shimmy that windows partition over a little.  Can anybody think of a way to actually use the 2Gb?

---

