---
title: "Startup Warning"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by SteveF on 2005-05-19
When Ubuntu boots up, I get the following error:

/etc/init.d/als: Warning: 'alsactl restore' failed with error message 'alsactl:set_control:930:warning:name mismatch (External Amplifier/EMU10K1 PCM Send Routing) for control #75
alsactl:set_control:1025:bad control_75.value type'

I got the message by pressing CTRL-ALT-F1 and luckily it was still on screen.

Two questions:

1) What does the error mean and how do I fix it?
2) How do I see all of the messages displayed on screen during bootup (what file is it in)?

Thanks for any help,

Steve

---

### Post by Xian on 2005-05-19
[QUOTE=SteveF]When Ubuntu boots up, I get the following error:

/etc/init.d/als: Warning: 'alsactl restore' failed with error message 'alsactl:set_control:930:warning:name mismatch (External Amplifier/EMU10K1 PCM Send Routing) for control #75
alsactl:set_control:1025:bad control_75.value type'
[/QUOTE]
A quick solution might be to open a terminal and save your alsa settings:
```
$ sudo alsactl store
```

---

### Post by SteveF on 2005-05-19
Thanks for the suggestion but it didn't work.  I still get the error message.

---

