---
title: "[SOLVED] Cannot Increase Screen Resolution Beyond 640x480"
date: 2008-05-31
forum: Hardware
---

### Post by Bubtottle on 2008-05-31
My computer has recently reverted to 640x480 screen resolution and I would like to dramatically increase that. When I start my computer, a window comes up telling me that the computer is running in reduced graphics mode. If I select 'Configure' the only resolution I have to choose from is 640x480. I have already tried:

```
sudo dpkg-reconfigure xserver-xorg
```
               All this does that I can tell is reconfigure the keyboard.
```
sudo apt-get install xresprobe
sudo dpkg-reconfigure xserver-xorg
```
               This had the same result as the previous attempt.

I have found the option of editing xorg.conf and adding screen resolutions but the problem is that I can't remember the resolution I used to have (I know it's far greater than my current resolution) and thus am not sure what to put into xorg.conf. Another problem is that all guides for editing screen resolutions in xorg.conf that I have found are quite vague which worries me.

If anyone can help me, please do.

---

### Post by Bubtottle on 2008-05-31
Right, I did
```

sudo dpkg-reconfigure -phigh xserver-xorg
```
and restarted and now everything works

---

