---
title: "trying to burn dvd with Kp3"
date: 2008-07-19
forum: General Help
---

### Post by paydaydaddy on 2008-07-19
I get an error telling me that there is not enough space available for temp file. Unable to select a different area to store the temp image. Is there a way to increase the default temp file. Suggested work around?

---

### Post by bodhi.zazen on 2008-07-19
See if this helps :

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075)

Otherwise , could you post the exact error message ?

---

### Post by Taxman415a on 2008-07-19
When you say you are "Unable to select a different area to store the temp image" does that mean you don't have enough space or that it doesn't listen to the setting you put in when you go to the settings menu, select configure k3b, and change the default temporary directory? It does make it look like that's for something else and maybe it is. How much space do you have left for /tmp and or / ?  ie what is the output of df -h  ?

---

### Post by BLTicklemonster on 2008-07-19
First of all, do you have enough physical space on your hard drive that you can use for a temp folder while burning the dvd?

If so, then:

in k3b, click on Settings, then Configure K3B.

Now in the window that opens you can see on the right a place where you can change where you save your temp files. The "default temporary directory".

Create a folder somewhere where you know you have space, and change that to show the new temp folder, and you should be ready to go.

Hope this helps!!!

Good luck!

Oh. Same info, different post. Sorry.

---

### Post by BLTicklemonster on 2008-07-20
> **bodhi.zazen said:**
> See if this helps :

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075)

Otherwise , could you post the exact error message ?

lol you been posting that all over the place! Great job, oh great and wise and benevolent one!!! And thanks, too.

---

### Post by paydaydaddy on 2008-07-20
```
dragon@smaug:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  3.8G  5.0G  44% /
varrun               1014M  272K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2              63G  6.6G   53G  12% /home
dragon@smaug:~$
```
Lots of open space in /dev/sda2, but when I try to change the temp file in settings it reverts back to default. Tried to burn on the fly and got the message "Failed to retrieve all CSS keys."

---

### Post by BLTicklemonster on 2008-07-20
Did you:


 dajero wrote on 2008-04-23: (permalink)

I had the same problem but was able to work around it by creating the directory /tmp/kde-<my_username>, where, ofcourse, you need to replace <my_username> with your own username. You'll notice that k3b says Temp: No info in the lower left corner of its window. Once you've created the aforementioned directory and restart k3b you'll notice that k3b now displays the correct amount of free disk space in /tmp.


?

---

### Post by paydaydaddy on 2008-07-20
> Did you:


dajero wrote on 2008-04-23: (permalink)

I had the same problem but was able to work around it by creating the directory /tmp/kde-<my_username>, where, ofcourse, you need to replace <my_username> with your own username. You'll notice that k3b says Temp: No info in the lower left corner of its window. Once you've created the aforementioned directory and restart k3b you'll notice that k3b now displays the correct amount of free disk space in /tmp.
Tried this, but I think the problem is my weakness with commands/terminal. Got error message: cannot create directory `/tmp/kde-dragon': File exists

---

### Post by paydaydaddy on 2008-07-20
It seems that I should be able to burn on the fly and forget the temp file problem, but how do I retrieve the CSS keys. Do I need to use a different burning program?

---

### Post by bodhi.zazen on 2008-07-20
lol, found that old unanswered thread trying to solve this one.

---

### Post by paydaydaddy on 2008-07-20
bttp
Anybody have suggestions about retrieving CSS keys as mentioned above.

---

### Post by paydaydaddy on 2008-07-20
Bump
Trying to create backup copy of encrypted DVD. The DVD will play with VLC but not kaffiene. When trying to burn copy I get the error: unable to retrieve all CSS keys. Any known solution?

---

### Post by bodhi.zazen on 2008-07-21
Sounds a little like cracking or that you may be trying to copy something you should not.

FYI Cracking is not supported on these forums.

---

### Post by paydaydaddy on 2008-07-21
I haven't thought of it as cracking or hacking or whatever you want to call it, but you may be right. Just trying to make a backup copy of a legally bought and paid for commercial dvd. Actually my wife wanted the copy to use so she could keep the original like new. Does that make us criminals? I may have to turn myself in.:) The gist of your comment is probably right though. The problem is most likely copy protection. As a test of my hardware I burned a copy of a different(older) dvd and it worked fine.I suppose I just have to tell the wife that she is SOL. Thanks for the replies.

---

### Post by bodhi.zazen on 2008-07-21
> **paydaydaddy said:**
> Does that make us criminals?

Unfortunately , yes, although I would assume it varies outside the United States. I did not say I agreed with the policies of the music/video industry.

---

### Post by Taxman415a on 2008-07-21
Assuming you are not in the US or another country whose politicians have sold to the highest bidder you can run dvddecrypter under wine and it will remove the css and the annoying PUOs that keep you from skipping various parts. See doom9.org

---

### Post by BLTicklemonster on 2008-07-21
Paydaydaddy, check your pm box.

bodhi.zazen, ;)

---

