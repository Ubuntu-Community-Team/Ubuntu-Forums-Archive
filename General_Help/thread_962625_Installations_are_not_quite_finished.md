---
title: "Installations are not quite finished"
date: 2008-10-29
forum: General Help
---

### Post by Jayhawker on 2008-10-29
In hardy 8.04, when installing packets by synaptic, once downloaded, I am frequently informed there are some aspects of the downloading which didn't run properly: a lot of things denied, blocked, depending on other files not installed and so on. It's bizarre because I don't notice anything and it seems installations are working. When checked at Synaptic, files appears being installed and there are not broken files to repair. In a previous installation I had to remove because when activating compiz sound disappeared, it didn't happened anything of that, but now, with a new brand installation working perfectly, all this sort of warnings appears. What's going on?

By the way, If I update tomorrow to 8.10. Will I keep compiz and the system working like now or it's more than possible I'll get new problems? There would be the chance all this blocked, dependences, and failing warnings be solved? 

Thank You

---

### Post by cariboo on 2008-10-29
If you plan on updating to Intrepid, I would suggest doing a clean install if you are having problems now. Back all the important files in your home directory, to see all the files and directories in your home directory including hidden ones, open Places-->Home Folder and press Ctrl-h.

Jim

---

### Post by prshah on 2008-10-29
> **Jayhawker said:**
> In hardy 8.04, when installing packets by synaptic, once downloaded, I am frequently informed there are some aspects of the downloading which didn't run properly: a lot of things denied, blocked, depending on other files not installed and so on. 

If the downloading is interrupted, or incomplete for some reason, you will get an option to do a "partial" upgrade. Is this what you're facing? In this case, choose "No", and then you'll get an error message about which files have failed during download. Just repeat the process until all files are downloaded successfully.

If you're using a "local" server, it may benefit you to switch to the main server instead; click System-Administration-Software Sources-Ubuntu Software-Download From: and select either Main Server or any other suitable (geographically close) server.

---

### Post by Jayhawker on 2008-10-30
> **prshah said:**
> If the downloading is interrupted, or incomplete for some reason, you will get an option to do a "partial" upgrade. Is this what you're facing? In this case, choose "No", and then you'll get an error message about which files have failed during download. Just repeat the process until all files are downloaded successfully.

If you're using a "local" server, it may benefit you to switch to the main server instead; click System-Administration-Software Sources-Ubuntu Software-Download From: and select either Main Server or any other suitable (geographically close) server.

Nevertheless, the problem keeps on. There re continous errors downloading or deleting, much of them referred to dependecies or denied accesses becasue of root. How could I solve it whitout the need of reinstalling?

There are errors from medibuntu, from clamav, from java 5, 6, 7... How to solve that? When trying to reinstall javas, downloading problems apperas, and medibuntu is not possible to find out with synaptic. 

Any suggestions?

---

### Post by prshah on 2008-10-30
> **Jayhawker said:**
> 
There are errors from medibuntu, from clamav, from java 5, 6, 7... How to solve that? When trying to reinstall javas, downloading problems apperas, and medibuntu is not possible to find out with synaptic. 


I think you've enabled a number of third party repositories; the updater should comment them out, but maybe it's missed it in your case... can you post your /etc/apt/sources.list file?

---

