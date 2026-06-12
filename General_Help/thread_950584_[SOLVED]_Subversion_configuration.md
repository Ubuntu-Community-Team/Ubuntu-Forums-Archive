---
title: "[SOLVED] Subversion configuration"
date: 2008-10-17
forum: General Help
---

### Post by porchrat on 2008-10-17
OK I've been googling for a while now and haven't found anything regarding how I move subversion's repository.  Do I edit that /etc/subversion/servers file?  If so can anyone point me to a guide I can follow as that file is REALLY confusing.

If not can someone please let me know how to do it, or point me towards a guide that can show me?

EDIT: Nevermind I've just found some literature on it.  Thanks anyway

---

### Post by ingo on 2008-10-23
Well, don't keep it all to yourself :)

I've just installed subversion and am facing the same brick wall you seem to have broken through - so I (and I bet others) would be very grateful a link to that documentation or even better a tiny howto ;)

Cheers

---

### Post by porchrat on 2008-10-24
it turns out the repository is self-contained you can perform a simple "mv" command on the darn thing and then as long as you rename the URL you use in your client to reflect the correct location it just works.  Woot.

For example if you have a repository in /svn/foo and want it in /bar/foo you just run:

```
mv /svn/foo /bar/foo
```

Add sudo if and when required.

Then (if you run Rapidsvn like I do) change your repository URL to match the new location of your repository (on the server) in your client, or if you merely use the svn command line tools then you don't even need to bother.

Please note that you need to move the ENTIRE repository directory and all subdirectories including the db, hooks, locks, dav and conf subdirectories.  You also need the format directory as that tells it whether the repository is BerkleyDB or fsfs.

Found most of this in the book "Version Control with Subversion" you can get it from [here]("http://svnbook.red-bean.com/")

It takes a LONG time to get to the point, but as long as you skim to the important bits then it is quite useful, covers pretty much everything I needed to know about subversion.

Hope it helps.

---

