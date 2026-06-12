---
title: "Cannot mount USB 2.0 External Hard Drive"
date: 2008-05-05
forum: Hardware
---

### Post by Ed933 on 2008-05-05
I plug in my Ritmo 320GB hard drive to the computer running Ubuntu Hardy, and a dialog bosx pops up saying : 

"Unable to mount the volume 'External Hard Drive'."

and then it goes on my saying 

"$LogFile indicates unclean shutdown (0,0) .................."

then another box pops up saying

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." 

I have tried unmounting it properly in windows but it still pops up?!

---

### Post by Arasfang on 2008-05-05
Try adding *force* to the options when mounting, that helped me.

/Mattias

---

### Post by Ed933 on 2008-05-05
Thanks for your reply Arasfang 

but ... sorry to be such a noob, but how do I add the force option while mounting it? Is it an option in the gui or do I have to go into the console?

---

### Post by argeas on 2008-05-07
same prob here and also noob!!!  with my 250gb wd usb external drive......

:( :(

---

### Post by vanadium on 2008-05-07
Don't use force, except for reading the data temporarily to another medium before a reformat.

Boot back into Windows, shut down Windows completely. If that doesn't work, boot back to Windows, have the drive checked using the appropriate tools, then shut down Windows completely. After that, it will mount automatically because it was properly "closed".

---

