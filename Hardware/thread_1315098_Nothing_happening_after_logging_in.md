---
title: "Nothing happening after logging in"
date: 2009-11-05
forum: Hardware
---

### Post by spida on 2009-11-05
Okay so I am some what new with ubuntu but not to great in describing the problem that I'm having right now.  After I type the user name and password and log in to ubuntu for my laptop all that appears is an orange background and in the top right corner is my terminal.  I feel as though I may of royally screwed something up somehow as it worked not to long ago perfectly fine.  (as in i could see my desktop and applications and use ubuntu)  Now I can only type in the terminal.  Someone please help.



If this is wrong thread post in I am sorry

---

### Post by lidex on 2009-11-05
Try running this command in your terminal:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

### Post by spida on 2009-11-05
after running the command it essentially did nothing still the same way as before, any other ideas?



Or is there a command that you can use to remove ubuntu using the terminal?

---

### Post by lidex on 2009-11-05
Did you reboot?

---

### Post by spida on 2009-11-05
Yes and did nothing

---

### Post by lidex on 2009-11-06
have a look [here]("http://ubuntuforums.org/showthread.php?t=1300013")

---

### Post by spida on 2009-11-06
Thanks for directing me there

---

