---
title: "Webcam can only show 720p image, although 3200x2400 Pictures are supported"
date: 2014-01-21
forum: Hardware
---

### Post by B_Tutzer on 2014-01-21
Hello to you all,
I just bought a Tecknet C016 Webcam from Amazon. My Ubuntu recognized it right away, but Cheese and other Programs can only take 720p Pictures. on the Packaging it says:
"-Webcam with 1280x720 hardware resolution for sharp image. ideal for MSN/Live Messenger, Skype, etc.
 - Up to 7.6 mega pixels resolution Image Capture: 3200x2400 Resolution (Enhanced by the Software)"
What Software can I use to Enhance the Pictures? Is it worth the work or will the Pictures be just as bad?
Thanks

---

### Post by sudodus on 2014-01-21
I think it means that you can create video with the resolution 1280x720 (p means progressive, opposite to interlaced) and photos with the resolution 3200x2400.

Try more with the available software, I think you'll find ways to create videos and photos according to the specs. Otherwise come back, and you'll get more advice :-)

---

### Post by B_Tutzer on 2014-01-23
That's the problem. There is no available software for linux, I can only use v4l2. With Mac OS X and Microsoft Windows I get better quality and higher Resolution Images.
Is there any software better than v4l2 that I can use?

---

### Post by sudodus on 2014-01-23
Can Cheese take only 1280x720 pictures (photos)?

Maybe the problem is that you have found no good linux program that can manage that webcam. Support for peripheral devices is one of the weak spots of linux, due to lack of interest from the manufacturers of those devices. But someone reading this might have a good suggestion.

What about the simple tool ***Guvcview*** available in Lubuntu? It works with a built-in webcam in my Toshiba laptop (it supports video4linux2, I don't know if it can do more advanced things with your camera).

---

### Post by amandaallen243 on 2014-05-06
> **B_Tutzer said:**
> Hello to you all,
I just bought a Tecknet C016 Webcam from Amazon. My Ubuntu recognized it right away, but Cheese and other Programs can only take 720p Pictures. on the Packaging it says:
"-Webcam with 1280x720 hardware resolution for sharp image. ideal for MSN/Live Messenger, Skype, etc.
 - Up to 7.6 mega pixels resolution [[COLOR=#272727]Image Capture[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/"): 3200x2400 Resolution (Enhanced by the Software)"
What Software can I use to [[COLOR=#272727]Enhance the Pictures[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/sdk-programming/")? Is it worth the work or will the Pictures be just as bad?
Thanks

Have you found desired software to solve this issue? Have you read this article?:KS

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

