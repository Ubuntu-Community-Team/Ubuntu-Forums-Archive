---
title: "Terminal freezing root login failing"
date: 2008-08-09
forum: General Help
---

### Post by technotika on 2008-08-09
Hi Guys

Just when I thought my 5 days of fiddling getting everything working in ubuntu were over I am now stumped and need some advice.

I want to auto mount an NTFS drive however the little app that i found to use wont work due some non specific error. Therefore I want to edit the fstab file. When I go to sudo gedit /etc/fstab it just hangs blinking cursor where the password prompt should be.

So I enabled root log in  to log in as root and do it manually.
More trouble - login window has stopped appearing; type in root then password just hangs on skin colour and no desktop. I rebooted tried the same but when I open  terminal it just hangs turns black and dies. After that nothing works and I have to ctrl  - alt BKSP to launch a new log in.

I have got no idea whats caused or when it started as i have logged in as root a few times over the last few days to do stuff. The only thing that might have some bearing on it is that the last thing I did before it happened was try to set my HOME dir as a shared folder so that I could access it in my XP virtual Box. It barked at me about errors and when I tried to log in i got a wierd error about "$HOME.dmrc is being ignored", I searched forums and fixed that but then this - could they be related.

I would love a bit of help as over the last few days I have posted and no one has got back to me.

Version 8.04.01 - thanks alot.

---

### Post by technotika on 2008-08-10
No worrys figured it out - there was something fishy going with my NTFS drive causing this to not work

I backed up data  - wiped disk  - reformatted to ext3 restored data  - set the permissions and now I could log in as root also edit the fstab - sorted.

Thanks

---

