---
title: "GNOME 3 on Toshiba Satellite M40-152 S4"
date: 2011-04-28
forum: Hardware
---

### Post by Fightback on 2011-04-28
Hi guys.

This issue might be related with that one ([Link]("http://ubuntuforums.org/showthread.php?t=1740815")). Please read that thread.
I have upgraded from ubuntu 10.10 to 11.04. It worked. No issues during upgrade. Upon rebooting I realized that unity doesn't work for me, but that's not that bad, I just chose Ubuntu Classic (or something like that) and it worked.
Then I read about GNOME 3 and I wanted to try it out. So I followed these [instructions ]("http://blog.sudobits.com/2011/04/26/how-to-install-gnome-3-on-ubuntu-11-04/")on how to install GNOME 3 on ubuntu 11.04, which, btw, are identical with these [instructions]("http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml"). Anyway, I rebooted and chose Ubuntu Gnome Shell Desktop from the dropdown menu. It boooted, and the only thing I got to see is a black screen and my mouse. I have to hard reboot to get back to somewhere where I can do something.
I tried to boot the other options, ubuntu and ubuntu classic. Instant error: Unable to load session 'ubuntu' (or 'classic-gnome' respectively) or a black screen with only my mouse.
I can boot into the recovery console. From there I tried
```
sudo apt-get install ppa-purge
```So that I can continue with ```
sudo ppa-purge ppa:gnome3-team/gnome3
```However, I don't have an internet connection in the console. Now, this was with wireless. I shall check a wired connection later on, and post results.
Is there any way that I can get internet access through the recovery console and then ppa-purge GNOME 3 away (which is the uninstall process suggested [here]("http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml") (scroll down to the comments))?
I hope you can help me.
~Fightback

---

