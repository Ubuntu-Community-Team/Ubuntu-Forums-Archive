---
title: "ALSA Drivers Producing Scratchy Sound after External Sound Card"
date: 2008-11-25
forum: Hardware
---

### Post by echo777 on 2008-11-25
A day ago I tried a new USB External Sound Card. It worked fine as I played around with System > Preferences > Sound. However, upon reboot and removing the card, all of my sound comes out as a strange scratchy sound.

I thought I had solved the problem when I set all of the sound drop downs to OOS, since that was working as opposed to ALSA. However, certain programs still have the scratchy sound. The 'Autodetect' setting is scratchy.

I am running Ubuntu 8.10.

lspci | grep -i audio
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

I followed, [Comprehensive Sound Problem Solution Guide]("http://ubuntuforums.org/showthread.php?t=205449") and reinstalled ALSA with no luck. I am just aggravated that everything was working fine with Ubuntu until I tried out that external sound card.

Any ideas?

---

