---
title: "Themes??"
date: 2008-11-19
forum: General Help
---

### Post by Jontyy on 2008-11-19
erm i dont know where to post this but anyway...
i have found some themes that look quite good but i cannot unzip them :S:S everytime i click extract i just get an error saying (null).
it says that the folders are gzip archives
has anybody got an idea why its doing this?

---

### Post by sirjoebob on 2008-11-19
Im not sure but you dont always need to unzip themes. Have you tried just adding them to the theme manager (System>preferences>appearance)? Just a thought.

---

### Post by Jontyy on 2008-11-19
lol yep, i just need to unzip the folders i think and then install them, i got the files from gnome-look. ive tried installing 7zip but then found that its only command line.

---

### Post by sirjoebob on 2008-11-19
When you install 7-zip, it adds its functionality to the "extract here" nautilus option. I usually just drag themes from Gnome-look to the Appearance window and it installs them for me. I don't recall having to unzip any theme folders....

---

### Post by Jontyy on 2008-11-19
nope ive jus tried the extract here option and it says the same thing "an error occuring while extracting files (null)". just tried dragging them onto the appearance themes bit and that did nothing for me lol. tried going into the compiz settings but cant find a themes bit in there. on the folders it says emerald, does that mean anything? 
cheers

---

### Post by sirjoebob on 2008-11-19
> **Jontyy said:**
> on the folders it says emerald, does that mean anything? 
cheers

Definitely. These are emerald themes for the emerald theme manager (install from synaptic). Then go to "system>preferences>emerald theme manager" and you can install the themes from there.

voila. Problem solved. Emerald is an amazing thing. You may have to run emerald --replace if it does not automatically replace your existing theme manager.  Feel free to post any more if that did not solve your issue.

---

### Post by shadow1983 on 2008-11-19
If its an emerald theme, install it using the Emerald theme manager, then go to CompizConfig settings manager, go to the effects option and click on window decoration. Where it says command type in emerald --replace. That should start your emerald theme.

---

### Post by Jontyy on 2008-11-19
lol they were under the compiz heading.
right lol ive installed emerald theme manager.
imported a theme
how do i get it to use the theme?
thanks for helping

---

### Post by Jontyy on 2008-11-19
ive changed the command in the compiz settings 
to "emerald --replace"
still nothings happening lol

---

### Post by sirjoebob on 2008-11-19
Open a terminal or hit alt+f2 and type emerald --replace

Additionally, go to system>preferences>sessions and add a new one called emerald and for the command use "emerald --replace" without the quotes. This will run emerald on login.

---

### Post by Jontyy on 2008-11-19
sikkk, got the theme working!
lol why doesnt the taskbars/panels change?? i thought everything would look the same.
thanks alot for the help!

---

### Post by shadow1983 on 2008-11-19
Also you can just restart your computer, most of the time it has kicked in right away for me, sometimes it just needed a restart to give it a bit of a kick :)

Cool glad you got it working

---

### Post by sirjoebob on 2008-11-19
Glad you got it. remember to mark thread as solved.

---

### Post by jairom70 on 2008-11-19
hi sry to post, i didi emerald --replace and it worked. but when i exit the terminal it stopped working and it got messed up , the Close,Minimize, maximize button were missgin and i cant move the wondow around

---

### Post by sirjoebob on 2008-11-19
This is because it relies on the terminal to keep it up. You can use the alt+f2 or run with "compiz --replace&" so it runs without the terminal window.

---

