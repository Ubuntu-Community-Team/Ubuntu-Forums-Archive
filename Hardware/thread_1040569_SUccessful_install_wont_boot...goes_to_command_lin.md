---
title: "SUccessful install wont boot...goes to command line??"
date: 2009-01-15
forum: Hardware
---

### Post by flattop1 on 2009-01-15
I'm new to Ubuntu but I have now installed it on 2 desktops at my house and want to have it on my averatec laptop too..
However it doesnt seem to work on the laptop.
After a seemingly successful install of Ubuntu the computer never boots up correctly afterwards.
It always goes to command line like this....

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/DSC_1374.jpg[/IMG]

I tried booting to the live cd and the same thing happens.
I even installed XUBUNTU alternative cd and the exact same thing happens.


I tried "startx" and "initx" and a few other suggestions that I saw on other threads around the forum,but nothing works.

The thing thats most annoying is I was able to run "opensuse" and "mint" without any problems at all.

Whats going on and how do I overcome this problem?

---

### Post by electrogeist on 2009-01-15
Maybe this thread will help you:

Help installing Ubuntu 8.04 in Averatec 3200 Series laptop 
[http://ubuntuforums.org/showthread.php?t=930121](http://ubuntuforums.org/showthread.php?t=930121)

---

### Post by flattop1 on 2009-01-15
> **electrogeist said:**
> Maybe this thread will help you:

Help installing Ubuntu 8.04 in Averatec 3200 Series laptop 
[http://ubuntuforums.org/showthread.php?t=930121](http://ubuntuforums.org/showthread.php?t=930121)
Thanks for that link..

I tried what they suggested and it still doesnt work.

Okay from reading that post above,the consensus is that post 34 (posted by Williams99) is the solution to the problem....

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/Screenshot-2.png[/IMG]

SO I went ahead and did step 1 -cd /etc/X11:

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/1.jpg[/IMG]

But as you can see step 2 didnt work out...I got "xorg.conf no such file or directory"?

I went ahead and did  step 3  anyway and used the command to download the file from williams99 and it seemed to work fine.

[IMG]http://i58.photobucket.com/albums/g251/keogh557/Non%20Skate%20photos/2.jpg[/IMG]

If Im not mistaken it seems to have saved the new xorg file as xorg.conf.2

??

I tried rebooting and just got the command line again.

I must be close to getting this right...Can anyway point me in the right direction?

---

### Post by electrogeist on 2009-01-15
Well from your screenshot it looks like you were trying williams99.com when it is supposed to be williamts99.com - note the "t".  Then your roadrunner ISP was redirecting you to one of their pages, which it may have saved with a long filename... you can do a "ls" to get a directory listing to see what is there, and "rm" to delete it with help of [tab] filename completion.

---

### Post by flattop1 on 2009-01-15
> **electrogeist said:**
> Well from your screenshot it looks like you were trying williams99.com when it is supposed to be williamts99.com - note the "t".  Then your roadrunner ISP was redirecting you to one of their pages, which it may have saved with a long filename... you can do a "ls" to get a directory listing to see what is there, and "rm" to delete it with help of [tab] filename completion.

Well spotted..I'll try again...

---

### Post by flattop1 on 2009-01-15
SOLVED....

thanks electrogeist and williamts99 ......Ubuntu is now working perfectly on my Averatec laptop.

---

