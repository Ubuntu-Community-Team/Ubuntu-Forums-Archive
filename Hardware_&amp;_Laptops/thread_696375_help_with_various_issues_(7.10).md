---
title: "help with various issues? (7.10)"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by phendric on 2008-02-13
I have a Dell Inspiron E1405 (2 GB RAM, core 2 duo, GMA 945 integrated graphics, Dell wireless 1390 card) that I'm currently using to dual boot between Windows and Ubuntu.  Though I've played with Ubuntu in the past (I like neither the quality of Windows nor the business practices of Microsoft), I now have reason to have it on my computer as I'm taking a programming class where everything is done on Unix(/Linux).

I've got a couple of issues/annoyances that I'm hoping you experienced users will be able to help me out with:

[INDENT][LIST]
[*]When I run an application, I'm used to having the window manager remember how big the window was the last time I ran the application, and where on the screen it was.  Therefore, it's kind of annoying when I open up a terminal window, and it opens up in a different corner of the screen than I want and its default size (I like to make it bigger).  Is there any way to override this default behavior?
[*]As mentioned above, I have the Dell 1390 wireless card, using the default driver that Gutsy offered to install when I first installed the OS.  However, on my school's wireless network, which my Windows installation doesn't usually have difficulty connecting to, Ubuntu can't seem to ever connect.  What are the reasons that could be causing this?
[*]The mouse tap-to-click feature is very iffy...sometimes just a light tap will register a click, and sometimes I really have to tap hard and long to get a click.  It's so annoying that I've disabled the feature, but I'd be curious to know what could be causing the problem.  It's a Synaptics touchpad, and I've installed the additional Synaptics application/driver, but nothing seems to help.  Comments?
[*]I don't like the default Firefox fonts.  What are some favorite alternative fonts out there?
[/LIST][/INDENT]

Thanks.

---

### Post by TerpInHotLanta on 2008-02-14
On your wireless question,

A) Does your school's network use an open or hidden network (ie did you have to enter in the network name info or does it find it automatically)?
B) If you use gnome, do you have your network management applet set to roaming mode or do you manually tell it which network to connect to?

I find using roaming mode works the best: it always aims to connect to networks to which you have previously connected. Also, it may take up to 2 minutes for your computer to find the wireless network-- especially hidden networks.

I have found that the manual-entry mode (not roaming mode) works really poorly on gnome, and sometimes kills my wireless connectivity; thus, it's worth your while to always stay roaming mode (which also lets you enter in network names manually-- I don't get it either).

---

