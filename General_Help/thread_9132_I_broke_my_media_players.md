---
title: "I broke my media players?"
date: 2004-12-24
forum: General Help
---

### Post by snipes420 on 2004-12-24
im not sure what caused this but xmms no longer works. it worked earlier yesterday and the only thing i can think of that might have done it is I tried to compile meta-input(plugin for xmms) and it gave me a bunch of errors. the first one being it couldn't find xmms-config(bad command or filename or something)
I tried to run some questionable mp3's this morning but I dont think that could fark it up that bad. So I tried to run xmms from the command line and it just hangs. if i run it with the -v argument it will return the version and quit like it should. hmmm

wll i figured i could live without xmms so I tried to install beep-media-player. It doesnt work either. I guess it uses some or most of the same librarys or something, it being a fork of xmms and all. 

I miss listening to my music from my other ubuntu machine. it has gnump3 set up on it and i dont have another program to play m3u files over the network.

any ideas ubuntu gods? :roll:

---

### Post by LongTooth on 2004-12-25
Despite years of Linux experience I still can't get my brain wrapped around tarballs. I stay away from them as much as I can. The problem I have with them is when they don't work I don't know how to get completed rid of them or how to correct the problem. I'm marking the as my next to-do project - Tarballs: They are your friends. 

Whenever I have a problem like this one I try to uninstall and reinstall the offending program. Try that. If that doen't work try it with Xmms. Sudo apt-get remove xmms followed by sudo apt-get install xmms. That's the nice thing about a Debian based distro. Easy install/unstall. Might save you much gnash of teeth.

---

### Post by snipes420 on 2004-12-25
I ended up going to #linux on freenode IRC and there was some helpful people in there. I had reinstalled xmms using the method you described in the previous post and still had no luck. one of the people on IRC recommended deleting my xmms setting directory and that sounded like a good idea. it worked after I did this.

```
rm -rf ~/.xmms/
sudo killall xmms
xmms
```

---

### Post by LongTooth on 2004-12-29
Well lo and behold. On a brand new PC I recently built, I messed up my Xmms . I deleted it and started from scratch using apt-remove and reinstalled with apt-get install all to no avail. I apt-remove Xmms once again and still have the /usr/bin/xmms directory. I used the the CLI command sudo rm -r /usr/bin/xmms to completely remove it. Verified that it is gone and did a fresh apt-get install and still no go. With a 'whereis xmms' I get this:

longtooth@ubuntu:~ $ whereis xmms
xmms: /usr/bin/xmms /usr/lib/xmms /usr/share/xmms /usr/share/man/man1/xmms.1.gz


But when I try to launch Xmms as a user or sudo, I get this error message:

longtooth@ubuntu:/usr/bin $ /usr/bin/xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!


I sudo cd usr/bin file, do a ls command, and I do see xmms listed. However even from here I can't cd into xmms. So what is my next step? Don't know where to go from here. Help anyone?  Thanks.

---

### Post by LongTooth on 2005-01-01
Any body have some tips for me?

---

### Post by Rancoras on 2005-01-02
Check and make sure libmikmod2 is installed.

---

### Post by LongTooth on 2005-01-02
Hot Damn! That did it. Simple as pie. Of course it help that someone pointed me in the right direction. For those not in the know, here's what I did. Since it didn't work I made certain Xmms was completed off my system. I did this with this command 'sudo apt-get remove --purge xmms'. I reinstalled Xmms as well as libmikmod2 using the sudo apt-get install...command. Now all is well in the world. Thanks Rancoras.

---

