---
title: "Where are the init files?"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by ollijav on 2006-02-03
Because my machine is terribly slow, I decided to install Xubuntu. So far everything seems to go all right, but the instructions tell me:

"Optional: if your computer is terribly slow, you do not need to install gdm nor kdm. Just start xfce with a command startxfce4 or just type xserver. For automating this, put it into the init files."

Of course I want to automate it. Only they don't tell me where the init files are!

---

### Post by MartinG on 2006-02-03
/etc/init.d contains the actual init files, and they are executed by symlinks in rc0.d through rc6.d.  You would put your script in init.d and then a link in rc2.d (Ubuntu's normal run level is 2).  If you call the link S99<script-name> it should be executed after everything else.

---

### Post by ollijav on 2006-02-04
I found the folders called init.d and rc2.d, but they were full of files written in a language unknown to me (whose skills only consist of HTML and PHP). Editing an existing file does not overcome my minuscule abilities, but writing a whole new file seems like a gigantic challenge.

Moreover, I have no idea whatsoever about how to make a link, as you told me.

So, if you, dear MartinG, or someone else, would be so kind to give me exact instructions on how to accomplish these two tasks, I'd be very grateful.

If I ever will have xfce4 run automatic on the startup, I definitely will write to wiki.ubuntu.com/InstallingXubuntu and ask them to add your instructions on their page. The actual installation is very well explained, but the most difficult part is given only as a passing remark.

---

### Post by Koybe on 2006-02-04
You can use the update-rc.d command to add/remove script from runlevel.

---

### Post by ollijav on 2006-02-04
Obviously this is a step to the right direction. I found some instructions on how to use update-rc.d, but since I am nearly linux-illiterate (learning more and more everyday, though), I feel very reluctant to mess around (I still need quite a lot of experience before I am able to decipher these instructions). Do you think you could give me the exact command I should type on the cammand line?

---

### Post by MartinG on 2006-02-04
[QUOTE=ollijav]I found the folders called init.d and rc2.d, but they were full of files written in a language unknown to me (whose skills only consist of HTML and PHP). Editing an existing file does not overcome my minuscule abilities, but writing a whole new file seems like a gigantic challenge.

Moreover, I have no idea whatsoever about how to make a link, as you told me.

So, if you, dear MartinG, or someone else, would be so kind to give me exact instructions on how to accomplish these two tasks, I'd be very grateful.

If I ever will have xfce4 run automatic on the startup, I definitely will write to wiki.ubuntu.com/InstallingXubuntu and ask them to add your instructions on their page. The actual installation is very well explained, but the most difficult part is given only as a passing remark.[/QUOTE]Your file can be much less complex than the ones you found, at the possible risk of it "falling over".  All you need in init.d is a simple script to launch xfce:

Step 1. Check which folder the command "startxfce4" is in.  You can do this by running "locate bin/startxfce4".  For the sake of argument, assume it's in /usr/bin (if not, modify Step 2 accordingly).

Step 2. Create a new text file in /etc/init.d (you'll need to use sudo or be working as root), called startxfce, and edit it to include the following lines:```
#! /bin/sh

/usr/bin/startxfce4
```

Step 3. Save the file and make it executable:```
sudo chmod +x /etc/init.d/startxfce
```

Step 4. Add it to the rcN.d folders:```
sudo update-rc. startxfce defaults 99
```

Hopefully that's it:) 

Update-rc.d has taken care of the symlinks, but if you ever need to do it by hand the syntax is:```
ln -s /folder/where/file/is/filename /folder/where/link/will/be/linkname

e.g.

ln -s /etc/init.d/startxfce /etc/rc2.d/S99startxfce
```

---

### Post by Huubke! on 2006-03-19
Hey, thanks, that works well.
Only thing is that now root is the active user in xfce4 instead of litte old stupid (as in breaking stuff) me
Any suggestions? (without having to put g/kdm on it)

---

