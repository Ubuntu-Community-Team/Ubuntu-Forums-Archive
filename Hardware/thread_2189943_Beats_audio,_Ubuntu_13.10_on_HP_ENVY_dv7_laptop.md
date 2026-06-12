---
title: "Beats audio, Ubuntu 13.10 on HP ENVY dv7 laptop"
date: 2013-11-24
forum: Hardware
---

### Post by jaime3 on 2013-11-24
How do I get all beats audio speaker working on Ubuntu 13.10 os on HP ENVY dv7 laptop

---

### Post by angi-sl on 2014-02-15
[http://www.reddit.com/r/linux/comments/17sov5/](http://www.reddit.com/r/linux/comments/17sov5/)

I tried this but it does not seem to work on 13.10 although I was able to get it working fine on 12.04.4 LTS..

Maybe its not yet out for saucy..

[https://launchpad.net/~diwic/+archive/hda](https://launchpad.net/~diwic/+archive/hda)

---

### Post by angi-sl on 2014-02-15
[http://ubuntuforums.org/showthread.php?p=12489414#post12489414](http://ubuntuforums.org/showthread.php?p=12489414#post12489414)

is the same

---

### Post by angi-sl on 2014-02-15
Just managed to get it fixed..

just use sudo apt-get install alsa-tools-gui

hda-jack-retask is available on that.. :) just follow the steps on the link above to get it set up accodingly.....

---

