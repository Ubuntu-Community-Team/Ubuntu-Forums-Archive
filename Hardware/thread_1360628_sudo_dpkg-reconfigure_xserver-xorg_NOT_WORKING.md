---
title: "sudo dpkg-reconfigure xserver-xorg NOT WORKING"
date: 2009-12-21
forum: Hardware
---

### Post by aminmatrix on 2009-12-21
ubuntu 9.10

this command didn't work in my pc
sudo dpkg-reconfigure xserver-xorg
nothing figur up!!!!!
```

root@ubuntu:~# sudo dpkg-reconfigure xserver-xorg
root@ubuntu:~# 

```

---

### Post by Grenage on 2009-12-21
I believe that command has been deprecated.

---

### Post by aminmatrix on 2009-12-21
thx i think that so

---

### Post by mickie.kext on 2009-12-21
After doing that comand, do 'echo $?' to see if comand executed.

PS: I just did that myself, and says 0. So command is executed successfully... but did nothing.

---

### Post by ajgreeny on 2009-12-21
What are you trying to do with the command?  I assume you have a display problem of some sort, and these are often solvable by other means now.

---

### Post by mickie.kext on 2010-01-11
> **ajgreeny said:**
> What are you trying to do with the command?  I assume you have a display problem of some sort, and these are often solvable by other means now.

Ok, I now need this command and it does not work:(. So please someone tell me about that "other means". There is nothing about that on internet, not even explanation why they removed good old  sudo dpkg-reconfigure xserver-xorg

---

### Post by tomm174 on 2010-02-12
Deprecated Eh !

Oh well then of course we would expect that any users who had learned their Ubuntu at the time it was fashionable would be left in the cold to research what the flaour of the month is now - just like those lost souls who learned how stuff worked before Ubuntu existed, or the people who came to put their faith in displayconfig-gtk 
If each time somone discovers a way to configure part of the system, the next time they try to use it, it silently fails, and they are left to google their way out of the problem, 
how long can it be before everyone abandons windoz in favour of the joy of an operating system where every month there's a new puzzle, and every update brings a new surprise.

One thing Microsoft have always taken seriously is backward compatibility.
Linux should be MUCH better at this. 
Breaking existing working systems weakens the project, and should be undertaken only if there is a genuine need for it.
In the proprietary world of course the reason to change things is to push consumers to buy the new product.
We don't need to think that way - which is why we have textual config files in /etc with open documentation, not some stupid registry to prevent people from using the developers' work.
Thar's why it makes sense to provide gui tools that work on the existing config files, allowing simple configuration yet not preventing tuning by someone using vi on a terminal. 
If there are types of configuration that can't be done that way, I don't know what they would be, and if there is a config that used to be in a particular file there ought to be a damned good reason before it is moved.

Is it that there are ppl out there who don't give a toss about the success of the platform as long as their project gets into the distro ?

---

### Post by tomm174 on 2010-02-13
YES that's right - Deprecated - without any warning posted in the places you used to look.
Yes it's been deprecated and replaced by HAL.

- Oh No - Sorry HAL's [been deprecated]("https://wiki.ubuntu.com/Halsectomy").

Actually no This is is : I've really got it now.
**Ubuntu's** been deprecated in favour of slackware or gentoo or suze 

Sod it let's just go back to Windows

---

### Post by Yellow Pasque on 2010-02-13
> **tomm174 said:**
> Sod it let's just go back to Windows
Yeah, because Windows never deprecated anything.., :rolleyes:

BTW, you can still use xorg.conf to configure X.

---

### Post by cprivers on 2010-02-14
> **Temüjin said:**
> BTW, you can still use xorg.conf to configure X.

I don't even have that file on my system. It will take more Googling to figure that out. The reconfigure command was an "old standby" for me. Made it easy to install a "test" disk in a new computer and just reconfig the video.

---

