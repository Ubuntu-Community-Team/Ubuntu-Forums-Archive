---
title: "ALPS touchpad"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by kreso on 2005-10-23
I'm using a HP Pavillion zv5000 with an ALPS touchpad and two very important things arent working, though strangely enough they worked in kubuntu preview release (it doesnt work in kubuntu 5.10 though)

1) vertical scrolling
2) drag&drop

any idea how to fix that?

---

### Post by John.Michael.Kane on 2005-10-23
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe" ----> this will fix drag and drop

try looking through these post see if there has been a fix for scroll [http://www.ubuntuforums.org/search.php?searchid=2198914](http://www.ubuntuforums.org/search.php?searchid=2198914)

```
 Re: synaptics driver does not work right  Posted by Trent Lloyd  at 2005-10-17 13:17:33 UTC

This was intended to be fixed, unfortunately the new synaptics driver caused worse issues with other people, such as horridly slow mouse speed, and the mouse running off randomly in the wrong direction.

Perhaps this may be fixed for dapper?
```


Please search the forum for any other issues before posting. As most questions have been answerd..

---

### Post by GoodPanos on 2005-10-23
There is a whole bunch of us that are trying to get this resolved.  So if you find any solution don't forget to post it here.:)

---

