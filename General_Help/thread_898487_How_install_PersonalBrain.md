---
title: "How install PersonalBrain?"
date: 2008-08-23
forum: General Help
---

### Post by jkph00 on 2008-08-23
Hi!

I have downloaded a brain mapping application called PersonalBrain ([http://thebrain.com/#-53](http://thebrain.com/#-53)).  The install file PersonalBrain_unix_4_5_0_9.sh is on my desktop.  I have tried to install it by clicking on it in case there was an installer package contained in it, by using Add/Remove from the Applications menu and by using the Synaptic Package Manager with no success because of ignorance.  On the site they say it has been tested successfully under Ubuntu.  I'm new at this and am puzzled.  What am I overlooking?

My warmest thanks in advance for any help.

--Kurt

---

### Post by aloshbennett on 2008-08-23
If its a .sh file, you can run it from command prompt by first changing your directory to Desktop
> cd ~/Desktop
and then running the shell script
> ./PersonalBrain_unix_4_5_0_9.sh

But be sure what you are installing can be trusted.

---

### Post by jkph00 on 2008-08-23
> **aloshbennett said:**
> If its a .sh file, you can run it from command prompt by first changing your directory to Desktop

and then running the shell script


But be sure what you are installing can be trusted.

The only addition I had to make was to run the script as you told me above as superuser (su).  It worked handsomely, thanks ever so much!

---

### Post by abinoam on 2008-08-24
Installing software as superuser (root) is usually not a good idea.

I have successfully installed it (PB) without root permissions.

What was the message you got when trying to install it without sudo?

Did you verify the execute permissions of the script?

```
chmod u+x ./PersonalBrain_unix_4_5_0_9.sh
```

---

