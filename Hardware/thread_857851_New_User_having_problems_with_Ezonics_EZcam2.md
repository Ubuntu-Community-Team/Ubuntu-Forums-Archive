---
title: "New User having problems with Ezonics EZcam2"
date: 2008-07-12
forum: Hardware
---

### Post by enak19 on 2008-07-12
Afternoon everyone...I am a brand new Linux user, who is having a lot of trouble setting up my webcam to work on Linux...everything I try seems to fail...I have an Ezonics EZcam2...running a Dell Inspiron Notebook...if anyone could give me a hand, I'd really appreciate it.

---

### Post by matt$2 on 2008-07-13
Well I've been there done that.  I spent months getting my webcam to work.  It's all a matter of acquiring the driver package.

There is a website somewhere dedicated to listing webcams and the linux compatable drivers they require.  I used it ages ago. I can't just supply it.  This is your task.

Hit google,  enter your make and model as keywords.  Persevere until you FIND IT.  I did.

Then you're almost there.

---

### Post by renfrew on 2008-09-02
Enak, if you're still having trouble, I think the site that matt referred to is: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams).  I haven't had much luck getting my EZCAM2 to work yet either, not to say it won't work eventually ;)

---

### Post by IntuitiveNipple on 2008-09-02
Guys, please give some details so people can help you. Brand names doesn't help here, we need to know the unique PCI <vendor>:<product> IDs. You can report that simply by running the following commands:
```

lspci -nn

lsusb

udevinfo --query=all --name=/dev/video0 --attribute-walk

```

---

