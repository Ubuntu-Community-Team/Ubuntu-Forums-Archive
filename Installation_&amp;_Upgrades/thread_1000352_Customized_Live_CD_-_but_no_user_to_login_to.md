---
title: "Customized Live CD - but no user to login to?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Linz on 2008-12-02
I was following this guide: [HTML]http://ubuntuforums.org/showthread.php?t=688872[/HTML] to make a livecd from my ubuntu 8.10 installation that I have customized, inside VirtualBox.

I followed the steps to include my personal settings from my home directory, by going:
```
CONFIG='.asu .cache .config .gconf .gconfd .gnome2 .gnome2_private .local .mozilla .themes .thumbnails .wine .winetrickscache .bashrc'
cd ~ && for i in $CONFIG
do
sudo cp -rpv --parents $i ${WORK}/rootfs/etc/skel
done
```

When I insert my livecd dvd into a computer and boot off it, I select the first option of starting a graphical interface, then it boots up off the DVD and I'm presented with the graphical login screen. I tried various username/password combinations to no avail. (My original credendials on the system were "elbuntu" "elbuntu", I tried "ubuntu" "ubuntu", "ubuntu" "", "elbuntu" "", none worked.)

I did execute the code to remove non-system users.
```
for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "999" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done
```

How to I fix this up so I can have a user to login to, with all my custom home directory settings? Is it because of that last bit of code?

Thanks in advance.

---

