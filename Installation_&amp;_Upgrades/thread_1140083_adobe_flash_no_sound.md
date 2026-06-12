---
title: "adobe flash no sound"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by DJJo on 2009-04-27
when I did upgrade from 8.10 to 9.04, my sound in youtube did not work.

I thought if I upgrade it wil be better. bud i was wrong.
then no more flash. Now I gegooglet it and came down to "remove my free-flash-plugin" and install the wan from adobe it zelf.

when I did that my flash did work but I stil got no sound.
I have searched everywhere but I can not find it.

now if I have VLC open. I can not play music with amarok.
now I had also been searching about that. but they keep telling me to install oss sound and use that.

so i am searching for a solution to fix my sound and a solution for my sound from adobe flash.

i am using ubuntu 9.04 32bit 
creative sound card + C-meadia sound card.

    
sorry for my bad english

---

### Post by Fl0ris on 2009-04-27
I'm experiencing the same problems with Flash player after upgrading from Ubuntu Jaunty 8.10 to 9.04! It was a 'down'grade for Flash player, because first it worked well. I'm able to here all the other sounds in my distro. Hopefully there will be an upgrade to fix this soon. BTW, I have spent five hours trying to fix this bug but nothing i found on the internet worked.

> sorry for my bad english
No apologies, it's understandable.

---

### Post by Fl0ris on 2009-04-27
No probs anymore.

**This might be the right solution:**
[I]Try if the 64 bit's version works:
[http://queleimporta.com/en/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/](http://queleimporta.com/en/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/)[/I]
No need to uninstall anything! Previous versions of Flash Player will be uninstalled automatically.

If not, please report back.

---

### Post by DJJo on 2009-04-27
i do not have 64 bit.

---

### Post by Fl0ris on 2009-04-27
Have you tried to reinstall flash player?

> $ sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree
$ sudo apt-get install flashplugin-installer flashplugin-nonfree

There are lots of solutions out of here.

Else [Google]("http://www.google.com/search?hl=en&q=ubuntu+9.04+flash+sound&btnG=Google+Search&aq=f&oq=") is your friend.

---

### Post by DJJo on 2009-04-27
yes i did
> Now I gegooglet it and came down to "remove my free-flash-plugin" and install the wan from adobe it zelf.
did i not explain myself good in off.

---

### Post by s3ntinel76 on 2009-04-27
Thanks Fl0ris - worked a treat.

---

### Post by Fl0ris on 2009-04-27
Exuse-me I did not read very well...

---

### Post by Fl0ris on 2009-04-27
@s3ntinel76 - I'm glad to hear my help was useful :)

@DJJo - Actually I'm new in Ubuntu, so I'm afraid i can't help you if you've tried everything you could find. A good tip might be to search in this forum instead of searching in Google (more [relevant] hits).
[These instructions]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio") worked for me before.

---

