---
title: "Mplayer doesnt detect sound"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by andbert on 2004-12-01
I updated to Hoary the other day.
None of my multimedia apps seemed to have sound after that.
Ive manage to solve the problems for all of them except Mplayer...

The following message occurs when i run a videofile:
"Could not open/initialize audio device -> no sound"

I have a int. Intel Sound Card

Any solution to this problem?
I tried reinstalling Mplayer but that doesnt seem to help either.

---

### Post by Orcrist on 2004-12-01
As I just went through this kind of thing myself, I might be able to shed a little light.

Mplayer gave me the same error messages, when I installed from the universe component in synaptic.   I went to [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/) and then got the newest sources, fonts, and skins and still was a no-go.    I got a 'cannot find device /dev/mixer' error every time I selected alsa drivers, and no sound from any of the others. I then hunted around on freenode #ubuntu and got some advice.  Turns out the marillat sources for mplayer (pretty sure this is what the ubuntu package is built on) are kind of quirky/buggy depending on your hardware.  This is a known issue, but apparently not too well-known.

What I had to do to resolve my problems was to download a CVS version of Mplayer from the above mentioned site. Once I had it, the codecs and the font/skins (getting the codecs put in the right directory BEFORE you run make is very important!  Else you won't have support for win32 codecs) I made sure I had the necessary packages to support mplayer by typing:

sudo apt-get build-dep mplayer

from the command line.   After that I did a compile using the instructions on this site:

[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

I just changed the directories/file names he gives there for the version of MPlayer I was compiling, and left all else the exact same.

When I was done, all my woes were solved.   Hope this helps.

PS. I did uninstall my existing mplayer from within synaptic, but I'm not quite sure this is necessary.  Also (not trying to insult you, but always check the most obvious thing first)  make sure you've selected alsa drivers from within mplayer, and run alsamixer from the cmd line and make sure you've got everything cranked up.

---

