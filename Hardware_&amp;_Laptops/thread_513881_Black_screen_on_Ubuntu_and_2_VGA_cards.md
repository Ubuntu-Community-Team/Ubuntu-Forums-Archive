---
title: "Black screen on Ubuntu and 2 VGA cards"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by b2dnz on 2007-07-31
Hi Guys

[I]I'm new to linux (new not noob) but am able to do most common tasks and configurations, have been an advanced windows user for a while, however, I have to use linux for a particular situation (cost)

I am using a Gigabyte GAM57SLI-S4 and a couple of Asus 7300GS cards, I am trying to basically get tri- view (or Quad-View) and need to run 4 different resolutions on each output, anyway, I have done this on windows (with slightly different hardware)[/I]

Typically I would have expected this to be breeze, however, I get Ubuntu 7.04 to boot fine but it gives me a black screen (not blank as in off or suspend, there is a video signal), The thing is I hear the Gnome's sound when it gets to login screen and I type in the username and password (even though I can't see it) and I hear the Ubuntu sound as its loading X, however, the screen stays black. I know its black (instead of blank) for two reasons, one is that when I connect the monitor to the other output, I get a monitor OSB message saying "no Video Signal" and when I plug it back, I notice the screen becoming ever so slightly illuminated and don't get the OSD message, also when I hit CTRL-ALT-F1, I actually get a virtual tty console come up on screen 

I took the second card out and it booted fine and got to log onto desktop (I did the initial install on one card), I updated the system (except for openoffice) and chose to use restricted drivers as well, still no luck when I plug in the 2nd card. I do get two cards showing when I do lspci on virtual console.

Initially I resigned myself to thinking that it was a hardware incompatibility, just to make I tried Ubuntu 6.10 (same issue), however, when I tried Fedora Core 5, it booted, did install and got to the desktop without even needing the restricted drivers

 I'm not all that familiar with Fedora so I'd rather use Ubuntu, has anybody come across this issue before or know how to solve it? Any urgent help would be appreciated

 :(

b2dnz

---

### Post by ndefontenay on 2007-07-31
Hi.

A few questions concerning this:

1) Do you get anything at all when plugging only one card and then it fails after you plug the 2nd one?

2) What are your graphic cards?

---

### Post by b2dnz on 2007-07-31
Hi mate

[LIST=1]
[*]As soon as I remove one graphic card from the system, it boots to a visible desktop, when I reboot with it plugged in, the screen goes black, I even see post screen and ubuntu splash screen fine, its only after the gnome login arrives that it goes black
[*]I am using 2x Asus N7300GS PCI-E cards
[/LIST]

The wierd thing is that this issue happens with both 6.10 and 7.04, however, when I tried with Fedora Core 5, default install, it got to the desktop with both cards plugged, haven't actually checked if the other card is able to display anything though

---

### Post by b2dnz on 2007-07-31
Found out what the problem was, Ubuntu for some strange reason chooses the secondary vga card as the primary, it does detect the other monitor, however, as soon as it gets to gnome desktop, it disables the 1st monitor (from primary vga) and enables the second monitor (on secondary VGA) as primary [shakes fist at annoying bug]

Anyway, thanks to anyone who has tested  this out and hopefully if someone else comes across this issue they will now know what it is.

---

