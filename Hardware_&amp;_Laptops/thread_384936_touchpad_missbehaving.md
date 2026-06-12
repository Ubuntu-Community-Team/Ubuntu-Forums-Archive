---
title: "touchpad missbehaving"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by sheds on 2007-03-15
Hello there, noob here at the forums.

I just upgraded to feisty fawn and i had to reinstall xorg. I finally got it running again, but the touchpad on my satellite laptop is showing the menu that appears when you hit the right click button on a regular mouse.

I compared my xorg.conf file part for synaptics part with others on the internet and added what i was missing, but nothing has fixed this.

It was working fine before by the way.

Thanks in advance for the help.

---

### Post by cisforcojo on 2007-03-15
You do know that Feisty Fawn is not stable right?
It's in ALPHA because it's still very bug prone. 

If it was working in Edgy, I suggest going back to Edgy for the time being.

---

### Post by sheds on 2007-03-15
Can i just change feisty to edgy in the /etc/apt/sources.list and do the downgrade? Or do you suggest other means of performing the downgrade?

---

### Post by cisforcojo on 2007-03-15
Hmm, good question. Since you've just installed I'd recommend a fresh install. Backup anything you have that's important and do a fresh install of Edgy. There might be easier ways. I'm not familiar at all with Feisty. Been waiting for the April release! :)

EDIT: To clarify, you COULD change feisty to edgy in sources.list and use Synaptics to downgrade. When in Synaptics, click on the package you which to downgrade and hit Ctrl-E, then select the version you want. I'm not sure which packages you'd have to downgrade and I think it'd be easier to reinstall Edgy. If you change sources.list and update it, your system won't downgrade automatically because it only flags new downloads for higher versions, not lower.

---

