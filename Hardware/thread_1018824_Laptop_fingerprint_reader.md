---
title: "Laptop fingerprint reader"
date: 2008-12-22
forum: Hardware
---

### Post by gramsyn on 2008-12-22
How can I set my laptop in Ubuntu to recognise my fingerprint?

---

### Post by hursto75 on 2008-12-22
Have you tried [https://wiki.ubuntu.com/ThinkFinger?](https://wiki.ubuntu.com/ThinkFinger?)

Might help.

Thanks,
Brad K.
[http://www.techjaws.com](http://www.techjaws.com)

---

### Post by zephyrcat on 2008-12-22
If you purchased a Dell computer with Ubuntu, it should already be installed. You just need to set it up. (There are instructions in a PDF file located in one of the folders on your desktop.) If not, just ignore this.

---

### Post by gramsyn on 2008-12-22
Thanks. I have checked the page and I can do it till the midway. I can scan and validate my fingerprint. But I cannot understand how can I set it temporarily at log in. Can you help? I cannot understand what the page you suggested says.
Thanks in advance

---

### Post by zephyrcat on 2008-12-22
What point do you have trouble with? If you have a Dell that came with Ubuntu, you just need to restart your computer. It should be the same if you are using Intrepid Ibex. If you are using Hardy Heron, the page indicates that you may need to issue the following command:

sudo tf-tool --add-user *your username here*

Then reboot and let us know if it works.

---

### Post by gramsyn on 2008-12-22
I try to modify the file common-auth, but I can't save it. The following message appears:

Could not save the file /etc/pam.d/common-auth1.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by gramsyn on 2008-12-23
Please someone help me. What should I do? I open the file from the nautilus. Should I use a command from the console to edit it?

---

### Post by zephyrcat on 2008-12-23
I doubt you have to modify that file. The ThinkFinger page says this:

> NOTE: This step is not needed and won't work in ver. 0.3 and superior. 

If you do have to modify it, enter this command to launch nautilus in root mode:

```
gksudo nautilus
```

(Just for interest, you can learn about gksudo here: [http://ubuntulinuxhowto.blogspot.com/2006/06/root-access-with-sudo-and-gksudo.html](http://ubuntulinuxhowto.blogspot.com/2006/06/root-access-with-sudo-and-gksudo.html) )

---

