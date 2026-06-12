---
title: "How can i make sure my graphics are installed right"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Elotero on 2008-02-26
Just installed 8.04 and the resolution or something is terrible. Let me describe my screen. There is a thin black line directly down the center of the screen, When im on 1 side of this line the graphicson the other side clear up a tad bit and vice versa. The graphics have many lines of green bright yellow for no reason. Can someoone help me correct this problem?

---

### Post by taurus on 2008-02-26
What kind of graphic card does it have and have you looked in System -> Administration -> Restricted Drivers Manager to see if there is a driver for that?

---

### Post by Elotero on 2008-02-26
here is a screenshot.

---

### Post by taurus on 2008-02-26
What am I supposed to look for from that screenshot?

---

### Post by Elotero on 2008-02-26
> **taurus said:**
> What kind of graphic card does it have and have you looked in System -> Administration -> Restricted Drivers Manager to see if there is a driver for that?

Thanks so much for taking the time to help. In 8.04 there is no folder for restricted drivers.Do i enable the repositories in synaptic or something?  BTW.. i posted a screenshot and it looks awesome but on my screen it looks like junk.

---

### Post by taurus on 2008-02-26
Try clicking **System**, the third option from the left, and then **Administration**.

---

### Post by Elotero on 2008-02-26
> **taurus said:**
> Try clicking **System**, the third option from the left, and then **Administration**.

Under administration there is no folder for Restricted Drivers

---

### Post by taurus on 2008-02-26
What graphic card do you have and what driver do you use in /etc/X11/xorg.conf?

```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

Maybe you need to include the horizontal and vertical refreshing rates for your monitor in /etc/X11/xorg.conf.

---

### Post by Elotero on 2008-02-26
Okay after the updates installed i restarted and its back up looking like the screenshot. No clue how it resolved itself. Thanks for taking the time out to listen and help Taurus.

---

### Post by taurus on 2008-02-26
So everything is peachy now.

---

