---
title: "Desktop effects can not be enabled"
date: 2008-07-26
forum: General Help
---

### Post by erans on 2008-07-26
I get that error when I try to enable normal visual effects. I don't know what's up because the first time I installed Ubuntu, they worked fine and were on by default. When I formatted and reinstalled, no dice. 

Here's the output for Compiz: 
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

---

### Post by Rocket2DMn on 2008-07-26
Moved to Desktop Effects & Customization forum.

I suggest having a look at the compiz-check script - [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Other users will be happy to help you out, but you will need to tell them what video card you are using, so please post the output of
```
lspci | grep VGA
```

---

### Post by erans on 2008-07-26
Sure. I forgot to mention I have an ATI Radeon 9200 SE on this machine. That command gives the following error: ```
bash: lscpi: command not found

```

---

### Post by Kevbert on 2008-07-26
Syntax error, should read
```
lspci
```
List PCI devices.
It's probably the display driver that you need to change.

---

### Post by erans on 2008-07-26
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

``` is what I get from that command. 

AFAIK, the only driver I can use with this card is the one that comes with Ubuntu because of its age.

---

### Post by Saint Angeles on 2008-07-26
heya! check out the link in my sig. its a way to make sure the proprietary ATI driver (fglrx) is working correctly.

---

### Post by Rocket2DMn on 2008-07-26
Ugh, typo on that command, sorry.  I fixed it in my original post.

Do not use the fglrx drivers suggested in post 6, your card is too old to support those.  Your card uses the open source drivers, which are installed by default.

---

### Post by Kevbert on 2008-07-26
I have a Radeon (RV250) 9000 in my laptop.  Do not use the fglrx drivers as you'll end up at a $ prompt.  On it I have Xubuntu 8.0.4.1 (no driver is mentioned in xorg.conf) and using
lsmod
in terminal is says it's using the "radeon" driver (compiz does not work, but may be a settings problem).  I also have Ubuntu 7.10 which is using the "ati" driver (in xorg.conf) and compiz works fine.
Hope this is of use.

---

### Post by Rocket2DMn on 2008-07-26
Hi Kevbert, read here for enabling compiz on your card - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by erans on 2008-07-26
So this has nothing to do with the "XGL not found?" I was thinking I might need to install some of those things, but I'm not sure which ones. Thought there would be more clues in the compiz output. This is an annoying problem because the effects WORKED the first time I installed Ubuntu.

---

### Post by Rocket2DMn on 2008-07-26
erans, not having xgl shouldn't be a problem by itself, there are different methods available to allow compiz to work.  If you are still having trouble, I suggest reinstalling compiz
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```

---

### Post by Kevbert on 2008-07-27
Thanks Rocket2DMn.  Since compiz has been upgraded the problem with using it has occurred (probably due to blacklisting my card).  The old configuration works fine on 7.10 but not in 8.0.4.1.  Thanks to your other post it now works in 8.0.4.1 (Xubuntu).  Now all I need to do is to get Emerald to work.
One other question.  Does this now mean that compiz will work on Via S3 and S9 cards (as they don't support 3d graphics acceleration) ?

---

### Post by Rocket2DMn on 2008-07-27
That is correct, those Via cards will not work with Compiz.  I posted a link on page 1 that tells you how to get around the blacklist for the open source drivers if that is still a problem for you.

---

### Post by erans on 2008-07-27
> **Rocket2DMn said:**
> erans, not having xgl shouldn't be a problem by itself, there are different methods available to allow compiz to work.  If you are still having trouble, I suggest reinstalling compiz
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```

I tried this. Still doesn't work. :(

Any other ideas?

---

### Post by Rocket2DMn on 2008-07-27
> **erans said:**
> I tried this. Still doesn't work. :(

Any other ideas?

I'm afraid not.  A number of users have had trouble getting their older ati cards to work, despite the existence of the workaround I posted on a thread I linked to earlier.  Since cards that use the open source ati drivers are not officially supported by compiz, there isn't much we can do there either.  I believe they are working on re-supporting these cards in future releases, though I'm not sure when.  Everybody's problem seems to be a little different, so since I am out of ideas, I suggest using the forum search function to see if anybody else has had this problem with your model video card - I'm sure you'll at least get some hits, but no guarantees on successful fixes.

---

### Post by erans on 2008-07-27
Alrighty, thanks! I feel like there is a solution to this problem because (as I said), these effects worked previously. Hopefully I'll find it.

---

