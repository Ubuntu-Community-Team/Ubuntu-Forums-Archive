---
title: "Installing PHP5/MySQL5 without internet"
date: 2005-11-23
forum: General Help
---

### Post by Littleweseth on 2005-11-23
[ Before we begin : my stated knowledge level w.r.t linux is 'used the OSX terminal for basic stuff like manually killing/restarting httpd, editing config files using pico', and other lightweight things. I'm not scared of a command line, but have a helluva lot to learn. ]

Okay, my desire is straightforward : i'm just burnin' to install PHP 5 and that brand-spankin' new MySQL 5 (or just MySQL 4, not an issue) on my Hoary box. If I had a connection to the internet (incidentally, i'm on 3-hour limited 56k) that would be all peachy : synaptic, or apt-get to the rescue. However, it ain't that simple.

The problem lies in the fact that :
- My external serial modem decided it was tired of life - it's not pining for the fjords, this is a *dead modem!*
- My internal modem (alarm bells already) happens to be a cheap Compaq POS (Lucent WinModem). Can't find *nix drivers for it, damn cheapskate Compaq.
- This iMac i'm on does have a working modem.... but the LAN controller is dead (or flaky at the very least.) I can't run out the RJ45 and create a magic pathway from the Hoary box to this one without some heavy magic.

Therefore, I have to do any necessary downloading on an OSX iMac (yes, it does have a terminal and all the usual *nix tools like wget (aah wget, we lub j00) and cURL, though fink != apt-get) and then, using a 256mb flashdrive, move them across and do $magic with them once there.

I've started down the logical path by downloading the PHP 5.0.5 source (gotta md5 it later) and what i presume is the mysql5 binary from [http://dev.mysql.com/downloads/mysql/5.0.html](http://dev.mysql.com/downloads/mysql/5.0.html) - very first file under 'linux'. However, two questions arise, even presuming i'm on the right path and am not a total, complete idiot :

[Duffman wants more of that enumerated list. Oh-yeah! ]

a) I read in some arcane text somewhere (Ubuntu wikis methinks) that MYSQL has some funky dependencies. If so, the usual course would be 'run apt-get and it'll take care of it automagically' : however, seeing as I have no direct internet connection, that's not an option. 

b) I'm embarrased to admit that i have these two wonderful files slooowly working their way through my phone line, but I have nil idea what to actually do with 'em. Except that you need to do arcane stuff like make and gcc to the PHP5 source.

Um. [Ubuntu forum fellas], you're my only thousand or so hopes. Please advise as to the wisdom of my current course, or feel free to tell me i'm a damn idiot and there's a simpler way, as long as you tell me what it is.

And if someone tells me all this stuff is lurking in the install CD somewhere, I *am* gonna do something rash :D

- Li-aung 'lws' Yip
Phear the SphericalCUBE (tm)

---

