---
title: "Synaptic doesn't show new packages on reload"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by stringkarma on 2009-04-15
I just added the partner repo to jaunty to install acroread and synaptic still doesn't show that the package is available, even after INSTALLING acroread via apt-get at the command line.

Does anyone have any idea why synaptic will not update its package lists?

---

### Post by stringkarma on 2009-04-15
Ok so after some more reading of old threads I see that the package is actually in the list but ...

1) doesn't show up in quick search
2) doesn't show up in search
3) the partner repo doesn't appear in the origin filters list

My new question I guess is: How can I get Synaptic to fully refresh itself upon adding a repository?

---

### Post by ahbart on 2009-04-15
Never head of that. have you pressed reload in synaptic? What package are you looking for?

---

### Post by stringkarma on 2009-04-15
Reload doesn't do anything but check the repos, I need it to refresh itself somehow.

I am getting acroread for 32bit (64bit comes from medibuntu rather than partner)

---

### Post by ahbart on 2009-04-15
Aah. Now we are getting somewhere! 
you can not install acroread 32bit via synaptic. You have to use the command line for that (as far as I know). And give apt-get an force architecture option somehow.

edit: But why? Why do you want to install a 32bit version of acroread? No reason for that my opinion!

---

### Post by stringkarma on 2009-04-15
Sorry I should say I am doing this on a 32 bit computer, for a co-worker. He is trying linux for the first time, so I want everything to "just work" as much as possible for him.

Also you will notice that I did install acroread (32) for him (from partner repo) its just that little quirk with synaptic that I am asking about.

---

### Post by ahbart on 2009-04-15
So, he/she has a 32bit ubuntu system. You've added the repository. You installed acroread via command line. But you don't see acroread in synaptic.

Personally I like Evince (standard viewer in Ubuntu) much more that package proprietary acroread. If you did install via apt-get or aptitude and not via a dowloaded file, it should be visible in synaptic too. Haven't you set any filters or something?

---

### Post by Rook777 on 2009-04-25
Try running this in terminal:

	sudo update-apt-xapian-index 

I had the same problem.  This fixed it.  However, every time you add a repository, you have to run this command again...

---

