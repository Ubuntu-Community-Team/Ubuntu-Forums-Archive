---
title: "Laptop Acceleration Detection"
date: 2013-03-28
forum: Hardware
---

### Post by JaySeeJC on 2013-03-28
I was just wondering if this is possible, and possibly any hints as to where to look.

Under window$, my manufacturer (Toshiba) provides a driver that detects when my laptop is jarred or is falling, and stops the hard drive temporarily. Would this be possible to pull off under Ubuntu  Would I look somewhere under the /proc tree to try and find said acceleration readings? Somewhere else? Possibly load some module?

---

### Post by slickymaster on 2013-03-28
There is Smartmontools which is a set of applications that can test hard drives and read their hardware SMART statistics, providing advanced warning of disk degradation and failure.
You can install by typing the following into the terminal:
```
sudo apt-get install smartmontools 
```

---

### Post by JaySeeJC on 2013-03-28
Not exactly what I'm looking for... What the window$ driver does is stop the hard drive if say the laptop is falling off the table, to reduce the risk of a head crash. Any chance there's anything I can use for that?

---

### Post by Mark Phelps on 2013-03-29
> **slickymaster said:**
> There is Smartmontools which is a set of applications ...

That's not what the OP is talking about.  

He's talking about some laptops that have accelerometers installed that can detect the laptop being dropped and instantly park the heads on the hard drive.

---

### Post by slickymaster on 2013-03-29
> **Mark Phelps said:**
> That's not what the OP is talking about.  

He's talking about some laptops that have accelerometers installed that can detect the laptop being dropped and instantly park the heads on the hard drive.

Yes, I saw that after the OP's answer to my previous post.

But the only thing that comes to mind is [HDAPS]("http://www.thinkwiki.org/wiki/HDAPS"). The question is that I'm not sure that it has the specific feature the OP describes. As far as I can remember it's main feature was the purpose of protecting t hard drive from sudden shocks by parking the disk heads, so that shocks do not cause them to crash into the drive's platters.

Maybe it's worth a look, though.

---

### Post by technophant on 2013-04-26
The best answer I've found is "not yet" however in the last two weeks a developer, Nathaniel M Nelson, has developed a patch that can read the sensor as well as set the protection level. In his [blog]("http://nathanielmnelson.com/node/24") he says that he is currently working on a park/unpark daemon to accompany this patch. There's a long-standing bug report open at Launchpad where progress can be followed.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/116045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/116045)

---

