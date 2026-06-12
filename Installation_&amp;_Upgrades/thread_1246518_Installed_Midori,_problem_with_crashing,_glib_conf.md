---
title: "Installed Midori, problem with crashing, glib conflict?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by Jennytalia on 2009-08-21
Hi guys!  I am a very new ubuntu user, and and totally lost on installing new software.  It's SO different from what Im used to.

I've been having serious slowdown problems with FireFox, and a browser called Midori was recommended to me.  I downloaded and installed it, but it crashed trying to connect to a site.  The FAQ for Midori says this is a problem with Glib 2.6, and to install Glib 2.8.  

So...um...how exactly does one do that?  I downloaded glib-2.20.8.tar.bz2 (which I assume is the newest version of whatever this Glib thing is) but I am at a loss as to what to do with it.

I realize that this is pretty basic information I am asking for, but the many sites I have visited to try to get help with this all seem to be written with the assumption that the reader has some basis of knowledge to work from.  I don't, unfortunately.  So I am hoping someone can help me who has the patience of a saint and the ability to talk to someone like they're 8.

Thanks in advance-
Jenny

---

### Post by starcraft.man on 2009-08-21
Unfortunately, I don't think that one change will make midori stable. It's under active development just like arora another webkit browser, same with chrmoium. Use of any of these is not without risk of crashing. I know midori crashes enough when I use it.

If ya want a faster browser, probably best bet is Opera. I personally, stick with Firefox.

Can you explain what the slowdowns were? Just generally too much for current hardware?

Also, varies depending on what ya downloaded. I'm gonna assume it's not compiled since it's not a deb, then you'd need to follow [these instructions. ]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by Jennytalia on 2009-08-22
I believe you have just saved me a world a headache, Starcraft.man, and thanks for that.  I installed Opera, and Im not having the headaches I was having with Firefox. (It was just unbelievably slow.  XP and IE 7 on a half of gig of RAM ran better than FF and ubuntu with 2 gigs.)  

But there's a different issue that I was dealing with in FF after the last time I updated it, and am still having now.  Flash isn't working.  At all.  I googled around a bit and removed the swfdec-mozilla package, and used this command -- sudo apt-get install flashplugin-installer --.
Plugins are enabled.  I pretty much don't know what else to try.  

Thanks for getting back to me so quickly.  You sure know how to make a girl feel special.  :-P

---

### Post by starcraft.man on 2009-08-22
> **Jennytalia said:**
> I believe you have just saved me a world a headache, Starcraft.man, and thanks for that.  I installed Opera, and Im not having the headaches I was having with Firefox. (It was just unbelievably slow.  XP and IE 7 on a half of gig of RAM ran better than FF and ubuntu with 2 gigs.)  
People experience firefox differently, sadly, it is not ideal on some machines. You might wish to try **epiphany-browser**, that's the package name in the repos. It's a gecko based browser and most people find much less hassle with it than firefox. Or stick with opera if it takes your fancy.

> But there's a different issue that I was dealing with in FF after the last time I updated it, and am still having now.  Flash isn't working.  At all.  I googled around a bit and removed the swfdec-mozilla package, and used this command -- sudo apt-get install flashplugin-installer --.
Plugins are enabled.  I pretty much don't know what else to try.  
Not even in opera? Hmmm, curious. Check about:plugins in the url of firefox, it listed there at all? If not lets try reinstalling it after a purge and see if that fixes it. Open the great geek swiss army knife (i.e. terminal, applications > accessories > terminal) and then type the following:

```
sudo apt-get purge flashplugin-installer flashplugin-nonfree
```

```
sudo apt-get install flashplugin-install
```

Restart browsers and see if its in the plugins entry, if not, we can try some more...

>  Thanks for getting back to me so quickly.  You sure know how to make a girl feel special.  :-P

Well now, that's what I'm here for. Also, as a Canadian, I'd be remiss to do less. :)

Side note, ya might wanna see the Ubuntu Women group. It's a group for women to chat and stuff, I wouldn't know, man as my name indicates... You probably know that female geeks are not in huge numbers. I'll catch one, one day... with a large fishing rod baited with... gah, what to put to catch right women. Maple syrup covered Ubuntu notebook playing a Futurama episode, maybe? :p

Edit: If your confused by the squirrels all about, [see my announcement.]("http://ubuntuforums.org/showthread.php?t=1244946")  I'm not liable for any unwanted laughter.

---

