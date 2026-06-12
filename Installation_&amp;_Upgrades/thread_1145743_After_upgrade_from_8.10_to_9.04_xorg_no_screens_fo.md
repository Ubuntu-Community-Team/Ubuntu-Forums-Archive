---
title: "After upgrade from 8.10 to 9.04 xorg no screens found"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by jsedwards on 2009-05-01
I installed Ubuntu 8.10 on my Averatec 3225 laptop a few weeks ago and it ran great.  So when 9.04 came out I decided to do a clean install of it, and now X windows doesn't start:

(EE) CHROME(0): No valid modes found
(EE) Screens(s) found, but none have a usable configuration

Fatal server error:
no screens found

When I installed 8.10 I had to install the openchrome package, edit the xorg.conf file and then it worked fine.

When I installed 9.04 the xorg.conf file was empty, so I copied the xorg.conf file that I had from 8.10.

Is the xorg.conf file from 8.10 need to be changed for 9.04?

Thanks
  -Scott

---

### Post by tommcd on 2009-05-02
You could use the xorg.conf from 8.10 in 9.04 and it will likely work.
Are the open chrome drivers installed in your 9.04? They should have been installed by default. I have xserver-xorg-video-openchrome automatically installed on my laptop; and my laptop uses the intel driver. So the open chrome must have been installed as part of the standard installation.

---

### Post by jsedwards on 2009-05-02
Yes, in 9.04 the openchrome driver was installed by default.

I forgot to mention one thing that might be important: when I went to install 8.10 it would not boot up correctly from the regular Ubuntu 8.10 Desktop i386 CD so I installed it from the Ubuntu 8.10 Alternate i386 CD.

When I installed 9.04, I didn't want to waste time so I didn't try to install from the Ubuntu 9.04 Desktop i386 CD, I started with the Alternate CD.

---

### Post by jsedwards on 2009-05-02
In looking again at the Xorg.0.log, I notice there are some weird warnings that I didn't pay attention to before (I was just looking at the (EE) stuff).

When using the file from 8.10 (which may have been derived from the Ubuntu 6.10 xorg.conf file, I can't remember now) there were these warnings:

```
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Generic Keyboard
(WW) Disabling Configured Mouse
```

Since that xorg.conf file could be really old (the paths to the fonts were wrong) I decided to try another xorg.conf file from another machine.  It doesn't work either, but it also seems to complain about no mouse or keyboard:

```
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
```

With both xorg.conf files it repeats that no modes work over and over for various sizes, the correct size should be 1024x768, but they all fail:

```
(II) CHROME(0): ViaFirstCRTCModeValid
(II) CHROME(0): ViaPanelGetIndex
(II) CHROME(0): ViaPanelGetIndex: Mode not supported by Panel.
(II) CHROME(0): Not using default mode "1024x768" (unknown reason)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
```

---

### Post by jsedwards on 2009-05-03
I'm sorry, I gave up last night and reinstalled 8.10 on my laptop.  I had hoped I could contribute and solve the problem for those who had the same problem.  I spent at least 6 or 7 hours trying to solve it, with no luck, and I just couldn't afford any more time.  (Plus it cost me almost 3 hours to reinstall 8.10 and get it all configured again because I only did a partial backup before I installed 9.04.)

A few days ago there was a thread in this forum asking everyone to describe their 9.04 install or upgrade experience.  While I was fooling with 9.04 it seems to have disappeared.  So I thought I would just comment here.  This experience with 9.04 made me realize that upgrading some machines is just always going to be a crap shoot.

I originally had SuSE Linux on this laptop, it has been so many years since then I don't remember how well that worked.  IIRC the built-in wireless never worked, I had to plug in a wireless card.

I think I tried Kubuntu 5.10 on it.  But again it has been so many years, I can't remember how well that worked, if at all.

I had Kubuntu 6.06 on it for a while and it seems like that worked pretty well, except for the wireless.  Once in a while the wireless worked, but it was pretty rare.

I upgraded to Kubuntu 6.10 and it worked okay, the wireless rarely worked, and the sound stopped working.  I screwed around with the sound off and on, but never got it to work.  It wasn't essential so I just left it and used it without sound.

I tried to upgrade to Kubuntu 7.04 and the CD wouldn't even boot up... well it would but, and I am not making this up, it took over an hour to boot up.  I think something in Kubuntu 7.04 wanted more memory than this laptop has, because I installed Xubuntu 7.04 and it worked normally.  Xubuntu looked nice but I didn't have time to learn it at the time, so I reverted back to Kubuntu 6.10.

I can't remember if I ever had time to try 7.10.  I think I skipped over it and tried Kubuntu 8.04.  It installed okay, but the sound still didn't work.  I spent a couple of hours and finally discovered there was an obtuse mixer setting that was the problem.  I assume that may have been the problem in 6.10 too.  I never could get the networking to work (Ethernet or Wireless).  BTW - I thought the Network Settings GUI in that version made no sense at all.

I should explain that I have been using Linux since 1998 and I have a lot of experience with setting up the Ethernet.  I have used RedHat SuSE, Xandros, Gentoo, Debian, Arch, Zenwalk, Fedora, WhiteBox, CentOS and several others.  Over a period of weeks I fooled around trying to get the networking in 8.04 working.  I even had the IT guy at work, who also has a lot of Linux experience, look at it.  He couldn't get it to work either.

I tried Kubuntu 8.10 and I want to say that I applaud the KDE people for trying new things.  However, I found the new KDE 4.x cumbersome.  If I had time to spend learning it and tweaking it, perhaps I could get it to my liking, I don't know.

By this time I had gNewSense on another machine of mine.  Since it had Gnome as the default desktop, I found that most of things I previously didn't like about Gnome could be configured to my liking.  I don't like the tabs at the top of Gnome terminal but I have found a patch that will hopefully fix that.  There is some bad interaction between Emacs and Gnome Terminal that drives me insane, so I may switch to a different terminal altogether.

Meanwhile back at the laptop, I tried a couple of other distros on it without success.  Then I decided since Gnome seemed workable on one of my desktops, I would try Ubuntu 8.10.  As I mentioned in my original posting to this thread, there was a little fooling around to get Xorg working, but then everything else worked very well.  For the first time on this laptop, the wireless worked wonderfully.  I was in heaven!  After all these years the wireless just worked, I didn't have to do anything!!

I was so happy with Ubuntu 8.10 that when 9.04 came out I thought I just have to try it, I'll bet it is even better than 8.10.  Oh well, I am still really, really happy with 8.10.  If I can free up some time and a separate partition, I may try to experiment with 9.04 some more.  Of course, I'm so slow, 9.10 will probably be out by then :)

---

