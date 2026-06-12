---
title: "Guest Login causes Intrepid Crash - powerdown required"
date: 2008-10-31
forum: General Help
---

### Post by employeeno5 on 2008-10-31
I'm not seeing anyone else with this issue searching around, so maybe it's just a quirk of my rig...

Anyhow, I had a very successful upgrade to 8.10. The only issue I've found is that if I attempt to try out the new "Guest" option everything goes black and I get a crash that only a forced power down seems to get me out of. 

I have no idea how I might start trouble shooting this issue never mind solving it. 

If anyone has any ideas or similar experiences let me know.

All that said, everything else is working great and I don't necessarily need a guest login. I'd love to know what's up though and see if I can't get it going.

Many thanks!

---

### Post by dulbirakan on 2008-10-31
I am also having this same problem...

---

### Post by dulbirakan on 2008-11-01
I think adding some details wont hurt anyone.

Immediately after I press the guest account button my screen goes black and I see some graphical artifacts. My screen is filled with 4-8 color boxes 10x10 pixels wide clustered around the center of the screen for less than a second.

Then I see the background with red lines running over it vertically then the wall paper and half of the gnome panels appear. My mouse cursor appears in wait mode and stays so. I am seeing some slight graphic distortions, those vertical red lines are partially revealed by the wallpaper, appears to be passing through it. I can move the mouse for a while but then even that freezes along with the icon animation.

After here the only option is to push the reset buton on the case. No CTRL+ALT+Backspace, no CTRL+ALT+F1, no nothing works here...

I am using ATI proprietary graphics drivers with my ATI4850, My Processor is an Athlon 64 X2 5600+. I have 4 gigs memory and am running the 32bit verson of UBUNTU 8.10.

---

### Post by employeeno5 on 2008-11-01
Aha, you see I have none of those details.

Mine just goes black and that's it, and no set of key escapes will illicit any response from the computer. Just a black screen, instantly and permanently.


I'm using 32bit also, and I upgraded from a Dell factory installation of Ubuntu 8.04 for their N530 Desktop (great computer by the way). I'm using 3GB RAM and an ATI card with the FGLRX proprietary driver.

However, my system came with Intel integrated graphics that do not require proprietary drivers. When I switch back over to the Intel graphics, this problem persists so I do not think it's related to the Video drivers.

Switching video cards was as far as I've figured out how to trouble shoot this one. 

However, I am experiencing significantly poorer video performance in general, so much so that I'm actually considering doing a clean reinstall of Hardy, so perhaps this does come back to video issues. 

That's what I've got for now. I'll write back if I can figure anything else out.

---

### Post by Marat89 on 2008-11-02
Hi I have this Problem too using Dell Inspiron 530n ATI Radeon HD 2400 PRO-
I found out that the Guest account startet in the LowGraphics Mode when the xorg.conf was configured wrong.
Anyone a idea?

---

### Post by dulbirakan on 2008-11-02
I am not so sure about this being a non graphics issue, I know you have a seperate graphics card o/b but, you also have flgrx drivers installed dont you? I tried it with my laptop and it worked like a charm... Tommorow I will try a few other computers with nvidia and intel graphics cards, we'll see how they will fare.

And I do not know anything about misconfiguration...

---

### Post by employeeno5 on 2008-11-02
Right. In fact, as I received the email alert to your reply, I was about to start purging my fglrx driver to see if I could get "guest" to work then. Also, I thought that perhaps, regardless of this issue, that full reinstallation of the driver later might improve my ATI video performance a bit, which has had a severe drop in performance upon upgradding to Ibex. Not only is compiz slow and choppy now, but even games like OpenArena are not rendering well and flash video is choppier. 

If those don't improve, I'm most likely going to first try a clean installation of Ibex, which I would not expect improvement from, but I'm figuring it couldn't hurt as if it doesn't produce results what I'm going to end up doing is a clean install back to Hardy anyways.  

I will let you know if ditching fglrx clears up the guest issue though, regardless.

Thanks again for the feed back and good luck.

---

### Post by Marat89 on 2008-11-02
I found out that its really a fglrx bug in my case.
When I click on Guest Account in LOW graphics mode, eyerything works like a charm.

---

