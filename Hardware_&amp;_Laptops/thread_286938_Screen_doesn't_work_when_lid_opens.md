---
title: "Screen doesn't work when lid opens"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by brohan on 2006-10-28
Hi,

I've got a d420 which is running Xubuntu which I recently upgraded to Edgy.

In dapper somewhere along the line when I opened my laptop lid I got a blank screen, I didn't worry too much and I pressed CTRL-ALT-F1 then CTRL-ALT-F7 to go back to an already running X. Now under edgy whenever I close the lid and open it again nothing comes up, I haven't ssh'd in to see if X has crashed or anything (yet)

I think my issue lies in /etc/acpi/resume.sh (/etc/acpi/resume.d), though I don't know how to fix it. I have not tried suspend or hibernate since the edgy upgrade. I am using 915resolution which may mean something.

Thanks for any help!

---

### Post by GStubbs43 on 2006-10-28
Hi, I had the exact same problem with Dapper and Edgy! I just fixed it like 1 minute ago so I'm not sure exactly how well this works, but it works so far!

Just do 
```
sudo cp /etc/acpi/lid.sh /etc/acpi/lid.sh.bak
```
then
```
gksudo gedit /etc/acpi/lid.sh 
```
Erase the entire thing, and replace it with this:

```

#!/bin/sh

# turns the screen off on lid close & on on lid open

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        /usr/sbin/vbetool dpms off
else
        /usr/sbin/vbetool dpms on
fi

```
then save.

I hope this works for you!

---

### Post by antealin on 2006-11-03
Wow! Thanks a lot for that!
Seems like it works for me aswell :)
I didn't have this problem with Dapper, but now when I upgraded to Edgy, I noticed some things didn't work as before. :)
Thanks, once again :)

---

### Post by insub2 on 2006-11-11
GStubbs43,
just thought i'd mention my gratitude for you fixing my problem.  thanks.

---

### Post by dolphinsonar on 2006-11-21
Thank you!  That was a problem I had lived with for 6 months before I got a fix.

I used to have to press Ctrl Alt F1 then Ctrl Alt F7 almost everytime I opened my laptop lid, which was quite a pain, since I get up, close my laptop and go somewhere else to open it numerous times in a day.

sticky this!  Great solution.

---

### Post by Tannwald on 2006-11-27
I had same problem after upgrading.Now it's solved.Thanx a lot!:)

---

