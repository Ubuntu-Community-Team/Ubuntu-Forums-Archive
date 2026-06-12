---
title: "Dell 700m Users: Need your advice please"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by shuttleworthwannabe on 2006-01-20
Hi guys, this is my first post here. And I am new to Linux as well. But have been trying various dsitro (Mepis on another box then now SUSE 10 my Dell 700m)

was wondering if users of Dell 700m and Ubuntu have had any problems with the hardware. I have succefully installed SUSE 10 dual booting with WinXP, and all seems to be working as far as I can see. The problems I encountered were:

1. Screen resolution (had to get 855resolution app and edit a text file by inserting the 1280x800 res). Does Ubuntu pick up this device automatically, or do we have to also do the same here.

2. Hot keys: Like fn+volume control does not work in SUSE 10. How about in ubuntu?

3. The font setting in both KDE and GNOME, i have not been abe to get the hideously ugly and unnecessarily large font in KDE to apply to ALL applicatins. I played around with the font sizes in control center a gazillion times but the font just keeps coming back. Does anyone have a recommended setting for the Dell screen: Theme, fonts, style, icons, etc. I want something sleek, minimalist, and not resource intensive (ie. can live without some fo the eye candy). What is the optimal dpi setting in GNOME fonts so that ALL applications (including media players (gxine, Totem), GAIM, Nautilus, OOo, etc) have the same font size and res (Man is this irritating to fix.)

4. Some one on this forum aslo recently mentioned the suspend to ram function; for me in SUSE this does not work well ( I have not tried to fix it though).

Lastly, If I do install Ubuntu on this laptop (with SUSE 10, and Win XP duall boot) how would I go about doing it. I wnt to replace the SUSE intall with Ubuntu and leave the Win Xp as it is.

Thanks for the attention.
swb

---

### Post by aysiu on 2006-01-20
These links may help you out:
[http://www.celifornia.com/documents/dell700m.html](http://www.celifornia.com/documents/dell700m.html)
[http://www.progsoc.org/~wildfire/notes/dell700m.html](http://www.progsoc.org/~wildfire/notes/dell700m.html)

---

### Post by shuttleworthwannabe on 2006-01-21
Thanks that was helpful. I was wondering if user of the dell had any preferences regrding their screen settings: fonts, dpi, etc.

The reason I ask is this: Application menus do not comply with the set font in control center, perhaps I have not understood the way to get them to do this.

You see the fonts are not as crisp as they are in MS WinXP. Is there a way to tweak the system to recognize fonts as WinXP does. I feel like i am in nned of glasses when I stare at this wide screen 12.1"

Getting Firefox 1.5 menu fonts to the preferred size wasa mission, so I decided to downgrade to 1.0.7, and it seemed to solve the issue.

Take e.g. Gaim in KDE, occupies the whole freagen screen, when in GNOME it seeems to be fine (but still larger than other apps).

I hope this is a fair request.

swb

---

### Post by bettlebrox on 2006-02-11
If the fonts don't look great then maybe U need to enable autohinting? Have a look at this: [http://gnome-hacks.jodrell.net/hacks.html?id=67](http://gnome-hacks.jodrell.net/hacks.html?id=67)

---

### Post by mtrichardson on 2006-02-18
My fonts look great on my 700m.  Of course, I don't try and change them from the default, but they do look very crisp and clean for me.

Ubuntu on the 700m is a great thing.

---

### Post by NiceGuy on 2006-02-22
Hi all,

I've also got a 700m (well nearly: its actually an aopen 1551 barebook but its the same thing, just with no dell branding and a bit cheaper)

I don't know if it will help but I installed breezy and followed the advice in the ubuntu wiki for screen resolution and suspend and hibernate: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28dell%29%7C%28700m%29]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%28dell%29%7C%28700m%29")

Additionaly all the function buttons (ie press Fn and then another key) seem to work fine including suspend and volume keys (which some people seem to have trouble with)

And now comes the bit where I hijack the thread (sorry :oops:)

Everything seems to work fine EXCEPT the launch keys (or hot keys whatever you call them - the ones next to the power button) for wireless, email and web browser. I even tried upgrading to dapper but that didn't fix it either. I've tried to configure them by using xbindkeys but it doesn't seem to pick them up and I'm at a bit of a loss - any ideas?

ADDITIONAL: I tried running xev (event tester) and that didn't pick up anything either :(

EDIT: solution found! The drivers I needed were actually the acer ones - weird but at least everything is working now!

---

