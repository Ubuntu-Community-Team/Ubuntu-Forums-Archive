---
title: "Setting Nvidia ptimus on new netbook?"
date: 2011-07-02
forum: Hardware
---

### Post by rodvil on 2011-07-02
Hello.

I have a new netbook, Asus eeepc 1015PN. This asus has the new Nvidia Optimus technology. It has 1 Intel and 1 Nvidia and supposedly it can change between them according to the needs.
I read about a linux solution for this Optimus,something called bumblebee.
But honestly I can't really understand it at all.
Can anyone help me to set this up on my netbook?

Or is there any other solution to switch between the 2 graphic processors?

I'm running a fresh install of Lubuntu 11.04 (32bit) (tried the new ubuntu for a week but wasn't happy at all)

Thanks!!

---

### Post by wolfen69 on 2011-07-02
Open a terminal and copy and paste the following:
```
git clone http://github.com/MrMEEE/bumblebee.git
```
then
```
cd bumblebee/
```
then
```
sudo ./install.sh
```

---

### Post by rodvil on 2011-07-02
Thanks for the reply.

It seams it installed correctly.
How do I change from one to the other? Is there any interface to choose or does it change automatically?

---

### Post by wolfen69 on 2011-07-02
If no one can answer how to switch, perhaps you could ask [here]("http://forums.nvidia.com/index.php?showtopic=203600").

---

### Post by mtron on 2011-07-10
bumblebee uses intel as primary gpu and if you want to use the nvidia gpu start an application with optirun32 <application>

see: [https://github.com/MrMEEE/bumblebee#readme](https://github.com/MrMEEE/bumblebee#readme)

---

### Post by rodvil on 2011-07-27
I still can't get this thing to work!
Is there any way to make the Nvidia the default graphic card and just use that one all the time?
It will be shorter battery life but it should give me a better performance.

If anyone knows how to do this, thanks!

---

### Post by mtron on 2011-07-27
> Is there any way to make the Nvidia the default graphic card
yes, there is. 

See: [http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)

---

