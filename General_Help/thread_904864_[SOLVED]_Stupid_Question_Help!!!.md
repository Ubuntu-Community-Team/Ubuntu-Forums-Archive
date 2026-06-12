---
title: "[SOLVED] Stupid Question Help!!!"
date: 2008-08-29
forum: General Help
---

### Post by dphoenixa on 2008-08-29
Alright so I've been using Azureus and i forgot to redirect the files and they say it's in /home/(user)/.azureus/Documents/Azureus Downloads/(file name) 

I've used search, I've tried everything I could think of, but I am coming up with nothing. So the question being, How do I get to them? How can I find them? Cause I cannot reach them with anything I can think of.

---

### Post by drs305 on 2008-08-29
How exactly have you searched for them? And what are you trying to do with them (open, copy, etc).

If you were using nautilus, do you have the 'view hidden files' option enabled (CTRL-h)?
```
nautilus /home/**(user)**/.azureus/Documents/Azureus Downloads/ 
```

Have you tried:
```
ls -a /home/**(user)**/.azureus/Documents/Azureus Downloads/
```

If you aren't sure where they are located but you know the name or part of a name of one of the files:
```
sudo find / -type f -iname ****enternamehere****
```

---

### Post by jeepers on 2008-08-29
Try using Ctrl+H to show hidden files, the (.) before a file indicates its a hidden file.

cheers

---

### Post by dphoenixa on 2008-08-29
ctrl+h did the trick....man i feel like a complete idiot....thanks guys.

---

### Post by mike1234 on 2008-08-29
Why is is it "hiding" your downloads to have to use Ctrl + H. Strange.

M.

---

