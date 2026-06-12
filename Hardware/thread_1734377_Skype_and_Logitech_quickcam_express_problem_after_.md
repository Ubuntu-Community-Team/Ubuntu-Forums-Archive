---
title: "Skype and Logitech quickcam express problem after recent skype update"
date: 2011-04-20
forum: Hardware
---

### Post by deskman on 2011-04-20
hi i use both maverick and natty and skype on both. After a recent skype update my Logitech quickcam express stopped working. Whhen i click on "test video" in skypes properties, i see only black, no picture. The cam works well with guvcview and cheese. Please help meeeeee !!
i tried to install older skype version that i managed to find in Mint repos but the problem persists.
My specs: P4 3.00ghz, nvidia 9400gt, 2gigs ddr2, 160gigs wd.

---

### Post by bootdoc on 2011-04-21
I have the same problem.  I tried installing v4l2ucp as well as linux-backports-modules-input-maverick-generic
linux-backports-modules-media-maverick-generic

after installing those I was able to get a very dark image in the skype video test screen.  I removed v4l2ucp and it was a little better.

I then found the following command in another thread
export XLIB_SKIP_ARGB_VISUALS=1 && skype
which worked perfectly.  I tried adding the command to the launcher properties and now I am back to square one!  Black screen in the sype test.

i have tried all the other workarounds with no success.

---

### Post by earthpigg on 2011-04-22
the solution that worked for me, [from here]("http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html"), was to start skype like this:

> - Ubuntu 32 bit: install ""libv4l-0"" package and launch Skype with: ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
``` 

I also changed the menu entry so that instead of 'skype', it had the above command.

---

### Post by zeiz on 2011-05-17
Thank you!
It works from terminal.
However menu (and custom launcher too) both give the error:

> Failed to execute child process "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so" (No such file or directory)

I have 10.4 64bit.
What I did wrong?

---

### Post by mjvdkolk on 2011-08-16
ref: [http://ubuntuforums.org/showthread.php?t=1741971](http://ubuntuforums.org/showthread.php?t=1741971)

in start menu, or with launcher use:  "env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype" without the quotes

---

### Post by fabrixx on 2011-12-18
Not work on my Ubuntu 11.10 Logiteck quickcam express

Cheese video is ok skype preview is black

---

