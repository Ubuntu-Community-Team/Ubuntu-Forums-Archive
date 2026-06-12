---
title: "dual display problems in 7.10"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by eurostyle360 on 2007-10-18
i just installed ubuntu 7.10 and so far it's great

the only problem i have is with dual displays.  i have two 17" plug and play monitors but i can't seem to get them set up properly.  in the "Screens and Graphics" app i configure one monitor with its proper model (it didnt auto detect for whatever reason) and the second monitor isn't even listen (it is in *very* no-name territory), so i just configure that one as generic with its proper resolution and refresh rate.  The thing is that with this setup both monitors display with their proper settings, but one seems to show a "zoomed-in" view of the desktop, and the desktop scrolls around the display whenever i move my mouse to the edge.  This is obviously a driver problem (i think) and i wanted to know if there was a way to fix this.  (I'm using nvidia-glx-new btw..)

One more thing happens with this setup:  it won't let me enable desktop effects (something I'm disappointed about, but i know can be solved along with the problem mentioned above, because i was able to use desktop effects before the dual display)

any help?:confused: sorry for the extremely long post, but i wanted to get as much detail in so i don't have ppl saying "provide so-and-so info, you idiot!:))

---

### Post by Alfdog on 2007-10-18
same problem, bump

---

### Post by puleen on 2007-10-18
Same problem.....

---

### Post by buntunub on 2007-10-18
:popcorn:

Im just enjoying the show. Dont mind me :)

This is a thoroughly reported bug from the Alpha days through to the Beta and RC days. The Devs apparently dont feel that bugs like these are important, or so I was told on #ubuntu+1 by one.

---

### Post by puleen on 2007-10-18
Same problem.....

---

### Post by eurostyle360 on 2007-10-19
:( that sucks.. is there nothing that can be done about this issue?

I got the scrolling to stop by setting them both to generic lcd's (albeit sacrificing a higher refresh rate for them), however the effects still wont work with both monitors enabled.  It works perfectly fine with only one monitor.  There must be a way!  You can see videos all over youtube with dual monitors running fusion.

This may sound like a stupid idea, but would trying to enable with something else work?  Either through terminal, or some other daemon for it?

---

### Post by cayhorstmann on 2007-10-19
Same problem. I have seen that stupid Screens and Graphics tools so often that I want to scream every time it comes up again. 

I had more luck editing xorg.conf by hand in Feisty than I had with this utility in Gutsy. 

It is critically important for me to be able to run a laptop with an external projector, and no amount of fussing has worked for me. 

What does it take to make this priority #1?

---

### Post by Lil on 2007-10-19
The easiest way would be to use the open source 'nv' driver and use xrandr 1.2 on the command line (see this thread [http://ubuntuforums.org/showthread.php?p=3572795](http://ubuntuforums.org/showthread.php?p=3572795)) which does work well.

Not ideal but the Screens & Graphics prefs pane is something of... a thorn in my side too. I will eventually set up my GX240 which has a FX5200 with Gutsy but whilst it's A OK on Feisty I've left it has it is.

Vicky

---

### Post by eurostyle360 on 2007-10-20
Would i still be able to use fusion with the open source nv driver?  I thought that there was no hardware acceleration when you used the nv driver:confused:
And what is xrandr 1.2?

---

### Post by TheodoreWard on 2007-10-20
> **cayhorstmann said:**
> Same problem. I have seen that stupid Screens and Graphics tools so often that I want to scream every time it comes up again. 

I had more luck editing xorg.conf by hand in Feisty than I had with this utility in Gutsy. 

It is critically important for me to be able to run a laptop with an external projector, and no amount of fussing has worked for me. 

What does it take to make this priority #1?

I teach and am also using a projector daily. With 7.04, I could use the FN+(external display) key and it would switch to external (only, not both screens at once) at 1280x1024 or whatever. But if I rebooted (or restarted X) while the projector was connected, I would get both monitors on at once HOWEVER max resolution of 800x600.

With 7.10, I have ONLY been able to get things to work by rebooting with the monitor attached, and then it ONLY works at 800x600 or 640x480.

<sigh>

---

### Post by Zamboniman on 2007-10-20
Yup, I too found out the hard way that this tool is useless.  Great idea, too bad it doesn't work.  At all.  They should have just left it out so that it wouldn't annoy and frustrate people.  

My laptop has an nvidia card and I'm using the restricted drivers so using nvidia-settings worked perfectly for setting up dual monitors.  Tweaking the xorg.conf file by hand should also work fine.  Of course, that belies the whole point of having a nice gui to do it, but whatever.

---

### Post by eurostyle360 on 2007-10-21
I suppose&#8230;
It wouldn't be so bad if maybe i had two well-known monitors instead of one well-known and another no-name brand.  What puzzles me is the fact that this should be an obstacle at all.  If windows can properly set up plug & play monitors, why can't Linux?  Are there *really* drivers for monitors?  I always thought of displays as things that receive signals, and display them with no strings attached.
One more complaint:  Whats the deal with refresh rates in Ubuntu, or Linux in general?  You'll set it to one thing, then go back only to find that its a weird number completely different to what it was previously set to, or what  the monitor actually reports it being.
Please, get it right!

---

### Post by d0rp on 2007-10-22
I had the same problem, but managed to get it to work. The new Screens tool only ever shows me one screen (and no option to add another!), even though I have 2 monitors. I wonder if since the monitors are the same model that it only thinks there is one.

Actually, when I first upgraded, it did work, but it put both monitors into one big screen, so the gnome bars, and maximized windows were spread across both screens, instead of two separate screens like I had in 7.04.

I was able to get a working xorg.conf using  nvidia-settings, however, for some reason installing that package requires removing the nvidia restricted driver! And then, when you restart X, it defaults to the nv driver and nvidia-settings won't let you do anything because you are not running an nvidia driver. So I  had to trick it.

What I did to fix it:

1 ) Install nvidia-settings (this removes the nvidia restricted driver -- nvidia-glx-new)
2 ) run nvidia-settings WITHOUT restarting X (since you're still running the drivers it works)
3 ) configure the screens
4 ) save xorg.conf to a DIFFERENT file (I used xorg.conf.shouldwork)
5 ) restart X (ctrl-alt-backspace or restart machine)
6 ) reinstall restricted drivers
7 ) overwrite xorg.conf file with saved copy
8 ) restart X
9 ) screens worked as intended

The only issue I have now, is that I can't enable the desktop effects (I had compiz-fusion working just fine in 7.04). I suspect that its because I am running with Xinerama. I'll have to try it with Twinview, but I think Twnview is what was causing my one giant screen problem.

---

### Post by outdooricon on 2007-10-22
> **d0rp said:**
> I had the same problem, but managed to get it to work. The new Screens tool only ever shows me one screen (and no option to add another!), even though I have 2 monitors. I wonder if since the monitors are the same model that it only thinks there is one.

Actually, when I first upgraded, it did work, but it put both monitors into one big screen, so the gnome bars, and maximized windows were spread across both screens, instead of two separate screens like I had in 7.04.

I was able to get a working xorg.conf using  nvidia-settings, however, for some reason installing that package requires removing the nvidia restricted driver! And then, when you restart X, it defaults to the nv driver and nvidia-settings won't let you do anything because you are not running an nvidia driver. So I  had to trick it.

What I did to fix it:

1 ) Install nvidia-settings (this removes the nvidia restricted driver -- nvidia-glx-new)
2 ) run nvidia-settings WITHOUT restarting X (since you're still running the drivers it works)
3 ) configure the screens
4 ) save xorg.conf to a DIFFERENT file (I used xorg.conf.shouldwork)
5 ) restart X (ctrl-alt-backspace or restart machine)
6 ) reinstall restricted drivers
7 ) overwrite xorg.conf file with saved copy
8 ) restart X
9 ) screens worked as intended

The only issue I have now, is that I can't enable the desktop effects (I had compiz-fusion working just fine in 7.04). I suspect that its because I am running with Xinerama. I'll have to try it with Twinview, but I think Twnview is what was causing my one giant screen problem.

I hate to be the one to say this, as I just discovered this about 25 mins ago, but nvidia-settings is there with the nvidia-glx-new, it's aprt of that package now (not a dependency but actually part of it) which chops off a few of the steps you listed... to run it, open terminal and type: sudo nvidia-settings

---

### Post by YoYoSan on 2007-10-22
Yep - similar problems here guys.

My gutsy upgrade from 7.04 has given me some problems that look as though they'll take a while to fix: 1024x768 max res. Reboots to the low res after editing the xorgconfig. When I get a higher res the Open Office presentation only fills 2/3 of the screen.

Hmmm:confused:

My experience from installing Feisty is that you won't get much response from posting about screen resolution from the expert audience here.

Google and fiddle - burning hours on this.

I'm reading reviews to see if there are any other linux distros that are more hardware friendly - no luck to date.

Might have to go back to 7.04 and see if I can remember what I did to sort the wireless and screen res on that!!

Cheers

---

### Post by Alfdog on 2007-10-22
I did a reinstall, and used Envy to install the driver, and then used the nvidia config tool that it also installs, SUPER EASY, ironically this is how I got my monitors working on kubuntu 7.04, and I forgot that I used it then.  Anyways I now have my dual 22" CRT's working with effects

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by d0rp on 2007-10-23
> **outdooricon said:**
> I hate to be the one to say this, as I just discovered this about 25 mins ago, but nvidia-settings is there with the nvidia-glx-new, it's aprt of that package now (not a dependency but actually part of it) which chops off a few of the steps you listed... to run it, open terminal and type: sudo nvidia-settings
That was the first thing I tried, and it didn't work. Command not found. So, I went into Synaptic and installed it manually, and then ran into the problems I mentioned above.

---

### Post by namru on 2007-10-23
I've got a similiar problem. 

HW:
Laptop with:
i915 and display -> 1280x800
external lcd monitor - Samsung 205BW  - 1680x1050

When I installed gutsy, the external monitor was successfully detected and everything seemed fine with resulution and all. the displays were configured into dual-head mode.

The problems started when I changed the external monitor to be an extension of the laptops display. The resolution of both displays were 800x600. and changing them to correct ones didn't really affect anything. Now I can't get the resolution back with dual-head mode nor single display.

Is it better to forget the "screen & resolution" application and fight with the xorg.conf instead?

---

### Post by buntunub on 2007-10-23
> **YoYoSan said:**
> 

My experience from installing Feisty is that you won't get much response from posting about screen resolution from the expert audience here.

Google and fiddle - burning hours on this.

I'm reading reviews to see if there are any other linux distros that are more hardware friendly - no luck to date.


Cheers

Thats hardly true. Its mostly that it gets rather boring and tiresome to answer the same question over and over and over because people are generally too lazy to use that magic "search" button built into the Forums, and actually read! For 98.9999% of any issue someone is posting about, the answers were already posted earlier by one of those "experts". 

As far as distro's that can handle new hardware, try Sabayon or Fedora 7. Both those, particularly Sabayon, are pretty notorious for being able to handle pretty much anything thrown at it. Fedora is way ahead of Ubuntu when it comes to functionality, but is VERY un-userfriendly. Their community I have found to be generally closed and snarky, if they even bother to answer forum posts at all. Probably because of the reason I listed above. Then there is Slackware/Gentoo. Those distro's should handle anything..at the cost of an exceptionally steep learning curve, which you will be expected to burden 100% yourself from the community. Documentation for those two are really good, and you will see no end of RTFM replies on their IRC if any questions are asked lol. :)

Seriously, Ubuntu is THE distro of distro's for linux nubs, and the Ubuntu codebase is probably the most comprehensive when it comes to functionality and ease of use. All other distro's have their own limitations, many or most of which make Ubuntu seem like a gentle summer breaze in comparison. Dont let this one bug throw you off.

---

### Post by yclian on 2007-10-24
Hi guys,

I am having the same issue as well. In the past few days been trying to solve the problem but there's still no solution to it 'til today.

- I'm able to enable TwinView. However, instead of giving me 2560x1024, it's giving 3000x1200. :-(

- I am not able to run nvidia-settings at all, It's always telling me "You do not appear to be using the NVIDIA X driver...". I have tried running nvidia-xconfig but that doesn't make any difference. I have also tried manually modifying my xorg.conf.. with so many different combinations. :-S

- Maximizing a screen, instead of making the window to expand fully on a screen, it goes two screens.

My output for `nvidia-settings --verbose=all`:

```

WARNING: NV-CONTROL extension not found on this Display.


WARNING: Unable to determine number of NVIDIA GPUs on ':1.0'.


WARNING: Unable to determine number of NVIDIA Frame Lock Devices on ':1.0'.


WARNING: Unable to determine number of NVIDIA VCSCs on ':1.0'.

```

Cheers,
yc

---

### Post by buntunub on 2007-10-24
> **yclian said:**
> Hi guys,

I am having the same issue as well. In the past few days been trying to solve the problem but there's still no solution to it 'til today.

- I'm able to enable TwinView. However, instead of giving me 2560x1024, it's giving 3000x1200. :-(

- I am not able to run nvidia-settings at all, It's always telling me "You do not appear to be using the NVIDIA X driver...". I have tried running nvidia-xconfig but that doesn't make any difference. I have also tried manually modifying my xorg.conf.. with so many different combinations. :-S

- Maximizing a screen, instead of making the window to expand fully on a screen, it goes two screens.

My output for `nvidia-settings --verbose=all`:

```

WARNING: NV-CONTROL extension not found on this Display.


WARNING: Unable to determine number of NVIDIA GPUs on ':1.0'.


WARNING: Unable to determine number of NVIDIA Frame Lock Devices on ':1.0'.


WARNING: Unable to determine number of NVIDIA VCSCs on ':1.0'.

```

Cheers,
yc

Lol. Hard to read those logs from Windows Notepad as im scanning through them here at work, but I did notice that you have Xinerama enabled. Disable it. Open a console and try nvidia-settings &. If you get some error message then either do what it tells you to do (ie. sudo apt-get install nvidia-settings, or whatever) or go to Synaptic and do it from there. If your using that craptastic Screens and Graphics utility (which I cant imagine works properly for anyone) then your in for a world of pain as I can attest.

PS. I have found that litterally ALL my graphics issues went bye bye after I disabled Xinerama. Use Twinview or dual x screens for Compiz and disable Xinerama, and you should notice a pretty large difference in performance.

---

### Post by d0rp on 2007-10-24
> **d0rp said:**
> That was the first thing I tried, and it didn't work. Command not found. So, I went into Synaptic and installed it manually, and then ran into the problems I mentioned above.
Just an update: I tried running nvidia-settings again last night with the drivers installed and it worked (not sure why it didn't work the first time). I was then able to set it use Twinview (instead of Xinerama) and it kept my screens correctly and now allows me to enable desktop effects as well.

---

### Post by buntunub on 2007-10-24
Congratz!

---

### Post by eurostyle360 on 2007-10-25
> **buntunub said:**
> 
PS. I have found that litterally ALL my graphics issues went bye bye after I disabled Xinerama. Use Twinview or dual x screens for Compiz and disable Xinerama, and you should notice a pretty large difference in performance.
I would love to have an increase in performance as well as the usage of fusion, but do i really have to give up use of xinerama?  I don't want to use twinview because i want to be able to maximize windows into only one screen and configure toolbars, etc. on a per-monitor basis.  And just to clarify, by dual x screens you mean to run two seperate instances of x for each desktop/monitor, right?

---

### Post by yclian on 2007-10-25
> **d0rp said:**
> Just an update: I tried running nvidia-settings again last night with the drivers installed and it worked (not sure why it didn't work the first time). I was then able to set it use Twinview (instead of Xinerama) and it kept my screens correctly and now allows me to enable desktop effects as well.
Do you mind to share us with your xorg.conf? Thanks.

---

### Post by nowhere.elysium on 2007-10-26
'Nice' to know that I'm not the only one with this problem.
I've got a dell inspiron 1501, and the hardware in it's great: it's got a radeon card in there, which runs just fine with fglrx, but it's vital that i can use a projector: I use ubuntu for VJing, and that bloody screens configuration thing is sodding up every attempt to get it working. I had to throw a gig on wednesday, because of it!
As such, I'm jumping back to 7.04 for now, and if that continues to give me grief over the wifi card, then sod it - I'll jump to debian.
This is the annoying thing: I started with Red Hat (version 7), carried on with them up to FC1, and then discovered how much better the .deb package management was! I now CANNOT go back, even though they're a bit better on hardware detection. I know that I'll go mental if I try. I don't even know what the FC7 equivalent of Synaptic is called...
Grr.

---

### Post by Cyber-J on 2007-10-26
Another distro that I recently tried that worked for me right out of the box is PCLinuxOS. Not a bad distro but the don't have a 64-bit version out yet. I prefer Ubuntu and if I could get dual display thing working, I'd be quite happy.

---

### Post by dougmorin on 2007-10-26
I had this problem in dapper and I solved it by finding a resolution that one monitor liked ( did not scroll ) and then set both of them to that resolution.

If you mess around enough with the default monitors setting you will eventually get it to how you like.

Remember if you do any configuring to your displays, backup your xorg.conf file so you can easily revert back to your original settings.

---

### Post by yclian on 2007-10-26
> **yclian said:**
> Do you mind to share us with your xorg.conf? Thanks.

Hi guys,

Like I have mentioned earlier, I have tried manually editing my xorg.conf. This time.. I got it working, basically.. if I'm not wrong:

1. I got rid of Xinerama
2. I disabled second device, monitor and screen
3. I got rid of the ServerLayout 

Attached is my xorg.conf. The only thing that bugs me now is maximizing a window takes up two screens.. which I believe I can get a solution pretty quick by googling.

So.. thanks for the response. I'm happy now. :-)

---

### Post by nowhere.elysium on 2007-10-26
Is there any way to disable this crappy feature? It's the only significant gripe I've *ever* had with Ubuntu...

---

### Post by TekNullOG on 2007-10-29
> **cayhorstmann said:**
> Same problem. I have seen that stupid Screens and Graphics tools so often that I want to scream every time it comes up again. 

I had more luck editing xorg.conf by hand in Feisty than I had with this utility in Gutsy. 



You're telling me! It took me 5 mins under feisty editing it manually but it's been 2 weeks and I can't get it to work in Gutsy.

Specs:

IBM T43
ATI Radeon X300
Laptop screen = 1400x1050
LG screen = 1680x1050

Of my 5 friends that run Ubuntu, not a single one has been able to run dual screens properly.

---

### Post by likemindead on 2007-10-29
Same problem here.

IBM R50p
ATI Mobility FireGL T2
1600x1200

When I hook up to my NEC data projector, the Screens & Graphics saw nothing. I restart X and get a projected image of 60% of my screen. The only way I could get it to work was to use the restricted driver (blech) and drop down to 640x480. Yikes! What a pain!

Very much looking forward to a fix for the, for now, useless GUI.

:(

---

### Post by TekNullOG on 2007-11-09
My personal solution is posted here :

[http://ubuntuforums.org/showthread.php?p=3734077#post3734077]("http://ubuntuforums.org/showthread.php?p=3734077#post3734077")

Hope it helps someone

---

