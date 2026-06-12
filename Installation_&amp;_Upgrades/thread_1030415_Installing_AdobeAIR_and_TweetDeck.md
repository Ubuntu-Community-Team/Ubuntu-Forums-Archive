---
title: "Installing AdobeAIR and TweetDeck"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Tchaguito on 2009-01-04
I am trying to set up a Twitter reader in my PC, namely TweetDeck. But it says I have to install Adobe AIR first, which is a .bin file, which I can't seem to able to open. Do I need a .bin reader? How do I download one?

Please bear with me, I am an absolute beginner with Ubuntu!

---

### Post by tosh54 on 2009-01-04
You have to make the .bin executable. To do this open a terminal and type

chmod +x AdobeAIRInstaller.bin

and than to launch the installer type

sudo ./AdobeAIRInstaller.bin

Regards, Peter

---

### Post by GJCT on 2009-04-13
I tried doing the above and I got "no such file or directory". The .bin file is on my desktop - should it be somewhere else for it to be accessed?

---

### Post by xpan on 2009-04-23
Hi, I have exactly the same problem... any solutions to it, yet?

---

### Post by vvo3v on 2009-04-23
try doing cd Desktop first then following the directions above

---

### Post by xpan on 2009-04-24
> **vvo3v said:**
> try doing cd Desktop first then following the directions above

Thanks. I found out that the problem was with the version of Ubuntu I use (64bit). It seems that Adobe AIR is aimed at 32bit versions at the moment.

This is the solution I have found:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

However I couldn't manage to run TweetDeck (it starts but displays a black screen), I managed to run Twhirl which is equivalent.

---

### Post by PendragonUK on 2009-04-24
It would be real nice if this was in the repo's

---

### Post by madverb on 2009-04-24
Step 1: [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

Step 2: [http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

---

### Post by xpan on 2009-04-25
> **madverb said:**
> Step 1: [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

Step 2: [http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

Thanks. It worked! However Twhirl doesn't need to download all those libraries and I had just started to get used to it!

Thanks again!

---

### Post by Insane_Homer on 2009-04-25
> **madverb said:**
> Step 1: [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

Step 2: [http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

thanks! needed that 2nd link to get Tweekdeck working on my x64 install.

:KS

---

