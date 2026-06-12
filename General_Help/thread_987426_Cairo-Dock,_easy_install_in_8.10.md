---
title: "Cairo-Dock, easy install in 8.10"
date: 2008-11-19
forum: General Help
---

### Post by Tex786 on 2008-11-19
Cairo-Dock, If I can't get it i'am going back to Hardy!

Please teach me how to get it in 8.10 with everything explained in detail..

---

### Post by sirjoebob on 2008-11-19
holding your computer hostage is not an effective solution... lol. 

I did not like the performance of cairo-dock so I have not messed with it in a long time. I use AWN and it works great. Perhaps somone else will have a good solution for you.

---

### Post by andrewabc on 2008-11-19
Read through
[http://ubuntuforums.org/showthread.php?t=983396](http://ubuntuforums.org/showthread.php?t=983396)

basically you have to enable cairo-dock repository. Although we have yet to figure out why it is not possible to change "views".

---

### Post by binbash on 2008-11-19
you will just go to the official site and download 2 debs (cairo dock and plugins deb).That is all

---

### Post by Tex786 on 2008-11-19
> **sirjoebob said:**
> holding your computer hostage is not an effective solution... lol. 

I did not like the performance of cairo-dock so I have not messed with it in a long time. I use AWN and it works great. Perhaps somone else will have a good solution for you.


does avant work that well in 8.10?

---

### Post by sirjoebob on 2008-11-19
> **Tex786 said:**
> does avant work that well in 8.10?

I use it all day every day without issue. Mine runs like a Mac dock and looks brilliant! Check my screenshot. It is very easy to install and customize and definitely is my favorite dock ATM.

---

### Post by vgrisham on 2008-11-24
> **Tex786 said:**
> does avant work that well in 8.10?

It works great on Intrepid unless you have an nvidia graphics card. If you do, there are some weird rendering issues that are coming up but the dock is still functional.

---

### Post by sirjoebob on 2008-11-24
> **vgrisham said:**
> It works great on Intrepid unless you have an nvidia graphics card. If you do, there are some weird rendering issues that are coming up but the dock is still functional.

REALLY???? I am running a Dell Vostro 1500 with Nvidia graphics card with NO issues with the dock whatsoever. Runs wonderfully for me and has been easy to customize. Make sure you are running the newest restricted drivers b/c I have had no issues... see the screenshot above.

---

### Post by vgrisham on 2008-11-24
> **sirjoebob said:**
> REALLY???? I am running a Dell Vostro 1500 with Nvidia graphics card with NO issues with the dock whatsoever. Runs wonderfully for me and has been easy to customize. Make sure you are running the newest restricted drivers b/c I have had no issues... see the screenshot above.

Yep. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=762363&page=50&highlight=cairo+dock") and the embedded bug report link. 

AWN works great on my laptop but is giving me fits on my desktop which is running an nvidia card.

---

### Post by sirjoebob on 2008-11-24
Ah, I did have a similar issue but only when I enabled the weather plugin. If you don't use a lot of the apps, you may not have an issue. Mine is running great and I am using the Nvidia restricted driver from Ubuntu.

---

### Post by vgrisham on 2008-11-24
> **sirjoebob said:**
> Ah, I did have a similar issue but only when I enabled the weather plugin. If you don't use a lot of the apps, you may not have an issue. Mine is running great and I am using the Nvidia restricted driver from Ubuntu.

It was working great until the upgrade to Intrepid. I didn't have any such issues in Hardy and I had the same driver. To complicate things further, there is a new driver that seems to resolve the issue *if* one has a newer nvidia card. Mine is about 18 months old and is apparently not going to be getting access to the new restricted driver. 

But, I'm leading this thread off-topic. Cairo-Dock looks pretty nice and I may try it on my desktop until my AWN problem clears up (or until I take a hammer to my nvidia g7600).

---

### Post by sirjoebob on 2008-11-24
I'm in intrepid with no issue. Perhaps I have the new driver. ENVY may help you get newer drivers than restricted manager but I have not used it in some time and can't say how good it is now.

---

### Post by loomsen on 2008-11-24
> **vgrisham said:**
> It was working great until the upgrade to Intrepid. I didn't have any such issues in Hardy and I had the same driver. To complicate things further, there is a new driver that seems to resolve the issue *if* one has a newer nvidia card. Mine is about 18 months old and is apparently not going to be getting access to the new restricted driver. 

But, I'm leading this thread off-topic. Cairo-Dock looks pretty nice and I may try it on my desktop until my AWN problem clears up (or until I take a hammer to my nvidia g7600).

Once more I point to my signature... The newest driver will work with your card. But, well, stop. Which one do you assume is the newest?

I'm running 180.08 atm with a custom Modeline for reduced blanking and one for composite. Both working well. I've tried 173.* too, as well as 177.* The beta driver tho, once again, fixed it for me.

You should be aware that, if you wanna run on the cutting edge, you probably WILL get cut here n there. So you should be able to fix some bugs yourself. Otherwise stick with hardy and wait.

*LOL* just noticed the packages in the repos are the ones I build :D Then I think I'll skip rebuilding them this time ^^

---

