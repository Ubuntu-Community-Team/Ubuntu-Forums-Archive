---
title: "Acer Aspire 5002 WLMI Touchpad Problems"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Protazoid on 2006-06-12
Hello Everyone,

Recently my sluggish windoze operating system made me decide to try out linux again (I have had tried several times in the past, but found it confusing), and so I downloaded and installed Dapper Drake 6.06 LTS AMD64.

My initial impressions were very good, apt-get makes installing and managing packages very simple (the complexity of software install is what previously turned me off from linux), however the screen resolution was not displayed correctly, as my laptop (Acer Aspire 5002 WLMI) has a 15.4WXGA LCD screen (it showed a streched 1024x768 image).

So I did a quick google (once I finally got my wireless working with ndiswrapper :D ) and found a couple forum posts of adding "1280x800" to the monitor section of xorg.conf in /etx/X11.  Upon doing this I rebooted my system and was pleased to see that I now had the correct resolution, or so I thought!
thought!

It still was not quite right, the screen would flicker, and there were 'jaggies' around curved and fonts looked different depending on where they were located on the screen.  So after a quick look on the laptop wiki hosted on the Ubuntu home page, I found that I could resolve this problem by running the xorg configuration in a terminal.  Upon reboot everything was looking great!!!

However, this killed my touchpad settings.  The initial install had set it up perfectly.  But now if I double tap the pad to register a double click it acts strangely.  For example if I double click while browsing the internet in firefox and then move the cursor, it highlites text following it (the cursor).  Or if I click a launcher on my start menu, the application will load up, but when I move the cursor the launcher buttom moves with it.  This makes me think that double tapping on the touchpad now has some sort of left click lock (if that makes sense).

So I would really appreciate any advice you linux guru's could give me, and if this is a fairly simple problem to resolve please just link me to the appropiate documentation and sorry for bothering you :D.  Or is there some way to reload the default dapper touchpad settings without screwing around with my other xorg settings?

Cheers,

Protazoid

---

### Post by Protazoid on 2006-06-12
Figured out the problem on my own, all I had to do was install the latest synaptic driver.  Things look great!!!

Cudos to the development team for making such an amazing, free desktop.

---

