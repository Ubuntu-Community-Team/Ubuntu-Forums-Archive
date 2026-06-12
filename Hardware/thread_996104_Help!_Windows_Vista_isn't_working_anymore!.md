---
title: "Help! Windows Vista isn't working anymore!"
date: 2008-11-28
forum: Hardware
---

### Post by Andrew1989 on 2008-11-28
I couldn't really find a better forum to make this thread in, so please bear with me.

I installed Ubuntu on my Dell Studio 15 laptop. Everything was working swell. But one day, when I wanted to use Windows Vista, something incredibly odd happened. The Desktop and user settings were back to exactly the way they were when I first got the computer. All the program files were still intact, but not my user profile. I could do something like change the desktop background, but when I rebooted it was back to nothing. I'm pretty sure Ubuntu had something to do with this, but I wouldn't know what.

Recently, things have taken a turn for the worse. Whereas once it logged in but with nothing for user settings, now it tells me that the client server won't allow me to log in to the only user account I have for Vista. I have no way of getting into Windows now!

Has this issue ever been encountered before? I wouldn't mind having to full-system restore my Vista installation to get back to normal, but I'm pretty sure even *THAT* has to be done from inside Windows.

Please help me.

---

### Post by sergiom99 on 2008-11-29
Andrew, not many of us use Windows, or at least Vista.
I think you might find better help in the Dell support forums.
I could guess that in order to do a system restore you need a restore disc or a restore partition. (at least thats how it works in HP)
Good luck.

---

### Post by cdtech on 2008-11-29
Are you booting through the GRUB bootloader?

---

### Post by finito on 2008-11-29
You managed to do something that is very easy (Break vista). You could just repair reinstall. But it seems to be another problem, When you installed Ubuntu did you resize the harddrive to make a partition or did you have a partition from before. How old is the drive with vista installed. Try running chkdsk on the vista drive.

---

### Post by TheLions on 2008-11-29
> **Andrew1989 said:**
> I couldn't really find a better forum to make this thread in, so please bear with me.

I installed Ubuntu on my Dell Studio 15 laptop. Everything was working swell. But one day, when I wanted to use Windows Vista, something incredibly odd happened. The Desktop and user settings were back to exactly the way they were when I first got the computer. All the program files were still intact, but not my user profile. I could do something like change the desktop background, but when I rebooted it was back to nothing. I'm pretty sure Ubuntu had something to do with this, but I wouldn't know what.

Recently, things have taken a turn for the worse. Whereas once it logged in but with nothing for user settings, now it tells me that the client server won't allow me to log in to the only user account I have for Vista. I have no way of getting into Windows now!

Has this issue ever been encountered before? I wouldn't mind having to full-system restore my Vista installation to get back to normal, but I'm pretty sure even *THAT* has to be done from inside Windows.

Please help me.

what happened?
you went to system restore instead to Windows. Why? Because GRUB didn't recognized properly your partition, had similar mess.
No it needs to run outside Windows.
How? I don't know, i would try installing GRUB again and then run it fro there.
Hope I helped.

---

### Post by TheLions on 2008-11-29
> **Andrew1989 said:**
> I couldn't really find a better forum to make this thread in, so please bear with me.

I installed Ubuntu on my Dell Studio 15 laptop. Everything was working swell. But one day, when I wanted to use Windows Vista, something incredibly odd happened. The Desktop and user settings were back to exactly the way they were when I first got the computer. All the program files were still intact, but not my user profile. I could do something like change the desktop background, but when I rebooted it was back to nothing. I'm pretty sure Ubuntu had something to do with this, but I wouldn't know what.

Recently, things have taken a turn for the worse. Whereas once it logged in but with nothing for user settings, now it tells me that the client server won't allow me to log in to the only user account I have for Vista. I have no way of getting into Windows now!

Has this issue ever been encountered before? I wouldn't mind having to full-system restore my Vista installation to get back to normal, but I'm pretty sure even *THAT* has to be done from inside Windows.

Please help me.

what happened?
you went to system restore instead to Windows. Why? Because GRUB didn't recognized properly your partition, had similar mess.
No it needs to run outside Windows.
How? I don't know, i would try installing GRUB again and then run it fro there.
Hope I helped.

---

