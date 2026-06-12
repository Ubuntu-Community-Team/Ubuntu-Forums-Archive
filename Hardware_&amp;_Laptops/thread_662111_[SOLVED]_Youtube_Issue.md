---
title: "[SOLVED] Youtube Issue"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by blueyedboy88 on 2008-01-08
Hi, my name is Seth and I just installed Ubuntu this weekened ( I've been a Windows user my whole life ). I really like Ubuntu but I keep discovering little things that I need to fix. One of the bigs ones is YouTube. When I view a video, control bar at the bottom of the video is all messed up looking and I can't control the video. Also the videos don't play very well ( slower loading and bad clearity ). What can I do to fix this?

---

### Post by ARhere on 2008-01-08
If you think about it, when you first started using Windows (whatever version) you found yourself keep finding... > little things that I need to fix as well but you are just used to Windows now.  Glad you made the switch, you will love it once you get used to Ubuntu Linux.



What flash player are you using?  My guess is you installed the open source version which is not ready for full release and it has problems.  You should go ahead and install Adobe flash player and all should be good.

**Follow these instructions.**
(Applications -> Accessories -> Terminal):
```
 sudo apt-get remove flashplugin-nonfree
```

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): 
[CLICKME]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb")

now just double-click the .deb file and you will be good to go!

-AR

NOTE:  Info copied from [this forum]("https://answers.launchpad.net/ubuntu/+question/19584")!

---

### Post by ARhere on 2008-01-08
Also, something to note.

Make sure you search the forums for your topic before posting.  This thread is discussed a few times here and having multiple threads on the same topic can be frustrating.

Also check out [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") for LOTS of good info!

-AR

---

### Post by blueyedboy88 on 2008-01-08
Oh I'm sorry :( Thanks for being so nice :) And you're very right, I'm already loving it ( I didn't even expect the effects that it comes with, like the "jello" windows lol ).

Thanks for all your help, I'll try and see if that switch to adobe helps...

---

### Post by blueyedboy88 on 2008-01-08
Okay now the little YouTube control bar looks right but a little of the bottom is cut off and I can't pause it. Also when a video plays the number zero keeps flashing on it really big :/

---

### Post by murmel on 2008-01-08
> **blueyedboy88 said:**
> Okay now the little YouTube control bar looks right but a little of the bottom is cut off and I can't pause it. Also when a video plays the number zero keeps flashing on it really big :/
[http://plugindoc.mozdev.org/faqs/flash.html#install-linux](http://plugindoc.mozdev.org/faqs/flash.html#install-linux)
Try it out that way. Just download the latest and copy it like it says.
I had to do this to make youtube live-able! ;)

---

### Post by blueyedboy88 on 2008-01-08
I keep trying to copy the file to the Mozilla plugins folder but my computer keeps saying that I don't won the file so I can't make modifications...

---

### Post by ARhere on 2008-01-09
> **blueyedboy88 said:**
> Okay now the little YouTube control bar looks right but a little of the bottom is cut off and I can't pause it. Also when a video plays the number zero keeps flashing on it really big :/

I know what that is, you did not uninstall the open source flash player Gnash first and it is defaulting to that.

Follow my steps again but this time use
```
sudo apt-get remove gnash
```

1.  Close your browser
2.  Uninstall Gnash
3.  double-click the *.deb you have and tell the manager to reinstall the package.
5.  Enjoy youtube.com

-AR

---

