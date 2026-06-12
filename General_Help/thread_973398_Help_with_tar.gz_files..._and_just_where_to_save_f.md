---
title: "Help with tar.gz files... and just where to save files"
date: 2008-11-06
forum: General Help
---

### Post by epicbattle on 2008-11-06
Alright, I still have the darnedest time installing anything that requires more then one command in terminal. I never know what I am doing. I don't know if I should save it in a certain directory, or if I even was able to save it at all. I'm still a total noob to Linux. Can someone tell me how to install tar.gz files? Specifically ponyprog2000. You can use whatever example you want to show me, but just assume I have no idea what any lingo is (because it's kind of true).

And as just a general understanding for the system, is there a place that I should save all my files and programs? Do I want it all in my /usr folder? Any help will be appreciated.

Ubuntu 8.04

---

### Post by taurus on 2008-11-06
When you save a file to your harddrive, the default directory is your Desktop--~/Desktop.  And since it's tar.gz, it means that you probably have to unpack and build it from source.

Basically, you would do all that, building and installing, from a terminal, Applications -> Accessories -> Terminal.

```
cd ~/Desktop
tar xvzf filename.tar.gz
cd filename
sudo apt-get update
sudo apt-get install build-essential checkinstall
./configure
make
sudo checkinstall
```

---

