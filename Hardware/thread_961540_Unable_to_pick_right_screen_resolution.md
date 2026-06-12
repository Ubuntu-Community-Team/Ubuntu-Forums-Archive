---
title: "Unable to pick right screen resolution"
date: 2008-10-28
forum: Hardware
---

### Post by pbean on 2008-10-28
Dear Ubuntu and Kubuntu people,

I have a laptop with an extra screen attached to it. The monitor is capable of a 1680x1050 resolution (or so, it's a 20" widescreen). However the display settings dialog does not offer this resolution. It does however offer the resolutions my laptop screen supports (up to and including the native 1280x800 of that screen) and the 1920x1200 which is supported by neither. So as you can see, I cannot get my monitor to display in the right resolution.

The (very) strange thing is that when I ran the live CD the display was fine. My external screen displayed at it's native resolution and on the laptop screen it was cloned and cropped (which I do not mind as I don't use that screen any when the external one is attached).

I tried to switch my laptop to 'external display' only mode (by pressing FN+F2 on this particular machine) before booting, but that did not make a difference (in fact, the login screen simply ignored it and displayed on the laptop screen as well).

Does anyone have any suggestions how I can resolve this minor issue? The rest works perfectly, like wireless networking, browsing the internet and network shared, and it even plays MP3 (which was a surprise to me).

Kind regards,
Paul

PS.
You might say wait a few days until the new Kubuntu, but I really prefer KDE 3 over KDE 4 (seriously, it's just way better) and want to try and stick to it for now. I tried the live CD of the release candidate and as well as the Kubuntu 8.4 one worked so flawlessly, equally as bad (if not worse) ran the 8.10 one. It felt like a blast back to the stone age.

---

### Post by phidia on 2008-10-28
I think it's going to be helpful to know what video card your laptop has.

See the video wiki [here]("https://help.ubuntu.com/community/Video") for how to determine that as well as links to other guides.

> lspci | grep VGA entered in a terminal should provide your card type.

---

### Post by pbean on 2008-10-28
> **phidia said:**
> I think it's going to be helpful to know what video card your laptop has.

See the video wiki [here]("https://help.ubuntu.com/community/Video") for how to determine that as well as links to other guides.

 entered in a terminal should provide your card type.

Thank you for your quick answer. Yes I forgot to mention my video card type. It's an Intel 945GM (sometimes called GMA950 if I recall correctly). I shall have a peek at the Wiki page you suggested and will let you know if I find anything.

Edit: well I can be rather quick about that one... there wasn't really a lot of useful information in that page, just some stuff about graphics cards, open source, etc. Also something about loading a xorg.conf file from the Live CD, but I can't find it on the Live CD. I will reboot with the Live CD and copy the file from there to the partition. Let's pray that works.

---

### Post by pbean on 2008-10-28
I copied the xorg.conf file from the Live CD to the installation partition and apparently it worked. After the reboot I got the login screen already in the right resolution, as was the KDE session after login. I did a quick test and shut down the laptop, unplugged the screen and booted again. The resolution this time around was the maximum of the laptop screen, which is perfect (this means it will work at home with the screen and on the road without the screen).

Still... I find it a bit silly that the Live CD's configuration works and then the installed configuration does not.

---

