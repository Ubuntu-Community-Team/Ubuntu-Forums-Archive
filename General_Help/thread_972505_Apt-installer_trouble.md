---
title: "Apt-installer trouble"
date: 2008-11-05
forum: General Help
---

### Post by Squegee on 2008-11-05
When i try to open APT-installer I am presented with:
"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

I then try to run apt-setup and get: "sudo: apt-setup: command not found"

Then I try to run apt-get update and i get: 
"E: Type '/usr/lib/xine/plugins/1.20/xineplug_decode_a52.so' is not known on line 62 in source list /etc/apt/sources.list"

I looked for help online and i found a question like the one i have and the answer was: 
"1. Backup the current configuration, in case we break things further
sudo cp /etc/apt/sources.list /etc/apt/sources.list.broken
2. Edit the configuration, to reset it to a good version
gksudo gedit /etc/apt/sources.list"

I tried "sudo cp /etc/apt/sources.list /etc/apt/sources.list.broken" and nothing happened, I tried gksudo gedit /etc/apt/sources.list and it said program not installed so i tried installing gksu and i came up with the error:
"E: Type '/usr/lib/xine/plugins/1.20/xineplug_decode_a52.so' is not known on line 62 in source list /etc/apt/sources.list
E: The list of sources could not be read."

I am completely lost at what to do and any help would be greatly appreciated. I am using Kubuntu

---

### Post by taurus on 2008-11-05
There is something with line 62 in your /etc/apt/sources.list.  Edit it and either remove it or place a # in front of it to comment it out.

```
sudo nano -Bw /etc/apt/sources.list
```
You can save and exit the changes by holding down <Ctrl>x and then Y.

Then, run those two commands again to update your system.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Squegee on 2008-11-06
It worked, thank you very much

---

