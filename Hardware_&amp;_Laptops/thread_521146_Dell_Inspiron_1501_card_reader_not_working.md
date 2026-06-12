---
title: "Dell Inspiron 1501 card reader not working"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by Baby Boy on 2007-08-09
Any suggestions? The Inspiron 1510 blog says that the problem is resolved, however, when I insert SD card it doesn't detect anything.

---

### Post by dje on 2007-08-09
What version of ubuntu are you using, if you have feisty it should work out of the box. Also what kernel do you have as the blog says there is a bug that stops it working in kernel 2.60? Hope this helps :)

---

### Post by Baby Boy on 2007-08-09
> **dje said:**
> What version of ubuntu are you using, if you have feisty it should work out of the box. Also what kernel do you have as the blog says there is a bug that stops it working in kernel 2.60? Hope this helps :)

I have Feisty Fawn 7.04 and no idea which kernel version. How do I update it?

---

### Post by dje on 2007-08-09
The default kernel in feisty is fine to find which you are using press esc at the GRUB loading screen at bootup, it will show a list of all installed kernels.

Go to the Filesystem and navigate to the folder 'etc', search for and open a file called modules, what modules are listed (beneath the hashed lines).

---

### Post by Baby Boy on 2007-08-10
Hmm, after trying to read a 128MB SD card it appears that my card reader *does* work :???: . The 2GB SD card is not recognized though - any idea why?

---

### Post by dje on 2007-08-10
[http://en.wikipedia.org/wiki/Secure_Digital_card#Compatibility_issues_with_2GB_and_larger_cards]("http://en.wikipedia.org/wiki/Secure_Digital_card#Compatibility_issues_with_2GB_and_larger_cards")
That could be why? Or you could try reformatting it? Hope this helps :)

---

### Post by Baby Boy on 2007-08-11
But I've tried it on WinXP and it works. How could formatting help?

---

### Post by dje on 2007-08-11
Sorry i can't provide a definitive answer, i can only suggest it is what is explained in the link i posted earlier. All the sd cards ive tried have worked, but they only went up to 256mb. :confused:

---

