---
title: "Customise Guest Session"
date: 2008-10-26
forum: General Help
---

### Post by philliptweedie on 2008-10-26
Apologies if this has been asked before, but is there a way to customise the Guest account in terms of appearance, wallpaper, firefox plugins etc.

---

### Post by defaulk on 2008-11-01
I'd also like to know.  This needs a bump.

---

### Post by mcduck on 2008-11-06
I bump this one too.

Usually new users settings can be configured by dropping the configuration files into /etc/skel, but this doesn't seem to work with the guest session. I've been trying to search for information about this but can't seem to find anything. :/

Although I found the script that is used to start the guest session, in /usr/share/gdm/guest-session/guestsession-setup.sh, and there seems to be some gconftol commands in the end of the script. It could be possible to just add there your own commands to change the gconf settings and copy other setting files to the guest user's newly-created home dir. I'm just hoping that there would be some better way to configure the guest session..

---

### Post by RedG on 2008-11-09
Obviosly I'm not alone!
I bump this one too.

---

### Post by jis on 2008-11-10
I think higher priority problems are that you can not start a guest session in GDM or in Xubuntu.

---

### Post by Jardiland on 2008-11-12
Hi,

I have encountered this question in a french forum and submited a patch that make the guest session script use the /etc/skel directory.

There are just 2 lines to add/modify in the /usr/share/gdm/guest-session/guest-session-setup.sh file.

Here is the bug on launchpad (with the modfied file) :
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/296993](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/296993)

Here is the french forum thread for the same question :
[http://forum.ubuntu-fr.org/viewtopic.php?id=266881](http://forum.ubuntu-fr.org/viewtopic.php?id=266881)

---

### Post by RedG on 2008-11-12
Thanks!
Now I only have to learn how to use the /etc/skel dir.
But that I think is a minor problem... :)

---

### Post by PoolSnoopy on 2008-12-01
maybe it's because I messed something up, but your patch seems not to work with hidden files.
I wanted to have a custom .bashrc for the guest account, but cp won't copy that. So I came up with this - not perfect either - solution:

for MYFILE in `find /etc/skel.guest/ -name '.*'` ; do cp -r $MYFILE "$HOME" ; done
chown -R $USER:$USER "$HOME"

as you can see I use /etc/skel.guest. Moreover I do a recursive chown afterwards.

If you patch the script this way, then there is an easy way to get your guest session set up, just the way you want it:

1.) start a guest session and customize it to your needs
2.) switch to your normal user
3.) look for a guest-home.?????? folder in /tmp
4.) sudo for MYFILE in `find /tmp/<this guest-home-folder> -name '.*'` ; do cp -r $MYFILE /etc/skel.guest/ ; done
5.) sudo passwd guest
6.) give the guest user a new password so that you can switch back to his session and terminate it properly
7.) switch user to guest with the new password
8.) log out off the guest session

the next time you start a guest session it should use all the settings you customised before step 4.)

---

### Post by Jardiland on 2009-01-03
Thanks PoolSnoopy, and sorry for not showing up more quickly.

You are right, my first patch didn't work with hidden files (which is a pain because all config files ARE hidden).

But I am affraid that your solution will *ONLY* copy hidden files. I have proposed an other solution : replace de cp line with :

```
cp -rT /etc/skel/ "$HOME" 
```

---

