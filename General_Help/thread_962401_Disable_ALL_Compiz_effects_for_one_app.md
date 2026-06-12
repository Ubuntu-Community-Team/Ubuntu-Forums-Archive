---
title: "Disable ALL Compiz effects for one app"
date: 2008-10-29
forum: General Help
---

### Post by sototallycarl on 2008-10-29
Is it possible to disable all compiz effects for, in my case, VMware?
I was running with the generic drivers and no compiz on a fresh install and VMware was near native speeds. With compiz and fglrx it runs at about half and its mostly because of mouse pointer performance. For example, the select tool in Photoshop becomes useless with compiz on, super sluggish.

Thanks,
Carl

---

### Post by Forlong on 2008-10-29
This is not possible. Even if it were, your graphics chip would be still busy rendering the rest of the desktop, which is most probably the source to your problem.

I'm afraid you have to switch Compiz off before launching VMware.

---

### Post by sototallycarl on 2008-10-29
> **Forlong said:**
> This is not possible. Even if it were, your graphics chip would be still busy rendering the rest of the desktop, which is most probably the source to your problem.

I'm afraid you have to switch Compiz off before launching VMware.

I was doing some tests and that what I assumed sadly. Its crazy that a relatively decent card/machine (2.8 core duo, 4gb ram, 256mb ATI 2600)  would have such trouble. Guess I will just get used to not using hot corners for window controls.

Thanks for the reply.

---

### Post by sototallycarl on 2008-11-03
A solution I found was simply upgrading to Adobe CS4. If you have the same issue, grab the trial and see if it fixes it for you. I can actually use CS4 apps maximized (on 1920x1200 monitor) in VMWare Unity mode and experience no lag at all.

This one solution will make me ditch my OS X partition for good since I need production performance CS4 to make the switch, along with an "Expose" type feature for workflow niceness. Who said you can't have your cake and eat it too?

---

### Post by inspired on 2009-01-07
> **Forlong said:**
> This is not possible. Even if it were, your graphics chip would be still busy rendering the rest of the desktop, which is most probably the source to your problem.

I'm afraid you have to switch Compiz off before launching VMware.

I am experiencing similar issues. How does one disable Compiz easily? (and then re-enable it afterwards)

Thanks
Jonathan

---

### Post by Forlong on 2009-01-07
[Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch) -- switch Compiz off and on easily :-)

---

### Post by chamber on 2009-01-07
Look in Forlongs signature, 

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by chamber on 2009-01-07
Dang, 

Too slow!!

---

### Post by inspired on 2009-01-07
> **chamber said:**
> Look in Forlongs signature, 

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)
Oh nice. That was easy. Will check that page out now.
Cheers...

Jonathan

---

### Post by bixejo on 2009-01-07
> **inspired said:**
> I am experiencing similar issues. How does one disable Compiz easily? (and then re-enable it afterwards)
 
Thanks
Jonathan
 
Hi, Jonathan.
 
I got about the same problem. Before knowing anything about Forlong Compiz-Switch utility, I wrote a rather rudimentary script to do this job. This script just checks whether there exists a process called "metacity", and then launches "compiz --replace" or "metacity --replace" accordingly.
 
Script **toggle_compiz**:
 
```
#!/bin/bash
#
if [[ $( ps aux | grep metacity | grep -v "grep metacity" | wc -l ) == "0" ]]; then
    # metacity is not running but (probably) compiz, so launch metacity to
    # replace whatever is running (if any):
    { metacity --replace & }
else
    # metacity is running, launch compiz to replace it:
    { compiz --replace & }
fi
```Then I associated a shortcut to this script: System -> Preferences -> Advanced desktop effects settings, click on "General options" and then "Commands" tab.
 
I know this is not an utterly clean and elegant way to switch on/off compiz (it leaves some compiz process running when switching to metacity, but it does not matter too much as it is not duplicated when switching back to compiz) but it's quite simple and works fine for me.
 
Regards,

---

### Post by inspired on 2009-01-09
Thanks for the switch (installed and now in use) and also for the script info (bixejo).

There is an issue, however, that one of you may be able to suggest a solution to.
I use Avant Window navigator in place of the bottom panel that comes out of the box with Ubuntu. It seems that the way Metacity is configured in Ubuntu, AWN does not work. It needs Compiz or a fully functional Metacity.
So when I turn off Compiz I end up with no AWN and thus no bottom panel. Is there any script based way to activate the bottom panel (set up the same way as the default one in Ubuntu)?

I can probably survive without it :) but it would be nice to turn that off and on too.

Much thanks,
Jonathan

---

### Post by Forlong on 2009-01-09
No that's not possible, but I'm sure I can think of a Compiz-based workaround so it's not visible while Compiz is activated.

I'll come back to you later.
Please bump this thread when it seems I forgot about it.

---

### Post by inspired on 2009-01-09
> **Forlong said:**
> No that's not possible, but I'm sure I can think of a Compiz-based workaround so it's not visible while Compiz is activated.

I'll come back to you later.
Please bump this thread when it seems I forgot about it.
I may have found a solution to this.
Using the Ubuntu Tweak application I was able to activate compositing on Metacity. So now when I switch off Compiz AWN reloads successfully in metacity.

Thanks a lot of being so willing to figure out a solution!

By the way... you Compiz guide is just fantastic. It made fine tuning my Compiz a breeze. Thanks a lot for sharing all that info.

---

### Post by Forlong on 2009-01-09
Found it!

Enable the **Widget Layer** plugin in ccsm.
Then go to the **Behaviour** tab and click on the [+] next to **Widget Windows**.
As **Type** choose **Window Title** (that's important, because otherwise both panels will be affected)
Now click on **Grab** &#8211; the cursor should turn into an cross-hair.
Finally click on the bottom panel and choose **Add**

Et voilà, the bottom panel should immediately vanish.
If you switch Compiz off, the panel will come back again.

---

### Post by inspired on 2009-01-11
> **Forlong said:**
> Found it!

Enable the **Widget Layer** plugin in ccsm.
Then go to the **Behaviour** tab and click on the [+] next to **Widget Windows**.
As **Type** choose **Window Title** (that's important, because otherwise both panels will be affected)
Now click on **Grab** &#8211; the cursor should turn into an cross-hair.
Finally click on the bottom panel and choose **Add**

Et voilà, the bottom panel should immediately vanish.
If you switch Compiz off, the panel will come back again.

Thanks Forlong,
That's fantastic.
I can't try implementing it just yet because for some reason something I did yesterday has "broken" my compiz. I am not sure if it's broken in the true sense of the word... but basically I am not able to adjust any settings and none of the effects are working. Also my screenlets won't stay in the position I place them in since this happened.

So... I am now trying to fix compiz. If you have any suggestions they are very welcome.

I think what broke it was installing Win4lin as per the instructions on this page: [http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08](http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08)

I already had a slightly earlier implimentation of Win4lin although that was not installed via a script... I simply imported the themes etc. This one was installed with a script though.

UPDATE::
In the Appearance settings I note that the Effects are set to NONE. When I try to set it to something else Compiz tries to load (deskt vanishes, things start happening) and then I get an error "Desktop effects could not be enabled". So it seems something is broke. I am now reinstalling all the major compiz apps in package manager. Will see if that helps.

ANOTHER UPDATE:
Ok. How odd. When I first install Compiz I turned off the option to automatically sort the plugins. I did that because the plugin lists on that preferences page would vanish when it was ticked on. I figured it was best if I they were at least visible. I found out that unticking that can make all the plugins not work. Odd. Fixed.

So I've now tried out your trick and it works like a charm. Nice one.
Now all I have to figure out is why Sreenlets are duplicating each time they are restarted.

Anyway... more fiddling around on this computer..

Jonathan

---

### Post by Forlong on 2009-01-11
You can use Compiz-Check to see what's wrong with your Compiz install: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

