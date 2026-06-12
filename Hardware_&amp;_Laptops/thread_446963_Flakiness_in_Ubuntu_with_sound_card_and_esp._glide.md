---
title: "Flakiness in Ubuntu with sound card and esp. glidepoint touchpad"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by khw on 2007-05-17
I just installed Feisty Fawn, and am getting seemingly random behaviors that are making it unusable at times.  

First, sometimes when it boots it recognizes the sound card (Creative Labs Sound Blaster Live! Value) and sometimes it doesn't, so sounds come out of the PC speaker.

More importantly, often the behavior of my USB Cirque glidepoint touchpad is flaky.  On some boots, iit works fine.  When misbehaving, the pointer seemingly moves properly as I run my finger on it, but help bubble boxes remain up as if the pointer hadn't moved.  Often, the left button won't work.  Clicking the right button usually seems to work, but will often bring up the context menu for where the pointer was when the left button was clicked.  Sometimes, the left button will work sort of for buttons in the current window, but I won't be able to select another window.  Sometimes both buttons don't work, but some combination of keyboard buttons will get things in a state that I can get to a terminal window and reboot.  Sometimes rebooting will solve the problem; sometimes not.  Today I rebooted maybe a dozen times without success, before I gave up, and booted into Windows so I could make this post.

I had been using Mandriva, whose driver for the mouse worked much better than this, but had other problems.

When no one answered this post, I decided to file a bug report, and found a similar one, in which the solution worked for me giving me instantly a working mouse.   [Bug 106619]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106619") . Unfortunately on next boot, the improper behavior was back.

---

