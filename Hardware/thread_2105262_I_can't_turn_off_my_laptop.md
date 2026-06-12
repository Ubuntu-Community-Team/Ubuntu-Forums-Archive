---
title: "I can't turn off my laptop"
date: 2013-01-15
forum: Hardware
---

### Post by Jonahtan on 2013-01-15
I recently installed Ubuntu 12.04 and most of the times I can't turn off my laptop. It freezes at the purple "page" with the white and red dots. I have to unplug the battery for the computer to shut down.

Any ideas?

12.04 (precise) 32-bit
Linux 3.2.0-35-generic-pae
GNOME 3.4.2
encrypted LVM
Samsung R522

---

### Post by tgalati4 on 2013-01-15
Next time you need to shut down, try the following:

Control-Alt-F1 to get to terminal mode:

```
sudo shutdown -h now
```

Pay attention to any messages that show up and if the machine shuts down completely.

---

### Post by yossell on 2013-01-16
Are you using nvidia drivers? There have been a number of people having this problem because of their nvidia drivers -- and I had this problem too. 

[http://ubuntuforums.org/showthread.php?t=1973236](http://ubuntuforums.org/showthread.php?t=1973236)

discusses various attempts at a solution, but I'm not sure there's an ideal answer.

---

### Post by Jonahtan on 2013-01-18
Thank you guys!

Though a bit inconvenient the terminal trick worked like a charm. Guess I have to get used to it. :)

Ctrl-Alt-t

sudo shutdown -h now

I don't have Nvidia drivers. I have ATI/AMD drivers. I read in the thread you linked to yossell, that the terminal trick doesn't work for everyone. Weird issue.

---

### Post by dannyboy79 on 2013-01-18
you should be able to change the the command that the shutdown button actually performs, just need to find out what config file to edit, and then you can change it from whatever it is to the "sudo shutdown -h now"

---

### Post by leef on 2013-01-18
you can view the shutdown messages but pressing F2 whilst shutting down, which should save you the trouble of executing the shutdown command. Pressing F2 solves this very same problem on the laptop I'm using ATM.

---

