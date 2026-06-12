---
title: "Only One Software Management Tool is Allowed"
date: 2008-10-19
forum: General Help
---

### Post by mental1ty on 2008-10-19
Hi All Well I made the switch and I am windows free Yay.
But now I need some help. After trying to install Limewire I get the message "Only one software tool is allowed to run at the same time
Close EG: Update Manager Aptitude Synaptic. Any and all advice is welcome.

Mental.:guitar:

---

### Post by Bucky Ball on 2008-10-19
Close Synaptics Package Manager and all should be fine. The error is self explanatory.

---

### Post by scragar on 2008-10-19
You can only run one installer at a time because otherwise there is a chance of libraries conflicting with each other(not likely, but since it can happen it's best to avoid it), so if your running the update manager, either of the add/remove tools(synaptic and the other one) or something similar you will need to wait for it to do what it is doing and close it before you can start another. It's all in the intrest of keeping the system stable.

---

### Post by retiefdv on 2008-12-03
> **Bucky Ball said:**
> Close Synaptics Package Manager and all should be fine. The error is self explanatory.

I ran into exactly the same problem and the error is definitely NOT as self explanatory as mentioned. I first got this error message while trying to install an application from a deb package. To make sure that there is no other package managers running, I rebooted my machine (sounds like something I did more than a year ago when I last used Windows!) and I tried to install the package again before opening any other application, but I got exactly the same message.

How do I get past this do install a few applications that I really need?

---

### Post by philinux on 2008-12-03
You haven't set the option in System>prefs>sessions to automatically remember running apps have you?

---

### Post by retiefdv on 2008-12-03
OK, my problem is now solved and I will quickly describe what happened, in case it can help somebody else. I am busy getting a new laptop configured with Ubuntu and I remember that a Flash plug-in installation into my Firefox browser got stuck (due to proxy settings for the network that was wrong). After another reboot, I specifically opened the Synaptic Package manager and got an error message about some task that had not yet completed. I had to run something like "dkpg --configure -a" in the terminal. Now that my proxy was correctly set, the Flash plug-in install completed where it was stuck. After this was completed, I could go ahead and finish my deb installations. I am a bit baffled that the System Monitor did not show this task still "hanging" somewhere.

---

### Post by keygiwawah on 2008-12-03
I think that works... whenever i was disconnected from the internet (moving my computer), it gave me that same prompt about having only one manager open at a time... when i connect it to the internet again it works just fine.  I'm not sure why it doesn't show anything waiting to be downloaded or installed.

---

