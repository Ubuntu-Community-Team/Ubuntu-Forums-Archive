---
title: "Touchpad problems on HP Pavilion dv5000"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by henrikwl on 2007-08-26
I'm having a great deal of trouble getting the touchpad to work properly on my GF's Pavilion dv5000 running Feisty. Here's the story:

Right after installation, I got the wireless card up and running with bcm43xx-fwcutter. After a while, I noticed that the touchpad was acting up. The pointer was skipping around, clicks weren't registered - those kinds of errors. I don't know if the wireless drivers have anything to do with it, seeing as how they were the first thing I installed, but I read on this forum that switching to the ndiswrapper drivers would help so I tried. It didn't help.

Now the touchpad hardly registers anything at all. And yes, it works fine in Windows, so it's not a hardware flaw.

I've searched a great many places, but haven't found anything that helps yet. I'm a bit disappointed, as I would expect that stuff like this just works on hardware that's as old as this laptop is.

Or am I missing something?

---

### Post by be4truth on 2007-08-26
Did you install gsynaptics or qsynaptics? If not do this first. This are front ends (graphical tools) to configure touchpads.

```
sudo apt-get install gsynaptics
```
 
or

```
sudo apt-get install qsynaptics
```

After that you find this GUI tools in Administration somewhere. Load them and configure your touchpad properly. Should there be more troubles read this one

[http://ubuntuforums.org/showthread.php?t=168581&highlight=touchpad+dell]("http://ubuntuforums.org/showthread.php?t=168581&highlight=touchpad+dell")

Come back if you need more help.

---

### Post by henrikwl on 2007-08-26
Works great, thanks! I had installed the gsynaptics application earlier but never thought about it as it was set correctly. Apparently, installing the ndiswrapper had set its sensitivity setting way down low.

I'm liking this OS more and more the more I use it. I've set my GF up with Skype and aMSN - the only two applications she ever uses. I even got webcam working. Just need to test that the microphone works now, and she'll be all set. :-D

---

### Post by be4truth on 2007-08-27
Could you go to the top of this page, go to Thread Tools and mark it as solved. Thx.
Bye and have fun with Ubuntu.

---

