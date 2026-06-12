---
title: "Internal Speakers Fine, Headphones No Sound???"
date: 2009-05-18
forum: Hardware
---

### Post by Daeboy on 2009-05-18
All right... so I needed to reinstall Ubuntu and I previously had Gutsy Gibbon. I decided to try out Hardy this time. Everything worked great straight-away - except for the headphones. I have a Toshiba Satellite laptop, which usually has the issue of no sound with Ubuntu. I've tried several solutions.

I've tried adding lines to /etc/modprobe.d/alsa.base.
I've checked alsamixer.
I've played with the gnome volume controls more times than I can count.

I don't understand what the problem could be. Sound comes from the internal speakers of the laptop perfectly fine, but I like to hook speakers up to it because I like loud music. For some technical specs...

The chip is a Realtek ALC861VD.
Audio Device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller.

Any solutions would be -greatly- appreciated. I registered just because of this problem. I've never had to do so before; I could usually just figure it out. This time, however, has made me want to rip my hair out. :P

Thanks in advance.

---

### Post by Acapulco on 2009-05-19
Have you tried upgrading your Alsa drivers?

I had some problems with sound on Jaunty. With Gutsy I had no problems, then upgraded to Hardy and quickly upgraded to Jaunty, so I had no time to check sound in Hardy.

Try this guide, I think it might help. 
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

---

### Post by Daeboy on 2009-05-20
Thank you very much for the reply and the guide. Two interesting things happened:

1) After completing the guide step-by-step with no error, my /proc/asound/version file is still saying I'm version 1.0.16.

2) And There's still no sound through the headphone jack, though I know it's not the jack or the speakers as I've tested both via other OS's.

Meh... any other suggestions???

---

### Post by Daeboy on 2009-06-03
Sorry for double-post, but still no solutions. Headphone jack worked fine under Gutsy Gibbon, but in Jaunty I get no sound. Tested speakers - they're fine. Still no other suggestions?

Oh, and I did successfully upgrade alsa - still didn't work.

---

