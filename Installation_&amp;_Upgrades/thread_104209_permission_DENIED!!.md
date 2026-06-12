---
title: "permission DENIED!!"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by gl0be on 2005-12-15
Took me like 3 days to install linux on my low ram pc (im a newb). I have IceWM running and everything was swell. Got a few apps. Was having a good time.

Then today when i tried to download a file to my directory Mozilla said the directory was not writeable. Hmmm. Checked my other apps. Ran my file manager which wasnt aload to delete files. Its excuse was Permission denied.

So i rebooted in hope it was a one off error. Nope still there. Mocking me. Why don'y i have permision? Im the only user on the machine!

So maybe i can edit a file somewere or something to get my permisiion back? I'm not very good at the terminal so please have patience.

Help me Please :( :confused: :???:

---

### Post by kaamos on 2005-12-15
You only have write access to your home directory /home/**username**/

I suggest reading these:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)

If you download stuff with mozilla, save it in your home directory. :)

---

### Post by gl0be on 2005-12-15
thats the problem! My username is mero and im saving files to /home/mero/

My access is denied

---

### Post by kaamos on 2005-12-15
interesting.. but you can login to the system just fine?
Open a terminal and type
```
sudo chown mero:mero -R /home/mero
```
Enter your password. Then test if this worked for example by creating a new folder or file in your home directory.
Hope this helps.

---

### Post by gl0be on 2005-12-15
that did it, i can delete files again. Thx man i owe u.

---

### Post by neymac on 2005-12-15
[QUOTE=gl0be]Took me like 3 days to install linux on my low ram pc (im a newb). I have IceWM running and everything was swell. Got a few apps. Was having a good time.

Help me Please :( :confused: :???:[/QUOTE]
In Ubuntu Breezy 5.10 (Gnome) right click the file->select Properties
Select the permission tab an click "write" to allow you delete or modify the file.
I don't know if is the same in IceWM, maybe there is some like.

---

### Post by Hootman on 2005-12-15
I tried that one mine it says invalid user.  I used my name

---

