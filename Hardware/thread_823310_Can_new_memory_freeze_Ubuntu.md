---
title: "Can new memory freeze Ubuntu?"
date: 2008-06-09
forum: Hardware
---

### Post by madu on 2008-06-09
Hello,

I have Ubuntu 8.04 installed in my Lenovo T60 and it worked fine so far. Did a very fresh install just onew week ago and never had any problems.

Today I upgraded the memory and installed additional 2GB ram. Everything worked fine initially and then suddenly Ubuntu just froze. Literally froze. Didnt respond to any commands. I had to turn off by holding the power switch. This happened about 3 times in a span of couple of hours.

I am really really depressed because the system was working fine, and also a freeze is something I last expected.

I checked the /var/log files and there is nothing special recorded at the times of freeze.

Can somebody shed some light about this?
Any suggestion is greatly appreciated.

Thanks a lot.

---

### Post by tysonh on 2008-06-09
I think I read somewhere once to install the memory sticks one at a time.  This could be total crap but it might help you out.  Good luck :)

---

### Post by madu on 2008-06-09
Thanks for that Tysonh.
But it was a single 2GB module. And also there is only one additional socket available.
Also, I know this memory module works fine because my mate installed the same module in his T60 (running Gentoo) and he has no problems.

---

### Post by msrinath80 on 2008-06-09
You have not inserted the module properly. Remove it and do it again.

---

### Post by madu on 2008-06-09
Thank you.
Actually now I have removed the memory module. And since then I had the freeze once. But seems OK until now.
Is there any procedure to insert new ram?

---

### Post by jespdj on 2008-06-09
New memory normally doesn't freeze Ubuntu. There is no special "magic" you have to do, like installing the modules one by one if you have multiple modules.

It can freeze the computer only if the memory you add is not compatible with the motherboard or with the memory that was already there (for example, because the speeds are different), or if the memory modules are broken.

Check the manual of your computer and/or motherboard, and the website of your computer or motherboard manufacturer, if they have a list of memory brands / types that they tested and that are guaranteed to work. If the memory you just bought is not on the list, then there's a possibility that it's not compatible with your computer.

To test memory, reboot your computer and start **memtest86+** from the boot menu. Let the memory test program run for a few hours to see if it finds memory errors.

---

### Post by madu on 2008-06-10
Thanks for the Memtest+ idea mate. Will try that out.

Cheers.

---

