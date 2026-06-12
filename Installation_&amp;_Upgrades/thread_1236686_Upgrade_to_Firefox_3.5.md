---
title: "Upgrade to Firefox 3.5"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by jrsc109 on 2009-08-10
Hi

I just ran sudo apt-get install firefox-3.5

All ran OK - but when I check the 'About Mozilla Firefox' link, it still says Firefox 3.0.8

Can someone please explain.  And is there anything I need to do now to get 3.5

Thanks

---

### Post by phillw on 2009-08-10
Hi.... This thread has the details

[http://ubuntuforums.org/showthread.php?t=1216114&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1216114&highlight=phillw)

Regards,

Phill.

---

### Post by p2bc on 2009-08-10
Well what I like to do is do a clean install from major update. I am also assuming you are like me you like to keep your existing settings.

So first back up you original Firefox setting/profile
```

<user>@<computer>:cp -R ~/.mozilla ~/mozilla_backup

```
All this is just in case, for a "Oh crap" moment, likehood it won't be a problem. Please note that the "." has been remove from the beginning of the mozilla_backup which will make it visible in your file manager.

Next remove Firefox
```

sudo apt-get remove firefox
sudo apt-get autoclean
sudo apt-get install firefox-3.5

```

Now you should be sure there is no redundant files left, and are running proper version of Firefox. With the ~/.mozilla folder still in place you should be good to go with your settings. If Firefox creates a new profile for the new installation, simple copy you old profile into the ~/.mozilla folder like so:
```

ls -la ~/mozilla-backup/firefox/
cp -R ~/mozilla-backup/firefox/<sequence of letters number>.default ~/.mozilla/firefox/

```

Then follow the instruction from [http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager) as to how to set that new profile (<sequence of letters number>.default) as you default profile from the profile manager.


Hope that helps.

---

