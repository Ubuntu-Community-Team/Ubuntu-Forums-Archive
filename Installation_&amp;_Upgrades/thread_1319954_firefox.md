---
title: "firefox"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by 824957q on 2009-11-08
would anyone know how to install firefox on kubuntu 9.4 when i try to run it or install it it says save a or open with ark can someone tell me how to do this

---

### Post by dvlchd3 on 2009-11-08
Can you install from the commandline?

```

sudo apt-get update
sudo apt-get install firefox

```

Sometimes Synaptics doesn't play well, this just may be one of those times.  (On the other hand, I've had to use Synaptics sometimes because apt-get and aptitude don't work right...o the odd things I'm finding hilarious right now...)

---

### Post by 824957q on 2009-11-08
man no i can't do that cause im having a problem with my computer cause my usernaame is unknown to sudo and i can't install anything can you help me with this?

---

### Post by GO%)$@*1 on 2009-11-08
I don't have much experience with kubuntu but maybe you could add your username to the sudoers file? Someone help  me out please, I don't know much about it.

---

### Post by 824957q on 2009-11-08
how do i do that

---

### Post by dvlchd3 on 2009-11-09
There is no way to install firefox globally without sudo rights.  You may be able to download firefox from Mozilla's site and try installing it that way.  If it is successful, only your user account will be able to use it.

As for restoring the sudoer rights, you have to boot into recovery mode:
Once you have the shell prompt do the following:

```

useradd -G admin [your_username]
shutdown -r now

```

This will add your user to the "admin" group which is the default sudoers group in Ubuntu.

---

