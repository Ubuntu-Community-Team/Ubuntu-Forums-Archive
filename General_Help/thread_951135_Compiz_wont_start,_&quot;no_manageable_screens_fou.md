---
title: "Compiz wont start, &quot;no manageable screens found&quot;"
date: 2008-10-17
forum: General Help
---

### Post by chenguo4 on 2008-10-17
I run compiz --replace in terminal and that happens. I had compiz on before, just turned it off temporarily. 

I was trying out svideo (didn't do much, just plugged it in then under resolution tried detect display). Now under monitor resolution settings there's just a big fat "unknown" in the white box, though I can still change the resolution and stuff. 

So obviously, since I can see stuff, my monitor's working. How do I get compiz to detect it?

Thanks in advance.

---

### Post by loomsen on 2008-10-17
So, you have multiple Displays defined and connected?

You can redirect output by prefixing DISPLAY=:0.1 for instance if it's Display number one.

You may find out by typing 
```

glxinfo | grep screen

```

giving me:
```

docter[~] glxinfo | grep screen
display: :0  screen: 0
display: :0  screen: 1
docter[~] 

```

So the pipes are obv:
```
DISPLAY=:0.0
DISPLAY=:0.1

```
for me...

---

### Post by chenguo4 on 2008-10-17
I dont think it was the monitor, but thanks anyway! 
I messed around a bit (uninstalled video driver, reinstalled) and the screen problem is gone now. 

When I run compiz --replace, it says

Checking for Xgl: not present
Found laptop using ati driver
aborting and using fallback: /usr/bin/metacity

Xgl was never the problem, it ran before fine without it.

I suspect this is the blacklisting of ati drivers I've heard of, but I dont know why it'd magically start blocking my drivers now, when it was working before. I'll look into that a bit further...

If anyone knows that this is something else, lemme know before I go on some wild goose chase, ya? Thanks a bunch.

---

### Post by chenguo4 on 2008-10-17
Ok it was the black list... I disabled it, and now when I try to start Compiz it just takes me to the login screen. What's up with that?

Would it make a difference from where I installed Ubuntu? When compiz used to work, it was on an Ubuntu installed off a customized Live-CD from a class.

Would downloading some system upgrades somehow make compiz not work? Anyone else having this problem?

---

### Post by loomsen on 2008-10-18
Oh well, I can't help you with that too much other than stating I'm actually pretty pleased with my nVidia, doing basically anything I tell her, like my own DPI smoothing thus forcing it to draw whichever Reslution I specify. 

But, in spite of that, I always try and walk on the cutting edge, but I also have sth like fun tracing bugs... 

So, you're using hardy? However, I'd not recommend upgrading your dist before the official release. Installing will work pretty well in the meanwhile, but upgrading will leave you with a broken filesystem pretty likely. Just happened to me yesterday with debians unstable too.

---

### Post by ad_267 on 2008-10-18
Doesn't really sound like this is the problem but if you've enabled compositing in metacity I've found you have to disable that to be able to enable compiz.

---

### Post by theApokalypsis on 2009-05-26
> **ad_267 said:**
> Doesn't really sound like this is the problem but if you've enabled compositing in metacity I've found you have to disable that to be able to enable compiz.

didnt think I would hit this. thank you searching. it was for me for so long! oh the simple things...

and even almost a year later LOL

:p

---

