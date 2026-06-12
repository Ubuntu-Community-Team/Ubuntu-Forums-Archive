---
title: "how can i get it to work ?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by pat boy on 2009-08-11
i am trying to down a client for a online game and this is waht come up, 

when i try to run through wine i come up ,

exception exception in module dwarclineten.exe at 000ae0a5
urlmondecoder : stdencodingfilterfac could not created

??? what up with it ?

also i down loaded the new ubuntu but my system did not change over and i can not find the new ubuntu on my system any were ??

---

### Post by 3rdalbum on 2009-08-11
> **pat boy said:**
> i am trying to down a client for a online game and this is waht come up, 

when i try to run through wine i come up ,

exception exception in module dwarclineten.exe at 000ae0a5
urlmondecoder : stdencodingfilterfac could not created

??? what up with it ?

What game is it, and have you looked at the AppDB on [www.winehq.org](www.winehq.org) to see if there are any extra steps you need to take to run the program?

> also i down loaded the new ubuntu but my system did not change over and i can not find the new ubuntu on my system any were ??

How did you download it?

The best way to update is to just run the Update Manager: System > Administration > Update Manager. If there's a new stable version available, and you have "Show normal releases" set in Software Sources, then you'll see a message at the top of the window saying that there's a new release. You can upgrade to it by clicking the button next to the message.

If you've downloaded a new .iso disk image of the Desktop CD, then you can't perform an in-place upgrade with this disc. You can do a fresh install of Ubuntu onto the partition without destroying your /home - this requires burning the disk image to a CD, booting up from it, and using the "Manual" partitioning method in the installer.

If you've downloaded a new .iso disk image of the **Alternate** CD, then there's a little script in the root of the disc called "cdromupgrade". Burn the image to disc, open a terminal, and run the "cdromupgrade" program as root to begin.

---

### Post by pat boy on 2009-08-11
i went to the update bit and try to down load but this comes up 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and when i try the run it , it  come up  

dpkg: requested operation requires superuser privilege


what do i do now ?

---

### Post by pat boy on 2009-08-11
i am down loading a clinet for the online game war of dragons . com :)

Legend: Legacy Of The Dragons this is the games name 

i have done all the updates now and it is will not work , still have same error report , but this time a wine sign come up . but it still does not work ?????

---

### Post by 3rdalbum on 2009-08-12
[QUOTE=pat boy]can you help me some more plz[/QUOTE]

The error message given by the package manager is actually a little incorrect. You need to type:

```
sudo dpkg --configure -a
```

in the terminal. Don't close your package manager or terminal window when it's adding or removing packages, or you'll get that error message.

If your terminal window brings up a Java license agreement screen, you need to press Tab in order to highlight the "I Agree" button, and then press Enter.

Also, about the game. Wine HQ has no information about it. I've barely used Wine so I don't know much more than you do about tracking down and fixing application compatibility problems. It looks like this is going to be one of those programs that Wine won't run.

Wine is an amazing project; it's amazing it works so well. But, from the official statistics, it works perfectly with less than 50% of tested programs. In reality, less than 50% of programs will work AT ALL with Wine.

---

### Post by Mark Phelps on 2009-08-12
> **3rdalbum said:**
>  ... In reality, less than 50% of programs will work AT ALL with Wine.

+1 on this!  

Actually, my own Wine experience (admittedly over a year ago, so things might have improved since) is that 100% of the programs I tried would not work!  A few weeks ago, I downloaded the CrossOver trial to test out IE7 and IE8 -- again, 100% failure of the apps.  So, given that there is no report on the CodeWeavers site for your game, it's most likely that it will NOT work.

---

### Post by pat boy on 2009-08-12
is there any thing i can use to get it to work ?? 

plz i need to make it run it is very important

---

### Post by Mark Phelps on 2009-08-13
> **pat boy said:**
> is there any thing i can use to get it to work ?? 
As I already said, there are no reports at the CodeWeavers site of anyone being able to get this to work with Wine.  So, unless someone here has been successful, you're out of luck.

You could install Virtualbox, and then a copy of MS Windows, and then install the game there ... but there's no guarantee that will work, and since 3D acceleration is not well supported in the virtual environment, if the game DOES work, it's likely to be so slow as to be useless.

You could also go to CodeWeavers and purchase one of their commercial emulation products.  Those seem to have more success than Wine.  But again, there is no guarantee that your game will work there, either.

>  plz i need to make it run it is very important
Then you need to go back to MS Windows and run the game there. That's the only place where MS Windows stuff is guaranteed to work.

---

