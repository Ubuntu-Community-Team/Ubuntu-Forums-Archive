---
title: "Ati Closed Source driver - unable to install"
date: 2010-05-02
forum: Hardware
---

### Post by datroubler on 2010-05-02
I already posted my problem in a german Ubuntu community without effort:
[http://forum.ubuntuusers.de/topic/beschaedigtes-paketsystem/](http://forum.ubuntuusers.de/topic/beschaedigtes-paketsystem/)

**The problem occurs since I updated Ubuntu to 10.4**
I am using the following laptop:
[http://board.gulli.com/thread/1428580-kleines-review-asus-n51tp-sx040c/](http://board.gulli.com/thread/1428580-kleines-review-asus-n51tp-sx040c/)
with the ** ATI Mobility Radeon HD 4650 1024MB** card.
At the moment I am using the opensource driver but I have the following problems:
- The Laptop makes a lot of noise (caused by the VideoCard)
- Laptop turns hot
- Suspend mode didn't works

If I try to activate the driver I get the following message:
[http://www.abload.de/image.php?img=activatedriverc589.png](http://www.abload.de/image.php?img=activatedriverc589.png)

If i try to install it through the softwarte center:
[http://paste.ubuntu.com/426448/](http://paste.ubuntu.com/426448/)

after that I can't install oder deinstall anything:
[http://www.abload.de/image.php?img=errora901.png](http://www.abload.de/image.php?img=errora901.png)

I have to type the following:
> sudo dpkg --purge $(dpkg -l|awk '/fglrx|libamdx/{print $2}'); rm -rf /etc/atiIs this a known bug or am I the only with this problem?

---

### Post by datroubler on 2010-05-03
The Manuall installation fails with the same problem.

---

### Post by datroubler on 2010-05-04
Finally arand helped me in the IRC but I can not say that the problem was we tried several things.

---

