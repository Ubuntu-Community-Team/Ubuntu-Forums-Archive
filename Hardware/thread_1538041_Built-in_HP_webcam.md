---
title: "Built-in HP webcam"
date: 2010-07-24
forum: Hardware
---

### Post by RockerForLife20 on 2010-07-24
Hey, so I've installed ubuntu on my HP HDX computer. And it's pretty amazing. Only concern I have is that my built-in webcam does not work. I have tried installing v4l-dvb modules, and it worked once when I did that, also one time in the past it worked. But now it does not work. I have tested it with cheese, and when I start cheese it just closes out. How do I get my webcam to work in ubuntu?

---

### Post by mikewhatever on 2010-07-24
Run 'gstreamer-properties' in a terminal window, perhaps you can select v4l-dvb under video input there.

---

### Post by RockerForLife20 on 2010-07-24
I typed gstreamer-properties into the terminal. A box with two tabs came up. I clicked on the tab that said video, and looked at my choices, but my only two choices were v4l and v4l2. No v4l-dvb. Also, when I tested my webcam, it didn't show a picture.

---

### Post by mikewhatever on 2010-07-24
Try this walk-through.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by RockerForLife20 on 2010-07-24
I've tried that link. Right now I'm trying to install Easycam as the link suggested. Hopefully that works. If not, do you have any other suggestions?

---

### Post by RockerForLife20 on 2010-07-24
Just an update. Easycam isn't installing. But I'll keep trying.

---

### Post by mikewhatever on 2010-07-25
The only other suggestion I can think of is Google.;)
Search for your laptop model, as someone had likely had a similar problem.

---

