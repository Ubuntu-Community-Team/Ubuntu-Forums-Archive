---
title: "How to install Telugu Fonts in Ubuntu 8.04"
date: 2008-09-19
forum: General Help
---

### Post by sukhhari on 2008-09-19
Hi,

I would like to know, how to install Telugu Fonts in ubuntu 8.04

request for steps

Regards

Harish Kumar R

---

### Post by northern lights on 2008-09-19
```
sudo apt-get install ttf-telugu-fonts ttf-indic-fonts language-pack-te
```
```
wget http://abhiomkar.googlepages.com/lohit_te.ttf && sudo cp lohit_te.ttf /usr/share/fonts/truetype/ttf-telugu-fonts/ && sudo fc-cache
```

Either should set you up.

---

### Post by sukhhari on 2008-09-19
Let me first thank you very much. even i try to load [www.eenadu.net](www.eenadu.net) or [www.vaarttha.com](www.vaarttha.com), but still i unable to view the Telugu Fonts.


Regards

Harish Kumar R

---

### Post by northern lights on 2008-09-20
eenadu has its own font, at least. You can download it from [here]("http://www.eenadu.net/font.zip"). Extract the archive and copy this font to ```
/usr/share/fonts/truetype/
```also. Afterwards, reboot, restart the session or run```
sudo fc-cache
```

---

### Post by sukhhari on 2008-09-20
Really iam very much thankful to your express support and once again one more question, 

how to expand .SIT files in ubuntu 8.04.

Actually i was tried with File-roller, but it fails

any suggestions on this.


Regards

Harish Kumar R

---

### Post by ananta.c on 2008-12-04
Hey all, I was fed up with stupid windows for years and trying to change. I like xubuntu but I have some problems doing some changes.

I tried extracing eenadu font to /usr/share/fonts/truetype/, but it gives no permissiion. I have created only one account while installing OS and thats the one I use.

how shall i fix this permission error????????

---

### Post by ananta.c on 2008-12-04
fyi - I don't know whats the root password as it never prompted to enter while installing OS, is there a default password?????????

plz help

---

### Post by ananta.c on 2008-12-04
I know, its quick... but i did it... thanks for Ubuntu active forms..

---

### Post by ravi14 on 2009-05-12
Thanks a lot for the fix. It works.

---

