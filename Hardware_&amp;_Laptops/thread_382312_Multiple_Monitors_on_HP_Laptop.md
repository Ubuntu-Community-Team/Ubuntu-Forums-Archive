---
title: "Multiple Monitors on HP Laptop"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Snyper64 on 2007-03-11
I am running an HP zv5000z laptop, the main display on the laptop works fine, but I have a Viewsonic n2750w monitor/TV that is running through a VGA connection. My video card is a GeForce4 420 Go. When I was running windows XP(just switched to Ubuntu this morning:lolflag:) I used to have the extend my desktop on to this monitor checkbox clicked, and had my second monitor(my viewsonic) set to the left of me and did not have any icons or taskbar on it(completely blank except for my background image) so that I could use it for movie watching(both DVD and Bittorrent). I often take my laptop with me on trips or for use in my church so the monitor will not always be connected(hope this will not be a problem) to my laptop.

Is there any way to set my Viewsonic display up like I used to have it on Windows XP without it interfering with moving my laptop around? It doesn't matter if I need to go into a control panel to disconnect and reconnect the monitor everytime I want to move it since I had to do that with XP so that I wouldn't lose the monitor settings.

Thanks
Snyper64

---

### Post by Snyper64 on 2007-03-12
Anyone?

---

### Post by Snyper64 on 2007-03-13
Its been 2 days, a little help please!

---

### Post by Snyper64 on 2007-03-13
Its been 2 days, a little help please!

---

### Post by tgalati4 on 2007-03-13
Unfortunately, this is an area where Windows is better for a dual monitor setup.  It's not that it can't be done, it's just difficult to setup and keep working correctly.

Under Windows, it's almost automatic.  The Display settings are easy to change and you can rearrange monitors with ease.  You can mirror, expand desktop, unplug the external video without ill effect.

Under Linux, you have to configure the xserver to drive two monitors and these tend to work best with fixed (native) resolutions for your devices.  Moving from a projector (at church for instance) to a home display may require a resolution change and restarting the xserver.

If  you search the forums for xserver dual display, you will find several ways to set dual display.  I have it running reliably on a desktop using the built-in video and a pci video card to drive a second display.  I use it for music editing.  I have the master tracks on one display and mixdown tracks on another.  It works well, but it was a pain to get setup correctly.  I don't change the orientation or resolution so I don't have to deal with mobility issues.

In your case you might have to write a script:

When at church:  sudo cp xorg_church_projector.conf xorg.conf

When at home:  sudo cp xorg_home_dual_display xorg.conf

I'm not familiar with roaming profiles (using wireless networking for instance) so there may be a profile script where you could place these so they have automatically when you change profiles.

Because of the complexity of your situation, there have been no replies.

After some research, you may be able to ask some more specific questions that others can help with.

Welcome to the community and keep the faith.

Also, a single post with the work "bump" will raise awareness of your issue.  "Anyone?" and "Please help" are not recognized by the post server.

---

### Post by Snyper64 on 2007-03-13
Thanks, I have yet to hook my pc up to a projector. I just use my laptop for note taking and watching the occasional video while on the road. I'll have to look at how to set up profiles so that it will automatically set up my monitor when it is plugged in and go back to single display when it is disconnected.

---

