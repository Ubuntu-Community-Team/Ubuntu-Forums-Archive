---
title: "Printer automatically scaling everything I print?"
date: 2020-07-21
forum: Hardware
---

### Post by chrysanthemum2 on 2020-07-21
I have an Epson WF-2630 printer connected via wifi which has been working fine with Ubuntu for years but just this last couple of days I noticed it's not printing to the size I tell it to. For example, I print a picture using GIMP (as I have done a million times before) which is 27cm tall, but it prints only 26cm tall. No matter what I scale the image to in GIMP, the printed image always ends up being a certain percentage smaller (approx. 10% but not totally sure or I'd just cancel it out by printing larger!) .

Here's what I've tried so far:
* Restarting computer
* Restarting printer
* Uninstalling and Reinstalling printer drivers
* Using another programme instead of GIMP
* Trying any other image
* Using different connection methods (IPP)
* Trying 'ignore page margins'

Any ideas what an earth is going on? Has there been a recent update which has broken something or changed a setting somewhere?

---

### Post by CatKiller on 2020-07-21
The thing that you haven't said you've looked at, which is where I'd expect the issue to be, is the page margins.

---

### Post by chrysanthemum2 on 2020-07-21
> **CatKiller said:**
> The thing that you haven't said you've looked at, which is where I'd expect the issue to be, is the page margins.

Clicking on 'ignore page margins' makes no difference. Is there other settings?

---

### Post by pqwoerituytrueiwoq on 2020-07-21
[https://imgur.com/vDeBhYX.png](https://imgur.com/vDeBhYX.png) (bottom left, this setting is remembered for next time)
edit: why is this set to 9 per side...

edit: also see printer options
[https://imgur.com/vDeBhYX.png](https://imgur.com/vDeBhYX.png)

---

### Post by chrysanthemum2 on 2020-07-22
> **pqwoerituytrueiwoq said:**
> [https://imgur.com/vDeBhYX.png](https://imgur.com/vDeBhYX.png) (bottom left, this setting is remembered for next time)
edit: why is this set to 9 per side...

edit: also see printer options
[https://imgur.com/vDeBhYX.png](https://imgur.com/vDeBhYX.png)

Here's mine, it all seems as it should be (however I have one less tab for some reason):
[https://i.imgur.com/PpAzaAP.png](https://i.imgur.com/PpAzaAP.png)

You used the word also... did you mean to post the same link twice?

---

### Post by chrysanthemum2 on 2020-07-22
Update with another thing tried, which gave a weird result but might provide clues...

I printed the image scaled to 1cm larger, to try and counter-act this scaling problem, and it instead printed fine to this new size. But printing to the size of the image still scales it down. It seems scaling it up overrides something. 
However, when I scaled the image to an arbitrary small amount larger (x0.5mm) in order to get the same override, it still scales smaller.

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2020-07-22
> **chrysanthemum2 said:**
> Here's mine, it all seems as it should be (however I have one less tab for some reason):
[https://i.imgur.com/PpAzaAP.png](https://i.imgur.com/PpAzaAP.png)

You used the word also... did you mean to post the same link twice?
yep i did post the same link by mistake
[https://imgur.com/iPWJmyd.png](https://imgur.com/iPWJmyd.png)

---

### Post by chrysanthemum2 on 2020-07-22
> **pqwoerituytrueiwoq said:**
> yep i did post the same link by mistake
[https://imgur.com/iPWJmyd.png](https://imgur.com/iPWJmyd.png)

Ah, thanks. Here's my version. Looks the same, and most importantly, 100% scaling.
[https://i.imgur.com/imMUc2l.png](https://i.imgur.com/imMUc2l.png)

---

