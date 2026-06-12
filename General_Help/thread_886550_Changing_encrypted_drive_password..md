---
title: "Changing encrypted drive password."
date: 2008-08-11
forum: General Help
---

### Post by solwic on 2008-08-11
I encrypted my Ubuntu install and used a 21 character password.  As is the case with such things, I realized directly after confirming that password that, while it contained the proper mixture of length, letters, numbers, and punctuation, it was still ridiculously easy to associate to me for anybody who even has passing knowledge about me.  

So...can I change it?  I have been looking on Google, and found [this]("http://vaidab.blogspot.com/2007/10/add-second-passphrase-to-ubuntus.html"), but it doesn't really tell me how to do it.  

Anybody help me out here?  It's not *life-or-death* important or anything, but I probably should change the password out to something a little more difficult to guess.  

Thanks!

---

### Post by hyper_ch on 2008-08-11
The link you have shown does tell you exactely how to do it. You cannot "change" the password but you can (1) add a new password / keyfile and then (2) delete the original one.

You can store up to 10 different password / keyfiles to unlock the encrpyted partition.

---

### Post by solwic on 2008-08-11
> **hyper_ch said:**
> The link you have shown does tell you exactely how to do it. You cannot "change" the password but you can (1) add a new password / keyfile and then (2) delete the original one.

EDIT:  Nevermind, I see how he's laying that out.  I've never seen the hashmark used to indicate a prompt.  Still kinda new to this command line stuff.....

Anyway, thanks for pointing out the obvious.  :lolflag:

---

### Post by hyper_ch on 2008-08-11
-->  # cryptsetup luksAddKey /dev/sda5

---

