---
title: "Hibernation killed my install"
date: 2009-10-09
forum: Hardware
---

### Post by SpitfireSMS on 2009-10-09
So I tried hibernation after a new install..
It hibernated fine, I left it like that over night.
This morning, it will turn on, go to grub, try to boot, and sit there with a blinking cursor indefinitely.

I believe its trying to resume and cant, but I dont have any other option to get it to boot.
I tried killing all the running power, by taking out the battery for a couple mins, but that didnt do anything.

Also, I edited the recovery mode out of grub, how would I edit the regular boot option to get me into recovery, and would that work?

---

### Post by SpitfireSMS on 2009-10-09
OK So I have no idea why it happened, but I wont be using hibernate anymore.

I was able to edit my grub menu from the grub boot screen.
After my UUID there was "ro quiet splash"
I edited this to "ro single" and it boot into recovery mode, where I selected boot normally and it came back on.
It actually came back from hibernate, with everything still running haha.

---

