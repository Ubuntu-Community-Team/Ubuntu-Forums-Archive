---
title: "window title messes up with desktop effects - Hardy"
date: 2008-11-26
forum: General Help
---

### Post by loserboy on 2008-11-26
I've done some looking around and I know others have had similar problems, but all seem to be separate issues.

I was hoping someone could look at the screenshot and diagnose it for me. 

The only thing I've done to try and address the issue is install EnvyNG, I may be imagining things but it seems to have helped because now it only happens when I switch tabs within Aptana.

Thanks

oh by the way, running Hardy and using a geforce 7800gt

the pink one happens sometimes when i minimize and restore Aptana

---

### Post by mvalviar on 2008-11-26
I was able to fix this by chance. I followed this guide > [http://theindexer.wordpress.com/2008/07/01/install-newhuman-theme-from-intrepid-ibex-on-hardy-heron/]("http://theindexer.wordpress.com/2008/07/01/install-newhuman-theme-from-intrepid-ibex-on-hardy-heron/") I wanted to try the New Human Theme from Ibex. The cool thing is I got an update and when I tried the default human theme on hardy the title bar glitch is gone.

---

### Post by loserboy on 2008-12-01
thanks I'll give it a shot and let you know

---

### Post by loserboy on 2008-12-03
nope, that didn't help.... but the theme is nice

---

### Post by Wartender on 2008-12-03
have you tried ```
metactiy --replace
```?

---

### Post by 9ico on 2008-12-03
[color=#282827]_I need nfl jerseys I do not belive shoping on websit before because i always thought that we could not buy a good products, but now i think it is very convinient for us to shopping on website. I feel truly grateful here _[http://www.9ico.com](http://www.9ico.com/)_._[/color]

---

### Post by loserboy on 2008-12-04
I haven't tried that, what does it do?

edit: ok i looked up what it does, thats seems to have fixed it, but I wonder if it will persist when i restart

---

### Post by Wartender on 2008-12-04
if it does, go to system->preferences->sessions and in the startup programs click add and in the command box type metacity --replace .

---

### Post by loserboy on 2008-12-04
oh wait a sec, it didn't fix it, all it did was turn off compiz fusion... I should have mentioned that I was running compiz or fusion or whatever the Desktop effects are called my bad

---

### Post by loserboy on 2008-12-04
```
mike@mike-work:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0092 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

dunno if that means anything to anyone

---

### Post by Usufruct on 2008-12-04
It very possibly may have something to do with the nVidia bug that causes title bars to render strangely.  I had similar issues until I updated to the 180.06 beta driver, and now my title bars work flawlessly.  

You can try using the beta driver from nVidia's site, or you can wait until the release version to see if it solves your issue.

---

### Post by loserboy on 2008-12-04
> **Usufruct said:**
> It very possibly may have something to do with the nVidia bug that causes title bars to render strangely.  I had similar issues until I updated to the 180.06 beta driver, and now my title bars work flawlessly.  

You can try using the beta driver from nVidia's site, or you can wait until the release version to see if it solves your issue.

heh, just before you posted thats what I did and everything is peachy now.

Thanks

---

