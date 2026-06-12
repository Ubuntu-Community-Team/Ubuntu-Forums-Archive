---
title: "[SOLVED] Using touchpad as scollwheel"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by smbm on 2007-08-02
Hi

I'm now the proud owner of a Thinkpad R61. It's superb.

There's one feature I would like to add though.

At the moment I'm using the red deeley in the keyboard as my main pointing device. It's a lot better at general purpose pointing than the touchpad. 

So at the moment it is just sitting dormant at the bottom which seems like a waste. Does any one know how to set it up to work like a scrollwheel? I only need vertical scrolling so would like to stop any horizontal movement. 

I've tried gsynaptics but it doesn't seem to do quite what I'm after.

Any ideas anyone?

Cheers

---

### Post by ugm6hr on 2007-08-02
Have a look at this:
[http://ubuntuforums.org/showpost.php?p=3105368&postcount=2](http://ubuntuforums.org/showpost.php?p=3105368&postcount=2)

It's not the same question you asked - but it gives you all the info you need to sort what you were asking for.

```
man synaptics
```
Presumably - you could set the RightEdge quite far to the left, and enable VertEdgeScroll.  Or just use the VertTwoFingerScroll option.

You might want to set MinSpeed and MaxSpeed to 0 to ensure it doesn't move the pointer when you are doing anything on the pad.

---

### Post by smbm on 2007-08-03
Hi

Cheers for pointing me in the right direction.

I managed to do it using this guide in the end:

[http://www.thinkwiki.org/wiki/Talk:Synaptics_TouchPad_driver_for_X]("http://www.thinkwiki.org/wiki/Talk:Synaptics_TouchPad_driver_for_X")

I'll try and collate it into a howto and post it when I get a chance.

---

### Post by ugm6hr on 2007-08-03
> **smbm said:**
> Hi

Cheers for pointing me in the right direction.

I managed to do it using this guide in the end:

[http://www.thinkwiki.org/wiki/Talk:Synaptics_TouchPad_driver_for_X]("http://www.thinkwiki.org/wiki/Talk:Synaptics_TouchPad_driver_for_X")

I'll try and collate it into a howto and post it when I get a chance.

That's the kind of thing I meant... Funny how you're never the first person to have a great idea :lolflag:

---

