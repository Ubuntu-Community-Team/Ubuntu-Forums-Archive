---
title: "How would one multiplex output from a script?"
date: 2008-10-11
forum: General Help
---

### Post by shaggy999 on 2008-10-11
I have a script that runs a bunch of stuff and I would like the output from the script and all the programs it runs to be sent to a file for logging purposes in addition to displaying on a screen. Is there an easy way to do this?

---

### Post by bodhi.zazen on 2008-10-11
tee

[http://www.devdaily.com/blog/post/linux-unix/use-unix-linux-tee-command-send-output-two-or-more-directions-a/](http://www.devdaily.com/blog/post/linux-unix/use-unix-linux-tee-command-send-output-two-or-more-directions-a/)

---

### Post by shaggy999 on 2008-10-11
Oh man. I should have known that. I've even used that before for that very purpose now that I remember. I feel like such a dolt. :(

---

### Post by bodhi.zazen on 2008-10-11
Lol

---

### Post by hyper_ch on 2008-10-12
```

sh script.sh > ~/Desktop/script_output.txt

```

---

