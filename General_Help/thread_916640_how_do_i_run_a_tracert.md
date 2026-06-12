---
title: "how do i run a tracert?"
date: 2008-09-11
forum: General Help
---

### Post by Breakar on 2008-09-11
How do i run a tracert to save to txt, for a example in windows cmd prompt id do something like

tracert [www.google.com](www.google.com) > c:/tracert.txt

---

### Post by iaculallad on 2008-09-11
> **Breakar said:**
> How do i run a tracert to save to txt, for a example in windows cmd prompt id do something like

tracert [www.google.com](www.google.com) > c:/tracert.txt

You could just use the 'network tool' provided in Ubuntu. System->Administration->Network Tool, "Traceroute" tab.

---

### Post by NoReflex on 2008-09-11
You can do the same in Linux : 
```
traceroute www.google.com > myfile.txt
``` 
Best wishes,
NoReflex

---

### Post by Ryadt on 2008-09-11
```
sudo tracert www.google.com > tracert.txt
```

---

### Post by iaculallad on 2008-09-11
> **Ryadt said:**
> ```
sudo tracert www.google.com > tracert.txt
```

And to do this, install the application first:

```
sudo apt-get install traceroute
```

---

