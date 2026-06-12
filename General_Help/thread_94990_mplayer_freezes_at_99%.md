---
title: "mplayer freezes at 99%"
date: 2005-11-25
forum: General Help
---

### Post by wazoo on 2005-11-25
The problem is getting Firefox 1.0.7 to play Apple trailers. I've tried the fixes I've seen here:

1. Removing the totem plugins from /usr/lib/mozilla-firefox

2. Installing mplayer, mozilla-mplayer, codecs.

That got me quicktime videos that ran up to 99% -- then froze.

So seeing that someone said the problems was an old mozilla-mplayer plugin, I "apt-get remove mozilla-mplayer"

wget [http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

dpkg -i mplayerplug-in_3.11-1_i386.deb 

Same deal: loads, freezes. Even a "reload" doesn't work.

So, I'm stuck. Any help?

---

### Post by Xian on 2005-11-25
I'm curious...is FF supposed to be able to play those QT files an an imbed or does it simply pass the link along to a media client? I honestly don't know as I use Opera and the configuration is probably different.

---

### Post by hoodwink on 2005-11-25
I can't offer much help. Just note that mplayer and the mozilla plugin have a long history of not always working. I ran Gentoo for years. When the 2.6 kernel came along, it was months and several bugfix releases before anything worked.

Now on Ubuntu, mplayer/firefox works for me most of the time, but occasional trailers on the Apple site cause mplayer/firefox to go poof.

---

### Post by sunny_nwho on 2005-12-09
I have the same problem with mplayer an it is not only working properly in FF but alos in ephipanytoooo....I would request any of you to look into this problem...the solution will be of great help to everyone...thank u in advance ...Sunny

---

### Post by yaddoshi on 2006-02-09
I also had this problem, even though it worked perfectly fine in the exact same configuration as my notebook.

After I installed mozilla-mplayer, I was following the directions listed [here]("http://ubuntuguide.org/#mplayer") I edited /etc/mplayer/mplayer.conf and did this:
> # Find this line

...
vo=x11,                  # To specify default video driver (see -vo help for
...

# Replace with the following line

vo=xv,                  # To specify default video driver (see -vo help for

# Save the edited file (sample)

On a clean install of Ubuntu, with the default Firefox, the movie trailer from trailers.apple.com would load to 99% and stop as you described.

I changed vo=xv back to vo=x11 - now it works perfectly.

Hope that helps.

---

### Post by ions on 2006-03-02
Yeah that fixed it.  Pain in the rear when the Howto is wrong.  Thanks yaddoshi! :)

---

### Post by jazzi on 2006-03-05
[QUOTE=ions]Yeah that fixed it.  Pain in the rear when the Howto is wrong.  Thanks yaddoshi! :)[/QUOTE]
that key seems not work for me.
It still freeze,and always shown that "get playlist" and don't go on
UnLUCKY!!:KS

---

### Post by powder on 2006-03-05
I noticed the same behavior after installing ATI's crappy drivers.  Changing video out to X11 as mentioned above only partially fixed things, and not to mention, you can't watch video in fullscreen using X11.

---

