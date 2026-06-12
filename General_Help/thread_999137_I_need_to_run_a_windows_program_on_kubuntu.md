---
title: "I need to run a windows program on kubuntu"
date: 2008-12-01
forum: General Help
---

### Post by wildmanne39 on 2008-12-01
Hi, can anyone tell me how to run a windows program on kubuntu?
I have the program installed on windows vista. I dual boot. If anyone can help please be exact I am still pretty new to linux. Thank you in advance.

---

### Post by spcwingo on 2008-12-01
First go to [http://appdb.winehq.org/](http://appdb.winehq.org/) and check if the app you're trying to run is listed and how well it performs.  If all looks good, open up synaptic and search for Wine.  Install Wine, then install the windows program.  After that you should see your windows app under the applications menu.  Choose and run.

---

### Post by wildmanne39 on 2008-12-01
Thank you I can look at the program and get in it through dolphine file manager but I cant figure out how to start it. If you have any idea's I will appreciate it.

---

### Post by spcwingo on 2008-12-01
Either try right clicking and select "open with" and choose wine or try running from a terminal.  To run from terminal do this:

wine "C:\\Program Files\\appdirectory\\app.exe"

Of course replace the path with a path that suits your app location.

---

### Post by wildmanne39 on 2008-12-01
Thank you for your help I am still having problems but I am on the right track.

---

### Post by hyper_ch on 2008-12-01
what do you need to run?

---

### Post by wildmanne39 on 2008-12-01
Hi,I need to run quickverse 2008 it is a bible program. I am a minister and I use it to prepare sermons and bible studies.

---

### Post by hyper_ch on 2008-12-01
if you can't get it to run in wine and if there's no linux version the last option will still be to install a virtual Windows for it... however you should have at least 1 GB ram just to make sure the host and guest are running fine.

---

### Post by spcwingo on 2008-12-01
When you run from the terminal does it give any errors?

---

