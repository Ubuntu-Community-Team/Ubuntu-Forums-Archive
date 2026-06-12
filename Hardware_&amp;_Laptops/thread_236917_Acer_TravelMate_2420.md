---
title: "Acer TravelMate 2420"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by involutaryhaxor on 2006-08-15
I bought an Acer TravelMate 2420 from Tigerdirect.com (against my better judgement getting it from them, but I had gift cards so I didn't really have a choice)

Anyways, everything worked lovely out of the box, even the little extra keys on the keyboard that are meant to launch an email client and browser! 

After I updated to the latest kernel, the wireless stopped working. I have no clue why. I did hear that there was something that was supposed to be added to the kernel to make more wireless cards work, but now mine doesn't work. I reinstalled and I am now just holding back on the new kernel, but is there anything I can do?

---

### Post by muadib on 2006-10-19
My Acer uses the ipw2200 driver which requires a firmware file which is in /lib/firmware/<kernel version number>

I had this same problem but I fixed it by making a symlink to an old kernel firmware directory.

#ln -s /lib/firmware/<old kernel dir> /lib/firmware/`uname -r`

Hope this helps.

Mathieu

---

### Post by oneyedjack on 2008-03-26
You folks seem to know a lot more than I, when it comes to the little extra keys on the keyboard of the TM 2420.

How do you turn them on and off?

My Son set up his windows password with the dollar sign and that other strange looking Euro symbol.  Then he forgot what he did to activate them.

After that of course, he brought it to me for repair.  

I suppose I could remove the keyboard to flash the bios, but there must be an easier way.

So help me please!  How do I turn those strange lookin'  keys on the lower right side of the keyboard off and on?

Many Thanks,

oneyedjack

---

