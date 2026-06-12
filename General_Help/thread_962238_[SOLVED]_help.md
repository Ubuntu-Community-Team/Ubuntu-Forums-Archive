---
title: "[SOLVED] help"
date: 2008-10-29
forum: General Help
---

### Post by Faleena on 2008-10-29
i cant remember my username/password...

is there any way i can recover my username??

someone please help...




i'm totally new to ubuntu... i know a little bit about command lines and stuff can anyone help...
i tryed looking thru the normal support from the ubuntu website but i didnt really get any where with it...

---

### Post by Xiong Chiamiov on 2008-10-29
[clicky]("http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/")

---

### Post by Faleena on 2008-10-29
is there anyway to recover a lost username??

or is reinstalling the only solution???

---

### Post by Sam on 2008-10-29
Did you look at Xiong Chiamiov's link ?

---

### Post by nitrousoxide82 on 2008-10-29
You may want to boot the system in recovery mode, and choose "root" to drop to the root shell prompt. First, you can try [font="Courier New"]ls /home[/font]. This will list the "home directories" for all users. This may help you remember.

If it doesn't, then look at [font="Courier New"]/etc/passwd[/font] with a text editor. By default, the first user account created will have user ID 1000, so look for a line containing the number 1000 (along with other things) or, look for the "full name" you entered when creating your account. This will help you remember your username. Close the text editor, and make sure you DO NOT change/save the file.

Then, having just recovered your username, and still in the root shell prompt, type [font="Courier New"]"passwd *username*"[/font], where *username* is your username. This will create a new password for your username. Enter it, and that takes care of the password.

Hope this helps.

---

### Post by Faleena on 2008-10-29
ty nitrousoxide82 i'll try what you suggested

---

### Post by Faleena on 2008-10-29
Thank you nitrousoxide82!!!! that worked!!:KS

---

