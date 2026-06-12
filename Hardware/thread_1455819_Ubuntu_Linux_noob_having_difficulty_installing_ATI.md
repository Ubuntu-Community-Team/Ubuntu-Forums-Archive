---
title: "Ubuntu Linux noob having difficulty installing ATI drivers"
date: 2010-04-16
forum: Hardware
---

### Post by sumigo on 2010-04-16
Hello,

I have never been a software wiz but I have always been proficient at getting a system running or fixed (windows pc's of course) and turning them back over to the people who own them to mess up again.

Recently I put together a Frankenstein system out of old parts to use as a HTPC, installed ubuntu and liked it enough to try a dual boot on my main system, so far so good for the most part, its been working.

However I noticed that the graphics are fuzzy and not what I feel they should be.

I am running an AMD X2 5200+ with a gigabyte mobo, 4 gigs of a-data vitesta, and just installed a new gigabyte 5830 (liked the price versus performance ratio of this card).

Ok so I went to download the current ATI drivers (not the new 10.1 driver) and when i go to install the driver in the terminal it says I need to be a [COLOR="Lime"]SUPER USER[/COLOR].  

I perused these forums and discovered that I need to go into the terminal and run "sudo -i" to get [COLOR="lime"]SUPER USER[/COLOR] privelages which I did, but then when I run the install it opens its own terminal, does not recognize my new [COLOR="lime"]SUPER USER[/COLOR] status and says the same error.

I came back to the forums and read some more, confused and frustrated, then I read about envy, I downladed the package for envy hoping this would solve my issue, the envy program found the recommended driver and downloaded it and installed it, then asked to reboot, I obliged, however now it will only boot in "low graphic mode" and even running in Ubuntu "recovery mode"  and running repair will not fix it.  Also now when I go into envy the program crashes and wants to file a bug report, which is totally flabergasting.

I want this to work very much, but if I cannot even install a simple driver even while doing as instructed then I am at a loss.  I really am tired of Microscrew but this scenario is frustrating.

Can someone please give me some dumbed down noob instructions on how to help me please?  

Is envy the way to go or through the terminal?

If through the terminal how do I get it to recognize the install and allow me to keep my super user status?  And as a follow up is "sudo -i" correct in getting SUPER USER privelages?  Is there another command I should be using once I do that?

I am trying to be patient but have been suffering through this for a few days now trying to solve it on my own,and would like a resolution.

Thank you in advance for your time.

EDIT: Forgot to mention I am using Ubuntu 9.10 Karmic Koala

---

### Post by sumigo on 2010-04-16
Can anyone help with this?

---

### Post by ultiva on 2010-04-16
If you want to install this driver from ATI installer - run terminal and type: sudo [path_to_downloaded_ati_driver] - it will run installer in super user mode.

Super user interactive mode (sudo -i) is restricted to terminal in which you run sudo command. If it's active you have prompt with "#" sign. You can type this command and from the same terminal type: sh [path_to_downloaded_ati_driver] - it will also run installed in SU mode.

I recommend installing Ubuntu 10.04 beta 2, my ATI 5650 works OK with ati drivers provided by this system. I think that ati driver provided with 9.10 does not support 5xxx series properly.

---

### Post by sumigo on 2010-04-16
Thank you for the reply, I am installing Lucid as I type this, its taking a while so I thought I would take a moment to thank you.

---

### Post by sumigo on 2010-04-16
Lucid Lynx solved the issue, graphics are much sharper and cleaner, still cant enable Normal or Extra effects on appearances, but at least everything inst fuzzy.

---

### Post by ultiva on 2010-04-17
Have you installed ATI driver under Lucid ? You must install it in order to have desktop effects. System -> Administration -> Device drivers (or sth similar).

---

### Post by arrimapirate on 2010-04-17
I have had problems with ATI drivers on my system as well. I started with 9.10 and the Hardware Drivers program found my x1250 card and installed the drivers. However i was not able to play any game that uses opengl and have tearing in my videos just like sumigo, yet all desktop effects work. Now i run 10.04 beta2 and Hardware Drivers can not find my card but effects still work and opengl still doesnt. 

Also sumigo i recommend getting compiz so you can better pick what settings are enabled.

---

### Post by Mark Phelps on 2010-04-19
> **arrimapirate said:**
> ... my x1250 card ...

That is an old ATI card and ATI dropped Linux driver support for that card over a year ago.  You are using the default open-source video drivers -- and that's all there is for that card.

---

### Post by arrimapirate on 2010-04-19
Yeah its on my 2005 laptop. I knew they dropped support, i was hoping for a solution to the tearing and opengl without rolling back to an older Ubuntu version.

---

