---
title: "t450s - keyboard going crazy"
date: 2015-04-27
forum: Hardware
---

### Post by pbrille on 2015-04-27
Hi,

I'm going bleeding edge by using a Lenovo T450s with Xubuntu 15.04.

From time to time my keyboard is going crazy. Sometimes it's when using the laptop only by itself, another time I'm using an external USB Keyboard via the Dock.

One time it was like this:
The device ran without problems, but suddenly in terminator terminal emulator no matter what key I pressed I always got the same sequence of letters back, like "a" "i" "f" and then "g" and than back to "a" again. This is just an example. I can't remember which letters there were.

More recently I wrote an Email in Thunderbird and it was not "that" bad, but also really annoying. Again after the device booting up and working fine for some minutes but suddenly only some letters didn't work and also sometimes they didn't.
When I used backward delete for example I sometimes got the letter "e" back, but only sometimes. I just had to repeat pressing the keys and sometimes they worked fine, another time they sent me some such a wrong letter back.
After clicking on "send" Thunderbird crashed completely but after that - no more false keys.

I know this might be a hard case to support me in, but could someone at least point me how I can maybe get to the bottom of this by myself when this happens again?

Thank you!

---

### Post by harobed on 2015-04-27
Have you found other T450s users with this issue*? (I would like to buy a T450s).

---

### Post by pbrille on 2015-04-28
No, I haven't. Here's a summary of my issues with the laptop so far. [http://www.winteltosh.de/2015/04/lenovo-t450s-ubuntu-15-04/](http://www.winteltosh.de/2015/04/lenovo-t450s-ubuntu-15-04/)

---

### Post by pbrille on 2015-04-28
Some more input. When it happens, it only affects one application, this time Firefox.
When I switch to another program - no issue.

---

### Post by pbrille on 2015-05-03
After I stopped using Firefox this problem did not occur any longer. So this might be some kind of Firefox glitch obviously.

---

### Post by pbrille on 2015-05-05
Ok, here I am back again.
This problem is *not* gone.
Now I've been using gedit and the problem is that sometimes a keystroke is just not registered at all. When I hit it 2 or 3 times it gets recognized, but that's really going me on the nerves when you want to work productively.

Could someone please lead me, what I can do to resolve this? I have no Idea how to address this. dmesg isn't showing anything when this happens.

---

### Post by pbrille on 2015-05-12
Still me....
Sometimes the first keystroke e.g. in an open-dialogue isn't recognized. Normally a very convenient method to search in a large list of files by just typing the first letters.
I'm not kidding you guys... yes, my keyboard inputs are totally xxxxxx up on very random occasions.

Also: When I enter a password with no optical feedback whatsoever: no clue what I typed at all.

---

### Post by pbrille on 2015-05-26
What am I doing wrong? Nobody responding?

---

### Post by Kmannn3n on 2015-05-29
Below is the procedure that may work for you. While in the Language Support, double check the two top tabs reflect the correct language support and regional support that what you want. The keyboard input method system is a drop down menu on the right hand side. The choices being ibus and none.
Hopefully these instructions can be of use to you.
System Settings > Language Support > Keyboard Input Method System > Choose None > Reboot the OS

---

### Post by gwgw9912 on 2015-09-01
Experiencing the same thing. However, it does not seem to affect google chrome. happening on dell inspiron 530. I thought it might just be my keyboard, but if that was the case, Chrome would not be any different. I can't do so much as trying to add a period to a filename, search for a program, or even type in my password without fighting with my keyboard for 5 minutes, but I can type an essay (and this post) just fine on chrome. 

oh, and i'm using regular ubuntu. Not xubtuntu.

---

### Post by seth-u on 2015-11-23
It seems I have the same problem.  It happens in both firefox and emacs.  usually the t key gets dropped, but if I go back and retype it, then it shows up.  Very annoying.  This does NOT happen under windows or under kubuntu 15.04.  It does happen on my just upgraded "Ubuntu 14.04.3 LTS"  HELP.  Did anyone get his solved?

---

