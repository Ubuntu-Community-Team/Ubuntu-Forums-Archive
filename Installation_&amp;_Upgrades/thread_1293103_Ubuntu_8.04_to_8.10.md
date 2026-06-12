---
title: "Ubuntu 8.04 to 8.10"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by FrontalNoize on 2009-10-16
I have installed all updates through the update manager, but somehow I don't get the option to upgrade to 8.10.  
Is this a small bug?  Or could it be something specific about my system/laptop?  And is there a way to circumvent it, by upgrading manually through the terminal or something for example?

---

### Post by utnubuuser on 2009-10-17
link> [http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server]("http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server")

> sudo apt-get dist-upgrade

---

### Post by wojox on 2009-10-17
```
sudo apt-get update
```

```
sudo update-manager -d
```

---

### Post by slakkie on 2009-10-17
> **FrontalNoize said:**
> I have installed all updates through the update manager, but somehow I don't get the option to upgrade to 8.10.  
Is this a small bug?  Or could it be something specific about my system/laptop?  And is there a way to circumvent it, by upgrading manually through the terminal or something for example?

cat /etc/update-manager/upgrade-releases

Then you should see Prompt=normal, otherwise you will only be able to upgrade to 10.04 which is the next lts (assuming Prompt=lts) or you will never upgrade, Prompt=none.

---

### Post by stlsaint on 2009-10-17
@slakkie nice help but you got the last two words switched :D
> cat /etc/update-manager/upgrade-releases
 
slight change to that...
correct cmd is:

```
cat /etc/update-manager/release-upgrades
```

---

### Post by slakkie on 2009-10-17
> **stlsaint said:**
> @slakkie nice help but you got the last two words switched :D

 
slight change to that...
correct cmd is:

```
cat /etc/update-manager/release-upgrades
```

Oops :) Not running Ubuntu atm so couldn't check. I always make a mistake when looking for that file...

---

