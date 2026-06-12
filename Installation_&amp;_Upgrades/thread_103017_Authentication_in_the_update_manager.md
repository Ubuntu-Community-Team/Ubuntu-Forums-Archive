---
title: "Authentication in the update manager"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by ianpeters on 2005-12-13
Hello folks!

My successful Breezy upgrade rendered the Update Manager crippled. It won't update stuff because the authentication signatures don't match, at least that's what it says. Any thoughts on how to resolve this? I tried the default option thingy but that didn't work. Thank you!!

---

### Post by ianpeters on 2005-12-15
OK, kinda bumping this one....please help!

---

### Post by nocturn on 2005-12-16
I went through the same thing, as did many others here.  
I'm still unsure about the cause, but it has something to do with the mirrors.

Are you comfortable with the command line?  If so, this will help...

```

sudo -s
cd /etc/apt
cp sources.list sources.list.saved
echo "" > sources.list
aptitude update
cp sources.list.saved sources.list
aptitude update

```

That shoud do it...

---

### Post by ianpeters on 2005-12-17
[QUOTE=nocturn]I went through the same thing, as did many others here.  
I'm still unsure about the cause, but it has something to do with the mirrors.

Are you comfortable with the command line?  If so, this will help...

```

sudo -s
cd /etc/apt
cp sources.list sources.list.saved
echo "" > sources.list
aptitude update
cp sources.list.saved sources.list
aptitude update

```

That shoud do it...[/QUOTE]

Hmmm, not sure how this is supposed to help but sure I can try that. I've updated the apt repositories numerous times with apt-get but sure, I can try this as well. I will let you know.

---

### Post by ianpeters on 2005-12-18
[QUOTE=nocturn]I went through the same thing, as did many others here.  
I'm still unsure about the cause, but it has something to do with the mirrors.

Are you comfortable with the command line?  If so, this will help...

```

sudo -s
cd /etc/apt
cp sources.list sources.list.saved
echo "" > sources.list
aptitude update
cp sources.list.saved sources.list
aptitude update

```

That shoud do it...[/QUOTE]

Thanks for the tip, although I'm not sure if it solved the problem. I have to press the Install-button numerous times before it begins to download and install. 
What happens first is that the Download dialogue pops up and quickly disappears again. After about the fifth time or so or even after a restart of the Updatemanager, it starts working.
Is it broken or what's the problem here?

---

