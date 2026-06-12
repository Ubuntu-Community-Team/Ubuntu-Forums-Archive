---
title: "inputlirc no longer works in karmic"
date: 2010-02-18
forum: Hardware
---

### Post by DefineByte on 2010-02-18
Since upgrading to Ubuntu 9.10 (64bit) my remote control no longer works. It's a Speedlink 6399 (shows up as a HOLTEK YaoCoo in Linux), which is basically a cheap USB HID keyboard/mouse masquerading as an MCE remote.

I can get it working with lirc on its own (after making a change to /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi) but, since it sends multiple commands for a lot of the buttons, it means some of them aren't usable. To get around this in jaunty (and previous releases) I used inputlirc, which has a handy feature of combining these multiple commands - e.g. Ctrl+Shift+P became Ctrl_Shift_P.

With karmic, no matter what I do, I can't get inputlirc working. inputlirc is supposed to work without needing to configure lirc first but if I don't set up lirc in karmic in *some* way lirc refuses to run (I don't recall this being a problem before). If I configure lirc (I set it up to use /dev/input/) no output from the remote is detected with irw. As soon as I remove inputlirc irw shows a response but I'm back to the multiple keys issue.

Has anyone got inputlirc working under 9.10? Care to share how? :)

---

### Post by DefineByte on 2010-02-20
Just tried the remote on a different PC. This has a fresh install of Ubuntu 9.10 and I still can't get inputlirc to work so it's either broken or I'm doing something wrong. Just wish I knew which.

---

### Post by DefineByte on 2010-02-23
To answer my own question, the reason it doesn't work any more is because inputlirc defaults to using /dev/lircd, but as of lirc 0.8.6-0ubuntu1 the Unix socket has been moved from /dev/lircd to /var/run/lirc/lircd.

The [change log](http://changelogs.ubuntu.com/changelogs/pool/main/l/lirc/lirc_0.8.6-0ubuntu1/changelog) states that LIRC has been altered to make a symlink at /dev/lircd to point to /var/run/lirc/lircd, which "makes all clients happy". This *does* happen (as long as you configure lirc), but for some reason inputlirc still doesn't work. Maybe inputlirc is looking for /dev/lircd before it's created. I shall refrain from delving further to protect my sanity. :D

The fix is to edit /etc/default/inputlirc to point to the new socket location, using the -d parameter. Here's my now working config:
```

# Options to be passed to inputlirc.
EVENTS="/dev/input/by-id/usb-HOLTEK_YaoCoo-event-*"
OPTIONS="-m0 -g -c -d/var/run/lirc/lircd"

```

If it still doesn't work just ```
sudo dpkg-reconfigure lirc
``` set it to use the Linux input layer and /dev/lirc0 then ```
sudo /etc/init.d/inputlirc restart
```

---

### Post by rileyp on 2010-05-19
Hi 
Great post thanks very much!
I find my receiver responds so well now that I so much as bump a button and the menus jump a miniimum of 3 places in mythtv
Is there way to filter out some of the repeated inputs. changing the repeat and delay in the lirccrc seems to nothing. 
I found this code here for a buetooth key board ...
Could I just edit this for my input device (usb-HOLTEK_PC_receiver-event-kbd)
```
#change key repeat rate
cd /sys/class/input
for dev in input* ; do
        if [ "$(cat $dev/name)" = "SerKBD" ] ; then
                cd $dev
                for ev in event* ; do
                        cp -a /dev/input/$ev /tmp/$$-$ev
                        #this works because /tmp is shared with initfs
                        chroot /mnt/initfs evrepeat /tmp/$$-$ev
$KEYREPEAT_DELAY $KEYREPEAT_PERIOD
                        rm /tmp/$$-$ev
                done
        fi
done
```  I found this code linked to here [http://fanoush.wz.cz/maemo/](http://fanoush.wz.cz/maemo/)
cheers rileyp

---

### Post by DefineByte on 2010-05-20
Honestly, I don't know. The repeat setting doesn't work for me either but it's not something I've looked into.

You could also try playing with the "-r" option in /etc/default/inputlirc. It sets the repeat rate in milliseconds (defaults to 0).

---

