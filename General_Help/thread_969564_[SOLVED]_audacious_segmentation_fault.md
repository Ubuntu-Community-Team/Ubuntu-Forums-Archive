---
title: "[SOLVED] audacious: segmentation fault"
date: 2008-11-03
forum: General Help
---

### Post by jesuisbenjamin on 2008-11-03
Hello Forum!):P

Since a short time Audacious is giving me some attitude and shuts down when opening a new (stream)file, or simply doesn't start up.
Running 'audacious' in terminal returns: 'segmentation fault'.

I use ubuntu 8.4

Anyone could help with this?
Thanks.

---

### Post by quonsar on 2008-11-03
same here. i have a nautilus action set up to open folders in audacious by calling audacious %M. this worked without fail in 8.04 but since upgrade to 8.10 i get segfault.

---

### Post by jesuisbenjamin on 2008-11-08
Audacious is not even opening anymore :(

Could anyone help me please? What to do?

---

### Post by quonsar on 2008-11-08
there is a proposed upgrade in the intrepid-proposed repository which solved my problems with audacious. go to system | administration | software sources | updates and check the box marked intrepid-proposed to get it. or just wait a few days!

---

### Post by NIT006.5 on 2008-11-08
> **quonsar said:**
> there is a proposed upgrade in the intrepid-proposed repository which solved my problems with audacious. go to system | administration | software sources | updates and check the box marked intrepid-proposed to get it. or just wait a few days!

I've upgraded to Intrepid, installed the latest Audacious and I'm still getting the same problem. Removed the .audacious directory from my home directory, in case it was something to do with settings within my profile, but that made no difference either.

---

### Post by NIT006.5 on 2008-11-08
> **jesuisbenjamin said:**
> ...Running 'audacious' in terminal returns: 'segmentation fault'...

Aha! Ok, I just did:

sudo apt-get purge audacious
sudo apt-get install audacious

And it is now running. It could have something to do with the cross-fade package or another plugin that was installed?

---

### Post by jesuisbenjamin on 2008-11-08
Well i did the purge and reinstall but it doesn't work.
I am not using Intrepid but Hardy... why would the problem suddenly arise anyway?

---

### Post by jesuisbenjamin on 2008-11-11
bump!

---

### Post by jesuisbenjamin on 2008-11-15
Solved by upgrading to 8.10

---

### Post by bodhi.zazen on 2008-11-21
Hmmm ... I just ran into this problem in 8.10

I found a lot of bug reports implicating crossfade :

[https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208425](https://bugs.launchpad.net/ubuntu/+source/xmms-crossfade/+bug/208425)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=491615](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=491615)

But I do not have that plug in installed :(

My solution was to delete the directory ~/.config/audacious

HTH, (Just posting on this thread as it was one of the top threads on a google search.

---

### Post by Ivo Moelans on 2008-11-21
This didn't solve it for me. Neither did removing ~/.local/share/audacious/ and/or ~/local/share/applications/audacious/. Strange however: the last two directories are identical. They both contain the subdirectories Plugins and Skins.
I also don't have the crossfade plugin installed.

Edit:

Had the crossfade plugin installed after all. Found it by looking with Synaptic Package Manager (audacious-crossfade). After removing with SPM audacious started up.

---

### Post by MttJocy on 2008-12-14
I can confirm that the removal of the ~/.config/audacious directory worked for me as well on 8.10 thank you bodhi.zazen for your post was nice to resolve the issue so quickly.

Anyone who is having the same problem on ubuntu 8.10 should try the command bellow:

```
rm -rf ~/.config/audacious
```

That will delete your old configuration file and allow audacious to start up normally.

---

