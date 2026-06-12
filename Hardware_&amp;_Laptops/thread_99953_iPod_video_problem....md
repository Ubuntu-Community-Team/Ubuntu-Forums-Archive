---
title: "iPod video problem..."
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by wham on 2005-12-06
I just switched over to Ubuntu about a week ago and my iPod works well with gtkpod, it mounts and unmounts fine, and I can add songs easily but I do I have one question. I had 3 episodes of Seinfeld (added when I had Windows) on there and the first time I added songs through gtkpod I had to unmount it by just unplugging it and now the videos don't play video, just the audio. Does that have anything to do with me just unplugging it (since I didn't know how to unmount it correctly)? Also, all the songs that are on there are now listed under the video section. Any help is much appreciated.


One unrelated question, my brother used to get his work schedule on the internet through IE, but now that we have Firefox, the site tells him he must use IE, is that the only option?

---

### Post by Digitallysick on 2005-12-06
as far as the ipod video, (i dont own one) but i do have an ipod, never used it with linux though, but i would say you would have to unmount it first, i have just unplugged my ipod without ejecting from the laptop, and it screws it up! , as far as another browser, you could download opera, it has several options, you can even set it to identify itself as IE

---

### Post by wham on 2005-12-07
Ok, I dowloaded Opera from the site and now I have this file (opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) on my computer desktop. What do I do to install it?

---

### Post by iam10ninjas on 2005-12-07
type sudo apt-get install opera into a terminal window, enter your password and it'll install all the packages and hopefully all the dependencies for you.

---

### Post by wham on 2005-12-08
Ths is what comes up:

Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

Now what?

---

### Post by PsyberOneZero on 2005-12-08
```
sudo dpkg -i ~/Desktop/opera*.deb
```
That will install the one on your desktop

If that's giving you too much grief, use Automatix to install it
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by wham on 2005-12-08
Ok, Automatix installed Opera but now when I click the Opera icon, nothing happens. It acts like it's about to open and then nothing.

Also, I'd like to thank everyone for all the help. You wouldn't believe (you probably could imagine) what asshole the people on the Windows forums are.

---

### Post by PsyberOneZero on 2005-12-10
I just ran Opera in a terminal and am getting a Seg Fault, and I cant trace it, but there's an extension for firefox to switch the User Agent (IE, Opera, Mozilla etc)

[http://chrispederick.com/work/useragentswitcher/](http://chrispederick.com/work/useragentswitcher/)
It works like a charm for me.

---

### Post by wham on 2005-12-10
Thanks, that worked great. One problem, however. A dialog with the following pops up on startup.

"Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/opera/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins"

How do I fix this?

---

### Post by PsyberOneZero on 2005-12-11
```
sudo apt-get install libmotif3
```
try that, that seems like it would be the cause of the problem.

---

### Post by wham on 2005-12-12
This is what I get:
Reading package lists... Done
Building dependency tree... Done
libmotif3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

---

### Post by PsyberOneZero on 2005-12-12
try
```
sudo apt-get install motifnls motif-clients
```
after that I'm out of ideas, I'll hit google and see what I can find

---

### Post by wham on 2005-12-12
It says the same things as with libmotif3. 

I sure appreciate you helping me because I wouldn't even know where to look.

---

### Post by WildTangent on 2005-12-12
There's a user agent switcher extension for firefox too...it would be MUCH easier to just use it.

[https://addons.mozilla.org/extensions/moreinfo.php?id=59&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=59&application=firefox)

-Wild

---

