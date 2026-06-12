---
title: "karmic DOES NOT &quot;just work&quot; on my Thinkpad X61-tablet"
date: 2010-02-09
forum: Hardware
---

### Post by SaintDanBert on 2010-02-09
I recently installed Ubuntu Karmic (v9.10) to my Thinkpad X61-tablet. Several basic features do not work out of the box even though so many postings say "... just works ...". I've tried posting questions but without answers. I'll worry about [highlight] tablet-pc [/highlight] specific operations once I have the basic features working.

Can someone, here, help me with these issues?
[list=1]
[*] any HIBERNATE fails to wake up
[*] any SLEEP fails to wake up
[*] cannot undock/redock the entire Ultrabase(tm) docking station
[*] cannot undock/redock DVD or HDD "cartridge drive" installed to the docking station.
[*] all sorts of keys and buttons don't accomplish what they did under Hardy (v8.04.3 LTS).
[*] cannot use laptop features for display, keyboard, pointers, and buttons.
[/list]

I have no troubles editing config files and such, but I cannot find these details anywhere. I'm not interested in hacks and clunky ways to work around issues. Here are some examples:
[indent]
Where is configuration that tells the Gnome Panel which program to launch when SLEEP gets requested?

Where is configuration that tells the Gnome Panel which program to launch when HIBERNATE gets requested?

Where is configuration that responds to requests to undock the Ultrabase or the DVD or HDD installed there?

Where is configuration that lets me inform my consoles, X11 and xterms about my keys and buttons?

Where is configuration that lets me inform X11 about the aspects of my hardware that is not discovered during the automagic processing?
[/indent]

I understand that Karmic introduced a lot of new things and that we are not far away from the Lucid Lynx (v10.04) release where troubles with these new things may likely settle down. However, I need to use my laptop's now not three months away.

Cheers,
~~~ 0;-Dan

---

### Post by mörgæs on 2010-02-10
Perhaps 10.04 is simply the solution, as you suggest. Though it is only an alpha, you could give it a try (I have done, and it works great on my machine). 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by SaintDanBert on 2010-02-10
When either suspend happens, I get a blinking "new moon" LED. Under Hardy, the LED was on solid after the nap starts. Also, HIBERNATE never turns off the power like it did under Hardy. These facts tell me that the programs involved are not doing the correct things.

Can you tell me which programs actually accomplish the suspend operations? (Given the programs, I can discover their config needs and details -- disk files, folders, dependencies, etc)

Can you tell me which programs actually accomplish the **wake-from-suspend** operations? (Given the programs, I can discover their config needs and details -- disk files, folders, dependencies, etc)

I suspect that there is a major pot-hole in my Karmic install and would like to just do-over. I fear that I will simply make the same mistake(s) the second time and the various **suspend-to-ram** and **suspend-to-disk** options still will not work. I also worry that I will lose what I've done that I want to keep because any effort to backup ==> do-over ==> restore will then put bad stuff over good stuff.

Cheers,
~~~ 0;-Dan

---

### Post by mörgæs on 2010-02-10
Sorry, I don't know the answers. 

Being in your shoes I would try to find the best of the supported Ubuntu versions (maybe 8.04) on this particular machine before digging deeper, but this is of course only an opinion.

---

