---
title: "preload (it might not work and You do not know it)"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by zika on 2009-01-04
today I've checked (for some strange reason) how the preload was working its job. there are three files that You might be interested:```
/etc/preload.conf
/var/lib/preload/preload.state
/var/log/preload.log
```a simple > cat /var/log/preload.log revealed that preload was just enter/exit-ing for some time due to an error that occurred in some of its writings to the file **/var/lib/preload/preload.state**. I've tried to edit that file but there were too many errors so I've just deleted it and now preload is gathering its information again and, (I hope) happily returning on duty.

excerpt from /var/log/preload.log at the point where (after not working) he got back on duty:```
[Sun Jan  4 15:28:47 2009] Exiting
[Sun Jan  4 15:31:42 2009] loading conf from /etc/preload.conf
[Sun Jan  4 15:31:42 2009] loading state from /var/lib/preload/preload.state
[Sun Jan  4 15:31:42 2009] failed reading state from /var/lib/preload/preload.state: line 45749: invalid tag
[Sun Jan  4 15:31:42 2009] Exiting
[Sun Jan  4 15:33:25 2009] loading conf from /etc/preload.conf
[Sun Jan  4 15:33:25 2009] loading state from /var/lib/preload/preload.state
[Sun Jan  4 15:33:25 2009] failed reading state from /var/lib/preload/preload.state: line 45762: invalid syntax
[Sun Jan  4 15:33:25 2009] Exiting
[Sun Jan  4 15:34:44 2009] loading conf from /etc/preload.conf
[Sun Jan  4 15:34:44 2009] loading state from /var/lib/preload/preload.state
[Sun Jan  4 15:34:44 2009] cannot open /var/lib/preload/preload.state for reading, ignoring: No such file or directory
[Sun Jan  4 15:34:44 2009] 1812330kb available for preloading, using 0kb of it
[Sun Jan  4 15:35:05 2009] 1822100kb available for preloading, using 0kb of it
[Sun Jan  4 15:35:25 2009] 1961300kb available for preloading, using 0kb of it
[Sun Jan  4 15:35:46 2009] 1923330kb available for preloading, using 0kb of it
[Sun Jan  4 15:36:07 2009] 1923030kb available for preloading, using 0kb of it
[Sun Jan  4 15:36:27 2009] 1923030kb available for preloading, using 0kb of it
[Sun Jan  4 15:36:48 2009] 1891800kb available for preloading, using 0kb of it
[Sun Jan  4 15:37:08 2009] 1881300kb available for preloading, using 0kb of it
[Sun Jan  4 15:37:29 2009] 1890650kb available for preloading, using 0kb of it
[Sun Jan  4 15:37:49 2009] 1884350kb available for preloading, using 4264kb of it

```then I rebooted and looked in that file again:```
[Sun Jan  4 16:07:54 2009] readaheading 72 files
[Sun Jan  4 16:07:59 2009] 1702790kb available for preloading, using 69068kb of it
[Sun Jan  4 16:07:59 2009] readaheading 65 files
[Sun Jan  4 16:08:13 2009] exit requested
[Sun Jan  4 16:08:13 2009] saving state to /var/lib/preload/preload.state
[Sun Jan  4 16:08:13 2009] exit requested
[Sun Jan  4 16:08:13 2009] saving state to /var/lib/preload/preload.state
[Sun Jan  4 16:08:13 2009] failed to rename /var/lib/preload/preload.state.tmp to /var/lib/preload/preload.state
[Sun Jan  4 16:09:05 2009] loading conf from /etc/preload.conf
[Sun Jan  4 16:09:05 2009] loading state from /var/lib/preload/preload.state
[Sun Jan  4 16:09:05 2009] failed reading state from /var/lib/preload/preload.state: line 12675: invalid tag
[Sun Jan  4 16:09:05 2009] Exiting
[Sun Jan  4 16:11:51 2009] loading conf from /etc/preload.conf
[Sun Jan  4 16:11:51 2009] loading state from /var/lib/preload/preload.state
[Sun Jan  4 16:11:51 2009] failed reading state from /var/lib/preload/preload.state: line 12675: invalid tag
[Sun Jan  4 16:11:51 2009] Exiting

```so, there is a problem with preload. I'll uninstall it for now (even though I'm not a uninstall gyu, I prefer to fix things) since I do not know how to help him. I've tried reinstall but it did not help. any hint would be welcomed but this is not a big issue ...

UPDATE: I've downloaded [http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/preload_0.6.3-0~0uninea1_amd64.deb]("http://ppa.launchpad.net/uninea/ubuntu/pool/main/p/preload/preload_0.6.3-0%7E0uninea1_amd64.deb") and installed it. will see.

---

### Post by flapane on 2009-02-23
any news?
I compiled myself 0.6.3 on hardy and i am testing it before i upload it on my sign repository.

sudo preload -V 10 -s /usr/local/var/lib/preload/preload.state -l /usr/local/var/log/preload.log


I am in doubte because of **0kb available for preloading**
```
 sudo tail -f /usr/local/var/log/preload.log
[Mon Feb 23 19:39:20 2009] state predicting begin
ln(prob(~EXE)) =        -0.0186576485   /usr/bin/tail
ln(prob(~EXE)) =        -0.0144734016   /usr/bin/wget
ln(prob(~EXE)) =        -0.0106433800   /usr/bin/apt-get
ln(prob(~EXE)) =        -0.0198437789   /usr/bin/aptitude
[Mon Feb 23 19:39:20 2009] 0kb available for preloading, using 0kb of it
[Mon Feb 23 19:39:20 2009] nothing to readahead
[Mon Feb 23 19:39:20 2009] state predicting end
[Mon Feb 23 19:39:30 2009] state updating begin
[Mon Feb 23 19:39:30 2009] state updating end
[Mon Feb 23 19:39:41 2009] state scanning begin
[Mon Feb 23 19:39:41 2009] state log dump requested
persistent state stats:
preload time = 2000
num exes = 18
num bad exes = 3
num maps = 605
runtime state stats:
num running exes = 15
[Mon Feb 23 19:39:41 2009] state log dump done
[Mon Feb 23 19:39:41 2009] state scanning end
[Mon Feb 23 19:39:41 2009] state predicting begin
ln(prob(~EXE)) =        -0.0143054348   /usr/bin/wget
ln(prob(~EXE)) =        -0.0106075780   /usr/bin/apt-get
ln(prob(~EXE)) =        -0.0196415696   /usr/bin/aptitude
[Mon Feb 23 19:39:41 2009] 0kb available for preloading, using 0kb of it
[Mon Feb 23 19:39:41 2009] nothing to readahead
[Mon Feb 23 19:39:41 2009] state predicting end

```

sudo less /usr/local/var/lib/preload/preload.state
/usr/local/var/lib/preload/preload.state: Nessun file o directory

---

### Post by zika on 2009-02-23
the .deb package I've mentioned earlier installed OK (on Intrepid). new version of preload worked just fine. I've uninstalled it because I needed auto-log-on to work. with preload it was impossible to get it to work. I've managed to get much more speed gain from some other methods I've came up, tmpfs and making FF to cache on /tmp that is mounted on tmpfs, for example, some tweaking of FF's parameters so the gain from preload was much smaller than the loss of auto-log-on (for me).

---

### Post by flapane on 2009-02-23
I had autologon on kde with 0.4 version and it worked

---

### Post by zika on 2009-02-23
> **flapane said:**
> I had autologon on kde with 0.4 version and it worked
I'm on gnome ... ;)

---

### Post by flapane on 2009-02-24
You know, it seems that this version can't be started with autologin on kde too.
Have we found a bug?

---

### Post by zika on 2009-02-24
> **flapane said:**
> You know, it seems that this version can't be started with autologin on kde too.
Have we found a bug?
yes, I'm telling that for couple of months but I'm not affected with it any longer ... ;)

---

