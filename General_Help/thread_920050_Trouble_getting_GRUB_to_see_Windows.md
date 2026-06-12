---
title: "Trouble getting GRUB to see Windows"
date: 2008-09-14
forum: General Help
---

### Post by nartehpierat on 2008-09-14
Okay, I've been running ubuntu for a couple years or so and I recently wanted to boot back into windows for a few things so I went and found my old NTFS drive and installed windows to it. I finally managed to get it to boot grub instead of windows(I believe it was a jumper setting problem) but now Windows is nowhere to be found.

I've added it to the grub list, most the tuts I found said hd0,0 should almost always work, but that's where I believe my ubuntu is found. All the other menu items point ubuntu toward 0,0, and I tried it anyway and tada, it loads ubuntu. So then I try 0,1, Error 12 doesn't exist. So then I go and try 1,0 and grub will say "Loading" or whatever, do a couple line breaks and just has a blinking underscore, no HD activity and it just sits there.

So my question is, how do I find out where my windows actually is? Again, ubuntu was installed first, and long before, and now there's a windows install on a second HD.

---

### Post by cariboo on 2008-09-14
If you type:

```
sudo fdisk -l
```

in a terminal it will give you a listing of your hard drives and partitions. It should be pretty easy to find windows.

Jim

---

### Post by caljohnsmith on 2008-09-15
Since you have Windows on a different drive then your Ubuntu, and because you did get a response when you tried (hd1,0), probably all you need to do is add the following to your menu.lst to get Windows booting:
```
title	   Windows
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, then please post the output of:
```
sudo fdisk -lu
```
Let me know how it goes.

---

