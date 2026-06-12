---
title: "Sony Vaio SZ-Series Screen brightness + power management"
date: 2011-03-08
forum: Hardware
---

### Post by kcxzero on 2011-03-08
Sony Vaio VGN-SZ750N
Ubuntu 10.10
Nvidia 8400M GS

I've been searching for a solution to this for the past three weeks. The problem is I cannot change the screen brightness, via power management or using fn+f5/f6 or any other method. I have no control over my screen brightness or power management. As a result my battery runs down fast and I'm going blind.

If anyone knows of a solution please let me know.

Additionally, seeing that I have not found one online searching for the past few weeks, please let me know if for a fact you know there is no solution to this. It would be understandable, I realize that Sony Vaios aren't exactly Ubuntu Friendly. That way I can stop searching and move on. Thanks.

---

### Post by bkye on 2011-03-08
I have similar problem on different vaio which is vpcy216fx with intel graphics. I need a solution, too. Maybe some of these can help to you. 

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=sony+vaio+brightness&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=sony+vaio+brightness&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by kcxzero on 2011-03-08
Thanks for the link, unfortunately I haven't found one that works yet. Just to let you know, if you are also having trouble with the backlight try installing nvclock. It's obviously not a solution to this problem, but at least it helps with the eyes.

```
sudo apt-get install nvclock

smartdimmer -s 15
```Range [15-100], I'll be using 15 for awhile to restore my eyes lol. I wasn't aware there was a difference between brightness and backlight.

[http://ubuntuforums.org/showthread.php?t=1557589](http://ubuntuforums.org/showthread.php?t=1557589)

Also, according to the battery estimate It's added approximately an hour to my battery life so that's good. Though this does not solve screen brightness or the power management, It's a decent solution to conserving battery life and decreasing the amount of light is produced through the screen.

---

