---
title: "Problem with installation of nividia 180.44"
date: 2009-05-04
forum: Hardware
---

### Post by tux1527 on 2009-05-04
Hi all!

I want to mention, that I'm not sure, if I'm right in this section, and if the following problem isn't already solved somewhere.  If so, please take me forward to the appropriate thread! 
I've just been searching for a long time without getting any answer to my problem.

I've just updated to Ubuntu Jaunty Jackalope. Due to some graphical problems especially concerning Firefox, I tried to integrate an Intel - Driver to my NVIDIA GeForce7400 (256MB Cache) using this thread:
[URL="http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+intel"]
[/URL][http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+intel](http://ubuntuforums.org/showthread.php?t=1130582&highlight=jaunty+intel)

Well, the installation worked perfectly, and the sytem booted rather normally and I can still use the most important things. I wondered that it is really working! BUT: Later as expected a serious problem occured: 
The formerly installed NVIDIA 180.44 driver is removed and CANNOT be reinstalled! Well, actually, the system acts as if it is installing properly, but after reboot, nothing has changed! 
I know, trying an INTEL Driver on my chip was a bit stupid, but I wanted to fix my problems and thought this would work, because, you may understand, I'm a total newbie in LINUX and want to learn. So I try anything! :S

Well, however, how can I fix that problem getting to the normal state like it was before?

And another question, I want to ask again that may have to do with driver problems. It is posted here: [http://ubuntuforums.org/showthread.php?p=7210032#post7210032](http://ubuntuforums.org/showthread.php?p=7210032#post7210032)

I would be grateful for any advice for a newbie :D

Yours,
Martin

---

### Post by stretch427 on 2009-05-05
have you tried possibly disabling the NVIDIA Drivers and then trying to install the 180.44? Have you used hardware manager to try and acquire the restricted drivers? 

```
System -> Administrator -> Hardware Drivers
```

You could also use Synaptic Package Manager to get rid of the NVIDIA drivers and start over. 
```
System -> Administrator -> Synaptic Package Manager
``` 

and then type in Nvidia and mark for removal everything nvidia and try  again. 

Cheers!

---

