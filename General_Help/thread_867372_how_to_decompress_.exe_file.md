---
title: "how to decompress .exe file?"
date: 2008-07-22
forum: General Help
---

### Post by chunchengch on 2008-07-22
I download a Windows .exe file, and I just want to decompress it to get some images in it, so is there any way to make it?

I have tried msexpand, but it does not work.

Thanks for help.

---

### Post by Dr Small on 2008-07-22
An exe is a Windows binary. You can't decompress them.

---

### Post by Joeb454 on 2008-07-22
You can install Wine to *run* them, but Dr Small is right, you can't decompress .exe files (not that I know of anyway)

---

### Post by chunchengch on 2008-07-22
I see, thanks a lot.

---

### Post by Dave-ie on 2008-09-14
Sorry for bring up a old thread, but I did came across this question when looking for the same answer. I found the answer.

Yes, you can decompress a .exe file. Just use the command **msexpand *[file name...]***.

Make sure a program called *mscompress* is installed, it should be installed, if not you should find it in the *Synaptic Package Manager* under *Cross Platform*.

Hope this helps...

----
-Dave

---

### Post by lisati on 2008-09-14
> **Dave-ie said:**
> Sorry for bring up a old thread, but I did came across this question when looking for the same answer. I found the answer.

Yes, you can decompress a .exe file. Just use the command **msexpand *[file name...]***.

Make sure a program called *mscompress* is installed, it should be installed, if not you should find it in the *Synaptic Package Manager* under *Cross Platform*.

Hope this helps...

----
-Dave
+1

> **Dr Small said:**
> An exe is a Windows binary. You can't decompress them.
What about self-extracting archives?

---

### Post by chunchengch on 2008-09-14
> **Dave-ie said:**
> Sorry for bring up a old thread, but I did came across this question when looking for the same answer. I found the answer.

Yes, you can decompress a .exe file. Just use the command **msexpand *[file name...]***.

Make sure a program called *mscompress* is installed, it should be installed, if not you should find it in the *Synaptic Package Manager* under *Cross Platform*.

Hope this helps...

----
-Dave


Thanks for reply, but I try command msexpand again, and it still give me the error message as follows:

[COLOR="Red"]$ msexpand fishpassionsetup.exe[/COLOR]
[COLOR="Green"]fishpassionsetup.exe: Doesn't end with underscore -- ignored[/COLOR]

---

