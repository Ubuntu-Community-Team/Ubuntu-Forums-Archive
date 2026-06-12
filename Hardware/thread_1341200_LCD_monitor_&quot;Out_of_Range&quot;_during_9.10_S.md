---
title: "LCD monitor &quot;Out of Range&quot; during 9.10 Splash Screen"
date: 2009-11-29
forum: Hardware
---

### Post by Viperman0986 on 2009-11-29
Hello,

     I'm a pretty new user to ubuntu and have successfully installed version 9.10 on my laptop.  When I installed the same version for my parents on their desktop, I ran into the problem where the LCD was not detected at all.  I then saw a forum that said to try and hook up an old crt monitor and when i did that the LCD worked.:D

     The problem is that when the splash screen is supposed to be shown, the "out of range" message pops up.  The thing that confuses me is the fact that the bios is displayed, grub is displayed, and the ubuntu screen with the loading line is shown after 15 secs and it does show the ubuntu desktop.

     The reason i need this problem solved is because its on my parents computer and if they dont see something loading for 15 secs, they might think the PC is broke.:o

     To clarify here is the boot sequence i see
1. bios
2. grub
3. out of range message(this is supposed to be the white ubuntu logo screen)
4. Ubuntu orange splash screen with the loading line 
5. desktop loads and is usable

-I also just noticed that when I shut down the PC I dont see the "ttyl" goodbye message

Thanks in advance for any help and this is my first post so if its too long please let me know and ill edit it.;)

---

### Post by darkmakozu on 2009-11-29
I too am experiencing the same issue with Karmic. I had out of range issues in the past with previous versions of Ubuntu which I had solved by editing /etc/X11/xorg.conf. But it seems that whatever controls the boot is not affected by that file (which still has my modified options since subsequent upgrades).

Usually this isn't a problem for me, but when FCSK is checking my drive I cannot see what is going on.

---

### Post by Viperman0986 on 2009-11-29
darkmakozu,

  Thanks for reminding me about the disk check that occurs during that screen as well. It would be nice to know when that is running.  I also was thinking about editing the xorg.conf files but from what i googled, it was for an older version of ubuntu; 7.10 i believe.  So i havent touched that file yet.

---

### Post by Viperman0986 on 2009-12-01
bump

---

### Post by pricetech on 2009-12-01
I had a similar problem with Hardy.  I installed StartUp-Manager (for an entirely different reason) and found that it lets me set, among other things, the resolution and color depth.  Solved my problem by setting mine for 1024x768 24bit color.

Hope that helps you as well.

PS I installed via Synaptic.  I understand there is a new way under Karmic.

---

### Post by Viperman0986 on 2009-12-01
Pricetech,
 
Thanks for your input!  I tried various resolutions and color depths in startup manager, including the one you mentioned, but still have the same out of range problem.  However, a difference I noticed was that some of the resolutions would force this message after grub:

"Undefined Video Mode Number: 312"
"Press<ENTER> to see video modes Available or Press <SPACE> to Continue"

-When I press <ENTER> this chart is displayed:

"Mode     :      Resolution     :     Type"
  0 F00               80x25             VGA
  1 F01               80x50                             VGA
  2 F02               80x43                             VGA
  3 F03               80x28                             VGA
  4 F05               80x30                             VGA
  5 F06               80x34                             VGA
  6 F07               80x60             VGA
  7 301             640x480x8                VESA
  8 303             800x600x8                 VESA
  9 311              640x480x16             VESA

-Then the next line says:
"Enter a video mode or "scan" to scan for additional modes"

-When I enter "scan" the same modes appear.

-On a side note, I do have the LCD monitor hooked up via VGA cable and I am using on-board display adapters, No graphics card.

Thanks again!

---

### Post by pricetech on 2009-12-03
It may work differently under Karmic.  I was hoping the solution I used under Hardy would help.  Beyond that, I don't know.

---

### Post by Viperman0986 on 2009-12-03
Ah, Ok. Well thank you for trying.  I might downgrade the computer to 8.04 if the users dont get comfortable with not having the splash screen displayed.

---

### Post by Viperman0986 on 2009-12-03
I actually stumbled upon this article that explains the Ubuntu release cycle.  

[http://www.tech-no-media.com/2009/11/is-ubuntu-broken.html](http://www.tech-no-media.com/2009/11/is-ubuntu-broken.html)

I recommend reading this for any new Ubuntu user.  It does a good job explaining that there are Long-Term Support releases every 2 years and interim releases every 6 months and it goes into further detail explaining the pro, cons of each.

Since I am trying to use 9.10 on older hardware, 8.04 might actually be the better solution until the next LTS release.

---

