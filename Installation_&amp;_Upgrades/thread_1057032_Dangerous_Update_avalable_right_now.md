---
title: "Dangerous Update avalable right now"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-02-01
My ubuntu was working fine few minutes ago, untill I was prompt the update sign on my screen, when I install it I can not get into ubuntu it only show the ubuntu wall paper, also write that gnome power has not been installed, and maybe more error mesage.
Any suggestion ? I don't want to reinstall ubuntu.

---

### Post by Pumalite on 2009-02-01
Bot into Recovery Mode, drop to a Shell and do:
```
apt-get -f install
apt-get update
apt-get dist-upgrade
reboot now
```

---

### Post by forumtalker on 2009-02-02
Hi
I'm suffering the same problem with the update -  just wallpaper and nowhere to go.  

My problem is that I'm completely new, installed Ubuntu for the first time yesterday from a disk on the cover of the Computeractive guide for beginners, ran the massive 245MB of updates and got locked out.  Being new I don't have a handle on terms like shell but when I rebooted did see an option that mentioned shell so I chose that one and got what I suppose is the equivalent of a dos line.

I tried to follow the advice -
apt-get -f install
apt-get update
apt-get dist-upgrade
reboot now
but when I pressed return it took each line to be a command.  I assume somewhere I should be able to type in all 4 lines together and press enter??

It's disappointing to have hit a problem so soon when I have so little knowledge about Linux - any advice would be appreciated. 
Thanks

---

### Post by hoboy on 2009-02-02
> **forumtalker said:**
> Hi
I'm suffering the same problem with the update -  just wallpaper and nowhere to go.  

My problem is that I'm completely new, installed Ubuntu for the first time yesterday from a disk on the cover of the Computeractive guide for beginners, ran the massive 245MB of updates and got locked out.  Being new I don't have a handle on terms like shell but when I rebooted did see an option that mentioned shell so I chose that one and got what I suppose is the equivalent of a dos line.

I tried to follow the advice -
apt-get -f install
apt-get update
apt-get dist-upgrade
reboot now
but when I pressed return it took each line to be a command.  I assume somewhere I should be able to type in all 4 lines together and press enter??

It's disappointing to have hit a problem so soon when I have so little knowledge about Linux - any advice would be appreciated. 
Thanks

I have reinstalled ubuntu from scratch.

---

### Post by jollyc on 2009-02-02
> **forumtalker said:**
> Hi
apt-get -f install
apt-get update
apt-get dist-upgrade
reboot now
but when I pressed return it took each line to be a command.  I assume somewhere I should be able to type in all 4 lines together and press enter??


No you'll want to try

```
sudo apt-get -f install
```
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
```
sudo reboot now
```

You will be prompted for a password when you try the first line. This will be the password you use to login with.

You need to do each on it's own, not all in one go, while you could do that, doing it one line at a time would be easier if you're starting out.

---

### Post by forumtalker on 2009-02-02
Hi - I wondered about a re-install but this cd wants to set up a new partition each time.  Thanks jollyc for the advise o
n entering the code, but how do I get the code entry screen? regards

---

### Post by forumtalker on 2009-02-03
I thought what the hell it won't break and eventually got a command line using alt and the numerals, so I guess that's how it's done?

I input the code complete with the 'sudo', it said certain headers weren't needed and could be deleted.  Followed through but on reboot still just the wallpaper.  Perhaps I'll have to reinstall too, but as I said this cd wants to create a new partition every time so you end up with multiple versions.  Is there an uninstall feature or a way of rolling back like you can in XP?

How do you install into an existing partition?
Regards

---

### Post by battleshipbadger on 2009-02-03
I'm having a similar problem. After the 49 item update last Thursday or Friday, it told me to do an autoremove. I did and lost my sound card and Dvd drive. Have been unsuccessful in reinstalling from flashdrive. v/r

---

### Post by forumtalker on 2009-02-03
This update has claimed another victim -
[http://ubuntuforums.org/showthread.php?t=1058851](http://ubuntuforums.org/showthread.php?t=1058851)

---

