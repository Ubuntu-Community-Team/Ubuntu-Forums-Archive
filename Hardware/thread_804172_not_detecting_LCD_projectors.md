---
title: "not detecting LCD projectors"
date: 2008-05-22
forum: Hardware
---

### Post by Spooky_Kilt on 2008-05-22
So I have plugged in to LCD projectors to my new Dell laptop and it did not detect either of them.  

has anyone ever used an LCD projector with ubuntu and was there anything spicific you had to do to get it to work?

---

### Post by yochaigal on 2008-05-22
I've used a few...

First, shut your machine down.
Then, plug them in.
Startup.

Still nothing? Attach your regular monitor, then run:
displayconfig-gtk

Try and detect them that way.

---

### Post by Spooky_Kilt on 2008-05-25
alright thank you  i'll try that.

---

### Post by yochaigal on 2008-05-25
Note: you might have to run:

gksudo displayconfig-gtk

---

### Post by Spooky_Kilt on 2008-05-26
okey well i plugged in a regular monitor and it copies what is on my lap top screen until after i log in.  it then goes blank and the monitor says it's in power safe mode and that i have to activate with my PC.  i have tried restarting my lap top but the screen still goes blank after i log in.

---

### Post by yochaigal on 2008-05-28
Once it "goes blank" open up screen resolution and see if there is a second screen there.

Also, you can try running displayconfig-gtk and adding the screen there.
If you've got an nvidia card, run 
gksudo nvidia-settings
And you can configure it from there.

---

