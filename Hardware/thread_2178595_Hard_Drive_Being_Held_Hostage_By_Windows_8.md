---
title: "Hard Drive Being Held Hostage By Windows 8"
date: 2013-10-04
forum: Hardware
---

### Post by pD43WfR on 2013-10-04
Well, the title says it all. I recently re-installed Windows 8 to give it another go, I forgot to turn off that stupid hybrid boot\sleep crap that makes Windows not play so nice in the sandbox with other operating systems, such as Linux.

And well, it's holding my hard drive hostage, I can't access it in Linux, and Windows 8 is well, crashing. And to make it clear I'm not trying to access my hard drive with Windows 8 on it, I'm trying to access a different hard drive, a nearly full TB drive and you can see why I would probably be freaking out.

I tried to do a chkdsk from within Windows while it was working... it crashed towards the end, so a few hours wasted. I booted up the install DVD for Windows 8, did a chkdsk, and at the end... it BSOD'd. Another few hours wasted.

So please, tell me the Linux way to fix hard drive problems because Windows 8, has just been causing me grief, grief, and you know more grief. Also I think it would be worth noting that I can access the hard drive perfectly fine from the Windows 8 install command prompt. And I did a hard drive check nearly a week ago and it was perfectly fine so I'm pretty sure it's Windows.

Any help is greatly appreciated.

---

### Post by Mark Phelps on 2013-10-04
Windows 8 hibernates all the paritions that were mounted when you did the shutdown, not just the OS partition.

You would do best posting your concerns in the Windows 8 forums (eightforums.com) -- where you can read tutorials and get help to solve the crashing problem.  You're NOT going to be able to fix that from Linux at this point because, in Win8, when it's hibernated, the partitions remain mounted -- denying you all access to them.

---

