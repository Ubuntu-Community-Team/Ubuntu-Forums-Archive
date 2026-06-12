---
title: "Bug in 8.04 ??"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by ottawa on 2009-08-16
Hello forum,

I am back to ubuntu (newbie) with a new install of 8.04 today. 
By setting my preferences for a screen saver I got my ubuntu machine stalled. Nothing was possible anymore, except to pull the plug and start again.
What I did:
 I searched through the screensaver options and the screensaver "molecule" is the ONLY one which is creating the problem.

After the new start the system is back, but going to "screensaver" I am presented with the last window when the machine stalled. That is, when the screensaver "molecule" is shown in the right hand window, NO preview of full screen. Again, only pulling the plug is the only option to stop and start.

Did others have the same problem ?
What can be done ? I am not afraid to work with the terminal, BUT need proper instructions.

For now: DON'T touch the screen saver "molecule" and one is toast.

Johannes

---

### Post by RedSingularity on 2009-08-16
Is your system fully updated?

```
sudo apt-get update

```

---

### Post by ottawa on 2009-08-16
thank you for the quick reply.
Yes, the system was updated.

Johannes

---

### Post by RedSingularity on 2009-08-16
You can try reinstalling the screen saver software.

Remove with.....

```
sudo apt-get autoremove gnome-screensaver

```

And reinstall it with.....

```
sudo apt-get install gnome-screensaver
```

---

### Post by ottawa on 2009-08-17
> **Shadow121 said:**
> You can try reinstalling the screen saver software.

Remove with.....

```
sudo apt-get autoremove gnome-screensaver

```

And reinstall it with.....

```
sudo apt-get install gnome-screensaver
```


thank you for the info, but unfortunately this didn't help. The problem still exists. To test it, I scrolled through the preview, the picture of the "molecule" screensaver is presented on the screen but immediately I got a non responding machine. The only thing left is moving the mouse.

So, either no gnome screensaver package 2.22.2 0ubuntu1  or not even touching the "molecule" screen saver. 
Something for the Devs to correct ?
Where would I have to post this to make aware of it ?

Johannes

---

### Post by RedSingularity on 2009-08-17
You post bug reports [here]("https://launchpad.net/")  

If you want though before you do that try one more thing......


```
sudo apt-get autoremove gnome-screensaver
```

```
sudo apt-get purge gnome-screensaver
```

```
sudo apt-get install gnome-screensaver
```

---

### Post by ottawa on 2009-08-17
> **Shadow121 said:**
> You post bug reports [here]("https://launchpad.net/")  

If you want though before you do that try one more thing......


```
sudo apt-get autoremove gnome-screensaver
```

```
sudo apt-get purge gnome-screensaver
```

```
sudo apt-get install gnome-screensaver
```

thank's for your suggestions, but...no difference. One thing I noticed, when starting ubuntu again and it "checks" the screen settings, the frozen window of the screen saver comes up in the test. The rest of the start-up procedure is normal. 
I guess I better will post it at the mentioned link above.

One more question, if allowed: As I want to make a new install now, how do I go about partitioning to achive the following:
1. one partition just for the ubuntu system
2. one partition for swap 
3. one partition for my privat files

Now, I was thinking about this to get the result I mentioned above:

1. one partition for /
2. one partition for swap
3. one partition for /home

Would that be correct, or even a good way, keeping future upgrades or new installations in mind ?

Thank you for any suggestions.
Johannes

---

### Post by slakkie on 2009-08-17
That would be a good partitioning scheme. It is almost what I have, I also have a seperate slice for /var/log.

As for the upgrades. If you want to spend some time and learn a thing or two you could make the upgrade (backup your / partition first, clonezilla is your friend) to 8.10/9.04. 

8.04 is still being supported till 2012 iirc, [http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle) for more info. But for a learning experience do the upgrades, although you can wait a year and upgrade directly to 10.04 LTS from 8.04 LTS.

---

### Post by ottawa on 2009-08-17
thank you for the quick answer.
I am just in the process of the new install.

Johannes

---

