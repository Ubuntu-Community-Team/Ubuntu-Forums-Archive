---
title: "ThinkPad T30: Help Please!"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by jeremyk on 2006-06-08
Hello,

I installed final dapper on a thinkpad T30. The video card is ati radeon 7500. 

1) If I use vesa driver for the card, every seems to be working. But then I cannot get 3D acceleration.

2) However, if I use radeon driver, I can get 3D acceleration, but then there are several problems. The resolution cannot be changed (despite I put several resolution in xorg.conf), the refresh rate is interpreted to be -25873 Hz(!!!). There are on menu buttons, smalll black dots. Moreover I cannot play any DVD. 

Please, any help to make things work with 3D acceleration would be greatly appreciated!!!!

3) A question, just has apparently no relation with the previous ones: Totem cannot read audio disc. The 'Play audio disc' option is not valid and when I dod open->audio disc, I get the following: 'cdda:///dev/hdc' not a valid URL.

Thanks for helping.
Jeremy.

---

### Post by jeremyk on 2006-06-09
Anyone, please?

---

### Post by siriusnova on 2006-06-09
[QUOTE=jeremyk]Hello,

I installed final dapper on a thinkpad T30. The video card is ati radeon 7500. 

1) If I use vesa driver for the card, every seems to be working. But then I cannot get 3D acceleration.

2) However, if I use radeon driver, I can get 3D acceleration, but then there are several problems. The resolution cannot be changed (despite I put several resolution in xorg.conf), the refresh rate is interpreted to be -25873 Hz(!!!). There are on menu buttons, smalll black dots. Moreover I cannot play any DVD. 

Please, any help to make things work with 3D acceleration would be greatly appreciated!!!!

3) A question, just has apparently no relation with the previous ones: Totem cannot read audio disc. The 'Play audio disc' option is not valid and when I dod open->audio disc, I get the following: 'cdda:///dev/hdc' not a valid URL.

Thanks for helping.
Jeremy.[/QUOTE]


I have a Thinkpad T30 also, 

3D acceleration ONLY works in 16bit mode with the "radeon" driver so your going to have to go down to the "Device" section and put "DefaultDepth 16" or something like that in that area to get 3D acceleration. As for the black dots, that is really really weird. Ive never experienced that problem before so I dont know how to help you.

the dvd thing is that you need to install the libdvdcss library to be able to watch dvds. 

as for your audio cd thing, ditch Totem its a piece of junk, try something like mplayer for video and Rhythmbox for music..

---

### Post by jeremyk on 2006-06-10
Hello,

Thanks for your answer, but for me 3D accelaration runs for both 16 and 24 color depth. 

However, i have still my problems: 1) I cannot change resolution 2) I have sometimes black dots on the menu. 

I post it my xorg.conf. I f you see some thing interesting, please let me know. Can you also post your xorg.conf? BTW, does hibernate run for you? 

I cannot play dvd only with the driver radeon (with vesa) it works pretty well. Of course, I have installed libdvdcss2. With the radeon driver, when I try to play a dvd, the player (totem or gxine) screen becomes blue and nor image neither sound is available. 

Have you any idea to solve these problems? Thanks,
Jeremy.

---

### Post by ret3 on 2006-06-11
I'm running Dapper on my T30 as well, and am also experiencing the "dots" probleml. I notice it occurs on non-default-selection buttons in dialog boxes. 

I have other problems as well; if anyone has suggestions, I'd appreciate it:

-My Orinoco PCMCIA wireless network adapter works fine, except that I have to "Activate" it every time I boot up.

-My computer freezes without warning. Suddenly, the mouse will cease to respond to inputs. Upon rebooting, everything is fine again until another freeze.

-My sound card is not bring recognized; it worked fine under Breezy, but seems to have vanished during the upgrade.

---

### Post by woodsworth on 2006-06-11
I'm having the freezing issue too. Seems to be a Gnome thing as it also happened when I was running a Gnome session in Kubuntu Dapper (upgraded from Breezy CD install via command line) but never in KDE. Now I'm running Ubuntu Dapper from a CD install and I'm also getting the freezing issue in Gnome but not KDE. There are other problems such as GDM failing to start in what seems to be one out of three reboots.

I'm thinking of going to Kubuntu Dapper from CD but want to be assured of a suspend-hibernate function; with Breezy, suspend and  could be activated via the Fn keys (F4 & F12), but under Dapper (upgraded from Breezy) the keys give no response and there is no option to suspend or hibernate in the logout dialog, as in Ubuntu Dapper (Gnome).

Has anyone got suspend-hibernate to work in Dapper KDE, and if so, how were you able?

---

### Post by jeremyk on 2006-06-11
1) The dot problem turned out to be related to the human theme. Change theme and it will disappear!!! At least, this is what happened for me.

2) I have still a problem with resolution. However my situation got better. I will attach my new xorg.conf, if someone needs it. At least, I can say that with this xorg.conf my computer does not seem to  freeeze at all.

---

### Post by ret3 on 2006-06-11
[QUOTE=jeremyk]1) The dot problem turned out to be related to the human theme. Change theme and it will disappear!!! At least, this is what happened for me.[/QUOTE]

I tried this not long after my previous post, and you're right: pretty much any other theme is black-dot-free. And Grand Canyon is much slicker anyhow.

---

### Post by Cysign on 2006-11-05
I've got the resolution-problem, too.
on my extern monitor the resolution works on 1024*768. but i want it to work with 1280*1024.

another problem is: when i put my extern DVB-T (Terratec Cinnergy T2 card into the usb-plug, my linux freezes after some time. nothing works, but when I reject the cable, everythink works fine.
perhaps it has to do with the PCMCIA-card that provides me USB2 (my ThinkPad T30 only has USB1 :-/ )

btw: I'm a linux n00b...perhaps somebody could write me a little step-by-step instruction how to get the resolution higher oder how to fix the problem with the Cinnergy T2.
thanks!
.............................
edit: my refreshrate is: -25862 Hz

---

### Post by Cysign on 2006-11-05
gtf 1280 1024 85 returns:
 # 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
  Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
----------------------------
that's why i changes my xorg.conf to:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
        Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

---

### Post by Cysign on 2006-11-05
oh, i've got a radeon 7500mobile in my T30...but it detects a 9000?
how may i change it?

---

