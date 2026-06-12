---
title: "Installing Canon LBP2900 on 13.04 Xubuntu"
date: 2013-05-22
forum: Hardware
---

### Post by forbajato on 2013-05-22
So I upgraded (maybe I shouldn't have!) and am again wrestling with getting my printer to work.

I started with Sivella's tutorial here: [http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091) that worked great for getting this thing going on 12.04, but now the ia32-libs  from oneric don't seem to be there anymore.  Can I just use the ia32-libs for 13.04 but otherwise do the same thing as in the tutorial?

thomas

---

### Post by forbajato on 2013-05-23
After waiting about 24 hours for help with no replies I decided to risk working on this myself and to my surprise I managed to make things work!  In case someone comes looking for help on this issue here is what I did:

1. Downloaded updated printer drivers from here: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)
2. Since the original post I used to help me get this working for 12.04 mentioned a ppa that has changed I went to the new version of the michael-gruz ppa and added the canon-stable repo ([https://launchpad.net/~michael-gruz/](https://launchpad.net/~michael-gruz/)).  (On that PPA there is also a repo for ia32-libs.  I tried to add it but it never updated with the next step. Things worked out anyway.)
```
sudo add-apt-repository ppa:michael-gruz/canon-stable
```
3. Did apt-get update.
```
sudo apt-get update
```
4. Installed cndrvcups-common from the repo.
```
sudo apt-get install cndrvcups-common
```
5. The repo doesn't have cndrvcups-capt so installed that from the downloaded drivers from support-asia.canon-asia.com site.(in the 32-bit drivers/Debian directory after you unzip the file).
6. Went to the excellent tutorial ([http://ubuntuforums.org/showthread.php?t=1983091](http://ubuntuforums.org/showthread.php?t=1983091)) and started from step #1 (i.e. skipped the pre-#1 step where you purge the drivers we just worked so hard to install!).

Everything is working great now!  Hope this helps someone else.

thomas

---

