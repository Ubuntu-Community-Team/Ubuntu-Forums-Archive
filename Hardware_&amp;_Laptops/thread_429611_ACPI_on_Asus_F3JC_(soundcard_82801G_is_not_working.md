---
title: "ACPI on Asus F3JC (soundcard 82801G is not working)"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by jermen on 2007-05-01
Hi all,

I have new and fresh installation of Feisty on my Asus F3JC and I have following problems not reported in 6.04 / 6.10:

After hybernation there is no way how to get my sound working. Soundcard is present, all channels unmuted, but no sound.

When I try to suspend, problem is the same. I've tried new Alsa 1.0.14rc3 (compiled from sources), but without any results (now I'm using this drivers).

When I run /etc/init.d/alsasound restart **two times** after resume from suspend, I can hear all sounds and music again.

So I prepared this stupid and ugly workaround in **/etc/acpi/resume.d/99-asus-sound.sh**:
```
/etc/init.d/alsasound restart
/etc/init.d/alsasound restart
alsactl restore 0
```

I also modified **/etc/asound.state** to contain following:
```
state.Intel {
        control.1 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Master Playback Switch'
                value.0 true
                value.1 true
        }

...etc.etc.etc.
```

Now my soundcard is working when I resume from suspend, but there is still no sound after hybernation even if I try to run "/etc/init.d/alsasound restart" X times.

Of course, when I resume, all applications using soundcard crash immediately (applet for volume and Listen (music player)).
 
I'm probably not the only one: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/104712](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/104712).

Please, do you have any ideas?

Thanks a lot for your time.

---

