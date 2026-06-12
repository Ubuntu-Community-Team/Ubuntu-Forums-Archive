---
title: "Debug HID module : How??"
date: 2008-08-20
forum: General Help
---

### Post by yellux on 2008-08-20
Hello,

I try to recovered the report hid debugging module for the kernel of info when I press the buttons on my keyboard that are not recognized.

I have compiled a kernel with HID debugging  support ( HID_DEBUG ) , loaded the module after the installation and reboot with:


```
sudo modprobe hid debug=2
```

Normally with dmesg or in the viewer logs systems I should reflect these information but nothing appears ??

I searched on the net and I did not find much...
There are an example to 5th message of this discussion: :
[http://groups.google.com/group/linux.ke &#8230; f?lnk=raot]("http://groups.google.com/group/linux.ke &#8230; f?lnk=raot")[http://groups.google.com/group/linux.ke](http://groups.google.com/group/linux.ke) &#8230; f?lnk=raot

I also tried as the person with debug=1 but still nothing.
I work with Hardy Heron and i try with git and with a kernel from kernel.org (2.6.26.2), always nothing.

If someone would have an idea, I thank you in advance.

PS : Sorry for my English, i'm French ;-)

---

