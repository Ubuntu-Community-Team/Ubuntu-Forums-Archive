---
title: "New Upgrade went perfectly"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by kibster on 2009-04-26
I install the new upgrade 9.04 and so far everything is going smooth even the system sound is there. 

My Question is this...Nothing will play in Firefox . Like CNN and 

youtube videos . They worked before ! 

How can I get the correct codecs again.

Russ

---

### Post by Tim Sharitt on 2009-04-26
To view flash videos, you need to install flashplugin-nonfree via Add/Remove, apt-get or what ever you prefer.

To install with apt-get from the command line:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kibster on 2009-04-26
Well apparently I had it installed already..but doesnt work ..so I un-installed it and re-installed. And it still does not work. I rebooted a couple of times thinking that the settings need to take (Remember  ? that was a windows thing ) And it won't work.

I wonder what be wrong ? 

Russ

---

### Post by rosswmcgee on 2009-04-26
Go to admin/ synaptic mgr/ search flash/ Adobe flash 10 is there/ if not installed re-install. Mine works fine in 9.04

---

### Post by A. J. Rimmer on 2009-04-26
Also, Adobe has a test site that will tell you if you have Flash properly installed and if so what version:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_15507)

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

---

### Post by H4rm0ny on 2009-04-26
Nope - same problem here. Am on Kubuntu and FLASH no longer works in Firefox or Konqueror. Doesn't seem to detect the plugin at all.

The flashplugin-nonfree package is installed. No sign of anything working though. The .deb file from the Adobe site is unusable for me due to being the wrong architecture (allegedly).  It says only i386 is available. I have a 64-bit dual core Athlon!

---

### Post by kibster on 2009-04-26
Thanks.. It worked perfectly for youtube... 

I went Synatic and typed in Adobe Flash Player 10  And about 4 different ones popped up... I un installed them all  re booted
and then went and intalled  The non free thing and it wanted to install one more  . I let it do what it wanted  re booted  Wella !!

Russ

---

### Post by H4rm0ny on 2009-04-26
Thanks. This has worked for me also. Don't like that this is like the old Windows days - uninstall, reinstall and it works. I'd like to know what got screwed up in the upgrade so I could have just changed it myself.

But everything now appears to be working fine and I can watch my boxing again so I shouldn't complain. ;)

Rest of the upgrade seems fine so well done to the maintainers.

H.

---

### Post by kibster on 2009-04-26
Well I'm glad you got it going... This is better than Windows by far . At least for me it is.. Windows had everybody attacking it and you couldnt do anything about it. Then buy software that you hoped would take of it. And didnt.  If this doesnt work .. Its off to a Apple box. 

Russ

---

