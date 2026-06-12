---
title: "I don't quite understand the issue."
date: 2013-10-29
forum: Hardware
---

### Post by Teethdude on 2013-10-29
While booting Ubuntu an odd stream of errors occured on a black screen.
It finally did boot but gave me an error. My only clue is something to do with Suspend/Resume.
Here are a couple of photos of the screen. The resolution isn't terrible.
[ATTACH=CONFIG]247351[/ATTACH][ATTACH=CONFIG]247352[/ATTACH]

---

### Post by 3rdalbum on 2013-10-29
If it did actually resume as expected, then any error messages are irrelevent.

---

### Post by grahammechanical on 2013-10-29
The messages that you saw on the black screen are not necessarily error messages. They could well be the usual Linux system messages. We do not usually see most of these messages because they are covered by a splash screen but it might be different when resuming from suspend.

Your other photograph shows the Apport crash reporting utility in action. Usually Apport is disabled by default in stable releases. It is usually enabled for development releases so that developers can get notice of bugs before the next version is released. So, I do not know why Apport is triggering on your system.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

> this occurred during a previous suspend and prevented it from resuming properly

Did you notice anything different during the suspend?

There is something else that I do not understand. Perhaps you could give more information. The Apport dialog says that you are running Ubuntu 13.10 but that you are using Linux-image 3.8. I ran 13.10 from the beginning of its development cycle until it was released, It is my understanding that 13.10 was released with Linux-image 3.11.

You may find that if you load into Linux-image 3.11 that any bugs with suspend/resume may have been fixed. But then again they may not have been.

Regards.

---

### Post by Teethdude on 2013-10-31
Things seem to be ok right now. I'll try checking the Kernal image number.

---

