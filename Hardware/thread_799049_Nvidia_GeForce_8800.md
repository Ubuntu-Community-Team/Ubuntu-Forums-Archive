---
title: "Nvidia GeForce 8800"
date: 2008-05-18
forum: Hardware
---

### Post by FaresH on 2008-05-18
Hi, 

I have ubuntu for a month now, and it worked fine until a week or 2 ago. It seems that the OS doesn't recognize my graphic card. I mean I get a low resolution. I can only use the 640*640 resolution. 

On windows my graphic card just works perfectly. 

Can you help me ? Or even point me to what may be the problem ?

---

### Post by sdennie on 2008-05-18
Did you manually download and install the nvidia drivers from the nvidia website?  If so, that could be your problem.  You may want to install envyng and let it install the drivers for you to see if it fixes your problem:

```

sudo apt-get install envyng-gtk

```

Then, you can either run the following from X:

```

envyng-gtk

```

Or this from the command line:

```

envyng

```

---

