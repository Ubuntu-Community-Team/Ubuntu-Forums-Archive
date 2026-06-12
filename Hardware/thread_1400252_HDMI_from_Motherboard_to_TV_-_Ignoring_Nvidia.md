---
title: "HDMI from Motherboard to TV - Ignoring Nvidia"
date: 2010-02-06
forum: Hardware
---

### Post by NertSkull on 2010-02-06
Today I bought a new TV that I have put near my computer and clearly would love to have it hooked up if possible.

Right now I have a dual-monitor set up working great using an NVIDIA GeForce 8800 (or 6800, i'd have to check, can't remember off the top of my head).

Anyway, the two monitors work fine and the card has a DVI out and a regular VGA out each connected to one of the two monitors.  I have the NVIDIA drivers installed doing that.

Now I have a HDMI out that comes from my motherboard.  I've never actually used it, because my monitors don't have HDMI, but I assume it works since I tried it once in windows a year back or so.

So my question is, can I possibly hook the TV up to the HDMI out on the motherboard while leaving my dual-monitors alone.  All I'm looking for is a way to hook up MythTV and XBMC to the TV.  I don't need it for regular computer use.  But since the HDMI is not part of the NVIDIA card it obviously doesn't show up in my NVIDIA settings config.

Is there a way to do this, that doesn't involve buying a new graphics card.

Thanks for the help.

---

### Post by NertSkull on 2010-02-07
So for others who may be slow like me, I've discovered the problem was in my BIOS.

Apparantly my BIOS had a setting that said if a graphics card is found, use that and disable the motherboard GPU.  So I changed that setting to Always Enable the motherboard GPU.

Now when I boot into ubuntu, the NVIDIA-Settings manager finds my two monitors as well as the TV plugged into the motherboard.  And I can set it up just as easy as setting up two monitors.  Pretty awesome.  I had to set it up to be seperate X sessions for each monitor.

Only drawback now is I've lost some of compiz multiple desktops.  I used to have 4, but now it only gives me two.  If anyone has any ideas how to get those back I'd appreciate it.  Its not a huge deal, but I used them rather extensively.  I've checked the gconf manager and the hsize is still 4 like it should be.  I don't know what's going on there.

But for all intents and purposes I'm a happy camper.

---

### Post by troll1602 on 2010-05-09
How exactly did you get the motherboard GPU to be recognized? I have an nvidia card with DVI output and the motherboard has the HDMI output and I wanted to use both for two different monitors.

---

### Post by troll1602 on 2010-05-09
Nevermind, I understand what you did. I got confused because my BIOS doesn't have a setting to allow both GPU's to run. If you have any advise on getting the HDMI port recognized without removing the nvidia card that would be awesome.

I'm using a Dell Studio XPS. The BIOS version is A03.

---

