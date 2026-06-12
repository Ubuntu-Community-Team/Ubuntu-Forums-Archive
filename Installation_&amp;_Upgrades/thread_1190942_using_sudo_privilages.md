---
title: "using sudo privilages"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by bavman on 2009-06-18
Im sorry but this is a really noobish question. 
Im totally new to linux and all this. But ive been having problems with my hp laptop and sound but i found an answer: 

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

So heres my question: Ive downloaded the file specified in the thread but what do i do with the code there? Does it go in the terminal or something?

Thanks for helping. :)

---

### Post by ~sHyLoCk~ on 2009-06-18
> **bavman said:**
> Im sorry but this is a really noobish question. 
Im totally new to linux and all this. But ive been having problems with my hp laptop and sound but i found an answer: 

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

So heres my question: Ive downloaded the file specified in the thread but what do i do with the code there? Does it go in the terminal or something?

Thanks for helping. :)

Yes! Suppose you have the file .tar.gz in your desktop, open terminal [Applications -> Accessories -> Terminal] and type the sugested commands! Make sure you have extracted the tar file first! You can simply do that by right clicking -> extract here.

---

### Post by bavman on 2009-06-18
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]

#> sudo reboot
when i put that in though it doesnt do anything. 
and when i take out the #> before it, it says this: No such file or directory

---

### Post by bavman on 2009-06-18
Basically i dont know what im doing. How do i put in the code. Step by step instructions would be appreciated =) With everything i need to do. I know you guys might think some of this is obvious but ive never done this before so i have no clue haha

---

### Post by ~sHyLoCk~ on 2009-06-18
Ok before compiling anything, you will first need something. Open terminal and type :
```
sudo apt-get install build-essential
```
Now did u extract the tar file on the desktop? Open the terminal again? Type:
```
cd ~/Desktop/foldername
```
replace "foldername" with the extracted folder's name
Now type in the terminal again:
```
 ./configure --enable-dynamic-minors
 make
sudo make install-modules
 sudo vim /etc/modprobe.d/alsa-base
```
Now you have to add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.  <---I don't know how to do that but you will figure it out while installing.
 
```
sudo reboot
```

Hope this helps

---

### Post by raymondh on 2009-06-18
For reference/reading

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal](http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal)

---

