---
title: "Startup Script"
date: 2008-07-23
forum: General Help
---

### Post by lyric0n on 2008-07-23
Hello,

I need to write a script which will run on startup and I am not sure how to do this. The script ultimately will dump the results of an ifconfig into a file and post it into a mounted folder. But I do not know where I should put something like this so that it will run on boot?

Thanks,
Chris

---

### Post by PGScooter on 2008-07-23
Hi lyric0n, there should be a place under settings called "autostarted applications"

For Xubuntu, its under "settings". Then just click on "add" and add your script.

Your script should then appear in $HOME/.config/autostart directory

Good luck!

---

### Post by lyric0n on 2008-07-23
Hi,

This is helpful, but I would like this to run at startup, before the user logs in. Will this perform this?

Thanks,
Chris

---

### Post by PGScooter on 2008-07-23
no, it will not. good point.

I think you need to put your script in /etc/init.d/ and make it executable by using ```
sudo chmod +x /etc/init.d/scriptname
```.
Then run ```
sudo update-rc.d scriptname defaults
```
I think that should do the trick.

---

### Post by lyric0n on 2008-07-23
Worked like a charm, thanks!

---

