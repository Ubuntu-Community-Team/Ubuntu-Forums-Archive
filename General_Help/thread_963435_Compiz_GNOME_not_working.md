---
title: "Compiz GNOME not working"
date: 2008-10-30
forum: General Help
---

### Post by Wickd on 2008-10-30
Hi there

I always ran Compiz fine and was a big fan of the cube effect. I then wanted to try the Cylinder effect on it, so uninstalled Compiz, which was stupid, since I only needed  but for some reason after removing WINE and installing wine-git and of course the new Compiz, everything just went wrong:

1) The Cube does not work
2) All my open windows move all the way to the top and the top bar thing with the minimize, maximize and close options are completely gone

If however turn of the all desktop effects, everything returns to normal, except of course the compiz effects.

Is there anyway that I can completely remove Compiz and start over again? Yes I have already removed all compiz packages from the synaptic package manager, but there still remains a compiz option in my system preferences menu??

Thx

---

### Post by northern lights on 2008-10-30
Run ```
sudo aptitude purge compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf compizconfig-settings-manager && sudo apt-get autoremove && sudo apt-get autoclean && rm -rf /home/USER/.compiz && sudo apt-get update
```where USER needs to be replace by your username. You should now be able to install compiz from the repos again.

---

### Post by Wickd on 2008-10-30
I copied this exact command and for some reason it has removed my headers?? But I dont see any code that could have caused that? Maybe the autoclean had something to do with this?

---

### Post by northern lights on 2008-10-30
What exactly do you mean by "headers"? Window frames / decoration?

If so, run ```
metacity --replace
```

---

### Post by Wickd on 2008-10-30
> **northern lights said:**
> What exactly do you mean by "headers"? Window frames / decoration?

If so, run ```
metacity --replace
```

No my linux headers were downgraded. How the hell that happened I am not sure? Haha Man I love screwing this thing up and repairing it!

---

### Post by Wickd on 2008-10-30
Ok I removed everything as you told me, but I still dont have any window decorations/frames (the close, minimize and maximise buttons). And also if I do metacity --replace i get an error telling me: 'Unable to open X display'

Thx.

---

