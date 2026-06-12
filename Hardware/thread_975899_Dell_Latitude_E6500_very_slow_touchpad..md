---
title: "Dell Latitude E6500: very slow touchpad."
date: 2008-11-08
forum: Hardware
---

### Post by softtower on 2008-11-08
I have a brand new Dell Latitude E6500 laptop and the touchpad has very low sensitivity and it's unbearably slow: moving a pointer across the entire screen takes 5-6 trips across the touchpad.

After a night of googling all I could find was a bunch of instructions on how to adjust Synaptics touchpads (that didn't work for me) and an old fixed bug regarding this touchpad not recognized by Intrepid:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270643](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270643)

My system is up to date, the touchpad is recognized, but any changes I make to xorg.conf don't have any effect (like in this article):
[http://www.zyxware.com/articles/2008/05/22/is-your-touchpad-too-slow-in-ubuntu-fix-it](http://www.zyxware.com/articles/2008/05/22/is-your-touchpad-too-slow-in-ubuntu-fix-it)

These laptops have been around for a while: does anyone have the issue fixed? I really like the machine, would hate sending it back to Dell.

P.S. On a side note, does any of E6500/6400 owners with Intel X4500HD have Compiz working with acceptable performance? 

Thank you!

---

### Post by softtower on 2008-11-09
Turns out in Ubuntu 8.10 these settings aren't in xorg.conf anymore. I had to edit this file to adjust the touchpad:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 

Funny how the absence of xorg.conf is presented as an improvement, while in reality we'll be adjusting settings via yet another set of XML (yep, XML) files scattered all over the place.

---

### Post by wgrant on 2008-11-09
Moving things out of xorg.conf is required to allow hotplugging of input devices, and is the start of a path towards much easier configuration over the next couple of releases. It wasn't done just for fun.

---

### Post by softtower on 2008-11-18
wgrant: I used to backup up my entire /etc folder, which helped me many-many times when I had to "relocate" to a new laptop or set up another computer.

Now, with these changes, my configuration is going to be scattered all over, being virtually impossible to collect&document.

It's hard to complain about something free, but it's also hard to silently watch how so-so situation with X configuration isn't getting better, but rather is transforming into completely different, yet still so-so situation. I'm an engineer myself and I just don't see how's multiple XML (!) files are better than a simple, single text file and how it prevents anyone from implementing hotplug. Moreover, I want to emphasize that going XML route for user-facing configuration files is a *very* bad idea: in the future we'll see tons of posts on these forums from people who forgot to close a tag or messed things up by copying&pasting "slightly" in the wrong place. In fact almost always the choice of XML is a bad idea. 

I'd be glad to post this somewhere else, where actual developers can read it, but I don't know how to track down bug databases/forums by a single isolated component. I hope you can help me deliver this message.

---

### Post by wgrant on 2008-11-18
> **softtower said:**
> wgrant: I used to backup up my entire /etc folder, which helped me many-many times when I had to "relocate" to a new laptop or set up another computer.

Now, with these changes, my configuration is going to be scattered all over, being virtually impossible to collect&document.


All configuration is still kept in /etc...

> It's hard to complain about something free, but it's also hard to silently watch how so-so situation with X configuration isn't getting better, but rather is transforming into completely different, yet still so-so situation. I'm an engineer myself and I just don't see how's multiple XML (!) files are better than a simple, single text file and how it prevents anyone from implementing hotplug.

xorg.conf InputDevice sections are for specific devices, so it's completely impossible to implement hotplug with them. Additionally, adding support for new types of devices would mean packages would have to mangle xorg.conf, which is very very nasty, sick and wrong. Now they just have to drop an fdi file somewhere, and they're done with it.

> Moreover, I want to emphasize that going XML route for user-facing configuration files is a *very* bad idea: in the future we'll see tons of posts on these forums from people who forgot to close a tag or messed things up by copying&pasting "slightly" in the wrong place. In fact almost always the choice of XML is a bad idea.

They're not user-facing configuration files. Almost no configuration file should be user-facing. XML is an awful lot easier to programmatically manipulate than xorg.conf, so they will be even less user-facing soon.

---

### Post by softtower on 2008-11-18
> Additionally, adding support for new types of devices would mean packages would have to mangle xorg.conf, which is very very nasty, sick and wrong

This is just one point of view, while there are many who disagree, for instance ArchLinux creators who went for a single BSD-style rc.conf file and thousands who loved it. Therefore there are many opinions about it to say the least, so I wouldn't agree with "nasty, sick and wrong" as a proper characterization of this approach. Although personally I generally prefer multiple files over one, I would have suggested having /etc/hal/config folder, instead of placing it in /usr, and I definitely, definitely, definitely would have avoided XML like a plague. 

Because... XML was meant to be computer readable, with human readability a distant second. This goes pretty much against general Linux philosophy of being text-based, human readable, and easily configurable. While XML files are close to impossible to manage without special tools. People *will* search for these files and try to manually edit them, cursing at XML tags forever, simply because there will always be new touchpad models with crazy options not supported by a current crop GUI configuration tools, it just how things have been in UNIX for decades.

I also have a lot to say about supposed "simplicity" of XML parsing, by the way, but I think this is a wrong place for such discussion, plus the discussion itself it pretty meaningless at this point.

---

### Post by washirv on 2009-08-02
> [quote]Additionally, adding support for new types of devices would mean packages would have to mangle xorg.conf, which is very very nasty, sick and wrong
This is just one point of view, while there are many who disagree, for instance ArchLinux creators who went for a single BSD-style rc.conf file and thousands who loved it.[/QUOTE]

rc.conf does nothing for hal besides start it at boot; you still get to play with XML files.  And the Arch wiki shows you how to make an xorg.conf-less system just like Ubuntu. :)

Back to the topic, my own E6400 appears to roll dice each time it boots.  Do I get a normal touchpad?  Very slow?  Completely unresponsive?  Same thing in Arch, despite my attempts to either let the OS figure it out, or fool hal into calling it a Synaptics.

Dell support was no help.  Ubuntu never had any trouble on my old Thinkpad; I've installed Arch on a number of notebooks without problem until now.

---

### Post by rdagold on 2010-03-21
Did you manage to find a solution to this problem? I am having exactly the same trouble. I followed [this tutorial]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics#ALPS_Touchpads") but it was all to no avail. Everything I set in the fdi hal file seems not to be loaded when I start X.

---

