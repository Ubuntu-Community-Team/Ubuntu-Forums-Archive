---
title: "how do I change video cards without having to reinstall"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by klick.here on 2008-04-15
I'm running gutsy and my old video card (nvidia mx400) is about burned out I think.  It works with compiz and everything but as soon as I start a game like Nexuiz or Tremulous even very simple games like tux racer it locks up for a few seconds then runs for a few seconds back and forth making the game unplayable.  So I was just going to use the integrated video since it is probably as good on this motherboard as the old 64 MB card.  I just found out it is not so simple as switching the monitor cable and rebooting.  X config has to be changed or something.

---

### Post by tommcd on 2008-04-15
Just remove the nvidia card, then restart the PC. If you need to change the video device in the BIOS, do that. Then when you boot up Ubuntu, choose the recovery mode option and run:
sudo dpkg-reconfigure xserver-xorg
This will ask you a series of questions about your mouse, keyboard and video. Answer them as per your computers specs. If you are unsure about some of the answers, just go with the preselected defaults. When finnished, just reboot or type "startx" and you should be good to go.
First, back your current xorg.conf for safety like this:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by klick.here on 2008-04-16
Sounds reasonable to me.  Thanks.  I went into the recovery mode but then had no idea what to do.

---

### Post by klick.here on 2008-04-16
Ok that worked fine but now I realize that wasn't such a good idea.  The onboard graphics won't do anything fun.  How do I get my backup xorg config back?  I guess I'll have to buy a new video card but I hate to sink money into an old machine that doesn't support pcie or ddr2 or dual core.  Does anyone have any idea my card does compiz but won't do video games?  I bought it back in 2000 so I could play quake 3 and the fan died a few years ago and it has been working without it for a while.  I guess it overheats as soon as I start a 3D game.  I could invest in a new fan for 5 bucks but I think it's probably to late for it.:)  Thanks  everyone for your help.

---

### Post by tommcd on 2008-04-17
> **klick.here said:**
> Ok that worked fine but now I realize that wasn't such a good idea.  The onboard graphics won't do anything fun.  How do I get my backup xorg config back?

If you backed up your xorg.conf with this command:
sudo cp /etc/X11/xorg.conf /etc/X11/xork.conf.bak
you can restore your original xorg.conf like this:
sudo cp -i /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
The "-i" switch is for interactive mode. It will ask you to confirm if you want to overwrite xorg.conf (good for safety, so you don't accidentally overwrite the wrong file). Just hit "y" for yes to confirm. The restart X with ctrl + alt + backspace. You should then get the nvidia logo and have your nvidia card working again. You wil obviously need to put back your nvidia card in the machine for that.
EDIT: You might want to do this from recovery mode because after you hook up your nvidia card and boot up, X might not work with xorg.conf set up for your onboard graphics. So replace xork.conf from recovery mode and just reboot. You should then get the nvidia logo and be ok.

---

### Post by klick.here on 2008-04-17
Ok I'll do that tonight.  thanks again

---

