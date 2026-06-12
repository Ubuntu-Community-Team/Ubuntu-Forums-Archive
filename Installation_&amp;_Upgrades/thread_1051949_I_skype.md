---
title: "I skype"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by sarma_men on 2009-01-27
I wanted to install skype. And now I have problem, and i can't solve it.
help:(

[LINK]("http://img149.imageshack.us/img149/9355/problemag3.jpg")

---

### Post by taurus on 2009-01-27
From the error message, there is something wrong with your /etc/apt/sources.list.d/medibuntu.list!  Open a terminal and post your /etc/apt/sources.list.d/medibuntu.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list.d/medibuntu.list
```
I get a feeling that you were trying to add a repo to /etc/apt/sources.list.d/medibuntu.list but somehow screwed it up.

---

### Post by sarma_men on 2009-01-27
I installed ubuntu 10 minutes ago.. and I dont understend anything :( this is probebly not a big problem. I did instructions as you sad and nothing happines

---

### Post by sarma_men on 2009-01-27
now I got this

[LINK]("http://img407.imageshack.us/img407/1917/screenshotkr2.png")

---

### Post by clueless on 2009-01-27
What version of ubuntu have you installed?

You can find out by typing in the terminal:

```
lsb_release -a
```

---

### Post by taurus on 2009-01-27
Are you still running feisty?

---

### Post by sarma_men on 2009-01-27
version: ubuntu 8.10

and what is "feisty"? :(:(

---

### Post by taurus on 2009-01-27
Feisty is an old release.  That's what it said in your second pic.

Open a terminal and run these (copy one line and paste it in your terminal at a time).

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install skype
```

---

### Post by clueless on 2009-01-27
Then you where using a source for a previous version...
You could try first removing the previous medibuntu entry:
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

and then add the correct source:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

add the GPG key:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

and finally install skype:
```
sudo apt-get install skype
```

---

### Post by clueless on 2009-01-27
Alright taurus was quicker than me, I'm glad we're saying the same thing thought!
:D

---

### Post by sarma_men on 2009-01-27
it is working now. thanks ;)

---

### Post by taurus on 2009-01-27
> **clueless said:**
> Alright taurus was quicker than me, I'm glad we're saying the same thing thought!
:D

So if we're both saying the same thing, it must be true then (probably)!  ;)

---

### Post by clueless on 2009-01-27
Well it worked! We were either right or got inexplicably lucky... I tend to think it's the first one.
:)

---

