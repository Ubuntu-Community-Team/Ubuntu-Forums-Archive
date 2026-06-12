---
title: "how do i map my own function keys"
date: 2009-04-25
forum: Hardware
---

### Post by Meow27 on 2009-04-25
hi,
     i have a sony vgn-fs980. i have these software only function keys, and they only work windows.apparently, no1 supports this laptop anymore in regards to this topic.

is there any program/guide/etc. that will allow me to program my function keys to do stuff? 

thanks in advance

---

### Post by Meow27 on 2009-04-26
bump. i ve looked at various tools but still couldnt find one that works

---

### Post by Meow27 on 2009-04-27
i also would like to point out that the function keys that are supposed to be mapped do work, but do nothing (as i when i press fn+num lock to get scroll lock, nothing happens, but when i just press num lock, numlock activates)

---

### Post by mjota on 2009-04-27
Try Xev in a terminal.
You can try keytouch too.

---

### Post by Meow27 on 2009-04-27
keytouch doesnt have my keyboard, sony vgn-fs series, and the editor for keytouch doesnt support my keyboard either

xev also doesnt see my function buttons

---

### Post by Meow27 on 2009-04-28
bump

---

### Post by Meow27 on 2009-04-29
please, i need help here :[

---

### Post by Marlonsm on 2009-04-29
I'm also intrested in this, my mouse has 4 extra buttons that Linux can't use (and Windows can only use them with some broken driver that came with the mouse, that crashed every 5 mins)

---

### Post by Meow27 on 2009-04-30
b ump

---

### Post by Meow27 on 2009-05-04
bump

---

### Post by Meow27 on 2009-05-06
bump

---

### Post by spaided on 2009-05-06
i wish someone could help us,.... i am in the same perdicament!!!

---

### Post by glotz on 2009-05-06
Seen this? [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

What kernel are you guys on? ```
uname -r
```

---

### Post by Meow27 on 2009-05-06
2.6.28-11 generic



when i try to configure something with the keyboard shortcuts, it doesnt recognize my function key, so when i press fn+ f3, where one of my function keys are supposed to be mapped, it recognizes nothing

---

### Post by glotz on 2009-05-07
I guess you could try different keyboard layouts and compiling the latest kernel. No guarantees.

---

### Post by Meow27 on 2009-05-09
regarding the new kernel, can you link me some good guides of how to compile them? 

ive used a couple and failed, can you end me one that doesnt involve the use of git? i feel really guilty downloading 200mb+ of kernel when i could simply download a smaller, compressed version

---

### Post by glotz on 2009-05-10
I actually use Debian these days and I've only compiled kernels on it, however since Ubuntu is based on Debian I expect the process to be similar. [Here's](http://forums.debian.net/viewtopic.php?f=16&t=36525) how I compiled mine. (No git.)

---

