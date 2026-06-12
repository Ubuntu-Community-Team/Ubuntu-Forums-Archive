---
title: "I updated my Ubuntu 17 computer, but now it won't boot past grub"
date: 2017-12-04
forum: Hardware
---

### Post by twaee on 2017-12-04
I was using my computer when an update for Ubuntu popped up. Obviously I started the installation. When I had to restart, I did so but I couldn't get back onto the computer. The computer starts up onto the grub page, I click launch Ubuntu, it gets onto the loading page and it stops there. I only see the infinitely moving loading dots. I have waited 2-3 hours for it to boot up, but it never works.


 I have tried many things: fsck, clean, dpkg, and plugged in nomodeset into the edit command section. None of them worked. Only nomodeset did something: it changed the loading screen into a black screen with only squares with the loading dots in them.

 I have tried elsewhere and still haven't gotten an answer. This lack of a Linux computer is really slowing down my school work.

When I press ESC while it is frozen in boot stage, the screen turns black. Nothing pops up. When I press it again it goes back to the loading screen. However when I plugin nomodeset there is a lot of words and numbers
 scrolling down. at the bottom it keeps getting errors of things not being able to load. This also happens when I try running another version in the additional options.

 I have not installed any proprietary drivers. I only have a intel driver the computer came with.

---

### Post by twaee on 2017-12-12
It works thanks to Segfault on linuxforums.org

Solution:
[http://www.linuxforums.org/forum/ubuntu-linux/210695-i-updated-my-ubuntu-17-computer-but-now-wont-boot-past-grub.html](http://www.linuxforums.org/forum/ubuntu-linux/210695-i-updated-my-ubuntu-17-computer-but-now-wont-boot-past-grub.html)

---

