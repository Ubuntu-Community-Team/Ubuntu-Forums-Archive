---
title: "How to or should I disable floppy drive before ubuntu install??"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by TheGames on 2009-07-29
Hello there,

I'm about to install Ubuntu 8.04.3 LTS and I ran the "Check CD for defects" upon booting the CD and it found no errors on the disc, but it showed "Buffer I/O Error on device fd0, logical block 0" error twice at the top. 

A) Is it okay if I run the install and just ignore this error?
B) I know this error is because I have no floppy drive in my desktop and I looked into disabling it in the bios.

I am confused though ... am I supposed to disable the "Onboard FDC Controller" and select the floppy drive as "None"?? I'm confused if I should disable the Onboard FDC Controller as well, as I read in various places that it may control more than just the floppy drive.

One other thing, I'm also dual booting with Windows XP Pro.

Thanks for the help! :)

---

### Post by jerrrys on 2009-07-29
will the live cd run without installing it?  if so, then you should be good to go.  about that error message...

[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

also defrag xp before installing and have a look here...

[http://www.google.com/search?q=dual+boot+xp+and+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=dual+boot+xp+and+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by TheGames on 2009-07-29
> **jerrrys said:**
> will the live cd run without installing it?  if so, then you should be good to go.  about that error message...

[https://answers.launchpad.net/ubuntu/+question/7697](https://answers.launchpad.net/ubuntu/+question/7697)

also defrag xp before installing and have a look here...

[http://www.google.com/search?q=dual+boot+xp+and+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=dual+boot+xp+and+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
Thanks for the info!:)

Can someone please also tell me how to properly disable the floppy drive from the bios? I really need assistance on the second part of my question in my original post.

Do I disable the onboard FDC controller and set the floppy drive from "1.44"etc. to "none"? Is it bad if I disable the onboard FDC controller while also having XP Pro on the system? Does it only control the floppy drive or more?:confused:

Thank you all!!:D

---

### Post by jerrrys on 2009-07-29
Do I disable the onboard FDC controller and set the floppy drive from "1.44"etc. to "none"?

Go for it.  should not interfere with anything else, but if it does, just go back to bios and enable.

---

