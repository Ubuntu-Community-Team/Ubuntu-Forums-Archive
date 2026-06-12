---
title: "How to execute &quot;sudo source&quot;"
date: 2008-10-30
forum: General Help
---

### Post by Shwick2 on 2008-10-30
Ubuntu 8.04

I have an install script that sets some environment variables.  To run the script I have to use the source command.

The script has to be run as sudo because the environment variables need to be set for the root account.

The problem is you can't execute "sudo source installScript".  How do I execute "source installScript" as sudo, or root user?

I already tried "sudo /bin/bash ./installScript".

This post is related to [http://ubuntuforums.org/showthread.php?t=962993](http://ubuntuforums.org/showthread.php?t=962993).

---

### Post by kk0sse54 on 2008-10-30
Is it a shell script because then ```
sudo sh ./<filename>.sh
``` should work otherwise you can make files executable through chmod +x command and then a simple ./<filename> would usually start it.

---

### Post by unutbu on 2008-10-30
Perhaps try
```
sudo ./vars
```
If that does not work, please post the output of
```

head -n10 vars
```

---

### Post by Shwick2 on 2008-10-30
Thanks but none of those commands execute the script properly because I don't see the environment variables after a "sudo env".

output of "head -n10 vars":

```

# easy-rsa parameter settings

# NOTE: If you installed from an RPM,
# don't edit this file in place in
# /usr/share/openvpn/easy-rsa --
# instead, you should copy the whole
# easy-rsa directory to another location
# (such as /etc/openvpn) so that your
# edits will not be wiped out by a future
# OpenVPN package upgrade.

```

I tried,
sudo ./vars
sudo sh vars
sudo sh ./vars
sudo sh ./vars.sh

---

### Post by unutbu on 2008-10-30
Okay, how about this:
```

sudo -i    # This gives you a root shell with root's environment variables set
source ./vars
```

---

### Post by Tichondrius on 2008-10-30
do "sudo -s" to get a root shell, then run "source ...." and whatever else you want.
You need to realize that whatever env variables you set up is only going to be active while your root shell is running.

---

### Post by Tichondrius on 2008-10-30
btw you can also do

su -c "bash installScript"

---

### Post by Shwick2 on 2008-10-31
I used "sudo -s" to enter root shell, then entered "source installScript" and it worked.

As you said the environment variables only persist as long as the root shell is open.  As soon as I exit the root shell back to priveleged user, I issue "sudo env" and the environment variables aren't set anymore.

This is ok as I can just run all the install scripts from the root shell.

Thanks greatly appreciated.

---

