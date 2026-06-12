---
title: "Microphone input"
date: 2010-01-25
forum: Hardware
---

### Post by csk157 on 2010-01-25
Hello,

I have a problem with my mic, I can hear it through my speakers very well, but nor skype, nor sound recorder are able to "hear" it. 

Settings seems to be ok (I've read lots of threads, an googled).
alsamixer (yes, mic is connected to the front):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144905&stc=1&d=1264410375[/IMG]

sound preferences:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144906&stc=1&d=1264410375[/IMG]

And I had also had some luck with Pulse manager, I managed to get my mic to work properly, but unfortunately only for ~10 minutes.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144907&stc=1&d=1264410375[/IMG]


The first source seems to work (volume meter of it differs depending on mic).
And the second one - doesn't.

I'm using Ubuntu 9.10

---

### Post by gradinaruvasile on 2010-01-25
If you tap the microphone when the volume properties is open, do the input volume indicator bars move?

Also, what hardware you have? Post the output of 

lspci

in a terminal

---

### Post by csk157 on 2010-01-25
I think I have solved the problem after checking and unchecking number of boxes, and million times restarting computer. Now it seems to work as it has to.

By the way **gradinaruvasile** thanks for your reply.

---

