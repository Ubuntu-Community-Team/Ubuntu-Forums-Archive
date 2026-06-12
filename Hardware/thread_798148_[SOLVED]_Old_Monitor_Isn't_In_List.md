---
title: "[SOLVED] Old Monitor Isn't In List"
date: 2008-05-17
forum: Hardware
---

### Post by timkoop on 2008-05-17
I just took possession of a really old, really heavy IBM PowerDisplay 20 monitor, but I'm having a lot of trouble getting it configured.  In the graphics settings window, I would like to pick it from the list, but it is not in there.  But I do know the specs: [http://www.monitorworld.com/Monitors/ibm/powerdisplay20.html](http://www.monitorworld.com/Monitors/ibm/powerdisplay20.html)

So I now know the frequencies, but how do I tell Hardy what they should be?  Dare I say that things used to be easier when you had to enter the refresh rates manually?

Thanks a lot.

--
Tim

---

### Post by bmac on 2008-05-17
Have you tried selecting the one of the generic monitor settings? I had an old monitor that worked extremely well on the generic 1024x768 with a refresh rate of 60hz... :idea:

Hope this helps..... [IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by timkoop on 2008-05-18
> **bmac said:**
> Have you tried selecting the one of the generic monitor settings? I had an old monitor that worked extremely well on the generic 1024x768 with a refresh rate of 60hz... :idea:

Yes I have.  In fact, I've tried almost every combination we can think of.  It's convenient that the horizontal and vertical frequencies are displayed there when you select one, but nothing is even close to this particular monitor.  It only has one vertical frequency, not a range. (see the url above for the specs)

I think if I could just enter the frequencies manually it would work, but I don't know how.

--
Tim

---

### Post by timkoop on 2008-05-19
> **bmac said:**
> Have you tried selecting the one of the generic monitor settings? I had an old monitor that worked extremely well on the generic 1024x768 with a refresh rate of 60hz... :idea:

Thanks bmac.  As I said before, yes I have tried this and it didn't work.  However, I just tried something else and it seems to work fine now.  I'll post here what I did.

I picked a generic monitor, the 1024x768 one, and that seemed to work until the next reboot at which time the screen seems bigger than the monitor can handle.  I made the following change:

Using displayconfig-gtk, I picked a generic crt monitor of size 1024x768.  I've done that before, but now in the xorg.conf file, in the "Screen" section, under the "Display" subsection, I had to set the Virtual to "1024 768".  It was set to something bigger, so not everything was showing on the screen at one time.  Now that Virtual is the same size as everything else, it seems to work fine.  It now survives even a full reboot.

---

### Post by bmac on 2008-05-19
I'm really glad to hear you found the solution. My old monitor didn't require that I manually change the xorg.conf.
However, my new monitor/video card did require a change in the display resolution for the login screen. Listed under Section "Screen"/Virtual. Nvida video card of course...
Have read quite a few posts that refer to that same problem. Hope you enjoying the Ubuntu experience as much as I am...:popcorn:

---

