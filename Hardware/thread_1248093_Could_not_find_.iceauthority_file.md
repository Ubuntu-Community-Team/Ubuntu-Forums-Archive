---
title: "Could not find .iceauthority file"
date: 2009-08-23
forum: Hardware
---

### Post by JoshStrobl on 2009-08-23
Help!
Ok, so I tried opening firefox, it wouldn't open saying (kill and open another window or something like that). that was after I restarted my firefox and it wouldn't pull up.
so I went in and couldn't find Firefox at all in my system monitor showing it even up.
so, i restarted my computer and logged on. it gave me a black screen for a few seconds and then it pulled up "Could not update ICEauthority /home/joshstrobl". i clicked ok, it still logged me on and when I tried to pull up firefox it still said that a window was still up, same with Skype! what the! i checked monitor and again, neither were up. I then shut my computer down, pulled out the battery, unplugged the ac, put it back in, turned it on, booted, same .iceauthority thing pulled up and still can't pull up skype or firefox.

I ended up downloading Arora web browser in order to even access the internet.

help me.

---

### Post by aysiu on 2009-08-24
You can't see it, because the .ICEauthority file is a hidden file (in the file browser, hit Control-H to see hidden files).

Pasting this command in [the terminal](http://www.psychocats.net/ubuntu/terminal) may help: ```
sudo chown -R joshstrobl:joshstrobl /home/joshstrobl
```

---

### Post by JoshStrobl on 2009-08-24
yea I already did all that stuff. It wouldn't fix so I just backup my files and reinstalled Ubuntu

---

