---
title: "Xonar DG no sound output"
date: 2015-01-22
forum: Hardware
---

### Post by Farinetes on 2015-01-22
Hi, I recently returned to the ubuntu world to check the improvements since my last linux experience (2008).
But, as usual, I have a problem, this time with my sound card, a ASUS Xonar DG. I just don't hear a sound from the speakers.
I googled a lot and I found an interesting bug report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1385770](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1385770) 
i'll quote:
> Using QasMixer to change the analog output to multichannel fixed the the no sound problem for me. It was set on headphone FP.

So i installed QasMixer but after trying some configs I gave up, nothing to hear here...
This is my current configuration:
[IMG]http://i62.tinypic.com/15wfith.png[/IMG]
What should I do?

Thanks a lot ;)

EDIT: I'm using Ubuntu 14.04.1 kernel 3.14.10

---

### Post by Yellow Pasque on 2015-01-22
Your screenshot doesn't even show the Xonar card.
Try this for more detailed information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Farinetes on 2015-01-22
Ok, I did it, let's see if it helps:
[http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695](http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695)

Just in case, the Xonar DG is plugged in a Gigabyte GA-970a-DS3P (rev.1)

---

### Post by ajgreeny on 2015-01-22
Your posted link seems to be faulty and goes nowhere; can you check it please.

---

### Post by Yellow Pasque on 2015-01-22
The kernel module is not loading. What happens when you try to load it manually?
```
sudo modprobe -v snd-oxygen
```

Is there a reason you're running a non-standard kernel?

---

### Post by Yellow Pasque on 2015-01-22
> **ajgreeny said:**
> Your posted link seems to be faulty and goes nowhere; can you check it please.

It worked for me (maybe edited?).
[http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695](http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695)

---

### Post by ajgreeny on 2015-01-22
> **Temüjin said:**
> It worked for me (maybe edited?).
[http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695](http://www.alsa-project.org/db/?f=684f279a380a5ebd360d4f09bbc1970b83f6e695)

It also works for me now, but it did not before.

---

### Post by Farinetes on 2015-01-22
> **Temüjin said:**
> The kernel module is not loading. What happens when you try to load it manually?
```
sudo modprobe -v snd-oxygen
```

Is there a reason you're running a non-standard kernel?

Because of this: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus) (suported since 3.14)
Now i have to go outside, but in a couple hours i'll load the kernel module and post the result.

---

### Post by phodges on 2015-01-22
I am watching this thread as I have the same problem.  I noted the bug and also a patch from March, and tried using the QasMixer fix.  If forthcoming info in this thread doesn't help I will post another thread.  Here is another solution which I have not had the opportunity to try, but you could try:

"I would go about running **alsamixer**, selecting the sound card using **F6** and trying **all** the different options and switches.  Once the culprit is found the defaults can be fixed."----"Thanks this did it! I selected Xonar DG then I switched Analog Output from Headphones to Multi-Channel."

---

### Post by Yellow Pasque on 2015-01-22
\nbm

---

### Post by Farinetes on 2015-01-23
[IMG]http://i59.tinypic.com/244yujm.png[/IMG]
I don't know if it helps, but i ran alsainfo again after that:
[http://www.alsa-project.org/db/?f=7fe96dfe928259a050d35816a15d6976a1da2838](http://www.alsa-project.org/db/?f=7fe96dfe928259a050d35816a15d6976a1da2838)

P.S. Running alsamixer and F6 doesn't work, Ubuntu doesn't seems to recognize my Xonar DG yet.

---

### Post by phodges on 2015-01-23
Farinetes it looks like it has the correct drivers installed.  When you run alsamixer, and select f6, does the xonar show up?  If it does, the then right arrow over to Analog Output and up arrow from Headphones to Multi-Channel.  This allowed me to get sound out of the "front" 5.1 sound 3.5mm jack

---

### Post by Yellow Pasque on 2015-01-23
This one has me stumped. The kernel module/driver loads without complaint, but the the card doesn't show up in aplay? Strange..

> When you run alsamixer, and select f6, does the xonar show up?

If you look at the alsa info, the card doesn't show up in a aplay -l, so it's not going to show up in alsamixer either.

---

### Post by Farinetes on 2015-01-25
No it doesen't 
[IMG]http://i59.tinypic.com/2mgtx8l.png[/IMG]

---

