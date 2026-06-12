---
title: "Compiz not loading after upgrade to Lucid"
date: 2010-05-03
forum: Hardware
---

### Post by lviggiani on 2010-05-03
Hi Guys,
I have upgraded to Lucid (64bit) my laptop equipped with an nvidia geforce 8400 card.
While running Karmic, I was using the latest nvidia drivers from nvidia-vdpau ppa.
On Lucid when gnome starts I have a X mouse pointer and no window decorations. I try selecting propretary drivers but I got errors.
So I first removed all nvidia-* stuff and then re installed nvidia-current and nvidia-current-modaliases. I could then enable visual effects having my compiz working.
The problem is that when I restart or power on the computer, I fall back to the previous situation (X pointer and no windows decorations).
I then removed again nvidia-* packages and installed the drivers from nvidia official installer but I have the same behaviour
Now I have removed nvidia drivers from nvidia installer and reinstalled nvidia-current packages.
SO any time a start gnome, I have to run "compiz --replace" in order to have window decorations... very bad.
I just checked with "hardware drivers" application: it tells me that nvidia-current is activated but not currently in use" which is very starnge... can some one help me please?

---

### Post by josarn on 2010-05-03
Try this, it worked for me:

```
sudo apt-get install compiz
```

I had the same problem and for some reason the compiz package wasn't installed.

---

### Post by lviggiani on 2010-05-03
Thanks for you hint but it is not my case. COmpiz is installed and can be manually started.

> **josarn said:**
> Try this, it worked for me:

```
sudo apt-get install compiz
```

I had the same problem and for some reason the compiz package wasn't installed.

---

### Post by notquitemichael on 2010-05-03
i know its not ideal, but adding an entry for compiz.real --replace in your session manager will automate your fix.

---

### Post by mattlopezdias on 2010-05-03
had the same problem, simply put compiz in start-up applications, been working fine ever since with no side effects. seems like a harmless workaround to me.

---

### Post by lviggiani on 2010-05-03
> **mattlopezdias said:**
> had the same problem, simply put compiz in start-up applications, been working fine ever since with no side effects. seems like a harmless workaround to me.

Hi Guys,
thank you for your hint. Well I came to the same conclusion as now after removing and re-installing nvidia-common and nvidia-current and rebooting, the driver appears enabled and in use. So perhaps there is something wrong in the gnome or compiz startup scripts.

So for the time being I think I'll add the start-up script although I'd rather find a real solution...
If some one has any idea about what went wrong while upgrading to lucid please let us know.
Thanks for now, Luca.

---

### Post by josarn on 2010-05-03
Hmmmm. Can you be as kind as to look in "System > Administration > Synaptic Package Manager", please? If "compiz-core" package is installed but compiz is not, then please read post #2 again.

---

### Post by lviggiani on 2010-05-03
> **josarn said:**
> Hmmmm. Can you be as kind as to look in "System > Administration > Synaptic Package Manager", please? If "compiz-core" package is installed but compiz is not, then please read post #2 again.

compiz
compiz-core
python-compizconfig
compiz-config-setting-manager
compiz-plugins
compiz-gnome
libdecoration0
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
compizconfig-backend-gconf

this is all about Compiz I have installed.

---

### Post by josarn on 2010-05-03
Too bad, in my case once the compiz package was installed I only had to activate desktop effects one last time for the change to be permanent. Hope you will find a solution soon, cheers!

---

### Post by MrPok on 2010-05-03
-- This thread is nearly identical to [ubuntuforum post9203353]("http://ubuntuforums.org/showthread.php?p=9203353#post9203353") --

> **josarn said:**
> Too bad, in my case once the compiz package was installed I only had to activate desktop effects one last time for the change to be permanent. Hope you will find a solution soon, cheers!

Be **AWARE** though that if you do this you will also _reset_ the compiz setup.. :( I didn't expect this to happen and it seems that I now have to set every tweaked little setting all over again.. ](*,)(and that takes a lot of time!)

So, my suggestion (correct me if I'm wrong here) would be to *first* go to CompizConfig Settings Manager --> "Preferences" ..and Export your current compiz setup/profile.

Then perform any workaround as listed in [Launchpad Bug #572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617"): 

> Other workarounds:

a. Having selected effects as above, select "Remember running applications" from Startup Applications
b. Invoke /usr/bin/compiz --replace as a startup application
c. ln -s /usr/bin/compiz /usr/bin/compiz.real
d. Invoke /usr/bin/metacity from command line or as a startup application
I would recommend option c.

..and then in CompizConfig Settings Manager --> "Preferences" import the exported setup/profile to restore ye' ol' splendour. :P

Good luck!

---

### Post by lviggiani on 2010-05-04
> **MrPok said:**
> -- This thread is nearly identical to [ubuntuforum post9203353]("http://ubuntuforums.org/showthread.php?p=9203353#post9203353") --



Be **AWARE** though that if you do this you will also _reset_ the compiz setup.. :( I didn't expect this to happen and it seems that I now have to set every tweaked little setting all over again.. ](*,)(and that takes a lot of time!)

So, my suggestion (correct me if I'm wrong here) would be to *first* go to CompizConfig Settings Manager --> "Preferences" ..and Export your current compiz setup/profile.

Then perform any workaround as listed in [Launchpad Bug #572617]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/572617"): 


I would recommend option c.

..and then in CompizConfig Settings Manager --> "Preferences" import the exported setup/profile to restore ye' ol' splendour. :P

Good luck!

Ahaaaa... so it looks like they compiz.real bin file has been removed... AFAIR in the past, /usr/bin/compiz.real was the real bin app whereas /usr/bin/compiz was a launching script... if so, workaround c would be the best to me too. As soos as I will put the hands on my ubuntu box I'll check and let you know. Thank you very much for now! Ciao!

---

### Post by lviggiani on 2010-05-05
```
sudo ln -s /usr/bin/compiz /usr/bin/compiz.real

```
worked flawless for me!

---

### Post by badlee on 2010-05-07
I had tried these solutions, and it did not work for me. I use Kubuntu, and after receiving an error about the kde-window-decorator, I installed the package fusion-icon and then in there changed the window decorator to emerald. 

Then went into the System Settings > Default applications > Window Manager and changed it to compiz.

Everything works fine now! 

Perhaps the Gnome window decorator is causing the same issue.

---

### Post by leopards on 2010-05-07
My problem was a little different!! Compiz-config-settings-manager was not installed by default, there was no way to change any settings till I manually installed it with synaptic! Weird!

---

### Post by jasxun on 2010-05-13
This worked for me as well.

> **josarn said:**
> Try this, it worked for me:

```
sudo apt-get install compiz
```I had the same problem and for some reason the compiz package wasn't installed.

---

