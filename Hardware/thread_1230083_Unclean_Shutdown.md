---
title: "Unclean Shutdown"
date: 2009-08-03
forum: Hardware
---

### Post by shyamsundar2007 on 2009-08-03
I have this very weird problem with Ubuntu and I'm really sick of it. What happens is, whenever I shutdown ubuntu, as the system prepares for shut down, it shows this small window with some message and a check box in it. I cannot read what the message says since my laptop witches off immediatly after that. When I boot up my laptop the next time, it tell me that there was an unclean shutdown and it runs the automatic fsck command. It then says that the fsck command has failed with exit 4. After I manually run fsck and restart my laptop, my laptop can never boot up properly after that. It always keeps running the fsck and then asks me to rum it manually again. I've even reinstalled ubuntu 3 times till now. Everytime I shutdown ubuntu and start it up again, I get this problem. Please tell me what the problem with ubuntu is and why I keep getting an error message just before shutdown. 
Thanks in advance!

---

### Post by hansdown on 2009-08-03
Hi shyamsundar2007.

Follow this thread, and look at the part in the screenshot.

Sorry to be cryptic.

---

### Post by shyamsundar2007 on 2009-08-03
when i followed the steps in the screenshot, i don't get the generic recovery option at all when i press the Esc key during the GRUB load. Am I doing something wrong here?

---

### Post by hansdown on 2009-08-03
You may need to** hold** ESC while it boots.

Don't worry, it won't hurt anything if you press and hold ESC as soon as you see "no signal" when you are restarting. 

Keep holding it until the boot list comes up.

You should see a black screen with white letters something like this;


```
ubuntu 9.04, kernel 2.6.28-14-generic
ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
```

I've only included the fist two lines from mine, because the second line is the one that is needed.

Just use the down arrow to scroll to the second line, and hit enter.

---

### Post by shyamsundar2007 on 2009-08-03
I tried the fsck command and recovered completely. I've actually done it several times already but what happens is whenever I shutdown my laptop, I get this error message and the same problem occurs again. I am not able to see the error message since the laptop shuts down before I can read it. SO every time I open my laptop I have to run fsck and the restart to get my desktop. Any help please?

---

### Post by wojox on 2009-08-03
Check you log files. /var/log

---

