---
title: "Installing firefox 2 on Ubuntu 8.04"
date: 2008-08-29
forum: General Help
---

### Post by shay_ts on 2008-08-29
For some reason I need to use firefox 2 on my system.

Is it possible?

I always surf using firefox 3, but I need to launch firefox 2 once a week.

Can I do that?

If yes, please explain how.

I'm new in linux.

Thank you very much!!

---

### Post by nicolaary on 2008-08-29
in my kubuntu I have just only ...

sudo apt-get update && sudo apt-get install firefox-2

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> in my kubuntu I have just only ...

sudo apt-get update && sudo apt-get install firefox-2

Thank you, but it installed firefox 2 - only that when I access it - it runs fire fox 3 :(

---

### Post by nicolaary on 2008-08-29
check in  /usr/bin/firefox-2 that the target directory is the right one...

post here also the result of locate firefox-2

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> check in  /usr/bin/firefox-2 that the target directory is the right one...

post here also the result of locate firefox-2

I beg your pardon. But what do you mean by "check in usr/bin/..." and how can I know that a directory is the right one?

Can you simplify for me?

I thank you very much in advance.

I would also comment that the reason I need firefox 2 is in order to use the older version of "unplug" which i need in order to watch movies from the university in which I study. 

Even after I unistalled firefox 3 using synaptic, I could not install that plugin. I believe that is because there are still leftovers of firefox 3 in the system (i see it when I browse the plugins).

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> 

post here also the result of locate firefox-2

```

shay@localhost:~$ locate firefox-2
/usr/share/app-install/desktop/firefox-2.desktop

```

---

### Post by nicolaary on 2008-08-29
Try:

```
/usr/lib/firefox/firefox-2
```

anyway..
What is the message you get if you type

```
apt-get install firefox-2
```

like firefox-2 is already the newest version ???

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> Try:

Thank you once again, but I still can't install the Unplug add-on using firefox 2 in the way you presented.

I believe that is so since there are leftovers of firefox 3 in the system. I see it when I browse the firefox 2 plugins and see there plugins which are connected to firefox 3.

how can I completley Uninstall firefox 3 from my system? I used Synaptic and it seems to be not good enough...

---

### Post by nicolaary on 2008-08-29
Wrong post. Check the next one

---

### Post by nicolaary on 2008-08-29
```
sudo apt-get remove firefox-3.0
```

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> ```
sudo apt-get remove firefox-3.0
```


Thank you. The firefox is uninstalled, but in firefox 2 I still have now the plugins of firefox 3. I believe (but not sure) that that is causing the errors when I'm trying to add the "unplug" add-on to firefox 2. 

Is there a way in which I can also remove the plugins of firefox3?

---

### Post by nicolaary on 2008-08-29
I think...

open firefox -> Tools -> Add-ons ->Find updates...

I guess it should disable the unsupported and re-align the right ones!

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> I think...

open firefox -> Tools -> Add-ons ->Find updates...

I guess it should disable the unsupported and re-align the right ones!


I tried that, the add ons are disabled but still appear... I want to remove them totally... I guess it's not possible? :(

---

### Post by shay_ts on 2008-08-29
> **shay_ts said:**
> I tried that, the add ons are disabled but still appear... I want to remove them totally... I guess it's not possible? :(


Oh one thing I didn't mention - the "find updates" button is gray. I only disabled the inappropriate plugins manually

---

### Post by nicolaary on 2008-08-29
If you do not care about bookmarks and themes just rename the directory in your home 

```
 mv  ~/.mozilla/firefox  ~/.mozilla/firefox_old   
```

and restart it!

---

### Post by nicolaary on 2008-08-29
I do not see any more replies :-)

I hope we did not cause any big problem ;-)

in case just move it back...

```
 mv  ~/.mozilla/firefox_old  ~/.mozilla/firefox
```

---

### Post by shay_ts on 2008-08-29
> **nicolaary said:**
> If you do not care about bookmarks and themes just rename the directory in your home 

```
 mv  ~/.mozilla/firefox  ~/.mozilla/firefox_old   
```

and restart it!

You're the man. YOU ARE THE MAN!

Y O U     A R E    T H E    M A N ! ! 

Thanks hips!!!

That was awesome. Everything I need works. 

:)

---

### Post by nicolaary on 2008-08-29
Enjoy....

bye

---

