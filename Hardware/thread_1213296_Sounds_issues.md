---
title: "Sounds issues"
date: 2009-07-14
forum: Hardware
---

### Post by crownedzero on 2009-07-14
So I'm giving dual booting a shot and I've run into a soundcard issue.
I'm a noob with Ubuntu but the threads I have been able to comprehend haven't been able to solve my audio problem.

Here is what I know:
Under my user profile the "Use audio devices" is not checked and greyed out.

I managed to determine(at least I think I did)that my sound card is detected.
```
crownedzero@crownedzero:~$ lspci | grep audio
03:03.0 Multimedia audio controller: Creative Labs SB X-Fi

```

I also attempted to install alsa drivers for said card(I use the term attempted very loosely.)

When I attempt to open the "Volume Control Panel" I receive "No volume control GStreamer plugins and/or devices found."

I am Ubuntu 9.04 patched and updated.

Any suggestions?

---

