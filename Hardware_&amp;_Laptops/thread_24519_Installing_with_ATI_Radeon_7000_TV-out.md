---
title: "Installing with ATI Radeon 7000 TV-out"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by Falc on 2005-04-07
I'm trying to turn my server into a litte multimedia box so I bought a new video card with an ATI 7000 chip. It's connected to an old Sony TV and I'm trying to install the Hoary rc2. I do NOT intend to install X, especially not after reading on these forums that the ATI 7000 doesn't seem to play nice with X (should have read that before buying the card, I guess).

The first problem I have is that the TV doesn't show the entire screen, the left-most column is cut off. Now, I get the same problem in my bios screen, so I know this is not an Ubuntu problem in and of itself, but I was hoping that there was some way I could have Ubuntu tell the video card to move it's output a bit to the right so I can read it all. Or perhaps just make it smaller so it fits better on the screen.

Then onto the actual installation problem: after I enter 'server' as install option, the installation appears to begin, but the screen is flickering horribly. This might very well be the same problem reported in [this thread](http://www.ubuntuforums.org/showthread.php?t=19168) about the 7000, though that seems mostly restricted to X environments. Also, it might be the screen updates that cause this, but I seem to recall that you need to start giving some install info pretty soon after the process starts (localization things, I believe) and I did leave it running for a bit.

So installing with the tv-out seems impossible, unless there's some install parameter I can give that might prevent the flickering. Any ideas there?

And if you have no ideas, then my final question would be: is there a way to do an Ubuntu Hoary install through SSL? Ie. have the CD start an SSL server so I can control the install from my desktop PC? Google hasn't given me any answers...

---

### Post by malcalypse on 2006-10-12
When you boot off of the install disk, you get to the Ubuntu screen where you can choose various install options (install as server, text install, oem install, recover, etc...).

At that screen, on the bottom, there are some other options.  If you look at them, one of them says F4: VGA.

Hit F4, and choose 640x400, for the tv install.  This should work out fine, allowing you to see everything at the correct resolution.

I just did this last night using a radeon 9500 with the tv out.  It worked ok.  I have to say though that I didn't notice that option at first either.

[edit] I just noticed that you're talking about hoary and not dapper.  What I describe above is true with the dapper alternate install disk, but I can't speak to hoary.

---

