---
title: "Touchpad issues: Scroll area too wide and Mouse jumps right"
date: 2011-04-30
forum: Hardware
---

### Post by monkeys on 2011-04-30
I've seen these bugs both reported in other areas and other distros, but thus far my attempts at fixing the problem haven't been successful.

1) Scroll region is too wide. Half my touchpad is a vertical scroll area. I've tried fixes similar to this: [http://blog.technicallyworks.com/2009/08/fix-touchpad-scroll-area-in-xubuntu-904.html](http://blog.technicallyworks.com/2009/08/fix-touchpad-scroll-area-in-xubuntu-904.html) but to no avail. My touchpad.fdi (there is also verticalscroll.fdi and shmconfig.fdi) looks like this:

```
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
<merge key="input.x11_options.RightEdge" type="string">5942</merge>
</match>
</device>
</deviceinfo>
```

The only thing that works temporarily is this in the Terminal:

```
synclient RightEdge=8175
```

I'm sorry if I've missed similar threads but none of my searches have come up too successful. Would love to know what you're searching if you're wiser (;

2) When approaching the right edge of the touchpad, my cursor jumps to the edge! I'm not familiar with patches so I haven't tried it, but am willing to if highly recommended (: The bug has been filed here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/591656](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/591656)

Thanks in advance for the help. After a few years of using Ubuntu, I am by far no pro!

---

