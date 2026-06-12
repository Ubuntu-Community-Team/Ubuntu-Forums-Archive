---
title: "[SOLVED] Logitech G11 Keyboard"
date: 2008-12-16
forum: Hardware
---

### Post by Cadeyrn on 2008-12-16
So, I followed the instructions on making my keyboard work from [here]("https://help.ubuntu.com/community/LogitechG15") perfectly, but then when I got to typing:

```
sudo g15daemon
```

it says:

```
sudo: g15daemon: command not found
```


I know I followed the instructions perfectly, and whenever ./configure had an error, I installed the missing package and did ./configure again and it worked perfectly all three times. I did nothing wrong.

There are three other sites about my exact problem on the internet, but they're in different languages and even hard to understand when translated. Plus no one's fixed it for them yet.

If it's any help, I'm running Ubuntu on an Intel iMac with iSight and the Mic already working perfectly.

---

### Post by Cadeyrn on 2008-12-16
BUMP.

I'm impatient.

---

### Post by Cadeyrn on 2008-12-20
Well, thanks for the help guys. I ended up fixing it mehself. There were some errors in the ./configure's that slipped past my eyes that I solved, and now it's working.

---

