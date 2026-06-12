---
title: "576p mode only for Gnome on PS3?"
date: 2008-11-23
forum: General Help
---

### Post by ps3_user on 2008-11-23
Hi all,

Newbie alert!!!! and my Linux skills are 20yrs old but it's fun coming back into it.

I've looked through many forums and although I've seen this fault posted, I've tried the recommended solutions but they dont resolve it for me?

I've recently installed Ubuntu 7.10 Gutsy Gibbon on my PS3, the unit is a 160Mb model and is connected to a Sony KDL-40W4500 via HDMI cable, the TV is capable of 1080p.

In game OS, the TV recognises 1080p mode and the games are superb, when I boot up into Ubuntu, at the kboot prompt I can set the ps3videomode to 1080p and the TV displays the mode, the text is very small as you'd expect but on filling up the command line, I can see I've got a full screen so it definately supports it.

When 7.10 auto starts into Gnome, the TV recognises a mode change and displays that its in 576p (mode 7 on ps3videomode) and gives me the age old problem that I've seen described elsewhere on the forums.

Gnome does not offer me any other options in Preferences/Screen Resolution, and the refresh rate is also set to 50Hz.

When I start a terminal screen, ps3videomode shows I've got mode 7, but if I try to go beyond that for 720 or 1080, I get the scrambled multiple screens in a bar across the top 10% of the screen as described by other users.
I then have to repeat the command replacing the mode with 7 to get it back to something readable.
The problem exists for both interlaced (i) and progressive modes (p).

I have tried all video modes listed by ps3videomode, including the PC VESA modes, but all give similar results.

Finally, following a suggestiion to exit the gdm (CTRL-ALT-F1?) I got the login prompt and was able to change the mode to 1080p, however I couldn't get back to Gnome (my Unix skills are so rusty).

In summary, the TV is happy displaying 1080p both for the PS3 game OS (XMB screen and games), as well as Ubuntu at the CLI before starting into Gnome, however Gnome doesn't seem to output a recognisable 1080p mode.

Am I doing something wrong, I've been looking at refresh rates, poured over all the forums, and tried anything that looked like an option but nothing seems to work?

I did consider upgrading to 8.04 but have seen many warnings against it, I wonder if replacing Gnome with another interface might give an alternative option but sadly I dont know if I need to reinstall Ubuntu with Xubuntu or Kbuntu, would prefer to add the new interface but dont know where to start, perhaps there's an update for Gnome that gives the alternative modes - because I'm pretty confident the problem is with the Gnome interface?

Any help would be gratefully received?

best regards.

---

