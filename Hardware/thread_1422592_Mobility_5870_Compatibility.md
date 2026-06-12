---
title: "Mobility 5870 Compatibility"
date: 2010-03-05
forum: Hardware
---

### Post by fallstoofast on 2010-03-05
Has anyone tried to install Ubuntu or some other linux variant with an ATI Mobility Radeon HD 5870 or other 58** series card?

How well does it work?

---

### Post by fallstoofast on 2010-03-06
bump

---

### Post by hellfeuer on 2010-06-22
bump. I too want to know how well this card works.

---

### Post by mavicus on 2010-07-20
I have this device in an Asus G73JH notebook.

Here's my experience so far, and I have been scouring the net for info but no help as of yet:

[HTML]http://ubuntuforums.org/showthread.php?p=9613394#post9613394[/HTML]

---

### Post by hellfeuer on 2010-07-22
Ok that's bad news. I was looking to get a similar laptop. Did you manage to get it to work well enough for Compiz to run? I do not care about 3d games for now (on Linux).

---

### Post by no1wantdthisname on 2010-07-23
Avoid at all costs.  Seriously.

My g73jh has been constantly freezing with vertical bars (the GSOD issue) in both windows 7 and ubuntu.  It even occurs just watching videos.

---

### Post by hellfeuer on 2010-07-23
BTW, have you checked to make sure its not just your GPU? I've read a few posts on the web claiming that lucid's drivers work well for this card. 

Still, I guess I'll be looking for a different laptop.

---

### Post by hellfeuer on 2010-07-23
Also, I was googling this issue and it seems that flashing your video bios with an updated version helps. Or use stock drivers. Both on windows. But a flashed vBios might fix your ubuntu problems as well.

---

### Post by no1wantdthisname on 2010-07-24
I ended up updating the vbios through this guide: [http://forum.notebookreview.com/asus/498015-g73-gsod-fixes-resources.html](http://forum.notebookreview.com/asus/498015-g73-gsod-fixes-resources.html)

When I ran furmark before updating vbios, I would experience a GSOD within 10 seconds. Now it lasts until around 2 minutes before a GSOD. So it has helped, but it's still far from perfect. 

The new driver for 10.7 should be coming out soon, but I'd say you'd be better off just avoiding both ATI and the g73jh.  

There's just so many issues.  

For example, the keyboard backlight doesn't work out of the box.  It requires adding some scripts to get it working.
Also the ethernet driver has to be updated.  The current version in lucid just stops working after a couple of hours. 
And finally, when I use an external monitor, there is a very annoying horizontal white flickering that occurs in both windows 7 and ubuntu.  There's no problem on my other laptop with a nvidia card using the same monitor/cable.

---

### Post by mavicus on 2010-08-03
Thanks for the new information guys.
So, if the bars are happening in both windows and ubuntu, and the GPU is suspect, are we talking about a bad GPU as in a warranty replacement, or are we talking bad as in, they are all "defective" by some design flaw, or both?
It's a shame imo that this laptop doesn't come with nVidia!

And yes to new readers, if I had it to do all over again, I also would consider another laptop besides the G73jh.

---

### Post by no1wantdthisname on 2010-08-05
It took a while, but I finally managed to get it stable in both win7 and lucid.  

For those having the same problem, I just followed everything in the link I posted earlier, except I left the clocks at 700/1000 and updated to 10.7.  I'm now able to run furmark for 20+ minutes without crashes and I haven't had crashes while watching videos for a couple of days.

But like mavicus said, avoid the g73jh, because it wasn't worth all the trouble.

EDIT: scratch that.  Starcraft 2 is able to consistently cause GSODs.

EDIT 2: Overclocking to 745/1100 seems to stop SC2 from crashing.

---

