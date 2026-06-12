---
title: "External Display issues 12.04 LTS"
date: 2013-11-22
forum: Hardware
---

### Post by dio5 on 2013-11-22
Hi pro's

I have a dell xps 13 with ubuntu.

Recently I've been having some display issues. Everytime I try to connect my U2711 monitor both my screens go black and all I can do is reboot and disconnect the external one. 

It only seems to happen on my account, i.e when I boot it goes  fine until I log in to my account. In a guest session it also seems to  work fine, which makes me think it's a config setting.

 I had been  experiencing the issue 3-4 times, but mostly it worked fine after rebooting. (At that point I didnt know the issues was only in my account... ) Until today  - as soon as I connect it (or have it connected already) under my  account, all goes black.

 
I'm guessing some settings must have been altered somehow, but which ones... 


 Any ideas before I dive in the web?

---

### Post by Kirboosy on 2013-11-22
Hi, I am not entirely sure what the solution would be, but it sounds like a bad config file. The one that keeps coming to mind is the monitors.xml file.

You could either delete the file or rename/move the file. I would recommend renaming it or moving it to a different folder. Open your 'Files Manager' and "Show hidden files".

The file you are looking for is as follows 

```
~/.config/monitors.xml
```

Let me know if that helps!

Hope that helps!
~Caboose

---

### Post by dio5 on 2013-11-25
That seems to have done it, thanks!

---

### Post by Kirboosy on 2013-11-25
Awesome, glad it was an easy fix!

---

