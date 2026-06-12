---
title: "Problems with Ubuntu 5.10 live CD - Newbie"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by spock2263 on 2005-12-28
Hi there!
I have some problems with 5.10 LiveCD:
I have an Acer Aspire 1693.
When I try to boot with the default live system it starts booting and after a few seconds I get the message: 'Uncompressing Linux...ok, booting the kernel' and then nothing at all happens.
When I type live acpi=off it boots ok,I choose language, keyboard, everything normal etc., etc., but just before start working with ubuntu I get a black scree and then nothing at all again!!!
I have no idea what to do, can you help me?

PS: I'm sorry if my english is not very good

Thanks for your time

---

### Post by Sef on 2006-01-05
1) You could have a bad CD.

2) Did you try to boot with another Live CD?  If the same problem comes up, then likely a hardware problem.  (Especially if you use 2 or 3 different ones with different bases:  Ubuntu basis is debian, vectorlinux is slackware, etc.)  

3) Your English is fine.   I had no problem understanding what you wrote.

---

### Post by ysse on 2006-01-06
On some machines, you need extra boot options like the acpi=off, that you've tried. I tried a quick google, and found a site, for some other Linux, but an Acer Aspire 1693, ([http://www.uni-koblenz.de/~ceinig/index.php?site=acer1693wlmi_en]("http://www.uni-koblenz.de/%7Eceinig/index.php?site=acer1693wlmi_en")) that gives the options ```
apm=power-off nomce vga=0x317
```

Don't ask me what "nomce" means. The vga setting is probably needed, though. You really won't break anything as long is it the live CD.

Good luck.

---

### Post by spock2263 on 2006-01-11
Thanks a lot guys. 
I tried this commands but I have the same problem
I've also installed 5.10 and I had the same problem and when it freezed I pressed Ctrl-Alt-F1, I put my username and password and then I got this: jim@ubuntu:~$ (jim is my username). What I should type?

---

