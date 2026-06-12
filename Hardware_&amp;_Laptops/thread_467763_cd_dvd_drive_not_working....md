---
title: "cd dvd drive not working..."
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by fflarex on 2007-06-08
I seem to be having problems with with my disc drive in ubuntu. Sometimes it works just as it's supposed to with no problems. Most of the time (90%), however, it fails to even identify that there is a disc inside. When it does manage to work, it will take a long time before it lets any program use the drive (Sound Juicer, Amarok, etc).

The model is: Optiarc DVD RW AD-7530A

As far as I can tell, there is no reason why it works sometimes and not others. I'm not doing anything different. It may also be worth noting that when I go to Computer in the file browser, two optical drives are listed when I really only have one.

How do I fix this? This is extremely annoying because I just got rid of my entire digital music collection with the intent to redo it completely (in flac for archiving and future-proofing, and lame mp3 for DAPs etc). Right now I have to reinsert the same CD ten times before it will even recognize it. Any help is greatly appreciated

---

### Post by fflarex on 2007-06-08
One more thing that is probably worth mentioning is that I had this exact same problem when my machine ran Windows Vista after I installed virtualization software. The difference is that on Windows I did something I could identify as the cause. Here though, I don't know what I could have done to cause it and suspect I didn't actually do anything. Changing a 0 to 1 in the registry solved it, but I don't remember what value it was.

Please help, this is the last big obstacle in my way before my switch to linux is complete. Anything after this is just icing.

---

### Post by fflarex on 2007-06-08
Okay, now I'm pretty sure it has something to do with GNOME. I could access everything fine on the same system when I went to audiocd:/ on KDE.

---

### Post by hummingbird59 on 2007-06-08
I had the same problem after upgrading to new kernel (ends in 16).  Going back to old kernel (ends in 15) solved it for me.  When you boot up, hit esc when you see grub, it will list kernels - choose second one .....15.  Maybe others can give you more specific info.  Hope this helps!

---

### Post by fflarex on 2007-06-08
Will I be able to easily go back to the new kernel after I do this?

---

### Post by hummingbird59 on 2007-06-08
As long as you don't delete it, yes.  But, I think you will have to choose the old kernel every time you boot if you keep both.  There could be a better way, but I chose to delete the old kernel because it caused alot of problems for me!

---

### Post by fflarex on 2007-06-08
Okay, I tried that and it didn't work for me. But I have narrowed down the problem a little bit. It seems that it's not really a gnome problem, as I can open the cd in gnome too if I do it with konquerer, even though the rest of the OS insists that it's not mounted, that there's nothing in the drive, etc.

This is weird. Why would one program be able to find a disc that doesn't officially exist to the rest of the OS?

---

### Post by hummingbird59 on 2007-06-08
Did you see this link [http://ubuntuforums.org/showthread.php?t=464423](http://ubuntuforums.org/showthread.php?t=464423) ?

---

### Post by fflarex on 2007-06-08
Thanks, that is exactly my same problem. I'll move over to that thread if those suggestions don't help.

---

