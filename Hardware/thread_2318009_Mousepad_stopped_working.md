---
title: "Mousepad stopped working"
date: 2016-03-22
forum: Hardware
---

### Post by ZannaStar on 2016-03-22
I'm running (limping would be a better verb...) Ubuntu 14.04 on my Asus X205T (there are lots of things i need to fix...) Yesterday the updater installed some stuff and asked to restart, I said later. The next time I started up, the mousepad doesn't work at all. Tried rebooting, apt-get update, and looked for a solution here, but didn't find anything that worked. I am a newbie (or just really lazy).

---

### Post by sudodus on 2016-03-22
I don't know how to fix the problem with mousepad, and I suggest that you file a bug at [https://launchpad.net/](https://launchpad.net/)

Until the bug is squashed, I suggest that you try to use another text editor, for example geany

```
sudo apt-get install geany
```

---

### Post by ZannaStar on 2016-03-22
Damn I'm pretty sure I have created a misunderstanding. I mean the touch pad does not work?

---

### Post by sudodus on 2016-03-22
Yes, mousepad is the name of a text editor :-D

I'm not the right person to trouble-shoot the touchpad. I can only suggest some simple things. I hope people who know better can chip in and help.

Some computers have a button to turn the touchpad on and off. Maybe you can check if you can turn in on with a hotkey combination, maybe the 'Fn' key + an 'F' key. My laptop has the Fn + F5 key combination for this purpose.

One alternative is to boot a previous kernel via the grub menu (press the shift key during boot is you don't see it).

I think it is important to file a bug at [https://launchpad.net/](https://launchpad.net/). It will help squashing the bug.

---

### Post by ZannaStar on 2016-03-22
Thanks for your help! Looks like it has been reported - I found what looks like my bug on launchpad and someone has noted the last kernel version that it worked in (3.19.0-51). Hopefully it will get fixed, meanwhile I'll go back to 51...

Yep, booted into previous version and thankfully it works. That fixed my immediate problem and increased my basic knowledge. Many thanks :-)

---

### Post by sudodus on 2016-03-22
Congratulations and thanks for sharing your solution :KS

Please share also the bug number or a link to the bug report :-)

---

### Post by ZannaStar on 2016-03-23
Here's the page
[https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1558489](https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-trusty/+bug/1558489)

---

### Post by sudodus on 2016-03-23
Thanks for taking active part in debugging :-)

---

### Post by mörgæs on 2016-03-23
Could you try a live boot of 16.04 please and tell how it works?

Besides, there is a [long thread]("http://ubuntuforums.org/showthread.php?t=2254322") where people discuss this particular Asus. If you encounter more problems that thread is a good place to search.

---

### Post by ZannaStar on 2016-03-24
Yes, I know that thread, I couldn't have got this far without it, but haven't had time to tinker with my machine for ages so not looked at it. Seeing all the updates, I'm tempted to back up and start again >_<

I will figure out how to do what you suggest!!

---

### Post by ZannaStar on 2016-03-31
Finally, I can report that in a live boot of 16.04 the touchpad works (although the pointer speed seems really slow even when I speed it up). Of course, many other things do not work (WiFi, sound, etc) but that's because of this laptop's compatibility issues. The kernel (downloaded the ISO yesterday) is 4.4.0-15

---

### Post by mörgæs on 2016-03-31
Good, please spread the word and thanks for posting in the bug report.

---

### Post by ZannaStar on 2016-04-08
Just a note in case it's useful - I could never get into the grub menu at boot by pressing shift, so eventually I edited /etc/default/grub with the help of this page [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup) so that I would be able to choose which kernel to boot every time.

---

